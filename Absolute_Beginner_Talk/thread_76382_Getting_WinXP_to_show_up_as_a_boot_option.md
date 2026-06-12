---
title: "Getting WinXP to show up as a boot option"
date: 2005-10-15
forum: Absolute Beginner Talk
---

### Post by Souljah on 2005-10-15
Hi. I posted this question a few days back, now what I setup is this:

1. WinXP which is alloted 15 gigabytes.

2. Ubuntu which is alloted for 10 gigabytes.

3. A FAT32 Filesystem for sharing with windows and linux.

Now I want to, when my computer restarts to show up windows xp as an option. By default, it goes straight to ubuntu without giving me an option. Before when I dual booted with winxp and win2k, it showed me in a DOS like structure which OS to boot up. How do I get up windows xp to show up with ubuntu? I'm right typing this out in ubuntu. Some help please :smile:

---

### Post by Kokanee on 2005-10-15
Assuming that Windows is on the first partition of the first hard drive then add this to [FONT=Courier New]/boot/grub/menu.lst

In a terminal type:
```
sudo gedit /boot/grub/menu.lst
``` 
then add...

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1
``` 
Change the [/FONT][FONT=Courier New] **root (hd0,0) **line if yor Windows is installed somewhere elese.
[/FONT]

---

### Post by Souljah on 2005-10-15
How do I find out which hd my windows xp is on? Thanks.

---

### Post by Kokanee on 2005-10-15
From the terminal do the following command:

```
sudo fdisk -l
``` 
It should show something like...

```
Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19928   160071628+   7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9541    76638051   83  Linux
/dev/hdb2            9542        9729     1510110    5  Extended
/dev/hdb5            9542        9729     1510078+  82  Linux swap / Solaris

``` 
This will be all your partitions. Look for one labelled as HPFS/NTFS or VFAT and that is Windows. In my case it is /dev/hda1 which means it is on hard drive A (or 1) and partion number 1. However in the menu.lst file they start counting at 0 not 1 so it would be hard disk 0 and partition 0.

Clear as mud right? :)

---

### Post by Souljah on 2005-10-15
Trying it out right now.

---

### Post by Souljah on 2005-10-15
Before I edit these changes, can you just let me know this if I should set also at hd5. It shows it's on hd6.

Disk /dev/hda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2               1        3648    29302528+   f  W95 Ext'd (LBA)
/dev/hda5            1276        1912     5116671    c  W95 FAT32 (LBA)
/dev/hda6            1913        3648    13944388+   7  HPFS/NTFS
/dev/hda7               1        1275    10241343   83  Linux

Partition table entries are not in disk order

The code you told me to put in, should I put it like this: root        (hd5,5)

Last thing, what is the chainloader?

---

### Post by darkmatter on 2005-10-15
hda6 would be (hd0,5)

a chainloader, in simplest terms, is used to boot an OS which is not supported natively. (it will tell GRUB to hand control over to that systems boot-loader), in this case XP.

---

### Post by Souljah on 2005-10-15
It did not work out. I did that procedure and it still went directly to linux. This is how it is on my menu.lst:

--
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda6
title        Microsoft Windows XP Professional
root        (hd0,5)
savedefault
makeactive
chainloader    +1
--

So did I do anything wrong there or what? Some help please.

EDITED TO ADD: I had to press ESC to see the menu list. Lol I am dumb. Anyway, I chose windows xp but it gave me this error message:

root (hd0,5)
 File System Type Unknown, partition type 0x7
savedefault
makeactive

Error 12: Invalid device requested

Press any key to continue...

---

### Post by Souljah on 2005-10-15
bump

---

### Post by coopns on 2005-10-15
I am considering installing ubuntu, but this is my biggest concern. I (my wife) needs to have the choice to go to xp for work, and I (she) would like xp to be the default. Xandros had it built into the control panel area for easy change.

As I noted, I have Xandros, if I install ubuntu on a new partition, will it automatically install a new grub or lilo, considering I already have it installed.

Please keep it really simple.

Thanks.

---

### Post by aysiu on 2005-10-15
Just type this in the terminal ```
sudo nano /boot/grub/menu.lst
``` You'll notice a line that says ```
default 0
``` That really means the default boot entry is the first one. The second one would be ```
default 1
``` The third would be ```
default 2
``` and so on. Find which entry the Windows one is (it may be the fourth or fifth entry), and change the default number appropriately. Once you're done, type 
control-x
y
Enter

You're done. Windows should now be the default boot option from Grub.

---

### Post by Souljah on 2005-10-16
Can anyone assist me here? WinXP doesn't load up because of that error message, could you guys tell me what is wrong. There is nothing wrong with windows, I had done a complete format. I need some help please.

---

### Post by Jussi Kukkonen on 2005-10-16
[QUOTE=Souljah]
root (hd0,5)
 **File System Type Unknown, partition type 0x7**
savedefault
makeactive

Error 12: Invalid device requested
[/QUOTE]


Hmm... Sounds familiar. You could try this: Go into your bios settings, find the hard drive setting called LBA or Large Access Mode, and set it to *LBA* or *LARGE* (or anything else but *AUTO*).

---

### Post by Arjen on 2005-10-16
Souljah, unless I'm very much mistaken Windows must ALWAYS be on (hd0,0) as that is where it's automatically installed. It doesn't work on anything else in fact. Could you set it to root(hd0,0) and test that?

coopns: While I'm not entirely sure here, I do believe that when you install Ubuntu there will be a new installation of grub as well. It will replace the Xandros one. If you want them both (e.g. if you install Ubuntu on a different partition than Xandros) you'll have to add the Xandros part manually to your grub list. This isn't very hard, especially if you first print out your menu.list in Xandros. Just look for the entry you always select to start it and enter that part into your new Ubuntu menu.list. The Windows part should be added automatically if you tell it to during the installation.

---

### Post by Jussi Kukkonen on 2005-10-16
[QUOTE=Arjen]Souljah, unless I'm very much mistaken Windows must ALWAYS be on (hd0,0) as that is where it's automatically installed. It doesn't work on anything else in fact. [/QUOTE]

Could someone confirm this? I thought this was true for DOS but not for modern Windowses... In case Arjen is right, one could use the *map* command in grub to 'fake' (hd0,5) as (hd0,0).

Souljah, could you run 
```
sudo cfdisk
```
and copy-paste the table here?

---

### Post by Arjen on 2005-10-16
Jussi Kukkonen, after reading your message I checked and it seems I was wrong. I think I was confused with something else. Thanks for the correction. Souljah, this means you can simply ignore what I said.

---

### Post by BLTicklemonster on 2005-11-19
```
bill@ubuntu:~$ sudo fdisk -l
Password: berfunkleykabiblermonickerstifirneglorpagordonkgordonkpfftsssssaaaaah

Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9729    78148161   83  Linux
/dev/hda2            9730       10011     2265165    5  Extended
/dev/hda5            9730       10011     2265133+  82  Linux swap / Solaris

Disk /dev/hdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9963    80027766    7  HPFS/NTFS
bill@ubuntu:~$

```

so my xp is on hdb1, what do I put? I put 1,0 not knowing any better, thinking that slave would be 1, and first partition would be 0. Good news is, it now shows up when I hit esc (wish I didn'thave to do that, but would have an automatic choice, but if it will work, I'll deal with it).

---

