---
title: "dual boot help"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by cmaranhao on 2006-10-08
i installed vmware but that won't solve my problem.. i knew that not all software (cad/cam programs) would be able to run in vmware but i tried anyway..

now, i must set up a dual boot.. but i have some questions i would like to be answered:

1)i have my main hard drive partitioned in two.. i have ubuntu installed in the first partition. is it possible to set up windows in a new partition without formating my current ubuntu partition? my idea is something like this (keep in mind i don't want to format the first partition, the one my ubuntu OS is installed):

1st partition - ubuntu instalation
2nd partition - windows
3rd partition - used to back files in ubuntu

2)each time i power on my pc, i want to run ubuntu by default, without the need to press any button.. like, after i turn the pc on, it goes to a menu with a time counter, if i do not choose to run windows, it goes for linux on its own.

---

### Post by bergfly on 2006-10-08
Bad news here, but windows needs that first partition to install into. However, the good news is you can simply copy your ubuntu to the second partition, however, then you will need to edit the Grub menu. If you don't have too much on the Ubuntu partition, then it might be easier to start again.

Install windows

Install Ubuntu

done!
By default ubuntu will run after the Grub counter counts down.

---

### Post by _lynX on 2006-10-08
> **cmaranhao said:**
> i installed vmware but that won't solve my problem.. i knew that not all software (cad/cam programs) would be able to run in vmware but i tried anyway..

now, i must set up a dual boot.. but i have some questions i would like to be answered:

1)i have my main hard drive partitioned in two.. i have ubuntu installed in the first partition. is it possible to set up windows in a new partition without formating my current ubuntu partition? my idea is something like this (keep in mind i don't want to format the first partition, the one my ubuntu OS is installed):

1st partition - ubuntu instalation
2nd partition - windows
3rd partition - used to back files in ubuntu

2)each time i power on my pc, i want to run ubuntu by default, without the need to press any button.. like, after i turn the pc on, it goes to a menu with a time counter, if i do not choose to run windows, it goes for linux on its own.

I recently went through with this same situation. The only problem that I ran into was the fact that Windows places its boot manager over Grub so you cannot boot into Linux right away after installing Windows. This is simple enough.

Simply partition your current partition in the correctly-sized partitions you would like to use using gparted, then use the Windows installation cd and choose the partition you set aside for it to use (I am not sure if you need to make this partition FAT32 when using gparted or not) and install it to that partition. Once you have gone through all of the Windows installation stuff and you are ready to boot back up into Windows, insert your Ubuntu Live CD and restart.

Load up into the Ubuntu Live environment, and then open a console. You will then need to configure Grub.

```

sudo grub
root (hd0,0) # First hard drive, first partition.
setup (hd0) # This will set up Grub to boot from the root.
quit
reboot

```

Once you reboot, the Grub loader will show up and give you the option of loading the menu. If you don't press escape, it will load straight to Ubuntu. Now that you're back in Ubuntu, you will need to add Windows XP to the Grub menu.

```

sudo nano /boot/grub/menu.lst

```

Add the following in it's appropriate place at the bottom of the file:

```

title           Windows
root            (hd0,1) # First hard drive, 2nd partition.
makeactive
chainloader     +1

```

These are the steps I followed to install Windows on a seperate partition, so I hope they work out for you!

---

### Post by Kateikyoushi on 2006-10-08
Install windows on the second partition, it will overwrite your mbr so you have to restore grub. [Follow this guide.]("http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub")

---

### Post by _lynX on 2006-10-08
> **bergfly said:**
> Bad news here, but windows needs that first partition to install into.

Not true. I currently have Windows as the second partition on my hard drive.

---

### Post by gn2 on 2006-10-08
An alternative strategy which will allow you to keep your Ubuntu entirely unchanged is to add another hard drive to install Windows to, and press F8 (or whatever) at boot time to select which OS to boot from.

When installing Windows, disconnect the Ubuntu drive.

If you have IDE drives, Windows will need to be master. Ubuntu will be happy as slave.

If you have a laptop, it is possible to have Ubuntu on a USB2 external drive.

This way, both drives are completely independent of each other, which is a distinct advantage.

---

### Post by Kateikyoushi on 2006-10-08
If he adds a new master drive for windows wouldn't it change his current ubuntu drive from hda to hdb ?

---

### Post by gn2 on 2006-10-08
> **Kateikyoushi said:**
> If he adds a new master drive for windows wouldn't it change his current ubuntu drive from hda to hdb ?

No it will stay hda, and the Windows drive can be added and named later.

The two drives and bootloaders are entirely separate 

mbr and windows on one drive,

grub and Ubuntu on another.

If each are installed with the other turned off, they will not know each other is there.

This is the safest way I know of dual-booting, it's like having two PC's in one box.

Access to files across drives can be configured later if desired. (Subject to file system compatibility)

---

### Post by cmaranhao on 2006-10-08
i decided to install windows first on the 1st partition, linux second on the second partition.. but one major thing happened>

from all the times i formated my hard drives before, it never happened to me.. 

when installing windows, at the time you can choose your regional settings, keyboard types, etc, i had no mouse..

for the first time i can-t choose those settings with a mouse.. i thought it was odd so i just pressed enter until the instalation completed.. guess what, i don-t have mouse in windows!!!!!!!!!

do you know what happened?

---

### Post by gn2 on 2006-10-10
Did you have the PC connected to the internet during install?

You may have picked up a virus?

---

