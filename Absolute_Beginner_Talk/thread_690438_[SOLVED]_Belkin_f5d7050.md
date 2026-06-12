---
title: "[SOLVED] Belkin f5d7050"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by jayg1169 on 2008-02-07
im qiute new to ubuntu been playing with it on a wired router for some time with much success!
i'll be honest i love it! but im having serious problems with my belkin wireles usb adapter it works on live cd but not after hdd install! any help?

---

### Post by Jdm111 on 2008-02-07
I used to have one of those. Try installing WICD.

---

### Post by dca on 2008-02-07
Were there separate revisions to that dealie?  Like f5d7050 v3 and f5d7050 v4???  Try putting the model# & version number in the Ubuntu search feature and see if other(s) have encountered the same issues w/ Live CD versus install.  It escapes me right now as I can only remember a version differences over the course of time w/ that model number...

---

### Post by sneeks on 2008-02-07
did you update your install before plugging in the dongle?

---

### Post by jayg1169 on 2008-02-07
its v 2

---

### Post by jayg1169 on 2008-02-07
cant! i can only b wireless on that comp! im gutted about this as i thought ubuntu was the solution to all my problems! need to have wireles network to stream video! want to use old computer as htpc

---

### Post by jayg1169 on 2008-02-07
Please help ive got 3 comps 1 tri boot win xp, ubuntu & kubuntu. and  laptop with xubuntu they allwork fine! final pc celeron d 3.06gh 1gb ram wireles belkin f5d7050

---

### Post by sneeks on 2008-02-07
hi again,i found that with doing all the updates via cable,then pluging in the dongle,it was nearly sorted for me,just a few tweaks and hey presto....
see if you can get to use someones wired router to update first mate

---

### Post by jayg1169 on 2008-02-08
Still wont work!
 done a complete reinstall done updates over ether connection!
 plugged in wireless usb and nothing!
 even more annoying is ive plugged the usb into my other pc (ubuntu 7.10 also) and it worked straight away!

---

### Post by sneeks on 2008-02-08
what machine specs..

---

### Post by dca on 2008-02-08
What happens when you type in lsusb or sudo lsusb at command line in terminal?

---

### Post by jayg1169 on 2008-02-09
this is what i get in  lsusb
Bus 004 Device 006: ID 050d:705a Belkin Components 
Bus 004 Device 004: ID 04b4:6830 Cypress Semiconductor Corp. USB-2.0 IDE Adapter
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 058f:9360 Alcor Micro Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c512 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000

---

### Post by jayg1169 on 2008-02-09
Thanks for your help!
 problem solved (after 3 days)

had to blacklist driver rt2500usb!
now using driver rt73usb and im typing this over a wireless connection! (at last)
Thanks again!

---

### Post by travismoore on 2008-02-09
Could i explain to me how you did that because i have the same usb adapter and i got it to work for about 10 minutes and its stopped worknig now ..

---

### Post by jayg1169 on 2008-02-09
type this in terminal
gksudo gedit /etc/modprobe.d/blacklist 

add the following two lines to the end of the file:

# Added when rt73 module was installed
blacklist rt2500usb


then save!

I restarted after this and its working for me!

---

