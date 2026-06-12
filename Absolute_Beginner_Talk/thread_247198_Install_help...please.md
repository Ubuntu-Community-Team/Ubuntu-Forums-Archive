---
title: "Install help...please?"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by wana10 on 2006-08-30
sorry about the pathetic sounding title but i had thought that maybe i had begun to get a grasp of linux. on my old computer it installed and booted no problem, but my new computer...well, thats why i'm here.
i ordered my new computer from a smaller company and although i ordered windows xp pro with it i asked them not to install it. so my computer comes from ups last night and i open it up. there is the familiar blue package with holographic disk so i quickly find my other familiar brown package with red disk. everything i had read said that windows should be installed first because it doesn't play nice with others, so i put in the windows disk and 2 hours later i'm staring at a familiar desktop, a few things aren't recognized but i decide to deal with that later. now to install ubuntu. i reboot into the live environment and double click install. now my problems start.
1) first problem, when i get to the partitioning it will not allow me to shrink my ntfs partition to make my linux and share partition. i found that if i drop the boot flag on the ntfs i can resize it and then put the boot flag back on, but this feels like opening a peanut with a hammer and i'm sure there is a better solution. (note: i have same problem in alternate text installer)
2) after the install rushes through the computer reboots and i'm facing the grub screen, i find this odd because it never actually asked where i wanted to install grub, and some of the guides i read said that it would, oh well it look correct, afterall there is windows and ubuntu. I first boot into windows and after a disk check it boots fine...but ubuntu doesn't. ubuntu loads necessary drivers and then sits at the root check, then it says waiting for root, and then finally it says "ALERT! cannot fin ubuntu at /dev/sda2 dropping to shell" and leaves me at a prompt. on my old computer the hard drive was always hda and most of the people here seem to have it as hda, so why is mine sda (i ask as it seems to be the cause of my problems)
any help would be greatly appreciated, otherwise i may have to resort to only running windows and booting ubuntu in parallels or vmware (neither of which i really want to do)

---

### Post by Tomosaur on 2006-08-30
This could be a little tricky considering your situation, but could you please post the output of the following two commands:
```

cat /boot/grub/menu.lst

```
and
```

sudo fdisk -lu

```

There's a console-based web-browser called lynx which will enable you to get online and post here, so you could try that (be warned, it's ugly), or you could email the output to yourself or something. If you want to convert the output to a text file, do this:
```

cat /boot/grub/menu.lst > GrubMenu.txt

```
and
```

sudo fdisk -lu > MyDrives.txt

```

---

### Post by PPAAUULL on 2006-08-30
Ok If there is nothing on the windows side then I would just reformat the hdd and set a partition for windows and save one for Ubuntu then install ubuntu on this partition and there should be no problems.

---

### Post by bruce89 on 2006-08-30
/dev/sda is just a SATA drive /dev/hda is a normal PATA drive.
> **PPAAUULL said:**
> Ok If there is nothing on the windows side then I would just reformat the hdd and set a partition for windows and save one for Ubuntu then install ubuntu on this partition and there should be no problems.

You'd have to reinstall GRUB after that - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by taurus on 2006-08-30
If you are using EIDE, then it's /dev/hda but if you have a SATA on your machine, then it's called /dev/sda!!!  You need to tell GRUB where is your root partition, /, in /boot/grub/menu.lst.  So, boot your machine with the LiveCD again, mount your Ubuntu, and edit menu.lst...

---

### Post by PPAAUULL on 2006-08-30
Reinstalling grub isn't hard though. The installation does it for you.

---

### Post by bruce89 on 2006-08-30
> **PPAAUULL said:**
> Reinstalling grub isn't hard though. The installation does it for you.

What I meant was if Windows was installed after Ubuntu, GRUB would have to be reinstalled, as Windows likes to pretend there are no other OS's.

---

### Post by PPAAUULL on 2006-08-30
Oh ok, and I ment that you install windows on one partition first then Ubuntu on the other next.

---

### Post by wana10 on 2006-08-30
ok i've booted into the live cd but have no internet so im typing from my other comp.

sudo fdisk says ive got 4 partition at dev/sda1,2,3,5 but i can't mount any of them, it says they dont exist... when i try the grub commands from [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) it says they don't exist...blast.
i'm gonna give PPAAUULL's plan a shot

i think it goes without saying that as i can't mount sda as it doesn't exist:confused: i can't edit grub menu.lst

well, i'll be back in a couple hours, thanks for the initial help

---

### Post by PPAAUULL on 2006-08-30
You are welcome and I hope it all turns out good for you.

---

### Post by wana10 on 2006-08-30
well...no dice, in fact its worse now than it was. i have a 100 gb hard drive. when i installed windows i gave it 70gb and left the rest. when i installed ubuntu i made a 20 gb shared partition, 9 gb for /, and the last gb for swap. the install continued on as normal and then said remove disk and reboot. i did so, grub came up, and only ubuntu was an option, no windows to be seen. so i tried ubuntu anyway and once again it loaded drivers ok. then it looked for root waited for root, and crashed to shell. im outa ideas, the live cd still says that sda doesn't exist.

edit* ok so fdisk says that i have the partitions on the drive, but nothing else can see them...:confused:

---

