---
title: "[SOLVED] Linksys ADSL2MUE and Ubuntu"
date: 2007-08-31
forum: Absolute Beginner Talk
---

### Post by confusedmatt on 2007-08-31
Hi,

I am totally new to Linux, but am desperate to be rid of all things MS.  I've had a look at other posts and can't see to find an answer.

I am using BT Broadband, and as the BT Voyager won't work have bought a Linksys ADSL2MUE to do the job.  

My problem is that I can't seem to get Ubuntu to recognise the modem as such.  It just keeps connecting it as a "Wiired Connection" rather than a modem.

All of the lights on the modem come on, although the Internet light only flashes red.

I've tried running sudo pppoeconf, but it keeps saying that the Access Concetrator isn't responding.

Any help, even very, very basic suggestions, welcomed.

Matt

---

### Post by benerivo on 2007-08-31
This is a model with both usb and ethernet connection isn't it? How do you have it connected to the pc? And does it work with windows?

---

### Post by confusedmatt on 2007-08-31
I've tried both, but the ethernet one is the only one that seems to work.

I've not tried on Wondows as I accidently deleted the XP partition when installing Ubuntu and don't want to risk it on this machine.  Although I will do if it helps!

---

### Post by benerivo on 2007-08-31
Have you connected to the router setup page (in a web browser) to see what it says about the internet connection.

---

### Post by confusedmatt on 2007-08-31
I've tried, but the browser doesn't find it at all.

Sorry for being rubbish!

---

### Post by benerivo on 2007-08-31
You may need to set it up through your browser. Have you set it up since you bought it?

---

### Post by confusedmatt on 2007-08-31
I'm trying to use the browser, Firefox, that came with Ubuntu.

I did find some messages about problem settings, but they didn't seem to apply.

What set-up should I have done?

---

### Post by benerivo on 2007-08-31
A new router needs to be told your broadband username and password, so that it can get a broadband connection from your supplier (tiscali, bt, sky, etc..). The red light might mean that it has not been able to establish a connection.

Firefox can connect to the router and change it's settings. This will be part of the router instructions - check them now.

You will need to type the router's address in the address bar in Firefox. It will be something like 192.168.0.0 or 192.168.0.1, or something similar. You will then be asked for a password and username (check instructions). Enter these, and there might be a quick setup option where you can enter your username and password. Save the options and switch off the both the router and pc, and then restart them both.

---

### Post by benerivo on 2007-08-31
The router's address is 192.168.1.1. Username is admin and the password is admin.

Check  this...[http://www.thinkbroadband.com/hardware/reviews/2005/q4/linksysADSL2.html]("http://www.thinkbroadband.com/hardware/reviews/2005/q4/linksysADSL2.html")

---

### Post by confusedmatt on 2007-08-31
Thanks so much for your help benerivo.

For some reason while using it through the CD rather than the installed system it's working.

So, now I'm going to try it on the installed system!!

Thanks once again for the help.

Matt.

---

