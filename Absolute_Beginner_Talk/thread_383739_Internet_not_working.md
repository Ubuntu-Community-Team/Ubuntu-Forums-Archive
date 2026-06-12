---
title: "Internet not working"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by caa101 on 2007-03-13
Hi I am an absolut noob and i cant figure out how to get internet. even when i plug the laptop directly into the ethernet it wont work:(  please help me

---

### Post by mathewb on 2007-03-13
Can you give some information, like what version of Ubuntu you are running. Also make sure that the connection is listed and enabled in System->Administration->Networking.

---

### Post by caa101 on 2007-03-13
bump?

---

### Post by caa101 on 2007-03-13
6.06.1 LTS
second question i do not understand

---

### Post by mathewb on 2007-03-13
On the top toolbar, there is a menu called "System" in that menu there is another menu called "Administration" and in that menu, there is a item called "Networking". Clicking on that will bring up the network connection manager.

---

### Post by Najand on 2007-03-13
Are you behind a proxy? Or do you use an internet connection which does not offer DHCP?

---

### Post by mojoman on 2007-03-13
Have a look at the menu in your top left corner.

system->administration->networking.

Hopefully, you should be able to see the connection there and just be able to add the information under properties.

/mojoman

edit: too slow as usual...

---

### Post by caa101 on 2007-03-13
im not sure what im looking for it says my eth0 is active but thats it

---

### Post by mathewb on 2007-03-13
are you connected directly to the internet, or do you go through a router?

---

### Post by caa101 on 2007-03-13
two routers

---

### Post by Najand on 2007-03-13
Use the  following tutorial:
[http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972)

---

### Post by miketime on 2007-03-13
I have a similar (I think) problem, so while not trying to hijack this thread I thought I might tag along.

Ubuntu 6.10, installed as dual boot with XP on a Toshiba laptop.  Install all seemed ok.  Have a Speedtouch modem, connected via ethernet not usb.  Have set up the ethernet card in network admin, and I can ping the modem, but I can't log in to my ISP, which I do via PPPOE.  Tried different combinations with sudo pppoeconf, as suggested in the help, but to no avail.  Haven't got the error messages to hand (I'm back in the XP partition to type this). Anything obvious I'm missing?

As a follow up question - I've set up text files on the desktop with sudo pppon/off etc in them, and made them executable.  How do I loose the dialog asking whether I want to edit them or run them or run them in a terminal, and just get them to run when I click on them?  Or is there no way to do that?

Regards, Mike

---

### Post by bks on 2007-03-13
> **miketime said:**
> I have a similar (I think) problem, so while not trying to hijack this thread I thought I might tag along.

Have you set up the DCHP or Static IP properties for your eth0? Also try disabling IPv6:

open your browser and in the address bar type "about:config"
there should be tons of options listed in the window now, use the Filter textbox to find "ipv6"
make sure the boolean value is set to "True"

See what that does, it fixed my problem.

---

### Post by miketime on 2007-03-17
Ha - I worked it out.  I'd stupidly left "username" before my ISP username.  :oops: 

Is there any thought of replacing pppoeconf with something a bit slicker GUI-wise?  It feels like a bit of throwback as a new user, to get into a terminal window first thing.  (This has probably been mentioned & thought of before).

Regards, Mike

---