### Post by wana10 on 2006-08-30
ok...new ballgame. i booted from knoppix, which interestingly enough found and mounted all of my partitions. i could also see my grub menu.lst, but i couldn't edit the damn thing. so i'm trying something new, i'm trying the install ubuntu from knoppix in the wiki ([https://help.ubuntu.com/community/Installation/FromKnoppix](https://help.ubuntu.com/community/Installation/FromKnoppix)) but when i try to run debootstrap im told permission denied. any one know how to go around this?
once again, any help would be greatly appreciated.

---

### Post by confused57 on 2006-08-30
Here's a similar thread using the live cd to install grub:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

You can edit grub by highlighting the Ubuntu entry at startup, press "e" and try some different things to see if you can boot, for example change root (hd0,1) to root (hd0,2), etc.  This is only a temporary fix, but if a change works you can make it permanent in your /boot/grub/menu.lst...

---

### Post by wana10 on 2006-08-30
ok heres the setup
sda1 is windows ntfs
sda5 is /
sda6 is swap
sda7 is /share

when I push e in grub on ubuntu it shows

root (0,4)
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/sda5 ro quiet splash
initrd /boot/initrd.img-2.6.15-26-386
savedefault
boot

i press b to boot and it loads driver and can't mount root file system. i don't know why as it seems that grub is pointing to /dev/sda5 which was formatted as / in the install...

i'm so utterly lost...i've dug through the install sections of every internet guide i could find and the 3 linux books i have and i'm befuddled. blast:-k

---

### Post by wana10 on 2006-08-30
ok did a manual edit of grub to boot windows, installed the ext2fs windows drivers and then edited menu.lst through windows notepad. now i can boot into windows but i'm still completely lost on how to fix ubuntu...piss, and i thought my ati card would be the biggest problem](*,)

---

### Post by confused57 on 2006-08-30
Your grub entry to boot Ubuntu looks OK, you might want to try:
rootnoverify  (hd0,4)

Could you boot with the live cd, open a terminal, and post the actual output of?:

```
sudo fdisk -l
```
The -l is a small "L"

---

### Post by wana10 on 2006-08-30
i have since reinstalled linux to a primary in the hope of fixing the problems, now sda2 is my / and sda3 is /home
```
knoppix@0[knoppix]$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9138    73400953+   7  HPFS/NTFS
/dev/sda2            9139       10182     8385930   83  Linux
/dev/sda3           10183       12030    14844060   83  Linux
/dev/sda4           12031       12161     1052257+  82  Linux swap / Solaris
```

tried 5.10 to see if it would work, it didn't, back to dapper and logical so extended is sda2, / is sda5, /home is sda6, and swap is sda7

---

### Post by wana10 on 2006-08-31
ok...now i'm just befuddled by the stupidity of my situation...check code below to see why
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9138    73400953+   7  HPFS/NTFS
/dev/sda2            9139       12161    24282247+   5  Extended
/dev/sda5            9139       10182     8385898+  83  Linux
/dev/sda6           10183       12030    14844028+  83  Linux
/dev/sda7           12031       12161     1052226   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mount /dev/sda5
mount: can't find /dev/sda5 in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo mkdir /mnt/sda5
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt/sda5
mount: special device /dev/sda5 does not exist

```

if fdisk says it exists how THE BLOODY HELL can it not exist 5 lines later!?!?!?!?
i read some other posts on this same situation and it said that ubuntu liked mounting sata srives in odd places so i edited menu.lst with everything from sda5 to sdf5 and still nothing

in other slightly better news this post is coming from my ubuntu live cd instead of knoppix so at least i managed to get the network working...less work when i get ubuntu fully up and running;)

---

### Post by wana10 on 2006-08-31
while trying to run the uuid fix it told me that sda5 didn't exist, so i ran gparted. gparted shows the partitions but the terminal outputs
```
ubuntu@ubuntu:~$ sudo gparted
The device /dev/sda1 doesn't exist
dumpe2fs 1.38 (30-Jun-2005)
dumpe2fs: No such file or directory while trying to open /dev/sda5
dumpe2fs 1.38 (30-Jun-2005)
dumpe2fs: No such file or directory while trying to open /dev/sda6

```
saying it doesn't exist...maybe i'm just crazy

---

### Post by wana10 on 2006-08-31
ok i may have found another solution. some other posters have reported success by downgrading their kernel. unfortunately i have no idea how to do this without logging in.
if someone could tell me how to downgrade my kernal without having the ability to boot that would be great. thanks for the help.

---

### Post by onlyoneskwalla on 2006-09-13
Your Root=(hd0,4) doesn't look right to me, that means that the /boot is on the fifth partition of your hardrive which is kinda hard to belieave specially since you only have 4 partitions. I believe you need to reconfigure grub. Grub counts up from zero so if you /boot is locate on your linux root partition then by what you've shown on this forum your root=(hd0,1). This is most certainly your problem. 

Way to reconfigure grub-

sudo -s
grub
device (hd0) /dev/sda
root (hd0,1)
setup (hd0)
quit

Now run

update-grub

if it asks to whether to make /boot/grub/menu.lst say yes

I believe that is all you'll need to do based on your setup, if you'd like to know my reference here's a link[FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto")

Quick Note: Not sure if this will resetup grub for windows also, if not you probably know the way to edit /boot/grub/menu.lst since you've already done it once.  You could also do what this fix manually simply by editing /boot/grub/menu.lst and replacing all instances of ROOT (hd0,4) with ROOT (hd0,1) or the like.

---

