---
title: "When I delete files in tmp they return on reboot"
date: 2012-08-22
forum: Asus Ubuntu Support (CLOSED)
---

### Post by halfhearted on 2012-08-22
I'm using an old Asus Eee PC-901 so I have very limited memory. I have files in the tmp folder that don't appear to do anything. I assume they are left there by earlier application/OS upates. When I delete them to free up memory using "sudo rm -rf filename" they appear to be deleted, in that "dir" no longer lists them. However when I reboot they are all back in the tmp directory and none have been deleted. It is driving me mad. Any help appreciated.

---

### Post by Lisiano on 2012-08-22
Enter this command, you will see exactly how much is used by /tmp
```
du -s -b
```
You can use sudo so it will also check folders you don't own
```
lisiano@Lisiano-Ubuntu:/tmp$ sudo du -s -b
[sudo] password for lisiano: 
1311043 .
lisiano@Lisiano-Ubuntu:/tmp$ 
```
It tells me /tmp is using 1.25 MiB, which is... Well... Nothing.
/tmp has some temporary files which some applications need while running. You don't really need to clean /tmp as it is cleaned whenever you reboot.

What I'm advising is, don't try cleaning /tmp unless you see it to be exceptionally large. You will have more luck saving space by deleting old logs.
```
lisiano@Lisiano-Ubuntu:/var/log$ sudo du -s -b
1234297555      .
lisiano@Lisiano-Ubuntu:/var/log$ 
```
Which is 1.14 GiB. Oldest log I noticed was from May this year.

---

### Post by mcduck on 2012-08-22
You really shouldn't delete anything in /tmp, the programs that create (and use) the temporary files will remove them automatically once theya ren't needed any more. And /tmp is also automatically emptied on reboot as well.

In general any file you ahve there is because some program or service actually needs to store that file on the disc at the moment.

(so yes, you dd actually delete the files, it's just that the program/service that needed those files created new ones on next boot).

If you are low on disc space the first places to look are your own home directory, apt's cache, and the amount of space used by all the programs you have installed. (you can empty apt's cached packages by running "sudo apt-get clean". Doing this has no bad effects apart from the fact that if you try to reinstall some package it needs to be downloaded from the server again)

---

### Post by halfhearted on 2012-08-22
Excellent advice, I will do as you suggest. Thank you very much Lisiano and mcduck.

---

### Post by halfhearted on 2012-08-24
> **halfhearted said:**
> Excellent advice, I will do as you suggest. Thank you very much Lisiano and mcduck.

You were right - it was the /var/log folder which was full of errrr.. logs. So I deleted them all and now have lots more room.

---

