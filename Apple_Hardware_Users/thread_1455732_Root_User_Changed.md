---
title: "Root User Changed"
date: 2010-04-16
forum: Apple Hardware Users
---

### Post by BFeaver on 2010-04-16
Ubunto 8.4, running on 2nd partition on Apple Intel iMac.  

Several months ago, following a routine update, I found I could no longer install routine updates.   Investigating further, I find "You don't have permissions to..."  then sudo: /etc/sudoers is owned by gid 1002, should be 0.  

That's not me!  I am the owner and root user of this computer.  How could this get changed?   How can I change it back to me?   The Linux platform of the computer has not been exposed to the net except for Ubuntu forums and updates.  No one else has used this computer.  

Blue side up,
Bob

---

### Post by linuxopjemac on 2010-04-16
In Linux, the administrator account is called root. The Ubuntu Security Model has root disabled by default. Instead a group of users with extended rights can assume root rights for a period of time using sudo/gksudo/gksu/kdesu (see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)).

The file '/etc/sudoers' lists all users with superuser rights, i.e. those than can use the 'sudo' command.

Currently, the user with the ID 1002 owns this file, while it should be owned by root(0). 

It's gotta be changed back for your system to function properly. The problem lies in the fact, that you have to have superuser rights to change permissions, which you can't assume, since sudoers is screwed.

This vicious cycle can be broken by booting into Recovery Mode (usually the second option in the GRUB menu). Recovery Mode is essentially a command line interface with the root account enabled. If the GRUB menu does not show during startup, hit 'ESC' when you see 'GRUB loading - Stage 1.5' appear on your screen.

In Recovery Mode, drop to a root shell, type 
```
chown root /etc/sudoers
```
and hit the Enter key.

The chown command changes a target file's ownership. It's syntax is ```
chown [-option] username /path/to/file
```

Boot back into your regular Ubuntu install, log in with your regular username and pass, Synaptic should open from the GUI.

As an aside, you should never run 'sudo synaptic', Synaptic being a graphical application, it should be run with 'gksu synaptic' (see above link).

It's a known [problem]("https://answers.launchpad.net/ubuntu/+question/45138").

---

### Post by BFeaver on 2010-04-16
Thank you.  I will try this later today.  

But how would this have gotten changed in the first place?  How can I avoid this happening again?  

Would I be better to do a fresh install of a more recent Ubuntu or will I find myself stymied by not having permissions to do the fresh install?  

Blue side up,
Bob

---

### Post by linuxopjemac on 2010-04-16
It seems like it was a bug in 8.04. Did you try to upgrade to Jaunty? I have seen more people trying to update to Jaunty from Hardy with this error.

---

### Post by BFeaver on 2010-04-16
Will I need to restore myself as root user before I can do a new install?  

Can I update to newer versions directly from a disc like changing versions on a Mac?  Or will I have to do fancy things like deleting the previous install or erasing the partition?  

If I am going to update then I may as well update to the latest and best.  What would you recommend?  

Blue side up,
Bob

---

### Post by linuxopjemac on 2010-04-16
You might want to upgrade from the version you are in now.
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

You have to first upgrade to 8.10, then to 9.04 and then to 9.10. You might also want to try a comple reinstallation over the partition where 8.04 resides. Up to you. I advise to reinstall. Copy your home folder to a stick or something and put it back later.

---

