---
title: "Tried to reinstall Breezy 5.10"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by rmaier on 2006-06-21
](*,) I decided to upgrade to the new 6.06. When I did I lost the internet connection. I tried to reinstall the Breezy 5.10. When I tried to reboot I got the following error.

I get an error that says Failed to start X Server your prahphical interface. It is likely that it is not set up correctly. Would you like to view the x server output to diagnose the problem. select YES

X window sys V 7.0.0
Release Date: 21 Dec 2005
X Protocol Version II, Revision 0 Release 7.0
Build Operating System Linuz 2.6.12 i686
Curent Operating Sys: Linux ubuntu 2.6.15-23-386 #1 Preemp
May 23 13.49:40 UTC 2006 i686
X server is now disabled
Restart GDM when configured correctly

Fail to initialize core devices
GLcore - module failed

xf86 open serial

then it goes to a command asking for user name: typed user
password requested: typed password

Ubuntu 6.06 LTS ubuntu ttyl

command line user@ubuntu: "$

have tried several words on the command like run, load, install, etc. but no success. 

To send and receive email messages I have to go to a friends house to get on their computer, take the directions and go back to my house to try them on my computer. 

Thanks for your help.

---

### Post by Winblowz on 2006-06-21
Well do you have the drivers for your video card installed and setup correctly? Have you tried-
```
sudo dpkg-reconfigure xserver-xorg
```
After you do that command, test out X to see if it's working correctly by doing-
```
startx
```
If none of this helps out, then post back and we'll try something else:wink:

---

### Post by rmaier on 2006-06-21
i did the reconfigure code and got a message that i need to choose a video card driver, it gives 30 choices 

apm
s3virge
voodoo
trident
cirrus
i740
 and  etc.     any idea which one to choose?

just on a guess, I entered voodoo....then i got a message to choose an identifier for the driver, a vendor name or a brand name....

thanks.

---

