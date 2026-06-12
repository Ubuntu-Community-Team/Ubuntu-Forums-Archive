---
title: "[SOLVED] GRUB Error 17.. help please"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by lian1238 on 2007-09-18
Hi
I got this Error 17 in grub right after I deleted a NTFS partition from Windows (it was /media/sda8 from ubuntu). At first, I couldn't even boot into windows, it stops after the error and there wasn't any OS choice, so I booted from my winxp cd and went into recovery console, typed:
```
fixmbr
```
after this, it booted into winxp right away. So, I put the ubuntu livecd in and in the terminal I typed this:
```

$ sudo grub
grub> find /boot/grub/stage1
 (hd0,7)
grub> root (hd0,7)
grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,7)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.
grub> quit

```
Now, I get my grub screen which looks like before: 4 choices for ubuntu, memtest and winxp. But, when I choose ubuntu, it still shows Error 17: cannot mount selected partition. I don't know what else to do.

Any help would be much appreciated..
(I am posting this from the livecd)

---

### Post by ajgreeny on 2007-09-18
I wonder if the grub menu shows the UUID of the ubuntu partition and it has changed since you got rid of the windows partition.  Check the UUID of your partitions using a live CD and the command[B]
ls -l /dev/disk/by-uuid [/B] 

If the ubuntu partition is different from that in the menu.lst file it may be the reason for the error so you will need to mount the partition using just the dev/hda# or dev/sda# and then edit the menu.lst file accordingly.

Of course, I could be completely wrong about the reason, in which case it will need a greater brain than mine to help you out, I'm afraid.  Good luck!

---

### Post by meierfra on 2007-09-18
It's unlikely that the UUID has changed. Try this first:

At the grub menu select "ubuntu" but do not press "enter". Instead press "e".
You get a new screen, the top line should  say "root (hd0,8 )". Press "e" again.
Change  the 8 to  7, so that is says "root (hd0,7)". Press "enter". 
This gets you back to the previous screen.
Press "b" and  you should boot into ubuntu.

If this worked you need to make the changes permanent by editing the file 
 /boot/grub/menu.lst:
In a terminal (applications->accessories->terminal)  type

```
gksudo gedit /boot/grub/menu.lst
```
( the l is a lower case L)

Change all appearances of 

root (hd0,8 )  

to 

root (hd0,7)

Save the file. You can test it by rebooting.

---

### Post by Duck2006 on 2007-09-18
Post the output of

fdisk -l

---

### Post by lian1238 on 2007-09-18
> **meierfra said:**
> It's unlikely that the UUID has changed. Try this first:

At the grub menu select "ubuntu" but do not press "enter". Instead press "e".
You get a new screen, the top line should  say "root (hd0,8 )". Press "e" again.
Change  the 8 to  7, so that is says "root (hd0,7)". Press "enter". 
This gets you back to the previous screen.
Press "b" and  you should boot into ubuntu.

If this worked you need to make the changes permanent by editing the file 
 /boot/grub/menu.lst:
In a terminal (applications->accessories->terminal)  type

```
sudo gedit /boot/grub/menu.lst
```
( the l is a lower case L)

Change all appearances of 

root (hd0,8 )  

to 

root (hd0,7)

Save the file. You can test it by rebooting.

Wow, that fixed it! Thanks, **meierfra**, you're a lifesaver!

If you don't mind, could someone tell me what happened? Next time I want to delete a windows partition, is this likely to happen again?

---

### Post by meierfra on 2007-09-18
Well, before you deleted the windows partition, ubuntu was on  sda9, the ninth partition on your hard drive. In grub language sda9 is (hd0,8 ). ( Grub starts counting at 0. So (hd0,8 ) is the ninth partition on the first hard drive.   So then ubuntu was installed, grub got instructed to look for the file  menu.lst on (hd0,8 ).  You deleted   a partition  and ubuntu   became  the eighth partition, (hd0,7).  But grub still was looking for menu.lst on (hd0,8 ). You fixed this problem by reinstalling  grub.

Now the grub menu appeared at boot up. The file  menu.lst contains instruction how to find the various operating systems, in your case it says to look for ubuntu on (hd0,8 ). Since ubuntu is no longer on (hd0,8 ) you got another error message.

If you want to learn more about grub, check out the hermanzone grub page:

[http://users.bigpond.net.au/hermanzone/p15.htm]("http://users.bigpond.net.au/hermanzone/p15.htm")


And yes, the same thing will happen the next time you delete a partition. But now you know how to fix it. You might even reinstall grub and edit /boot/grub/menu.lst  just before you  delete the partition, and you won't have any problem booting.

---

