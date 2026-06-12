---
title: "Can not boot windows xp or access drive"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by sotonin on 2007-12-23
OK. here's my harddrive setup.

I have 2 sata drive.

first drive is setup with 2 partitions
-windows os partition
-data 1 partition

second sata drive has 4 partitions
-windows ntfs data partition
-ext3 / partition
-ext3 /home partition
-swap partition

i also have 2 IDE drives

both have 1 partition on each.

Windows is installed on first partition of the first sata drive.

I installed ubuntu on the last 3 partitions of the second sata drive. the MBR grub installed on first partition of the first drive so it would give me a boot menu.

The boot menu was created and lists Windows xp on it. but when i go to it it says something about no NTLDR found or something.... it worked fine before the install.

Also inside ubuntu it mounts all drives i have EXCEPT the windows os drive.

heres the output of my fdisk -l
```

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x33c333c3

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x362cb2ef

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       30401   244196001    7  HPFS/NTFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 320.0 GB, 320072933376 bytes
16 heads, 63 sectors/track, 620181 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x42a242a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       71111    35839912+   7  HPFS/NTFS
/dev/sda2           71112      620180   276730776    f  W95 Ext'd (LBA)
/dev/sda5           71112      620180   276730744+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e34f47f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       28695   230492556    7  HPFS/NTFS
/dev/sdb2   *       28696       33558    39062047+  83  Linux
/dev/sdb3           33559       38421    39062047+  83  Linux
/dev/sdb4           38422       38913     3951990   82  Linux swap / Solaris

```

and the contents of my /etc/fstab
```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=eb1c3251-51df-4de9-a85a-cb93a3dbfc50 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb3
UUID=e19c88bb-5c21-469b-84df-d15f6c6021c7 /home           ext3    defaults        0       2
# /dev/hda1
UUID=BA2CD32F2CD2E603 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hdb1
UUID=84C4A4EDC4A4E2A2 /media/hdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=10B06951B0693E7A /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=A6B4D5C4B4D59761 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=C628758B28757AEF /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb4
UUID=557f69fc-d477-4857-8280-2432eef39425 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

here is the contents of my /boot/grub/menu.lst
```

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd3,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=eb1c3251-51df-4de9-a85a-cb93a3dbfc50 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd3,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=eb1c3251-51df-4de9-a85a-cb93a3dbfc50 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd3,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd2,0)
savedefault
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1

```

any help would be greatly appreciated. i really hope i havent somehow hosed my windows install :(

SDA is where my windows install is located.

SDB is the harddrive with ununtu is installed

---

### Post by meierfra on 2007-12-23
Things to try:


1)  Go the the bios and make sure that the boot order is:

First IDE drive
Second IDE Drive
First SATA Drive (Windows OS)
Second SATA  Drive (Ubuntu)

If this did not solve the problem:

2)  Select Windows in the Grub menu at boot up. But to not press "enter". Press "e" instead

In the new screen change all the "2"'s  to "1". 
To do this press "e". This will let you edit the first line.
 Change "root (hd2,0)" to "root (hd1,0)". Press Enter.
Select the second line. Press "e"
Change "map (hd0) (hd2)" to "map (hd0), (hd1)". Press Enter
Select the third  line. Press "e"
Change "map (hd2) (hd0)" to "map (hd1), (hd0)". Press Enter

Next press "b"  to boot. If this did not work, try again, this time replace 2 by 0 and delete the two map lines.


If either of these did work, you need to edit "menu.lst" accordingly.

If  none of this  worked:

3)  Get supergrub (see my signature).

---

### Post by sotonin on 2007-12-23
DOH. unfortunately none of those recommendations worked.

I do not have a blank CD at the moment, only blank DVD-R. i guess ill have to make a run to the store tomorrow and try the supergrub thing.

---

### Post by meierfra on 2007-12-23
You can also install supergrub on a usb flashdrive.

But since none of that worked I would guess that there is something wrong with your windows partition. In particular since you are not able to access it from Ubuntu. Try this in a terminal in ubuntu:


```
mkdir  windows
sudo mount -t ntfs /dev/sda1 windows
```

You probably will get an error message.


Do you have  a Windows CD?

---

### Post by inertz on 2007-12-23
Change

title           Microsoft Windows XP Professional
root            (hd2,0)

to

title           Microsoft Windows XP Professional
root            (hd0,0)

---

### Post by sotonin on 2007-12-23
```

