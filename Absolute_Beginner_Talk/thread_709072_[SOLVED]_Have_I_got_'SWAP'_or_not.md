---
title: "[SOLVED] Have I got 'SWAP' or not?"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by FrancesL on 2008-02-27
Hi, I have actually had a go at reading a lot of the info of previous threads about SWAP but I am still unsure if I have SWAP or not? I have been keeping an eye on systems monitor as I have been finding that after a few hours of browsing then maybe playing a game or 3 at Club Pogo, I slow down to such an extent that I just cant use the computer at all. It is worse with Pidgin running, am using Meebo webIM instead. Whatever I am doing the above, the memory can get really used up, usually so much I cant use sys monitor eventually, but at the same time SWAP is showing 0% used. I thought swap was used to help reassign RAM ? maybe I am wrong, any clues? Thanks in advance. Oh, specs in signature

---

### Post by jan quark on 2008-02-27
linux tries to use all your RAM memory first before accessing the swap

you can look up if you have a swap partition with

```

sudo fdisk -l
```

---

### Post by Arkenzor on 2008-02-27
No, you don't have any swap space (see "0 bytes of 0 bytes"). Did you create your partitions yourself when you installed ubuntu? If so, you probably forgot to create a swap partition.

An alternative would be using a swap file, supposedly it's about as fast as a whole partition but can be put on an existing partition without disturbing the data on it. I'll see if I can find info on that again.


EDIT: [This guide](http://www.debian-administration.org/articles/550)  explains a simple way of creating a swap file (since it's a Debian guide I guess it's compatible with ubuntu too).

it's up to you to decide wether you want to keep the default size of twice your RAM or reduce it, but I think having more than 1GB total "RAM" is fairly useful nowadays.

---

### Post by FrancesL on 2008-02-27
> **jan quark said:**
> linux tries to use all your RAM memory first before accessing the swap

you can look up if you have a swap partition with

```

sudo fdisk -l
```
Output is:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         513     4120641   82  Linux swap / Solaris
/dev/sda2   *         514        9729    74027520   83  Linux


Not sure about this, but does that mean YES? if so : is there a way to tell Ubuntu to use Swap more effieciently?

---

### Post by FrancesL on 2008-02-27
> **Arkenzor said:**
> No, you don't have any swap space (see "0 bytes of 0 bytes"). Did you create your partitions yourself when you installed ubuntu? If so, you probably forgot to create a swap partition.

An alternative would be using a swap file, supposedly it's about as fast as a whole partition but can be put on an existing partition without disturbing the data on it. I'll see if I can find info on that again.
 Thanks for info, I bought the laptop with Linux Ubuntu installed about 3 weeks back. 

Very new, very exciting, not expecting the World from this entry level laptop, but living on a pension, at least it is better than the alternative. I would like though, to get through a day of surfing, collecting email , chatting to mates on Pidgin and playing a round or three of Pogo without the need to restart so often. I will eventually, funds permitting, update RAM but that must wait. So any suggestions for the here and how, will be gratefully received.

---

### Post by Arkenzor on 2008-02-27
Judging from your fdisk output, you do have a swap partition ready, but the OS doesn't seem to know about it. You should take a look at your /etc/fstab file and check if you have a line like this:
```
/dev/sda1 swap swap defaults 0 0
```
If not, please post the contents of your fstab (you may also simply add this line in it, but your fstab may already contain an entry for /dev/sda1 in another format. Don't know what happens when you specify the same device twice but I wouldn't try it on my computer).

---

### Post by FrancesL on 2008-02-27
> **Arkenzor said:**
> Judging from your fdisk output, you do have a swap partition ready, but the OS doesn't seem to know about it. You should take a look at your /etc/fstab file and check if you have a line like this:
```
/dev/sda1 swap swap defaults 0 0
```
If not, please post the contents of your fstab (you may also simply add this line in it, but your fstab may already contain an entry for /dev/sda1 in another format. Don't know what happens when you specify the same device twice but I wouldn't try it on my computer).
 Ok, now I am confused..what code do I use to get that information in Terminal please?

---

### Post by Ianman on 2008-02-27
```
sudo gedit /etc/fstab
```

I think. You basically need to open the file that controls which partitions are mounted when you start Ubuntu up. When Gedit opens (text editor) look for the line Arkenzor mentioned.

---

### Post by FrancesL on 2008-02-27
> **Ianman said:**
> ```
sudo gedit /etc/fstab
```

I think. You basically need to open the file that controls which partitions are mounted when you start Ubuntu up. When Gedit opens (text editor) look for the line Arkenzor mentioned.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=bfff9d67-250f-4b91-a536-a87033e209e3 /               ext2    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=e6160560-3163-4e49-a6d2-6dc841ab145c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


Ok thats what I got..what do I interprut that to mean in relation to my original question? thanks

---

### Post by Ianman on 2008-02-27
Can someone please post their fstab contents for FrancesL? I am not currently able to get to my Ubuntu box and post mine for comparisson...

FrancesL,

It indeed looks as though your swap partition is not being mounted. If noone has answered before I get home I will post the contents of my fstab file so that we can compare.

Sorry I can't help right away!

---

### Post by mister_pink on 2008-02-27
Open the fstab file again with the same command, stick a '#' in front of the line under '# /dev/sda1' so it reads:
#UUID=e6160560-3163-4e49-a6d2-6dc841ab145c none swap sw 0 0
Then add this to the bottom:
/dev/sda1 none            swap    sw              0       0

Then restart. Open up the system monitor and it should say something bytes of something_which_isnt_zero bytes!

Edited: not sure if that was right before. Its definitely ok now, I copied it from my own fstab.

---

### Post by FrancesL on 2008-02-27
[QUOTE=mister_pink stick a '#' in front of the line under '# /dev/sda1' so it reads:
#UUID=e6160560-3163-4e49-a6d2-6dc841ab145c none swap sw 0 0
Then add this to the bottom:
/dev/sda1 none            swap    sw              0       0

Then restart. Open up the system monitor and it should say something bytes of something_which_isnt_zero bytes!

Edited: not sure if that was right before. Its definitely ok now, I copied it from my own fstab.[/QUOTE]

Followed your kind instructions and from this sudo gedit /etc/fstab after restart I got: 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=bfff9d67-250f-4b91-a536-a87033e209e3 /               ext2    defaults,errors=remount-ro 0       1
# /dev/sda1
#UUID=e6160560-3163-4e49-a6d2-6dc841ab145c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sda1 none swap sw 0 0

 Is this all I need do?

---

### Post by FrancesL on 2008-02-27
> **FrancesL said:**
> 


 Is this all I need do?

Thanks ...Swap is in play (so to speak) so many thanks to you for you kind assistance!

---

