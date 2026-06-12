---
title: "rescue mode root"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by Marfish on 2007-12-09
K, so I am a noob to linux. I am currently in the middle of a rescue mode as I cannot get it to boot any other way. It is asking me for a root, and I am not sure what command I should be putting in there. I have linux on an external hard drive and what it is asking looks like this:

root@marlon-laptop:~#

I tried putting in hd0,0 and it came back with this

bash:  hd0,0: command not found

What should I be putting in there to make it go forward, and what can I expect to deak with afterwards?

---

### Post by Marfish on 2007-12-09
*bump*

---

### Post by annda on 2007-12-09
what happens exactly when you try to do a regular boot?

technically, the root recovery boot in ubuntu is meant to give you full access to the system so that you will be able to solve a problem.

---

### Post by mcduck on 2007-12-09
It's not asking you anything. It's telling you that you are now logged in as user 'root' on a computer called 'marlon-laptop'. That's the command prompt, waiting for you to enter commands.

Could you tell more about what the actual problem is so we can tell you what you need to do to solve it? What happens when you try to boot into normal desktop?

---

### Post by Marfish on 2007-12-09
I come up with error 17, so I change the root to hd0,0 instead of hd1,0. It then starts to boot up, but stops at a certain point in the kernel. I believe this is because it is on a different computer than which I installed linux onto the external drive. Unfortunately, my original computer doesnt give me the option to edit the root and always give me error 17 whenever I try to boot. So, im just trying to make the root change permanent so I can boot it on my original computer.

---

### Post by Marfish on 2007-12-09
Im trying to permanently change the root hd1,0 to hd0,0.

---

### Post by annda on 2007-12-09
> **Marfish said:**
> Im trying to permanently change the root hd1,0 to hd0,0.

if you are sure this is the solution, then what you need to do is use a text editor (for example nano) to modify the grub configuration file:

```
nano /boot/grub/menu.lst
```

ctr+o to write the file, ctr+x to quit nano

---

### Post by ajgreeny on 2007-12-09
If your ubuntu is still only on the external drive, boot into the rescue mode and when you get to the prompt
root@marlon-laptop:~#
enter fdisk -l
(that's a lower case L, not a 1 at the end)
That will give you an output with disk information on it and we will need to know what the line(s) containing "ext3" say in detail.  You should then be able to edit your menu.lst file to allow you to boot ubuntu properly.  usually the partition should be the same as the recovery mode, so I'm slightly baffled but give it a try and let's see where we go from there.

You could also put grub on the external disk instead of the MBR of the main internal hard disk.  Then as long as the machine has been set to boot from the external disk first, then internal disk second, it should go straight to ubuntu when the external disk is attached.  When not attached the machine will boot as usual into the system on its own hard disk.

---

### Post by mcduck on 2007-12-09
OK, you'll need to edit the Grub's configuration file to do that.

Run  "nano /boot/grub/menu.lst" to open the file for editing. Then find following sections and change the root partition in them:

```
## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)
```

```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=694c24ca-a0f0-48a4-a3$
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=694c24ca-a0f0-48a4-a3$
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

```
(The first one is the default setting, it's used when the Grub menu is regenerated durin kernel updates Other entries are the actual boot lines. )

When you are done, hit Ctr-X to save & exit the editor. After that run 'reboot' to restart the machine.

---

### Post by Marfish on 2007-12-09
K, so I followed your advice to start the nano and get into the grub. Right now I see the default root for linux is (hd0,1) and for windows is (hd0,0). Should I switch the two or make them both the same? I also see the ones you have listed except they are listed (hd1,0), lol, what should I do?

---

### Post by mcduck on 2007-12-09
> **Marfish said:**
> K, so I followed your advice to start the nano and get into the grub. Right now I see the default root for linux is (hd0,1) and for windows is (hd0,0). Should I switch the two or make them both the same? I also see the ones you have listed except they are listed (hd1,0), lol, what should I do?

If you don't know the right partitions run the 'fdisk -l' command and post the output here.

---

### Post by Marfish on 2007-12-09
Device boot           start         end               blocks              id          system
/dev/sda1  *                1      14592         117210208+        7       hpfs/ntfs

Disk /dev/sdb: 120.0 gb, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
units = culinders of 16065 * 512 = 8225280 bytes
disk identifier: 0xb1732e49

Device boot          start            end          blocks            id         system
/dev/sdb1   *             1         14029      112687911       83       linux
/dev/sdb2             14030      14593      4530330           5         extended
/dev/sdb5             14030      14593      4530298+        82       linux swap / solaris

Lol, that took me a while to right down. So, what do you make of it? This is an external hard drive.

---

### Post by mcduck on 2007-12-09
> **Marfish said:**
> Device boot           start         end               blocks              id          system
/dev/sda1  *                1      14592         117210208+        7       hpfs/ntfs

Disk /dev/sdb: 120.0 gb, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
units = culinders of 16065 * 512 = 8225280 bytes
disk identifier: 0xb1732e49

Device boot          start            end          blocks            id         system
/dev/sdb1   *             1         14029      112687911       83       linux
/dev/sdb2             14030      14593      4530330           5         extended
/dev/sdb5             14030      14593      4530298+        82       linux swap / solaris

Lol, that took me a while to right down. So, what do you make of it? This is an external hard drive.
Based on that, the windows is on the first partition of the first hard disk, so the right entry for Grub would be (hd0,0).

Linux is on the first partition of the second drive, and it's entry is (hd1,0). The default root is the same.

---

### Post by annda on 2007-12-09
since you are on a different computer, we don't know what your original windows partition is. ubuntu is definitely sitting at hd1,0 so you can safely change that. leave windows as it is and try to boot with **your** computer.

---

### Post by Marfish on 2007-12-09
I changed the groot to hd0,0 and the three others, but it still has them set to hd1,0 at start up. Should I be changing something else?

---

### Post by Marfish on 2007-12-09
*bump*

---

### Post by annda on 2007-12-09
please post your whole /boot/grub/menu.lst file.

---

