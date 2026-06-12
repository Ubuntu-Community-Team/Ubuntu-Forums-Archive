---
title: "usplash screen color depth issue"
date: 2008-09-29
forum: Apple Hardware Users
---

### Post by usererror on 2008-09-29
I just installed Ubuntu 8.04 on my wife's ibook g4 for issues I have with the OS X talking nicely to windows server 2003.

the splash screen color is like 2bit and ugly.  I tried installing the startup manager to fix it but it doesn't start up like it does on my other linux boxes.

I could not find anything in search. :(

EDIT: Startup manager does not work on the PPC because it doesn't use GRUB! duh on my part.

---

### Post by mfox on 2008-09-29
So how did you fix this?  I had the same problem on my PowerBook G4 Aluminum.  There were also funny video effects at shutdown.

---

### Post by usererror on 2008-09-29
> **mfox said:**
> So how did you fix this?  I had the same problem on my PowerBook G4 Aluminum.  There were also funny video effects at shutdown.

Sadly I have not been able to resolve this yet.  Just found that startup-manager would NOT help solve it. :(

---

### Post by usererror on 2008-10-02
> **mfox said:**
> So how did you fix this?  I had the same problem on my PowerBook G4 Aluminum.  There were also funny video effects at shutdown.

This is how i fixed mine:

[http://ubuntuforums.org/showthread.php?t=798974](http://ubuntuforums.org/showthread.php?t=798974)

---

### Post by mfox on 2008-10-03
usererror, I noticed that the appended command used 1024x768 resolution, which is not the resolution of my PowerBook, or any of the more recent ones I know of.  Did you use this on a PowerBook?  If so, what is its native resolution and did you use 1024x768 in the command?

---

### Post by usererror on 2008-10-10
> **mfox said:**
> usererror, I noticed that the appended command used 1024x768 resolution, which is not the resolution of my PowerBook, or any of the more recent ones I know of.  Did you use this on a PowerBook?  If so, what is its native resolution and did you use 1024x768 in the command?

What is the resolution of your powerbook?  Mine will only do 1024x768 when it is booted up, so that is why I used that resolution.

---

### Post by BryannMelvin on 2008-10-25
sudo your_editor /etc/usplash.conf

then set the numbers for a resolution that works

then

sudo update-intramfs -x where x is the letter for which or all kernels installed

check the --help for that

---

