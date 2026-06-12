---
title: "Xserver problem part 2"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by maneesh77 on 2006-09-26
my x server had some problems and it does not load at start up. ubuntu goes straight to command line interface. I don't know how to reconfigure or correct the problem . So instead can I uninstall it or ubuntu as a whole and reinstall it again without losing my data, If not can I at least transfer my docs to a USB flash disk?? and just format the drive

Please help

logfile: "/var/log/xorg.0.log, time : tue sept 26 23:10:00:2006
(==) using config file : "etc/x11/xorg.conf"
(ww) nvidia- no matching device section for instance (bus ID PCI :1:0:0) found
(EE) no devices detected

fatal server error: no screens found

---

### Post by Bachstelze on 2006-09-26
Could you please paste your /etc/X11/xorg.conf ? I guess you're running an nvidia driver with a non-nvidia card.

---

### Post by bulldog on 2006-09-26
Is the problem a side effect off the new kernel?

Boot your previous kernel without an error?

---

### Post by maneesh77 on 2006-09-26
I do have nvidia and I installed nvidia-glx 

it was working fine for a month,  In the details there is a area where it says ATI radon installed. 
But I think it's something more coz I took out the vidio card from the motherboard slot and tried again but it didn't work 

What options do I have to save my data or bring the system back to order

---

### Post by maneesh77 on 2006-09-26
how exactly do i paste the log file /etc/x11/xorg.conf


Also I checked the details it shows device ATI tech inc radon 7000q. don't know where that got in

I tried going in grub and opening  ubuntu from yesterday but still the same problem

---

### Post by tideline on 2006-09-26
Prehaps check the /etc/X11/xorg.conf file.  Look in that file for the nv driver setting in "Video Card" section.  If there is anything other than that I think you may want to put that back in.

Mike

---

### Post by tideline on 2006-09-26
As to the how do I copy question.

In a terminal sudo gedit /var/log/Xorg.0.log then copy it

---

### Post by maneesh77 on 2006-09-26
I can't figure this out , please advice if I can reinstall it or save my files and reinstall ubuntu from the live CD again( not giving up on it)

---

### Post by Bachstelze on 2006-09-26
Run

sudo dpkg-reconfigure xserver-xorg

You'll be asked a few questions about your hardware, if you don't know what to answer to a question, just press enter to keep the defaults.

---

### Post by bulldog on 2006-09-26
Simple,type in your terminal,

cat /etc/X11/xorg.conf

select the text and copy it to the textbox on the forum.

---

### Post by bodhi.zazen on 2006-09-26
> **bulldog said:**
> Simple,type in your terminal,

cat /etc/X11/xorg.conf

select the text and copy it to the textbox on the forum.

Better:```
cat /etc/X11/xorg.conf > ~/xorg.conf.txt
```
:)

Better yet: post /etc/X11/xorg.conf as an attachment (see "Manage attachmnets" below the text box where you type your post.... Easier to read.

---

