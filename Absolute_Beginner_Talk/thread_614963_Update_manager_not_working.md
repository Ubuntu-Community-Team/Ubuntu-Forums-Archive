---
title: "Update manager not working"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by InsertNameHere on 2007-11-16
It detected the updates and I was pressing the install button then this error came up

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried restarting x and it didn't work

Same with applications can't install anything


Please help
Thanks..

---

### Post by Inxsible on 2007-11-16
open a terminal and type in ```
sudo dpkg --configure -a
```then try again

---

### Post by InsertNameHere on 2007-11-16
Now when I open the update manager no updates show and gives 

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

and whenever I tick something in add or remove (not synaptic) the little mouse cursor just moves like it's loading but never shows a checkmark.

---

### Post by Lord_Dicranius on 2007-11-16
Open up a terminal again and enter the command **sudo apt-get install -f** to fix the broken software index.  Then try and add/remove software again.

---

### Post by Inxsible on 2007-11-16
```
sudo apt-get install -f && sudo apt-get update && sudo apt-get upgrade
```

---

### Post by InsertNameHere on 2007-11-16
it will run now but I get this

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden

installing from update manager wont work.

Add and remove works perfectly

---

### Post by Inxsible on 2007-11-16
yeah. there was a security bug in some samba packages and therefore they have been disabled from the download. you can upgrade them at a later time. There have been a couple of threads about this already.

Here's one of them

[http://ubuntuforums.org/showthread.php?t=614968](http://ubuntuforums.org/showthread.php?t=614968)

---

### Post by InsertNameHere on 2007-11-16
OK, thanks, and Kudos to the devs for 130 MB worth of updates in less then a week

---

### Post by Levo75 on 2007-11-17
This is why i love this place, thank you guys.

---

