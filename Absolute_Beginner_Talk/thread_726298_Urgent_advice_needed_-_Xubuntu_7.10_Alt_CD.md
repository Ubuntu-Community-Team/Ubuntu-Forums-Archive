---
title: "Urgent advice needed - Xubuntu 7.10 Alt CD"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by Mazza558 on 2008-03-16
Hi,

I'm currently installing Xubuntu 7.10 via the Alternate CD, and I had no option to format my second, 40GB disk to /home, so it's installing everything to the first 10GB disk. Is there a way to format the second disk and move /home there after the install and once I'm up and running?

Thanks for any help.

---

### Post by Oldsoldier2003 on 2008-03-16
> **Mazza558 said:**
> Hi,

I'm currently installing Xubuntu 7.10 via the Alternate CD, and I had no option to format my second, 40GB disk to /home, so it's installing everything to the first 10GB disk. Is there a way to format the second disk and move /home there after the install and once I'm up and running?

Thanks for any help.

a very good tutorial for this can be found here:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Mazza558 on 2008-03-16
> **Oldsoldier2003 said:**
> a very good tutorial for this can be found here:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Ah. First problem is that the PC i'm installing Xubuntu on can't run a LiveCD (not enough RAM). :(

Can you run GParted off CD?

---

### Post by Oldsoldier2003 on 2008-03-16
> **Mazza558 said:**
> Ah. First problem is that the PC i'm installing Xubuntu on can't run a LiveCD (not enough RAM). :(

Can you run GParted off CD?
yes you can download the[ GPARTED live CD]("http://gparted-livecd.tuxfamily.org") and run it from there/

---

### Post by Mazza558 on 2008-03-16
> **Oldsoldier2003 said:**
> yes you can download the[ GPARTED live CD]("http://gparted-livecd.tuxfamily.org") and run it from there/

Second problem - the Gparted LiveCD doesn't have a text editor, which I need in order to complete that guide.

Actually, scratch that, can I just format the second disk as ext3, create my music/video/documents folders and go from there?

---

### Post by tommcd on 2008-03-16
Here is a good tutorial for adding a second hard drive. G-parted live CD is not needed:
[https://help.ubuntu.com/community/InstallingANewHardDrive?highlight=%28hard%29%7C%28drive%29%7C%28new%29](https://help.ubuntu.com/community/InstallingANewHardDrive?highlight=%28hard%29%7C%28drive%29%7C%28new%29)

---

### Post by Oldsoldier2003 on 2008-03-16
> **Mazza558 said:**
> Second problem - the Gparted LiveCD doesn't have a text editor, which I need in order to complete that guide.

Actually, scratch that, can I just format the second disk as ext3, create my music/video/documents folders and go from there?
yes the Gparted live cd is a very minimal build. you could try making the edits to fstab by running a live cd for puppy linux or damn small linux.

edit crossing posts. yes you could do that

---

### Post by peterx2 on 2008-03-16
> **Mazza558 said:**
> Second problem - the Gparted LiveCD doesn't have a text editor, which I need in order to complete that guide.

Actually, scratch that, can I just format the second disk as ext3, create my music/video/documents folders and go from there?

actually the best live cd's to use are sysrescue or knoppix. I prefer sysrescue as it is made for this purpose.
pete

---

### Post by Oldsoldier2003 on 2008-03-16
> **peterx2 said:**
> actually the best live cd's to use are sysrescue or knoppix. I prefer sysrescue as it is made for this purpose.
pete
the only reason i like the Gparted Live CD is because its partition moving support is better than most live CDs and I'm too lazy to check what version of Gparted is installed on the rescue cds LOL!

---