sudo mount -t ntfs /dev/sda1 windows
Unexpected clusters per mft record (-125).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

```

and i don't see how anything could be wrong with the windows partition. It was working 100% fine before the ubuntu install. its on a seperate hardrive from the ubuntu stuff and it should NOT have been touched.

I do have a windows disk. But i want to be able to dual boot both windows and ubuntu. I read you have to install windows first, thus my predicament.

---

### Post by meierfra on 2007-12-23
> WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

This could explain why you cannot mount your windows partition. You seem to have an unusual partition table. But I don't think that would prevent you from booting into windows.
But I don't really know. Do you know anything about GUID?


> and i don't see how anything could be wrong with the windows partition. It was working 100% fine before the ubuntu install. its on a seperate hardrive from the ubuntu stuff and it should NOT have been touched.

I agree,  So maybe your  GUID partition table requires  a special way of booting.  And   Ubuntu did overwrite the MBR. Which hard drive are you booting from right now? And which hard drive did you boot from before you installed ubuntu?  Did you have to  change the boot order according to my first suggestion 1) ?

Did you use any kind of special bootloader?

What was on the ubuntu partition before you installed ubuntu? Sometimes windows puts  booting  information on a different drive than the OS.

---

### Post by meierfra on 2007-12-23
> I read you have to install windows first

This is not all that important. Installing windows first is only slightly easier. But I'm not thinking about reinstalling Windows yet. You might use the Windows CD to fix the boot sector and the MBR via fixmbr and fixboot in the windows repair console. 

This might be worth trying, just to make sure Windows wasn't damaged. And fixboot might even solve your problem.

You would have to restore grub later on. But that is easy with the Ubuntu Live CD:

```
sudo grub
root (hd3,1)
setup (hd0)
quit
```

is all it takes to restore grub

---

### Post by sotonin on 2007-12-23
> 
I agree, So maybe your GUID partition table requires a special way of booting. And Ubuntu did overwrite the MBR. Which hard drive are you booting from right now? And which hard drive did you boot from before you installed ubuntu? Did you have to change the boot order according to my first suggestion 1) ?

Did you use any kind of special bootloader?


Same hardrive SDA is the one that booted windows. Same one that the grub is now on. I have not modified my boot order. It boots that hardrive above all others. I have no other bootable OS's. 

The hardrive that contains ubuntu used to be empty. I simply partitioned the empty space. so now it contains 3 ubtuntu partitions and one ntfs partition for storing data. (Which does show up in ubuntu as a mounted drive)

no special boot loaded at all.

ill try the fixboot stuff next and burn the grub cd...

for now off to the emergency room, my girlfriend is still sick after we went there on friday. really sucks so close to christmas :(

---

### Post by meierfra on 2007-12-23
I'im confused. My first instruction were to change the boot order so that the IDE drives are first in the boot order. But you never did that? Or did you try it and then reversed it? 

Booting from sda   means that sda is (hd0).
Well,  we did try (hd0) from the grub command line. But I would like to  try "rootnoverify" in place of "root". Maybe that avoids the problem with the strange partition table. So I suggest to use the following  as your Windows entry in "menu.lst"

title           Microsoft Windows XP Professional
rootnoverify    (hd0,0)
chainloader     +1

(you need to open menu.lst via "gksudo gedit /boot/grub/menu.lst" to be able to edit it.)

---

### Post by jingo811 on 2007-12-23
I'm not much of a GRUB and partition tables wizard but your problem looks really messy.  If I were you I would backup everything personal and do a complete make over for your 4 pieces of Hard drives.
And from there experiment with all the possible partition setups you would like to use and then transfer all your personal data back to your PC.  When the operating systems co-operates without any problems.

> **sotonin said:**
> 
OK. here's my harddrive setup.  I have 2 sata drive.

**first drive is setup with 2 partitions**
[LIST]
[*]-windows os partition
[*]-data 1 partition
[/LIST]

**second sata drive has 4 partitions**
[LIST]
[*]-windows ntfs data partition
[*]-ext3 / partition
[*]-ext3 /home partition
[*]-swap partition
[/LIST]

i also have 2 IDE drives both have 1 partition on each.


If I were in your shoes I would put all operating systems partitions on the first hard drive like this.
Like I said I'm not a very technical person I like to fix things the UGLY way by deleting and exorcising everything on your HD's.

**HD_1 (sata)**
[LIST]
[*][COLOR="Sienna"]Windows OS[/COLOR] (primary) - 10 GB
[*][ /=root ] [COLOR="Sienna"]Ubuntu OS[/COLOR] (primary) - 10 GB 
[*]Windows programs/games (logical) - around 20 GB
[*]unpartitioned free space for future expansion - the rest
[/LIST]

**HD_2 (sata)**
[LIST]
[*]Windows pagefile partition (logical) -1 GB
[*][ swap ] Linux (logical) - 1 GB
[*][ /home ] Linux (logical) - over 20 GB, the rest
[/LIST]

**HD_3 (ide)**
[LIST]
[*]whatever you want
[/LIST]

**HD_4 (ide)**
[LIST]
[*]whatever you want
[/LIST]

---

### Post by sotonin on 2007-12-23
Oh sorry. yeah i didn't fiddle with the boot order at all, there IDE drives don't have any bootable drives. My mistake. But yeah the hd0 didnt work either...

ill try with the new flag in a bit. I'll be at the hospital for a while unfortunately. girlfriend has sepsis (bacteria in the blood) and they wont let her leave for a while...

thanks for the assistance. hopefully ill square this all away after the hospital mess.

merry christmas :)

---

### Post by sotonin on 2007-12-23
Yeah. the thing is. ... I did this because i got a new harddrive and basically wanted ubuntu off on its own hardrive. i wanted to isolate it so it woudlnt effect anything else... little good that did huh!

the hardrive ubuntu is on is 300G so its plenty for anything i might need

---

### Post by meierfra on 2007-12-23
Did you try the "rootnoverify (hd0,0)"?  

I'm pretty sure your Windows Partition is intact. If "rootnoverify" did not work, I suggest to fix the MBR and make sure that Windows is working. (Click on FixMBR in my signature for a couple of ways to fix the MBR)

---

### Post by sotonin on 2007-12-23
OK. i'm really starting to wonder what the heck is going on.

The noverify thing did not work. When i put that in there, and choose windows it just reloads the grub again. infinite loop.

I loaded up a windows CD and went to recovery console. tried the whole fixmbr thing and fixboot. No tomale.

i read your fixmbr thing and tried the

sudo ms-sys -m /dev/sda

thing. .. No change. Grub still comes up.

I burned a copy of the supergrub thing but havent had a chance to load it up yet. it seems my options are running out.... I am not against reformatting that partition. ..  i wont lose much... most the data . documents etc are on another partition, which is still active.. I just am not sure exactly how to go about it.

thanks again

---

### Post by meierfra on 2007-12-23
If grub still comes up after "fixmbr" and "ms-sys -m /dev/sda", then  probably  grub is not installed on the MBR of the  sda.  And if that is true, then reformating /dev/sda1 might not solve your problem.  
Are you sure that you are booting from sda?

I suggest to   physically disconnect all the hard drives but sda. Just so we can isolate the problem.

---

### Post by meierfra on 2007-12-23
Even if you want to reinstall, I suggest to disconnect all the drives but the sda. At  least disconnect the two IDE drives. Grub and Ubuntu  don't like a mix of  SATA and IDE drives during installation.

---

### Post by meierfra on 2007-12-23
Don't  reinstall yet.  I have done some research and it seems that Grub  and GPT (your kind of partition table)) don't mix very well. Installing Windows and Ubuntu onto on sda is probably not going to work.

---

### Post by meierfra on 2007-12-23
What kind of computer to you have?

---

### Post by jingo811 on 2007-12-24
> **meierfra said:**
> Don't  reinstall yet.  I have done some research and it seems that Grub  and GPT (your kind of partition table)) don't mix very well. Installing Windows and Ubuntu onto on sda is probably not going to work.

Do you have some links to your reading material this sounds interesting I've heard about this happen before in these forums.  Don't know if they solved things it was also one big mess.

---

### Post by sotonin on 2007-12-24
There's really nothing special about my computer... and honestly i think i may know what the problem is....

I've been thinking while i was sitting around at the hospital about possible reasons why it's acting wierd.

I will of course try disconnecting everything except the 2 sata's and then install the os's. Thats my best bet.

Here's a quick recap of my ubuntu experience this time around.

I installed from the live cd the first time. Let it do all its stuff. and when it reboot and i removed the cd, nada happened. Windows resumed starting up like normal like the grub was never installed....  so i figured out.. wierd. i'll try the alternate cd.

I installed from the alternate cd the next round. choosing to format the 3 ubuntu partiitions again so it's from scratch again... Let its do it stuff. it popped up saying it found windows do i want to install grub on the MPT. i said sure. go ahead. it rebooted removed the cd and nada.. still windows....

so i said wtf. this is retarded....

i proceeded to do it yet again after reading a bit more on the forums, i figured out how to go back on that step and manually choose a location to install grub.

i chose /dev/sda1

first partition on sda.... now that i think back about it. that may have been the wrong choice. i probably should have just done /dev/sda for the whole disk... maybe somehow i corrupted that single partition, since it seems to be the only one affected... maybe this is why it loops when we tell it to load that partition for the windows option?

The hardrive is nothing special. just a NTFS partition installed by the windows XP pro install process... seagate harddrive nothing spectacular. thats why it is odd that it would be something out of the ordinary..

this is just an idea mind you, i'm far from a linux guru... quite a novice with installing it anyways. But my best guess...

So if this were the case. technically i might be able to reinstall that single partition with windows. then i'd somehow have to install grub back to just /dev/sda ... without installing ubuntu again preferably... but if not i could sit through another install. sat through 3 already haha.

I think the best bet is probably the removed the IDE's so its not confused though. I'll do that when i get some more free time.

---

### Post by sotonin on 2007-12-25
if anybody else has any thoughts on my idea about why it happened please let me know. i'd like to hear what the linux experts think about the situation. :)

---

### Post by sotonin on 2007-12-25
Welp. That did it!

it had to have been the targeting of the specific partition to install grub that screwed the pooch.

I disconnected the power on the 2 ide drives.. reinstalled XP pro on the same partition (erased and created new one in xp install partitioner) and got it functional.

Then i ran through the ubuntu alternate install again. this time when it got to the grub part i let it take care of it auto to hd0 

and this time it worked! both windows and ubuntu work from grub... now to plug my other harddrives back in and hope it keeps on working ! :)

thanks for the assistance folks!

---

### Post by meierfra on 2007-12-25
it seems jingo811   was right.  One of my many character flaws is that I never recommend reinstalling unless I  completely run  out of ideas.   Also I was convinced reinstalling would not work.  Since  reinstalling work, I  now have no idea  whatsoever what caused your problems.. Oh well.

I'm hope your girlfriend is recovering  well.

---

### Post by sotonin on 2007-12-25
I spoke too soon!!! i'll admit i havent had a chance to search yet about it. doing it now...

Here's the deal now...

With both IDE disconnected works like a charm both OS's will load up perfectly. As soon as i connect one of the IDE i get grub error 22 and nothing works...

i tried loading up the super grub disk and it was really confusing. i'll go look around for more detailed instructions. anyways ill check this thread also during my search.

thanks again!.

she's recovering.. unfortunately she wont get out today possibly tomorrow. christmas in the hospital really sucks ! :(

well i'm looking around and either the forum search sucks or i must be crazy. but searching for "error 22" or "grub 22" or "grub error 22" all comes up empty.... ok i'm at a loss now.

---

### Post by meierfra on 2007-12-25
This might be easy to fix. Change the boot order to 
SATA 1
SATA 2
IDE
IDE

---

### Post by sotonin on 2007-12-25
Thats the first thing i tried.. they are already in that order. :(

---

### Post by meierfra on 2007-12-25
Well we have to start all over again, The situation seems to be different than the  first time. So maybe we can solve it. Connect all the hard drives. Boot from the live cd.  Post the output of 

```
sudo  fdisk -l 
```

See whether you can mount windows or ubuntu (see post 4 for the general method)

For ubuntu use:

```
mkdir ubuntu
sudo mount -t ext3 /dev/sda2 ubuntu
```

But in place of  sda2, use the actual partition ubuntu is one ("fdisk -l" should tell you the partition)

If that was successful, post the output of

```
cat ubuntu/boot/grub/menu.lst
```

---

### Post by meierfra on 2007-12-25
> the forum search sucks 

Actually it does. Use google instead.

---

### Post by sotonin on 2007-12-25
fdisk -l
```

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x33c333c3

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x362cb2ef

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       30401   244196001    7  HPFS/NTFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 320.0 GB, 320072933376 bytes
16 heads, 63 sectors/track, 620181 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x42a242a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       71111    35839912+   7  HPFS/NTFS
/dev/sda2           71112      620180   276730776    f  W95 Ext'd (LBA)
/dev/sda5           71112      620180   276730744+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e34f47f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       28695   230492556    7  HPFS/NTFS
/dev/sdb2   *       28696       33558    39062047+  83  Linux
/dev/sdb3           33559       38421    39062047+  83  Linux
/dev/sdb4           38422       38913     3951990   82  Linux swap / Solaris

