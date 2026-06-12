---
title: "Looong boot/black screen"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by jaysons on 2007-11-28
Few things, when I fire up my laptop (IBM thinkpad R50) I get a black screen for about 3 mins then ubuntu loads...This is linux not windows whats the deal? also I have a cisco aironet 350 wireless adapter that is not working..

---

### Post by staticvoid on 2007-11-28
sudo gedit /etc/usplash.conf

# Usplash configuration file
xres=1024
yres=768

change to lower resolution then reboot and see

also, maybe try playing with SUM (start-up manager)

good luck

about the wireless:
[http://ubuntuforums.org/showthread.php?t=334419](http://ubuntuforums.org/showthread.php?t=334419)


hope his problems and troubleshooting helps yours.


sv

---

### Post by jaysons on 2007-11-28
where is the sum??

---

### Post by gubemton on 2007-11-28
I also have a long boot/black screen. the splash does not show up at all. Then ubuntu loads to the login screen

I get Bios bug #81 (whatever that measn, google yeilded very little)

And PCI cannot allocate something, blah, blah, blah.

I want to use Linux, but this is bothering me.

BTW its Ubuntu 7.10 on an Acer Aspire 5100 with an ATI xpress 1100 @ 1280x800

---

### Post by jaysons on 2007-11-28
I never had this problem with older ubuntu...I just updated to 7.10 and well its not fun so far

---

### Post by YoungPastor on 2007-11-28
I, too, have this problem. I'm running 7.10 on an old Compaq Presario 2100. 

Staticvoid, I tried the screen resolution, it was set too high, and I changed it, but it seems to have not solved the problem, as I am waiting through a long reboot right now. I'll try finding/using the start-up manager next.

---

