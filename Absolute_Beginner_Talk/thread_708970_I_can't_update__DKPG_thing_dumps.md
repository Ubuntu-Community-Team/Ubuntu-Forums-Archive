---
title: "I can't update  DKPG thing dumps"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by monarda22 on 2008-02-27
I can't update.

It says "updates available".  I go to do that and it says

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

I type in "sudo dpkg --configure -a" and my p[assword at a terminal window and it is toast.  It core dumped or something one time then it locked up with the caps lock and the scroll lock flashing another.

My system isn't stable and Firefox keeps crashing.  All I want to do is some sort of system update or clean install and I don't know how.  Please.

---

### Post by chris.a.barker on 2008-02-27
First attempt to reboot your computer and see if that stabilizes your machine a bit. Then we will work from there.

---

### Post by monarda22 on 2008-02-27
I've rebooted 3 dozen times already.  i can't get it to do anything.


When I do the dpkg configure thing I get

en_HK.UTF-8... Segmentation fault (core dumped)

and it is toast.  Lights flashing.  No life.

---

### Post by bazzawill on 2008-02-27
try booting into recovery mode from the grub menu (you will need to press esc if the grub menu does not show) this will give you a root shell so no sudo needed but you need to be careful. Type ```
 dpkg --configure -a
apt-get update&&apt-get upgrade
reboot
```

---

### Post by monarda22 on 2008-02-27
Okay.  Did the recovery mode thing.

Went through a bunch of en_(two letters).UTF-8 files.

Some said up-to-date, some said done.

Did the "apt-get update&&apt-get upgrade"

Flying screens of "Failed to fetch  (file name)" and "could not resolve"

Did the "reboot".

Rebooted into the desktop.


It said updates available.  Started Update Manager.  It didn't crash.  I said apply changes.  It said applying changes.  It said error and locked up.  Definitely farher along though.  I rebooted and tried again.  

Back to the original dkpg error thing.

I'll try the procedure again.

---

### Post by JoshuaRL on 2008-02-27
Also you can try:
```

sudo apt-get install -f

```
And, of course, if you're in Recovery Mode drop the sudo.

---

### Post by monarda22 on 2008-02-27
Ok.  Did the bazzawill procedure again.

Got the same amount of farther along.

Then I get" Error in package /var/cache/apt/archives/linux-image-2.6.22-14-gene..."

and the rest of the message is too long for the box.  

System is locked up.  Spinny wheel not spinning, no mouse repsonse.

---

### Post by monarda22 on 2008-02-27
Ok.  Did the JoshuaRL procedure.  That just gives me the original "dpkg --configure -a" error message telling me to run it manually.

Now when I do that, it immediately come back to to a prompt having taking no apparent action. 

I followed that with the Joshua -f thing again and it is doing something.  

"Setting up linux-image2.6.22-14-generic (2.6.22-14.52)... Running depmod."  

Back to a prompt.  

"Reboot"?


I rebooted.

it is running fsck and says /dev/hda1 has been mounted 28 times without being check,  check forced.

That sounds really sexual.

It did that.  

Into the desktop.

I looged in it said "Your session only lasted less than 10 seconds.  If you have not logged out  ( there are installation problem or you're out of disk space.)  "

I thik I have diskspace.  I viewed details.

Segmentation fault.  
/etc/gdm/Xsession:  Beginning session setup...


Crash.  Reboot.

Into the desktop.

Start update manager.

It has been unacking linux headers 2.6.22-14 for 5 minutes now.  I'm still waiting.

---

