---
title: "Dual-Booting OSX/Ubuntu, Can't Access the OSX Drive"
date: 2015-12-17
forum: Apple Hardware Users
---

### Post by orion9 on 2015-12-17
I'm on Ubuntu 14.04 on a Macbook (5,1), and I've created a 40GB partition for Ubuntu. I had planned to access the files from the OSX drive from within Ubuntu, but I don't have "the necessary permissions." Can anyone tell me how to grant myself permissions? I'd really just like access to my Documents and Movies folders. 

Thanks!

---

### Post by howefield on 2015-12-17
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by orion9 on 2015-12-17
I think I might have figured out what's wrong; I believe I formatted these disks using Apple's native formatting rather than FAT. I'll try reformatting something as FAT and see what happens.

---

### Post by play-coolgames on 2015-12-30
If you haven't solved it then apt-get install hfsprogs

The HFS+ file system used by Apple Computer for their Mac OS is
supported by the Linux kernel.  Apple provides mkfs and fsck for
HFS+ with the Unix core of their operating system, Darwin.


This package is a port of Apple's tools for HFS+ filesystems.

Home page from synaptic description
[http://www.opensource.apple.com/darwinsource/10.4/](http://www.opensource.apple.com/darwinsource/10.4/)

Posted from Ubuntu Studio 15.10 on 13" MacBook Air (mid 2013) dual boot with El Capitan

---

### Post by orion9 on 2016-01-07
I am not sure I understand those instructions. Are you saying I should load Terminal and key in "apt-get install hfsprogs"? If I do that, what happens? I *very* new.

---

### Post by 1clue on 2016-01-07
Exactly.

Only you need to say **sudo apt-get install hfsprogs**

---

### Post by orion9 on 2016-01-07
Nm.

---

### Post by orion9 on 2016-01-08
Okay, I ran that command in Linux Terminal, and I can now read the Apple drives but not write to them, Also, the majority of the directories are X'd out, I don't have "the necessary permissions" to access them. 

Is there a way to write to them? Is there a way to get "permissions"?

---

