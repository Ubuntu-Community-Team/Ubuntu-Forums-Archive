---
title: "Unable to get excesive lock help"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by mason215 on 2008-02-15
for some reason whenever i try to update my packages i get that error. I made sure i had no other programs running and also checked my processes. But i still couldn't update. I then rebooted and did the command apt-get update and got the error 

E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

any idea on how to fix this?

---

### Post by skymera on 2008-02-15
do you have any terminal open updating or installing a rogram?

---

### Post by oedha on 2008-02-15
did open one of these : synaptyc, add/remove, update manager ?
all of them must be closed
after that open terminal
type :==> sudo apt-get update

---

### Post by PeterJS on 2008-02-15
Try:
```

sudo apt-get update

```
usually that error message comes with a reminder asking you if it was run as root, odd that it didn't.

That's dumb, I just checked, it gives you the reminder for install but not update. For the other folks posting in the thread error 11 is the error that it can't lock the dpkg data because it's in use, error 13 is the error that it can not lock because you don't have the permissions to do so.

---

### Post by Sam Lars on 2008-02-15
sudo rm /var/lib/apt/lists/lock

---

### Post by mason215 on 2008-02-15
i closed all of these. heres some screenshots of my processes. Maybe you guys can see something i cant.

[http://img527.imageshack.us/my.php?image=screenshotom1.png](http://img527.imageshack.us/my.php?image=screenshotom1.png)
[http://img176.imageshack.us/my.php?image=screenshot1od9.png](http://img176.imageshack.us/my.php?image=screenshot1od9.png)
[http://img176.imageshack.us/my.php?image=screenshot2cn6.png](http://img176.imageshack.us/my.php?image=screenshot2cn6.png)
[http://img176.imageshack.us/my.php?image=screenshot3jf8.png](http://img176.imageshack.us/my.php?image=screenshot3jf8.png)

thanks

---

### Post by PeterJS on 2008-02-15
> **Sam Lars said:**
> sudo rm /var/lib/apt/lists/lock

As a general rule you shouldn't just go around removing random lock files unless you really really know what the lock is for, and that there is no legitimate reason for it to be locked right this second.

EDIT: some how I screwed that up, but my second point stands.

---

### Post by oedha on 2008-02-15
i think....restart can solve your problem :)

---

### Post by mason215 on 2008-02-15
> **Sam Lars said:**
> sudo rm /var/lib/apt/lists/lock

mason@mason-desktop:~$ sudo rm /var/lib/apt/lists/lock
[sudo] password for mason:
rm: cannot remove `/var/lib/apt/lists/lock': No such file or directory
mason@mason-desktop:~$ 

i dont why this happening

---

### Post by mason215 on 2008-02-15
well good news i just try to do the same thing and get prompted with a new error

mason@mason-desktop:~$ rm /var/lib/dpkg/lock
rm: remove write-protected regular empty file `/var/lib/dpkg/lock'? y
rm: cannot remove `/var/lib/dpkg/lock': Permission denied
mason@mason-desktop:~$ 

so then i went into the dpkg folder and get this error

[http://img146.imageshack.us/my.php?image=screenshotri3.png](http://img146.imageshack.us/my.php?image=screenshotri3.png)

help?

---

### Post by PeterJS on 2008-02-15
Use, sudo. /var/lib/dpkg/lock, is a system file therefor your account can't delete it without requesting elevated privileges. But as I said above you're problem isn't with the lock file, but that you need to run apt-get update with sudo.

---

### Post by mason215 on 2008-02-15
> **PeterJS said:**
> Use, sudo. /var/lib/dpkg/lock, is a system file therefor your account can't delete it without requesting elevated privileges. But as I said above you're problem isn't with the lock file, but that you need to run apt-get update with sudo.

ok sorry for my ignorance to see this. I then ran it with sudo in front and get this

Fetched 58.6kB in 1s (53.2kB/s)
Failed to fetch [http://www.getautomatix.com/apdeb/dists/http://ppa.launchpad.net/tualatrix/ubuntu/gutsy/binary-i386/Packages.gz](http://www.getautomatix.com/apdeb/dists/http://ppa.launchpad.net/tualatrix/ubuntu/gutsy/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://www.getautomatix.com/apdeb/dists/http://ppa.launchpad.net/tualatrix/ubuntu/main/binary-i386/Packages.gz](http://www.getautomatix.com/apdeb/dists/http://ppa.launchpad.net/tualatrix/ubuntu/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/Release](http://archive.canonical.com/ubuntu/dists/gutsy/Release)  Unable to find expected entry  partnerdeb/binary-i386/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://ppa.launchpad.net/tualatrix/ubuntu/dists/gutsy/maint/source/Sources.gz](http://ppa.launchpad.net/tualatrix/ubuntu/dists/gutsy/maint/source/Sources.gz)  404 Not Found
Failed to fetch [http://ppa.launchpad.net/tualatrix/ubuntu/dists/gutsy/gutsy/source/Sources.gz](http://ppa.launchpad.net/tualatrix/ubuntu/dists/gutsy/gutsy/source/Sources.gz)  404 Not Found
Reading package lists... Done
W: GPG error: [http://ftp.debian.org](http://ftp.debian.org) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
mason@mason-desktop:~$

---

### Post by PeterJS on 2008-02-15
Well that's an entirely differnt beast, in that case apt-get update is working (trying to anyway) like it should but is having network trouble connecting to automatix, a ppa for something, debian etch, and the canonical partner repository.

---

### Post by mason215 on 2008-02-15
> **PeterJS said:**
> Well that's an entirely differnt beast, in that case apt-get update is working (trying to anyway) like it should but is having network trouble connecting to automatix, a ppa for something, debian etch, and the canonical partner repository.

is there anything i can do?

---

### Post by PeterJS on 2008-02-15
You can either find out why you can't connect to those repositories, they might be temporarily down, moved, the sources entry for them may be malformed (I think that's the case for Canonical Partner). Or you can open up your software sources System > Administration > Software Sources and disable the problematic entries.

---

### Post by mason215 on 2008-02-15
> **PeterJS said:**
> You can either find out why you can't connect to those repositories, they might be temporarily down, moved, the sources entry for them may be malformed (I think that's the case for Canonical Partner). Or you can open up your software sources System > Administration > Software Sources and disable the problematic entries.

ok i did this but it still gave me 

Fetched 5B in 1s (5B/s)  
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
mason@mason-desktop:~$

---

### Post by PeterJS on 2008-02-15
> **mason215 said:**
> ok i did this but it still gave me 

Fetched 5B in 1s (5B/s)  
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
mason@mason-desktop:~$

Is synaptic open? some other package manager has the dpkg data locked right now, find it, close it, try again.

---

### Post by mason215 on 2008-02-15
> **PeterJS said:**
> Is synaptic open? some other package manager has the dpkg data locked right now, find it, close it, try again.

i honestly cant see it, but i posted my processes maybe you see something

[http://img527.imageshack.us/my.php?i...eenshotom1.png](http://img527.imageshack.us/my.php?i...eenshotom1.png)
[http://img176.imageshack.us/my.php?i...enshot1od9.png](http://img176.imageshack.us/my.php?i...enshot1od9.png)
[http://img176.imageshack.us/my.php?i...enshot2cn6.png](http://img176.imageshack.us/my.php?i...enshot2cn6.png)
[http://img176.imageshack.us/my.php?i...enshot3jf8.png](http://img176.imageshack.us/my.php?i...enshot3jf8.png)

---

### Post by PeterJS on 2008-02-16
I can't find anything in there, I loathe to suggest giving up like this, but if you reboot it will definately close the program and unlock the data.

---

