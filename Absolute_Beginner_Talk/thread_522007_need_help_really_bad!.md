---
title: "need help really bad!"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by FireStorm102389 on 2007-08-10
I installed updates and stuff in kubuntu 7.04...then i decided to upload Firefox with the adept-manager...it encountered an error and it closed.  Now every time I try and re-open it I get a warning telling me I can't modify anything because its already being in use...is there some way I can stop the stupid thing so I can update and stuff?

---

### Post by FireStorm102389 on 2007-08-10
I have a feeling that its going to do this every time it runs into an error..so I need to find out how to fix it because I'm not reinstalling kubuntu every time it encounters an error...so basically, the adeptmanager shut down on me and i don't know what it wa installing at the time and I need to know how to stop it...

---

### Post by cobrn1 on 2007-08-10
I guess you could try killing the process... But could you clarify first - what were you trying to do and what closed? What are you trying to re-open?

EDIT: so when you try to start up adeptmanager you get an error?

---

### Post by p_quarles on 2007-08-10
Have you tried restarting KDE?

---

### Post by overdrank on 2007-08-10
> **FireStorm102389 said:**
> I have a feeling that its going to do this every time it runs into an error..so I need to find out how to fix it because I'm not reinstalling kubuntu every time it encounters an error...so basically, the adeptmanager shut down on me and i don't know what it wa installing at the time and I need to know how to stop it...

Ok did all this start when your were trying to install java? Have you rebooted your system since? What is the exact error you are getting?

---

### Post by FireStorm102389 on 2007-08-10
ok, this is the error i get whnever I open the adept manager

"You will not be able to change your system settings in any way (install, remove or upgrade software), because another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one"

and i don't have the thing up cuz it closed it down on me when it tol me there was an error installing a firefox package...but idk which one.

---

### Post by SOULRiDER on 2007-08-10
Try rebooting, if after a reboot the problem is still there, copy/paste this into a console:

```
sudo fuser -vki /var/lib/dpkg/lock;sudo dpkg --configure -a
```

---

### Post by FireStorm102389 on 2007-08-10
OMG...SOULRiDER, you are a frikin GOD...it works now and im going to save that in a text document for future reffernce...

ty ty ty ty ty ty tty
THANK YOU

---

### Post by bwtranch on 2007-08-10
Run gedit /var/lib/dpkg/status and let's see the output.

---

### Post by bwtranch on 2007-08-10
I guess SOULRiDER is the man. I would still like to see the output though.

---

### Post by FireStorm102389 on 2007-08-10
ok, the problem was while i was trying to install the plugins for firefox for java...the java plugins for firefox had some sort of error and it kept causing problems...wuts up with that?

---

### Post by SOULRiDER on 2007-08-10
Some Java packages have to be downloaded manually, so unless you uninstall them and follow the instructions on how to get the files you need to continue installation, you will keep on getting an error.

I think Java-docs is one of those packages. Im not sure which package is the one that youre trying to install but i think sun-java6-jre will add support for java in firefox (although im not 100% sure)

Good luck with that!

---

