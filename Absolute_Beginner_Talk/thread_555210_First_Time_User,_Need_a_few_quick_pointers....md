---
title: "First Time User, Need a few quick pointers..."
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by RedmondHater4Life on 2007-09-19
Not much for words, but like all of you i got sick & tired of Redmond's bs, so I grabbed Ubuntu last night, and from what i'v experienced in the first 24 hrs., ubuntu will stay installed. I only have one major issue and two or three small ones.

The major one is the whole mounting hard drives into ubuntu. Obviously, the disk where ubuntu is installed, but I wish to add a second hard drive that will be used for organizing my personal files and torrents. Now using gparted in sudo mode, I can unmount the drive to format it into a ext3 partition, but I can't remount it after the formatting is done. Furthermore, i'm still not confident enough to edit etc/fstab, my last attempt ended in a reinstall of ubuntu.

Also, seems that once in a while my soundcard will cease to work, leaving me a little frustrated ( i listen to music while I work) so any help there would be appreciated. Soundcard model: Intel ICH82801DB AC'97 Audio Controller.

Any pointers as to where I can find the drivers for the Intel Extreme Graphics 2 onboard video controller, cus I can't stand working in 1024x768 anymore :P

I think that's it, like I said, pretty new to this, and I am willing to learn, even if my fingers fall off and I end up typing with my elbows lol...

-RH4L

---

### Post by vincentvee on 2007-09-20
can't help you with the disk mount thing, haven't mounted anything except my primary partition for ages....just ask my wife

sound failure....open the terminal and type:

alsamixer

it's pretty much self explanatory after that

---

### Post by Jeroen Vernooij on 2007-09-20
Graphics driver:
Most probably you are using xserver-xorg-video-i810 while you can better use xserver-xorg-video-intel because it is newer and better.

Just install xserver-xorg-video-intel from synaptic package manager or commandline.
After that you need to edit your xorg.conf to use the new driver:
```
sudo gedit /etc/X11/xorg.conf
```
search for i810 and replace it with intel.

After a reboot or X-server restart (which you can do with CTRL-ALT-BACKSPACE: **make sure you've saved all open documents**) you can remove xserver-xorg-video-i810.

If you now don't get any resolution higher than 1024, reboot in Recovery mode and type 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
It asks a lot of questions, if you don't know the answers, just press enter. Just make sure you choose the Intel driver and not the i810.

Mount drive:
For this one we have the command 'mount'. It's complicated and I don't have much knowledge of it, but you can read the 'man' page:
[http://linux.die.net/man/8/mount](http://linux.die.net/man/8/mount)

---

