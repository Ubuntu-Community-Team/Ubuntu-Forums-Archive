---
title: "Three sets of Ubuntu to choose from when booting"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by xjosie729 on 2007-02-18
When I am turning on my computer, at the screen where I can choose the Operating system to boot into, I see three sets of Ubuntu. I installed it twice, the first time it froze at 75% so I restarted and installed again. I checked the reformat option and installed it. Then I [made the swap partition]("http://ubuntuforums.org/showthread.php?t=359309") and there's three. How can I get rid of two of them? Thanks for any help!

---

### Post by skyhopper88 on 2007-02-18
Those just sound like different kernals. It's best to keep those on the list so if one gets messed up you can go back to a previous one and troubleshoot the problem.

---

### Post by Bloch on 2007-02-18
Whenever the kernel is updated the old kernel is left untouched and appears as an option on the boot screen. I think I have 4 or 5 'ubuntus' on my boot menu at this stage!!

Your multiple ubuntu installations are probably separate partitions, taking up space etc.

Run gparted as superuser i.i
su gparted

and take a look at your partitions. By examining the sizes can you figure out which one is the one holding the ubuntu installation you wish to keep?

Then reformat the others and delete them, and then increase the size of your main partition to take up the spare space.

---

### Post by livingtarget on 2007-02-18
You are probably see the kernel list in the beginning, there should be 3 options. Your default Kernel 2.6.17 something, Kernel 2.6.17 **Safe Mode** and some Memory Test boot option. If that's what you are seeing then there's nothing to worry about.

---

### Post by mcduck on 2007-02-18
When you get a kernel update the new kernel is installed, and old one is also kept so if you have troubles with new one you can still access your computer by selecting the old one from Grub menu.

When you are sure that the new kernel is working fine you can simply uninstall old kernel version using Synaptic (or apt-get or whatever you like). This will also automatically remove the extra entries from Grub menu.

Anyway, if you believe you might have installed Ubuntu multiple times please post the output of 'sudo fdisk -l' here. (this will list all your hard disks and partitions.)

---

### Post by linux_kid on 2007-02-18
To remove the extra items, type the following in terminal,
```
cp /boot/grub/menu.lst /boot/grub/menu.lst.old
```
The code above will copy your menu file to make sure you can restore if something goes wrong.

Now type this command to edit the menu,
```
sudo gedit /boot/grub/menu.lst
```
It will ask you for your password and then a large text file will come up.

Scroll down near the bottom of the page until you find the boot entries.  They should look similar to this,
```
title		Ubuntu Edgy Eft 6.10 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu Edgy Eft 6.10 Recovery
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title		Compaq Restore Partition
root		(hd0,3)
savedefault
makeactive
chainloader	+1

```
The area where it states "title" in every boot entry is how the entries are named

To remove an entry, simply select all text associated with it and click delete.

If you need any more help, post here:popcorn:

---

### Post by xjosie729 on 2007-02-18
@Bloch: I manually configured the partitions so they were all installed in the same place, and I made sure I checked "format".

@linux_kid: Thanks, I think that'd helped, but I'll have to restart to see. I hope it works because last time I made changes to Ubuntu, I couldn't even boot into Windows.
[edit]
It worked, thank you!

---

### Post by mcduck on 2007-02-18
just removing the entry from grub is like only solving half of the problem.. You still have all those kernels & related files wasting your disk space, and without entry in Grub you won't even be able to use them..

I just uninstalled my previous kernel & headers, freeing 173MB of disk space. And that was just for one kernel version. If you always just remove the entries you'll end with gigabytes of useless stuff on your harddisk..

Just search for 'linux' in 'name':

---

### Post by linux_kid on 2007-02-18
Don't worry about loosing Windows, we made a backup copy, remember :guitar:

---

