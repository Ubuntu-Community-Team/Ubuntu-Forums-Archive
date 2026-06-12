---
title: "update error"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by trugreg on 2007-12-23
got this error and now can't update or add programs

    E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by kdarkentity on 2007-12-23
Do you get this error every time you install updates?

---

### Post by trugreg on 2007-12-23
It worked fine yesterday (i am a total noob) only installed a couple of days ago. Will I was updating i tried downloading a new program. I guess I jammed something. 

I tried rebooting and still get the same error

---

### Post by kdarkentity on 2007-12-23
> **trugreg said:**
> It worked fine yesterday (i am a total noob) only installed a couple of days ago. Will I was updating i tried downloading a new program. I guess I jammed something. 

I tried rebooting and still get the same error

And you only get this error when checking for updates correct?

What program did you install?

---

### Post by trugreg on 2007-12-23
i was trying to download / install Limewire. it errored out and listed update manager was running and could not have 2 instantences running.

---

### Post by GrumpyBob on 2007-12-23
Did you try running dpkg --configure -a like it suggested?  You will probably need to prefix the command with sudo.

This has happened to me in the past.  You can see the various dpkg options by typing 
man dpkg
in a terminal

Robert

---

### Post by Locutus_of_Borg on 2007-12-23
I assume you did do "dpkg --configure -a"

you can also try "apt-get clean" and remove all .deb files from /var/cache/archives then run "apt-get update" and "apt-get upgrade"

---

### Post by kdarkentity on 2007-12-23
> **Locutus_of_Borg said:**
> I assume you did do "dpkg --configure -a"

you can also try "apt-get clean" and remove all .deb files from /var/cache/archives then run "apt-get update" and "apt-get upgrade"

"sudo apt-get autoclean"

---

### Post by trugreg on 2007-12-23
thank you all - it is working. I am so glad I started using Ubuntu - I feel like I am part of my computing again. I am just starting but I know it is the beginning of something great like the old Commodore 64 back in the day that I am sure none of you even ever heard of.

---

### Post by kdarkentity on 2007-12-23
> **trugreg said:**
> thank you all - it is working. I am so glad I started using Ubuntu - I feel like I am part of my computing again. I am just starting but I know it is the beginning of something great like the old Commodore 64 back in the day that I am sure none of you even ever heard of.

Commodore 64? is that linux?

---

