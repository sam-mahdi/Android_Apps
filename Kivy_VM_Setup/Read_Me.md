How to setup Linux VM for Kivy app development


I'm making this because the kivy docs are outdated and misleading. It took me quite a bit of time of googling, looking up github errors, rabbit holes to nowhere, till I was able to get kivy finally working. I'm also making this just for me in case I come back later and forget how to set it all up. 

This is just a resource page (thus, sites posted may be outdated). 

1) Download VirtualBox: https://www.virtualbox.org/wiki/Downloads
2) Download your IOS. I'm using Ubuntu so: https://ubuntu.com/download/desktop (this is quite large, downloading will take sometime)
You may use https://brb.nci.nih.gov/seqtools/installUbuntu.html for setting up Ubuntu details
3) Open VirtualBox, and choose the setup you desire (For Ubuntu, you can pick Linux and Ubuntu-x64) and pick the IOS you just downloaded
4) Most of the options you can pick the default, however I found I required at least 20+ GB to be able to download all the depencies, the IDE, etc.
5) Make sure when you've set everything up, and you've shut down your VM. Go to the settings of your VM, in System make sure to turn off Optical (otherwise the next time you boot it will try and setup again)
6) The first thing you might want to do is change your screen resolution (I can't work with a tiny screen).
Follow the answers in this link to get the resolution you wish: https://askubuntu.com/questions/377937/how-do-i-set-a-custom-resolution
```
If link problem, type: cvt width height refreshrate 
Then go to text editor:
#!/bin/sh
xrandr --newmode (cvt output)
xrandr --addmode Virtual1 ("cvtoutput")
I.E.
#!/bin/sh
xrandr --newmode "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync  
xrandr --addmode Virtual1 1680x1050_60.00
```
7) Python3 comes pre-installed. However you will need to install everything else. First install pip :https://linuxize.com/post/how-to-install-pip-on-ubuntu-18.04/
```
If link outdated:
sudo apt update 
sudo apt install python3-pip
```
8) Kivy requires a number of dependencies, use this site to get them: 
https://kivy.org/doc/stable/installation/installation-linux-venvs.html
```
To install, simply type: sudo apt-get (dependency)
I.E.
sudo apt-get build-essential
```
9) The stable kivy **does not work with Python 3.8**. There are a number of ways around this: 
https://stackoverflow.com/questions/59125232/how-to-deal-with-kivy-installing-error-in-python-3-8
I chose to install the rc version 2.0.0 you can install: 
```
python3 -m pip install kivy==2.0.0rc3
```
This will work with python3.8. If you wish you can use "pyenv" to install python3.7 instead and work with the stable kivy release. 

Additionally, rather than go through python-for-android (since that is the option on the page, and its still outdated) use buildozer: 
https://kivy.org/doc/stable-1.10.1/guide/packaging-android.html#packaging-your-application-into-apk