```

from the output i thought that ubuntu was the bootable partition sdb2

so i used.

```

sudo mount -t ext3 /dev/sdb2 ubuntu

```

---

### Post by sotonin on 2007-12-25
doh, nm i'm dumb.. ok.. it mounted.. heres the output..

```

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a71de822-43b0-436d-a5af-df4c31db83f5 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=a71de822-43b0-436d-a5af-df4c31db83f5 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1


```

I am also able to mount my windows partition just fine.. and access everything on it... 

So i think we're down to a grub specific issue... grub wont load period with these drives connected. it acts like it will then immediately says Error 22

---

### Post by meierfra on 2007-12-25
Lets try reinstalling grub:

```
sudo grub
root (hd1,1)
setup (hd0)
quit
```

Reboot any error messages.

Also just to save jingo811 some work:  He/she had recommended to put  Ubuntu and XP on  the same drive.  

Don't  do that yet. Try my current suggestion. If that does not work,  I have one more thing I would like to try. But after that I'll give up.

---

### Post by sotonin on 2007-12-25
```

root (hd1,1)

Error 22: No such partition

```

---

### Post by meierfra on 2007-12-25
That's  actually  progress.  Give me a couple of minutes to sort out the next move.

---

### Post by meierfra on 2007-12-25
Actually that  was just a stupid suggestion from my side. Try this

```
sudo grub
root (hd3,1)
setup  (hd3)
quit
```

Then open menu.lst


```

