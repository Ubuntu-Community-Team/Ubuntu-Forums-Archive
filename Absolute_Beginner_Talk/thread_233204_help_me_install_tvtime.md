---
title: "help me install tvtime"
date: 2006-08-09
forum: Absolute Beginner Talk
---

### Post by avidsensei on 2006-08-09
i downloaded the arcive from the tvtime website. but i can't figure out how to install it!
i have an ati wonder pro card 
running ubuntus latest update
please any help would be greatly apreciated

---

### Post by avidsensei on 2006-08-09
forgot to mention im useing a 64 bit version of ubuntu

---

### Post by fragos on 2006-08-09
Tvtime is available with the Synaptic Package Manager in binary form.  Its my favorite TV package.  We'll help with compiling the tvtime tar ball if you wish but using a binary package is always much simpler.  When using Synaptic you will want to enable the "Universe" and "Multiverse" repositories if you haven't done that yet.

---

### Post by avidsensei on 2006-08-09
could you walk me through that? or where is the link to unlocking those?

---

### Post by avidsensei on 2006-08-09
ok so new problem. this is what i get when i try and run tvtime
kyle@fast64:~$ sudo tvtime
Password:
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/kyle/.tvtime/tvtime.xml
Xlib:  extension "XVideo" missing on display ":0.0".
xvoutput: XVIDEO extension not found: X too old? didn't load extmod?
kyle@fast64:~$

---

### Post by fragos on 2006-08-10
> **avidsensei said:**
> could you walk me through that? or where is the link to unlocking those?
System-> Administration-> Synaptic Package Manager-> Settings-> Repositories-> select all the choices-> Close button-> Reload

If I've been to cryptic let me know.

---

### Post by fragos on 2006-08-10
> **avidsensei said:**
> ok so new problem. this is what i get when i try and run tvtime
kyle@fast64:~$ sudo tvtime
Password:
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/kyle/.tvtime/tvtime.xml
Xlib:  extension "XVideo" missing on display ":0.0".
xvoutput: XVIDEO extension not found: X too old? didn't load extmod?
kyle@fast64:~$
Install tvtime with Synaptic and all the dependancies will be filled.

---

### Post by glubrani on 2007-07-21
I just installed Ubuntu 7.04 (or whatever the newest release is) and need to get three things working in order to say good bye to Microsoft ... 

1) 56k PCI modem (Lucent Agere Winmodem)
2) HP PSC 1210
3) Hauppauge WinTV USB

ok, I opened Synaptic and enabled the "Universe" and "Multiverse" repositories but I don't see TVTime listed anywhere in Synaptic. I did a search within Synaptic but it doesn't find any 'TVTime'. I downloaded the TVTime file from the official website (as you nkow it's a tarball) so now what? Can you write a step by step using Synaptic package manager (including verifying that the binary TVTime is there) and any help/links for the other two harware items GREATLY appreciated

---

### Post by fragos on 2007-07-21
Very strange that you can't search and get it.  Perhaps you hadn't given synaptic a chance to get the new repositories before you did the search, they download from the web.  I did find the package for download and here's the URL:

[http://packages.ubuntu.com/feisty/x11/tvtime](http://packages.ubuntu.com/feisty/x11/tvtime)

This will be a deb file which Ubuntu will install for you.

Go to System-> Administration-> HPLIP Toolbox to setup the HP PSC 1210.  I've a 1410 and it works great.  There's a winmodem driver package "linux-restricted-modules" which may meet your needs.

---

### Post by glubrani on 2007-07-21
First, thanks for the links ... I'll give them a try.

---

### Post by glubrani on 2007-07-21
ok, TVTine was installed with no apparent errors, plugged the USB cable from the WinTV USB external box and ran TVTime. The TV window opens and the red LED on the WinTV USB box lights up but then the TV windows shows "no video source" and below that, "no signal" and at the bottom of the window, " framestoo short from USBVision, can not opencapture device /dev/video0

please keep in mind that I can't go online yet ...

Also, I went to System-> Administration-> but there's no HPLIP Toolbox in the list, can't find it in any list for that matter. I'm unable at this time to go online and update the files - so how do I get online with the PCI Winmodem Lucent/Agrere modem ? (DSL is so easy, Ubuntu takes care of it on the first boot but I no longer have DSL.

Don't give up on me, I'm willing to walk thru the steps to get all this working.

Thanks

---

### Post by glubrani on 2007-07-21
I forgot to mention that the red LED goes out right after the messages appear

---

