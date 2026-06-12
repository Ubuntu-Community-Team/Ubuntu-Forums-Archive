---
title: "moving harddisk"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by johnni@winther-andersen.d on 2007-09-21
dear all

i have just moved my harddisk from one computer to another and now the x server won't start. I'm an absolut beginner so a very basic instruction on how to set the graphics in the command line interface would be gratly appriciated

thanks in advance

Johnni

---

### Post by KCPokes on 2007-09-21
I'd assume at the very least you'd need to run dpkg-reconfigure -phigh xserver-xorg.  Not sure how successful you'll be.  I assume it'll depend on how comparable the two machines are.  If you've ever tried this in Windows you'll know that it's a real "crap shoot" as to whether it'll work or not.  For the most part it doesnt.

---

### Post by w4ett on 2007-09-21
A  question before I go any further:

1.  What video card is installed in the new machine?  :)

ATI, Nvidia, Via, Intel...etc.

I'd start by reconfiguring your xorg.conf.....boot into recovery mode.

From the command line type:


```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select [COLOR="Red"]"vesa"[/COLOR] as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:


```
startx
```

This should  get you to a GUI desktop with the basic video driver.

---

### Post by Pumalite on 2007-09-21
They say the kernel mounts the modules according to the hardware, but most of the time, switching hard drives does not work. You will probably need a re-install.

---

### Post by darren1270 on 2007-09-21
When you load an operating system on a hard drive it configures itself to that machine.  Most of the time it will not work especially if the machines are not similar.  You would have been better to back up your important data.... wipe the hard drive and reload the OS.  Just my two cents worth.

Good Luck

Darren

---

