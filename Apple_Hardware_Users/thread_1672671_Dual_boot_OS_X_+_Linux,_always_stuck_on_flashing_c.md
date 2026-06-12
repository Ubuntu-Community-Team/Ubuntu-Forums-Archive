---
title: "Dual boot OS X + Linux, always stuck on flashing cursor or black screen"
date: 2011-01-21
forum: Apple Hardware Users
---

### Post by Dolerho on 2011-01-21
Hello guys & girls,

I'm quite desperate : I tried some of the solutions on this forum, reinstalled GnackTrack or BackTrack 5 times trying different methods but I am always stuck at flashing cursor or black screen.

This is what I did :

[LIST=1]
[*]Clean OS X Install
[*]Boot Camp
[*]rEFIT
[*]Linux
[/LIST]
 I also tried to make the Boot Camp thing before installing rEFIT, same result.

When I try to sync partition with rEFIT, it always told me that they were already synced, but when I do it without shutting down my MacBook1,1, I don't have GRUB with flashing cursor but black screen.

Please help, I couldn't find a real solution surfing this forum and the web.

---

### Post by srs5694 on 2011-01-21
Can you boot OS X? If so, please post the output of the following commands, typed at an OS X Terminal:

```
sudo fdisk /dev/disk0

```

If you've got more than one disk, repeat this for each one (/dev/disk0, dev/disk1, and so on).

Please post the output between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility.

You may also want to check [my Web page on installing Ubunto on Macs with EFI-style booting.](http://www.rodsbooks.com/ubuntu-efi/) I'm not sure following my procedure will entirely work around your problem, but it might.

---

### Post by B_Free on 2011-01-21
What type of machine do you have?

---

### Post by Dolerho on 2011-01-22
Hello guys and thanks for your help.

Here is the result of fstab (only 1 HDD) :

```


Disk: /dev/disk0	geometry: 7296/255/63 [117210240 sectors]
Signature: 0xAA55
         Starting       Ending
 #: id  cyl  hd sec -  cyl  hd sec [     start -       size]
------------------------------------------------------------------------
 1: EE 1023 254  63 - 1023 254  63 [         1 -     409639] <Unknown ID>
*2: AF 1023 254  63 - 1023 254  63 [    409640 -   73400320] HFS+        
 3: 82 1023 254  63 - 1023 254  63 [  73811968 -    1951744] Linux swap  
 4: 83 1023 254  63 - 1023 254  63 [  75763712 -   41445376] Linux files*

```

(It's a 1st gen. MacBook)

EDIT : I'm giving a shot to your method, srs.

---

### Post by srs5694 on 2011-01-22
I'm not sure why it's not working for you. Your hybrid MBR looks OK (or as "OK" as hybrid MBRs can look), although I haven't done the math to check for overlapping MBR partitions.

If you're already well into attempting the procedure on my Web page, I wish you luck. If you haven't started it yet, though, it might be worth trying to boot from the [Super GRUB 2 Disk.](http://www.supergrubdisk.org/) Whether or not it works will help narrow down the scope of possible causes, and therefore possible solutions.

---

