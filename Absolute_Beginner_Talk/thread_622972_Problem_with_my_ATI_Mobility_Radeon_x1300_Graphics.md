---
title: "Problem with my ATI Mobility Radeon x1300 Graphics card"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by Lacent on 2007-11-25
Hi, as stated, I have the ATI mobility radeon x1300 graphics card that I cannot get the driver working for. When i go to the restricted drivers manager and try to enable it, it says:

The software source for the package

   xorg-driver-fglrx

 is not enabled.


  And I tried installing the driver from ATI, but that was to no avail. Any help would be appreciated.

---

### Post by Afkpuz on 2007-11-27
I had this problem too.  That means that the repository with the driver is not enabled.  Here's how to enable.


goto
System>Administration>Software Sources

Make sure all the check boxes except "Source Code" are checked.  I think the restricted driver is in the "Multiverse", but just enable them all.  

Click "close" and then it will prompt you to "reload".  Do it.  Then sometimes, ubuntu hangs here after it has reloaded.  Thats all right.  once it has reloaded, you can X out of software sources.  Now you should be able to install your beloved driver.

---

### Post by vivisectionnnn on 2008-02-23
Hey, I've got the same exact card but I different problem. I was wondering if you are using your card yet because I can only get Ubuntu 7.10 to startup using my onboard VGA. If i try to put in my card, nothing loads and it's a black screen. (with onboard vga) I tried to go into system > admin > restricted drivers manager and set up the driver for my card, but i got this error message. " your hardware does not need any restricted drivers".  you can see my situation, im stuck without the card because if i put it in, i cant boot up, but if i dont have the card in, the restricted drivers manager doesnt detect a need for it to be running. how did you do it ?

---

