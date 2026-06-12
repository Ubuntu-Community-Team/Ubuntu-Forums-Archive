---
title: "Install problem with Dell 2407WFP Flat Panel"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by lofftjm on 2006-09-12
I am trying to run the Ubuntu 6.06.01 live CD, but my end goal is to install and boot from hard drive.  My system is an IBM NetVista A30P with an ATI Radeon video adapter and a Dell 2407WFP monitor.

When I try to boot from the CD I get the initial boot menu.  At that point when I pick "Start or install..." I see the boot messages but eventually when X tries top start the monitor display the following:

Out of range signal. Cannot display this video mode. Change computer display input to 1920x1200 @ 60 Hz.

I know the optimal resolution for my monitor is 1920x1200, but according to the doc [http://support.dell.com/support/edocs/monitors/2407WFP/en/about.htm]("http://support.dell.com/support/edocs/monitors/2407WFP/en/about.htm") 
it does support other modes.  I've tried changing VGA modes with the f4 key, but haven't had any luck.

Any thoughts on how to remedy this? My goal is to actualy get ubuntu to install and boot from the hard drive.

---

### Post by indigoblu on 2006-09-12
Try using the DVD or Alternate CD to do a text based install (im not sure if this mode is supported by regular image, i have never used).

---

### Post by lofftjm on 2006-09-13
Thansk for the suggestion.

I used the "alternate" CD to do a text based installation.  I then edited /etc/X11/xorg.conf and added "VertRefresh 60.0 - 60.0" to the Monitor section.  I also added "1920x1200" to all the modes.

X now starts up fine.

---

### Post by felipelb on 2007-01-14
I had the same problem while trying to install Ubuntu 6.10, but I didn´t download the alternate cd. When you get the "out of signal" screen you press CTRL+ALT+F1 to have a terminal and then:

1. do a

**dpkg-reconfigure xserver-xorg**

2. fill all the information asked for, including the correct settings for your monitor

3. press CTRL+ALT+F7 and then CTRL+ALT+Backspace, and this should restart the xserver

BTW, this worked for me for the same monitor (Dell 2407WFP)

---

