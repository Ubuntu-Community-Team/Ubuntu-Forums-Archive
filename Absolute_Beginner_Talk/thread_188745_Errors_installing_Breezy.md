---
title: "Errors installing Breezy"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by JB_e on 2006-06-04
I just tried to install breezy on my ubuntu and I get this Error message please help!?!!?](*,) ](*,) ](*,) 

Failed to fetch cdrom:[Ubuntu 5.04 _breezy bagger_ - Release i386 (20050407)]/dists/breezy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 5.04 _breezy bagger_ - Release i386 (20050407)]/dists/breezy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Reading package lists... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _breezy bagger_ - Release i386 (20050407) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fbreezy%20bagger%5f%20-%20Release%20i386%20(20050407)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.04 _breezy bagger_ - Release i386 (20050407) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.04%20%5fbreezy%20bagger%5f%20-%20Release%20i386%20(20050407)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
How would I fix this?

---

### Post by taurus on 2006-06-04
Any reason why using such an old distro?  I think you should try Dapper Drake, 6.06, because it's only 4 days old instead of over two years old, 5.04!!!

[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

---

### Post by JB_e on 2006-06-04
[QUOTE=taurus]Any reason why using such an old distro?  I think you should try Dapper Drake, 6.06, because it's only 4 days old instead of over two years old, 5.04!!!

[http://www.ubuntu.com/download](http://www.ubuntu.com/download)[/QUOTE]
well I am new to it and I don't know much. I want to upgrade it but.
what you showed me is not truly helping.:-k 
How would I do that using the terminal?

---

### Post by taurus on 2006-06-04
[QUOTE=JB_e]well I am new to it and I don't know much. I want to upgrade it but.[/QUOTE]
That's why I recommand you use the newest version of Ubuntu instead of the one from two years ago!!!

> what you showed me is not truly helping.:-k
What I showed you is a link to download the latest version of Ubuntu--Dapper Drake!  But if you still want to use your 5.04, then post your /etc/apt/sources.list here and I will have a look at it...

> How would I do that using the terminal?
Okay, if you want step by step.  Open a terminal by Applications -> Accessories -> Terminal and type
```

wget -c http://ftp.wayne.edu/linux_distributions/ubuntu/6.06/ubuntu-6.06-desktop-i386.iso

```
Wait for it to finish and check to make sure the file is good during transfer by running
```

md5sum ubuntu-6.06-desktop-i386.iso

```
Now, make sure the output matches this sequence of numbers and letter...
```

e2e5e0bfb2edffd2ce02dd77bda4558e

```
If everything is good, fireup k3b either from a terminal or from the Applications' menu.  Click on Tools -> Burn CD Image.  The ubuntu-0.06-desktop-i386.iso should be in your home directory, /home/JB_e, assuming that JB_e is your login name.  Once it's done, leave the CD in the drive and reboot...

---

