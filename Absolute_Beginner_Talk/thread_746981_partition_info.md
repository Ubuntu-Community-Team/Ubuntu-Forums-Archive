---
title: "partition info"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by d3adp00l on 2008-04-06
Here is a simple question that I am kinda lost on. 

In windows its just a matter of parting a primary, a logical and what not, there exit and format with
/s to make the hd bootable.

Linux is very different, I suppose because windows hides the reality of whats going on from us, but truth is I am kinda lost

Ok so you part. the drive and it seems pretty much what I am used to, but then theres the whole mounting thing, / , /home, /vars, etc. What is all of that what does it do, and how does it work? Anyone here know and can please explain with small words? Thanks

Next is the whole myriad of file systems, can anbyone give a describtion of them ?

Next is the whole bootloader thing, grub. How does it get installed, how can I change where it gets installed to, and how do I get into it to make changes?

Thanks for reading, and hopefully responding.

---

### Post by Michael.Godawski on 2008-04-06
> Ok so you part. the drive and it seems pretty much what I am used to, but then theres the whole mounting thing, / , /home, /vars, etc. What is all of that what does it do, and how does it work? Anyone here know and can please explain with small words?

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

> Next is the whole myriad of file systems, can anbyone give a describtion of them
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)
> 
Next is the whole bootloader thing, grub. How does it get installed, how can I change where it gets installed to, and how do I get into it to make changes?
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by p_quarles on 2008-04-06
> **d3adp00l said:**
> Here is a simple question that I am kinda lost on. 

In windows its just a matter of parting a primary, a logical and what not, there exit and format with
/s to make the hd bootable.

Linux is very different, I suppose because windows hides the reality of whats going on from us, but truth is I am kinda lost

Ok so you part. the drive and it seems pretty much what I am used to, but then theres the whole mounting thing, / , /home, /vars, etc. What is all of that what does it do, and how does it work? Anyone here know and can please explain with small words? Thanks

Next is the whole myriad of file systems, can anbyone give a describtion of them ?

Next is the whole bootloader thing, grub. How does it get installed, how can I change where it gets installed to, and how do I get into it to make changes?

Thanks for reading, and hopefully responding.
The various sections of the root file filesystem (/var, /home, /etc, /proc, etc.) are simply different elements of the system. They can either be included on the root partition, or given their own. Whether or not you do so depends on the task for which the computer is intended.

/home = userspace
/etc = system configuration files
/var = system records and logs
/usr = elements of the system that are owned by root, but that need to be accessible to users
/dev = hardware and driver definition files
/proc = hardware and driver state information

That's a general description, at least, of the elements of the root filesystem. There are other parts too, of course.

The bootloader essentially gets installed on the first 512 bytes of the hard drive, which is automatically read for boot information by the BIOS. For GRUB, the configuration files are separate, and stored in /boot.

---

### Post by BaffledMollusc on 2008-04-06
> **d3adp00l said:**
> Here is a simple question that I am kinda lost on. 

In windows its just a matter of parting a primary, a logical and what not, there exit and format with
/s to make the hd bootable.

Linux is very different, I suppose because windows hides the reality of whats going on from us, but truth is I am kinda lost

Ok so you part. the drive and it seems pretty much what I am used to, but then theres the whole mounting thing, / , /home, /vars, etc. What is all of that what does it do, and how does it work? Anyone here know and can please explain with small words? Thanks

Essentially, mounting a file system just means giving you access to it. For example, you might have several hard drives, each with a different filesystem on it. Unless you mount each file system you won't be able to do anything to it or see the files on it. 

The mount point, e.g. /, /home etc, is where the mounted file system turns up in your current filesystem / directory structure. Here's an example: I have two hard drives, one with Windows and one with Ubuntu. I have chosen to mount the Windows file system under /media/Windows. This means that when I'm in Ubuntu, I have access to all my Windows files, with the c: drive directory heirarchy appearing at /media/Windows in my Ubuntu file structure.

The / in linux is the very top of the file structure, the "root directory". /home is a directory called "home" under this root directory, and it's where all the user files and home directories are stored.

When you're installing, you can choose to have things like the system files and home directories in separate partitions, so you have to specify where to mount them. You would mount the root directory at / and the home directories at /home.

That is probably over complicated for what you need to do, so I'd just put all Ubuntu on a single partition and mount it at /
> 
Next is the whole myriad of file systems, can anbyone give a describtion of them ?

I could, but it'd take a while :) Wikipedia is your friend. The short answer is, unless you have specific needs, just choose Ext3. It's most common linux file system, and is robust and performs well.

---

### Post by talsemgeest on 2008-04-06
As for the grub, part of it gets installed to the root (or MBR) of your hard drive. When you turn on your computer, it checks and executes what is in the MBR. That part of the grub then finds the rest of the grub that is stored in your linux partition which loads your operating system(s).

---

### Post by d3adp00l on 2008-04-06
Ok so for instance if I create a /boot partition and then drop grub in it, will that create a mbr that the system bios will recongnize? Say for instance on a usb thumb drive I make three partitions /boot, / , and /home. The first being 512mb, the second being 3g and the last everything else. Then I install ubuntu onto the thumb drive in /, will it install grub in the /boot partition?

---

### Post by talsemgeest on 2008-04-07
If, when you install ubuntu you specify the partition as /boot, then that is where the grub files will be placed. But just copying files to the /boot folder won't do anything to the MBR.

---

### Post by d3adp00l on 2008-04-08
Out of curiousity, if you make a primary partition and make it active and drop grub into it, how is that different than installing it. I know there must be some differences, but what is it exactly?

---

### Post by p_quarles on 2008-04-08
Well, like I said earlier, the master boot record (mbr) itself exists on the first 512 bytes of the hard drive. This can be configured to look into a filesystem on the disk for more information about how to proceed -- this is where the /boot directory comes in. Simply dropping files into /boot without having a program to run them wouldn't work.

---

### Post by talsemgeest on 2008-04-08
That has given me an idea. If you put the grub on another partition and ran the following coomands it should work.
```
sudo grub
```To open the grub program. ```
root (hd*,*)
``` Where *,* is the partition you want to boot off. This will tell the grub program that the partition is where the grubs files are. ```
setup (hd*)
```
That will write the changes to the mbr.

You can try it out if you like, I am pretty sure that it would work.

---