gksudo gedit ubuntu/boot/grub/menu.lst
```

(this assume that Ubuntu is mounted)

change 

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,1)

to

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)

Save the file. And reboot. Change the boot order such that the SATA 2 (the ubuntu drive) is first.

This should get you into ubuntu. We'll work on XP  later.

---

### Post by sotonin on 2007-12-25
Worked like a charm.

I am into ubuntu. I tried windows and yes, as you suspected it's toasted with a NTLDR error.

Also my IDE drives were not auto detected / mounted in ubuntu.

(i mounted them manually to media folder)

---

### Post by sotonin on 2007-12-25
Anyways. i'm off to the hospital to keep the gf company.. I'll keep checking the forums from time to time :)

curious as a side note i read somewhere about a "automounter" what is this where can i get it?

---

### Post by meierfra on 2007-12-25
Let's work on XP next. From Ubuntu (not the live cd)

```
gksudo gedit /boot/grub/menu/lst
```


Change 


title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactivechainloader     +1

to

title           Microsoft Windows XP Professional
root            (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader     +1

Save the file and reboot.  Still with Sata 2 in the  first place.

If this did not work, you can try the same thing we did yesterday.Namely  press "e" at the grub menu at boot up. And change all the 1's  to 2's,  and if that did not work, change all the 1's to 3's.

If any of those worked, change menu.lst accordingly.

If it didn't use your XP CD to  run  "fixmbr" on Sata 1. Then you should be able to boot into XP by booting from SATA 1

---

### Post by sotonin on 2007-12-25
It worked as well!. You are my hero. i noticed the drives i mounted are gone now upon reboot... back to my question about automounter :)

---

### Post by meierfra on 2007-12-25
>  automounter

Sorry, no idea.   You could mount them by adding them to fstab. But I guess that isn't the recommend method.  Do the IDE drives automount if  you plug them in after you booted into Ubuntu?


Just to make sure: Are you able to boot even if the  IDE drives are unplugged?

Also  you need to edit menu.lst one more time (could have done that earlier, but I wasn't sure that things would work out at the time. )  Open menu.lst as usual .

Change 

#groot (hd1,1)

to

#groot(hd0,1)

This is necessary, otherwise your "root(hd1,0)" line  will turn back to "root (hd1,1)"  during the next kernel update, 

Save the file. Then in a terminal

```
sudo update-grub
```

Now that we changed "groot" this will change all the "root (hd1,1)"  to  "root (hd0,1)". This will allow you to  run "recovery mode" and "memtest" from the Grub Menu at boot up.


Finally I recommend   to    fix the MBR of the SATA 1 drive with your Windows CD.(or via sudo ms-sys -m /dev/sda). This way, if anything happens to Ubuntu, you still will be able to boot XP by booting from SATA 1. It will not effect your current setup since Grub is installed on SATA 2.

---

### Post by meierfra on 2007-12-26
> . the MBR grub installed on first partition of the first drive so it would give me a boot

> i chose /dev/sda1
first partition on sda.... now that i think back about it. that may have been the wrong choice. i probably should have just done /dev/sda for the whole disk..


I can't believe that I overlooked this the whole time.  That's what caused all  your  problems.  What  you called the  MBR of the first partition of your first  hard drive, really is    the XP boot sector. So you destroyed  the XP boot sector. No wonder that you couldn't boot it anymore. 

It  also explains why grub still came up after fixmbr and ms-sys: This restores the Windows MBR. Now the Windows MBR just puts  the boot sector of the active partition in charge.  But that's  where Grub was sitting.

Allhough I don't understand why "fixboot" did not take care of the problem.


Just for future reference, The best choice probably have been to install grub  /dev/sdb and switching the boot order. That's  what you have now.  Keeps the OS's nicely separated.

---

### Post by sotonin on 2007-12-26
OK i did all that you mentioned. :)

I will test if i unplug them to see if grub still works.

as far as plugging them in while ubuntu is up, they are internal. i dont think it's wise to do this while the machine is running hehe.

My other harddrive partitions were detcted and auto mount after every reboot. But it only had drives that were present during the ubuntu install, not the new drives i connected... 

hmm

---

### Post by meierfra on 2007-12-26
Since they are internal, they need to be added to fstab. Ubuntu adds all  internal drives to fstab during installation, but since you unplugged the IDE drives you will need to add  them manually. If you need help with that   post the output of

```
sudo blkid
```

---

### Post by sotonin on 2007-12-26
```

