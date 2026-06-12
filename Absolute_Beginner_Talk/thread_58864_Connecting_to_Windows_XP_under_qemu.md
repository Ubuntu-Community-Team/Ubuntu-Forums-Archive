---
title: "Connecting to Windows XP under qemu"
date: 2005-08-21
forum: Absolute Beginner Talk
---

### Post by n1tro on 2005-08-21
Can someone tell me if I can fool Ubuntu to be able to connect to Windows XP under qemu emulation.  Or can someone tell me if it possible to pull data from the XP emulated partition on the Ubuntu drive? Reason I ask is because I couldn't find or compile a newsgroup reader (with nzb support) so I just ran my favorite one under XP and need to get the images off the partition to burn it onto DVD.  Any help is appreciated.

---

### Post by tonysathre on 2005-08-22
look at this link, it should help

[http://ubuntuforums.org/showthread.php?t=39513&highlight=qemu](http://ubuntuforums.org/showthread.php?t=39513&highlight=qemu)

---

### Post by n1tro on 2005-08-23
Yeah I read that thread and installed qemu (after many attempts  \\:D/ ) But now I'm trying to get samba to work so I can pull the files I download over to ubuntu so I can burn them.

[QUOTE=tonysathre]look at this link, it should help

[http://ubuntuforums.org/showthread.php?t=39513&highlight=qemu](http://ubuntuforums.org/showthread.php?t=39513&highlight=qemu)[/QUOTE]

---

### Post by tonysathre on 2005-08-23
an easier way to do that would be to create a FAT32 partition and just copy the files to that partition because linux can read and write to FAT32.... or are you trying to pull the files off a remote computer acrossed a network?

---

### Post by n1tro on 2005-08-23
I'm actually running Windows XP under emulation off qemu.  I want to be able to access the stuff I download in XP that is stored in it's C drive (which I believe is the qemu.img file) or have XP see a network Ubuntu folder so I can send over the files while under emulation.  You say to make a separate partition. I did that but Ubuntu doesn't see it as a separate drive.  If I mount the thing, it shows up as a folder in the linux file system.  This is no good because it brings me back to my original problem of not getting XP to see a shared linux folder or Ubuntu seeing the contents of the XP under emulation.  ](*,) 

[QUOTE=tonysathre]an easier way to do that would be to create a FAT32 partition and just copy the files to that partition because linux can read and write to FAT32.... or are you trying to pull the files off a remote computer acrossed a network?[/QUOTE]

---

### Post by sizzam on 2005-10-16
I'm sure theres a better way to do it, but here is what I do when I run Windows XP in VMWare on my Ubuntu desktop is this:

1.  set up ssh on your Ubuntu desktop

```
sudo apt-get install ssh
```

2.  In Windows XP, download WinSCP.  Set up your session so that your IP is the host, use port 22, and your Ubuntu username and password.   This will give you a session visibly similar to FTP to transfer files back and forth, and it goes over your network instead of the internet (since you're on the same IP), so its fast.

Note, I use SSH to remote access my machine from work, so I had to set up a port forward for port 22 in my router, I'm not sure if that will be necessary when working locally.

---

