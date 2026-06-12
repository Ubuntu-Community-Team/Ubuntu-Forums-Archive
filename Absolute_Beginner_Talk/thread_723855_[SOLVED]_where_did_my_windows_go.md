---
title: "[SOLVED] where did my windows go?"
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by wildwoodbill on 2008-03-13
I wasn't content to cut my teeth on one puter, I had to do two at once. 

Number one: (laptop) wouldn't partition for me (a new install of Gutsy over a recent install of Feisty) so I helped it along by going into Windows and deleting the partition Feisty was on. Bad news! Now Grub has error 17 and won't let me do anything. 

Number 2: My desktop which I was smart enough to back up before proceeding is dry docked too now. I tried looking into my disc details and can't seem to find partitions, it seems to only have the Ubuntu install files. Is there a secret door/window somewhere or did I really wipe windows? I've never even done a re-install before so this is really new. I must say that getting Windows back in the laptop was a reielf because I wouldn't be able to ask for help without a connection. Anybody got any silver bullets?

Summary:

My desktop on the other hand went smoothly enough with Gutsy but now I don't seem to have Windows (did I overwrite that partition?) although Gutsy is doing fine (a little pixilating but later right) it seems. So, I went from having no Windows and no Ubuntu on my laptop to having both but no modem recognition, hence no internet through Ubuntu.

---

### Post by czeckk on 2008-03-14
I really think that you should restate your problem...simplify...it seems you had a problem with one and then fixed it and had another but on the other...sigh...rewrite it please

---

### Post by bumanie on 2008-03-14
I agree. Members are happy to help, but one long paragraph with multiple issues is hard to follow. Could you put things into point form and differentiate between which computer is having which problem. It is best to sort one out at a time.

---

### Post by Sef on 2008-03-14
> Number one: (laptop) wouldn't partition for me (a new install of Gutsy over a recent install of Feisty) so I helped it along by going into Windows and deleting the partition Feisty was on. Bad news! Now Grub has error 17 and won't let me do anything

GRUB Error #17:

> 17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

What filesystem did you use?


> Number 2: My desktop which I was smart enough to back up before proceeding is dry docked too now. I tried looking into my disc details and can't seem to find partitions, it seems to only have the Ubuntu install files. Is there a secret door/window somewhere or did I really wipe windows? I've never even done a re-install before so this is really new. I must say that getting Windows back in the laptop was a reielf because I wouldn't be able to ask for help without a connection. Anybody got any silver bullets?


To find out if you have dual booted or overwritten Windows, do the following:

Applications > Accessories > Terminal

then type this code and paste the results in a new post:

```
sudo fdisk -l
``` (That's a small L.)

---

### Post by sandysandy on 2008-03-14
> **wildwoodbill said:**
> I wasn't content to cut my teeth on one puter, I had to do two at once. Number one (laptop) wouldn't partition for me (a new install of Gutsy over a recent install of Feisty) so I helped it along by going into Windows and deleting the partition Feisty was on. Bad news! Now Grub has error 17 and won't let me do anything.

use super grub disk ( [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/) ).

burn super grub disk as image onto CD and boot from it. (Live CD)

once booted u can browse thru the various options. one option is to fix MBR of windows. this should help u. the grub will be removed and u will boot directly into windows.

 >  My desktop on the other hand went smoothly enough with Gutsy but now I don't seem to have Windows (did I overwrite that partition?) although Gutsy is doing fine (a little pixilating but later right) it seems. So, I went from having no Windows and no Ubuntu on my laptop to having both but no modem recognition, hence no internet through Ubuntu. My desktop which I was smart enough to back up before proceeding is dry docked too now. I tried looking into my disc details and can't seem to find partitions, it seems to only have the Ubuntu install files. Is there a secret door/window somewhere or did I really wipe windows? I've never even done a re-install before so this is really new. I must say that getting Windows back in the laptop was a reielf because I wouldn't be able to ask for help without a connection. Anybody got any silver bullets?


please post output of 

sudo fdisk -lu

(for this command u will need to use terminal.  Applications--->  accessories ---->  terminal )

after analyzing output of the above command it can be determined whether the NTFS (windows) partition is there.

regards

---

### Post by wildwoodbill on 2008-03-14
I got this, my first terminal use.
~$ sudo fdisk -l 
 
Disk /dev/sda: 160.0 GB, 160000000000 bytes 
255 heads, 63 sectors/track, 19452 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0xe686f016 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1       19075   153219906   83  Linux 
/dev/sda2           19076       19452     3028252+   5  Extended 
/dev/sda5           19076       19452     3028221   82  Linux swap / Solaris

---

### Post by wildwoodbill on 2008-03-14
Thanks for the help you guys, Sef too for cleaning up my literary syntax.

$ sudo fdisk -lu 
 
Disk /dev/sda: 160.0 GB, 160000000000 bytes 
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Disk identifier: 0xe686f016 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *          63   306439874   153219906   83  Linux 
/dev/sda2       306439875   312496379     3028252+   5  Extended 
/dev/sda5       306439938   312496379     3028221   82  Linux swap / Solaris

---

### Post by bumanie on 2008-03-14
The output of your fdsik -lu indicates that you have indeed wiped your windows partition. If you need it back you will have to download test disk. Test disk is a data/partition recovery program that should be able to get atleast most, if not all your windows back. It will unfortunately in the process get rid of your ubuntu install however. You can reinstall it again of course. Get test disk here [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) It is a live cd and works well.

---

### Post by wildwoodbill on 2008-03-14
Thanks again I guess? I must have missed something on the install and screwed up with the partitioning. I'm done for the night now though.

---