kevinh@kevinh-ubuntu:~$ sudo blkid
/dev/sda1: UUID="D278F60078F5E361" TYPE="ntfs" LABEL="WINXP_OS" 
/dev/sda5: UUID="A6B4D5C4B4D59761" LABEL="SYS_DATA" TYPE="ntfs" 
/dev/sdb1: UUID="C628758B28757AEF" LABEL="DATA2" TYPE="ntfs" 
/dev/sdb2: UUID="a71de822-43b0-436d-a5af-df4c31db83f5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb3: UUID="51e9cc33-268b-43f9-841a-87c5a9306505" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb4: TYPE="swap" UUID="557f69fc-d477-4857-8280-2432eef39425" 
/dev/hda1: UUID="BA2CD32F2CD2E603" LABEL="MUSIC" TYPE="ntfs" 
/dev/hdb1: UUID="84C4A4EDC4A4E2A2" LABEL="DATA1" TYPE="ntfs"

```

Music and Data1 are the missing drives...

---

### Post by meierfra on 2007-12-26
Since the are internal there is also no reason to test whether booting works when they are unplugged.

Open fstab via

```
gksudo gedit /etc/fstab
```

The easiest way to add the two partition is to just  copy the lines you have for "sda5 /Sys_Data" and change the UUID according to blkid and change the mount points.

Or you can copy and paste this:

 #/dev/hda1
 UUID="BA2CD32F2CD2E603"  /media/MUSIC   ntfs  defaults,umask=007,gid=46 0    1
#/dev/hdb1
 UUID="84C4A4EDC4A4E2A2" /media/DATA1 ntfs  defaults,umask=007,gid=46 0    1

Here you can replace /media/MUSIC and /media/DATA1 by anything you want to. But you need to create those directories if you don't have them yet.

---

### Post by sotonin on 2007-12-26
Sweet i got that working.. something wierd happened probably along the step when i was doing the groot thing..

cause after i rebooted linux was broken... wnidows worked fine.. i booted up live cd and it had somehow changed my entries from what you had told me to manually input... i changedthem back again using this thread and they work again.

my drives mounted great :)

---

