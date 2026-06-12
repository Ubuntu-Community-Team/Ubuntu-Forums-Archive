---
title: "Error on starup &quot;fsck failed&quot;"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by SILENTFACTOR on 2007-09-11
Hi there I am new here and to Linux(Unbutu) so I hope I put this in a the right place.
 I recieved a dell with Unbutu and 2 hard drives that was working fine. I tried to read/copy the data on the drives through XP on another computer. Now when I put the drives back in the original comp. I get "fsck failed", "Run fsck MANUALLY to repair" and "Drive set to Read- Only
         # mount -n -o remount, rw

Is there a way I can get this to reboot normally without loosing any info on the disks? Any help would be appreciated.

---

### Post by Kobalt on 2007-09-11
You should try to boot your computer with a LiveCD and then run fsck from there. Here is some help on how to use fsck : [http://adminschoice.com/docs/fsck.htm](http://adminschoice.com/docs/fsck.htm)

---

### Post by bodhi.zazen on 2007-09-11
Basically (In a nutshell)

Plug in the hard drive

Boot to a live CD

Open a terminal and enter :

```
sudo fsck -y /dev/hdxy
```

where /dev/hdxy is the partition to check/fix

To list your partitions *sudo fdisk -* (that is a small L and not the number 1)l

If that fails, you have serious problmes :twisted:

Post the output  ....

---

### Post by SILENTFACTOR on 2007-09-12
Hi again, thanks for the info. I down loaded and burned a CD. Now I guess my question is, how do I run a terminal from this. It has an option to repair a system but it seems like it will try installing Ubuntu again if I choose that option. Again, any help would be appreciated. Thanks

---

### Post by Polemistis on 2007-09-12
u need to use the live cd to enter the terminal... select Install/Run ubuntu from the boot screen of cd

---

