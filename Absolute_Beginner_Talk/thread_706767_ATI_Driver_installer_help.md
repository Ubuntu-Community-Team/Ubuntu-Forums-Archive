---
title: "ATI Driver installer help"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by alever on 2008-02-24
I am really really confused.  I just successfully installed Ubuntu 7.10 today and ran all of the updates.  I am brand new to linux and have no idea what I am doing.  Now I am trying to install the drivers for my ATI Radeon X850 and am completely lost.

I downloaded the file ati-driver-installer-8-02-x86.x86_64.run from ati.com to my desktop.

Now I have no idea what to do with it.  I read through the forums and there is plenty of instructions on what to do, but none of it makes sense to me.  Can someone please please please give me exact step by step instructions that a total linux newbie can understand.

fyi...i tried installing the card using the restricted drivers and ended up with the black screen problem.

---

### Post by aktiwers on 2008-02-24
You could use Envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

It does it automatically for you.


To install Manually from the file you downloaded, do this.
Log out.
Hit CTRL+ALT+F1
Log in there.

Type:
Go to Desktop:
```
cd Desktop
```
Stop GDM:
```
sudo /etc/init.d/gdm stop
```
Make the file executable:
```
sudo chmod +x  ati-driver-installer-8-02-x86.x86_64.run
```
Run the file:
```
sudo ./ati-driver-installer-8-02-x86.x86_64.run
```And when done.. type:
```
sudo reboot
```
To reboot..  Now youre done!

---

