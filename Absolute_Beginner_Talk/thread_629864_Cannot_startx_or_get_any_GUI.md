---
title: "Cannot startx or get any GUI"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by xshagy on 2007-12-02
I'm new to ubuntu. I installed 7.10 webserver a couple times but i don't 
get any GUI. From what i've read here, i tried the following....

When I do startx, it gives me the error
x: cannot stat /etc/X11/x (no such file or directory), aborting
xinit: Server error

I tried sudo dpkg-reconfigure xserver-xorg and it gave me....
xserver-xorg not installed

I'm assuming i need to install xserver-xorg.  how do i do that and why 
wasn't it installed from the beginning? any help would be greatly 
appreciated, i'm confused.

i'm running a dual amd with a nvidia geforce6100.  I also tried an ati 
x1650 pro with the same results.

---

### Post by Dr Small on 2007-12-02
When you install a server, it doesn't come with a GUI.
You will need to install xorg:
```
sudo apt-get install xorg
```

---

### Post by xshagy on 2007-12-02
thanks for the quick response dr small
i installed xorg and then did startx again.  my terminal then showed up as a forth of my screen and the rest of the screen was just some weird brown shading.  my mouse showed up but typing and clicking did nothing.

i did sudo dpkg-reconfigure xserver-xorg
selected the nv driver, and tried startx again but got errors

I put an ati x1650pro card in and tried again. This time selecting the ati driver.  Tried startx again and this is what i got.......
(WW)RADEON: No matching device section for instance(BusID PCI:2:0:0) found
(WW)RADEON: No matching device section for instance(BusID PCI:2:0:1) found
(EE) No devices detected
Fatal server error
No screens found

What is it looking for?  The driver, the card, or my monitor?

I'm a beginner and I just want a webserver to play with and learn about.  should I just install apache and mysql on a desktop version of ubuntu?  Thanks.

---

### Post by louieb on 2007-12-02
What you just described is xorg without a window manager too:
The easiest way to go at this points is :
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install ubuntu-desktop 

```
then if want to install a LAMP server and didn't already
 [ApacheMySQLPHP - Community Ubuntu Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by xshagy on 2007-12-02
it's working!  the support on here is great.  thanks everyone that helps out us new guys (dr small & noe)

Here's what got it working for me

sudo apt-get install xorg
sudo dpkg-reconfigure xserver-xorg
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
sudo reboot
sudo apt-get install ubuntu-desktop

Now I have 7.10 server running with a GUI

The problem is I don't really understand what all of these commands did.  Could someone help me understand what each of these commands did for me please?

I'm running a dual amd with an ati x1650pro.

thanks again for everyones help.

---

