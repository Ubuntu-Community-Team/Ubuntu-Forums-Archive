---
title: "Installing Compiz - My experience"
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by lduplantie on 2008-02-02
Hello to all,

I have decided to document how I managed to install compiz with Ubuntu Gutsy Gibbon.

Its a bit convoluted, probably because I am new to Linux world and Ubuntu, but in the end it worked.

Hardware:
P3 1GHz, 512 MB RAM, 20 GB HDD, Nvidia Quadro2 32MB, Viewsonic VA520 15" LCD
OS
Ubuntu 7.10 Gutsy Gibbon

Procedure:
1. Activate 3D acceleration proprietary drivers for the graphic card. I got a message that desktop effects cannot be enabled. I executed compiz from a terminal. The message essentially says that I have not installed Xgl and that the card has less than 64MB memory, hence reverting to metacity (default gnome desktop manager).
2. Installed xserver-xgl; I found these instructions in a post.
First uninstall nvidia-glx and nvidia-kernel-common. I used Synaptics for this.
Then, in a terminal type in these commands:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get remove xorg-common
sudo apt-get install xserver-xorg
```
Then re-install the nvidia drivers
```
sudo apt-get install nvidia-kernel-common nvidia-glx
```
Compiz now works but the window frames disappeared (Title bar, etc)
3. Install compizconfig-settings-manager from Synaptic
4. From the menu launch System>Preferences>Advanced Desktop Effects Settings (sorry my translation I have my OS in French). Select the Window Decoration plugin. and in the command line type in "gtk-window-decorator --replace"
5. Modify the xorg.con file (again found in another post)
```
sudo nvidia-xconfig --composite
sudo nvidia-xconfig --render-accel
sudo nvidia-xconfig --allow-glx-with-composite
sudo nvidia-xconfig --add-argb-glx-visuals
```
6. Install the compiz-fusion icon (for some reason compiz refuses to start from a command "compiz" in the Terminal but it does using this applet)
Download and install package "fusion-icon-HEAD.tar.gz" go to:
[http://gitweb.opencompositing.org/?p=users/crdlb/fusion-icon;a=snapshot;h=HEAD;sf=tgz](http://gitweb.opencompositing.org/?p=users/crdlb/fusion-icon;a=snapshot;h=HEAD;sf=tgz)
Once it's downloaded, install it by entering these commands into a console window:
```
tar -zxvf fusion-icon-HEAD.tar.gz
cd fusion-icon
make install
```
You can find it in the menu from Applications->System Tools->Compiz Fusion Icon.

Compiz should be fully operational (Cube, etc.)

However, I noticed that menus in OpenOffice when launched in metacity are very slow. 
I uninstalled xsever-xgl using synaptics. The speed in back to normal.

I hope this help

---

### Post by jan quark on 2008-02-02
please post guides under the adequate section tutorials and tips 
thank you

---

