---
title: "Lost GUI X-server"
date: 2006-02-16
forum: Absolute Beginner Talk
---

### Post by KeyboardJockey on 2006-02-16
Tried to do an update from HH to BB.  Download update fell over.  I have a disc tht I downloaded using Win XP of BB but I need desparately to know how to install from it and get rid of the HH version of Ubuntu.  

This is Day 10 of trying to get Ubuntu to actually work :( 

I tried to reboot and had some 'locale' error messages and found that X-server has not loaded and I've lost all access to Ubuntu GUI.

What on earth do I do now??

---

### Post by az on 2006-02-16
[QUOTE=KeyboardJockey]Tried to do an update from HH to BB.  Download update fell over.  I have a disc tht I downloaded using Win XP of BB but I need desparately to know how to install from it and get rid of the HH version of Ubuntu.  

This is Day 10 of trying to get Ubuntu to actually work :( 

I tried to reboot and had some 'locale' error messages and found that X-server has not loaded and I've lost all access to Ubuntu GUI.

What on earth do I do now??[/QUOTE]

If you are connected to the net, boot into recovery mode and run
apt-get -f install

That will fix the uninstalled packages.

The run
apt-get install ubuntu-desktop

If there are error messages, you have hardware problems or non-ubuntu repos enabled.  The fix will be more complicated in that case.


If all you have is the Breezy cd, boot into recovery mode, put in the cd and run

apt-cdrom add

and then 

apt-get dist-upgrade.  You will need to run an apt-get -f install before you do this, though, since you have half-installed paclages on your box.

---

### Post by KeyboardJockey on 2006-02-16
[QUOTE=azz]If you are connected to the net, boot into recovery mode and run
apt-get -f install

That will fix the uninstalled packages.

The run
apt-get install ubuntu-desktop

If there are error messages, you have hardware problems or non-ubuntu repos enabled.  The fix will be more complicated in that case.


If all you have is the Breezy cd, boot into recovery mode, put in the cd and run

apt-cdrom add

and then 

apt-get dist-upgrade.  You will need to run an apt-get -f install before you do this, though, since you have half-installed paclages on your box.[/QUOTE]


Many thanks for this I'll just log off of Windoze and give it a try.

---

