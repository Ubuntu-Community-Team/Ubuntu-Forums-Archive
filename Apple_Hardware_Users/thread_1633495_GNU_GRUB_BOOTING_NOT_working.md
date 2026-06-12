---
title: "GNU GRUB BOOTING NOT working"
date: 2010-11-29
forum: Apple Hardware Users
---

### Post by idealistic on 2010-11-29
hi 
 
ive been using ubuntu lucyd lynx qnd then updqted to mqverick
ubuntu was working fine but this morning when i tried to start the computer i end up on a screen telling me :
 
GNU GRUB version 1.98+20100804-5ubuntu3
 
Ubuntu, with linux 2.6.35-23-generic
Ubuntu, with linux 2.6.35-23-generic (recovery mode)
Ubuntu, with linux 2.6.35-22-generic
Ubuntu, with linux 2.6.35-22-generic(recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200
 
use the up arrow and the down arrow keys to select which entry is highlighted. press enter to boot the selected OS, 'e' to edit the commands before booting or 'c' for a command-line.
 
 
Ive tried all 4 os's but nothing work.
it just gets stuck in the middle of the process and nothing happens.
 
i have some important unbacked up data in my computer so is there any way i can get it to work without reinstalling ubuntu ?
 
thanks

---

### Post by drs305 on 2010-11-29
When it gets 'stuck', what is displayed on the screen? 

If it's a grub problem we can probably figure it out if we get some more information. Please run the boot info script from the following site and post the contents of the RESULTS.txt:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by idealistic on 2010-11-29
yeah well i cannot access anything else from my coomputer than this first screen so icannot really run the thing u r saying.
 
the command lines that are used for the booting are these ones : 
 
recordfail
insmod part_gpt
insmod ext2
set root='(hd0,gpt2)"
search --no-floppy --fs-uuid --set bf6b26d1-c458-490d-beab-6728d80921fc
linux /boot/vmlinux-2.6.35-23-generic root=UUID=bf6b26d1-c458-490d-beab-6728d80921fc ro    quiet splash
initrd /boot/initrd.img-2.6.35-23-generic
 
its hard to tell you what the results are cuz i cannot see it all.
all i can see is that it tells me :
mount : mounting /dev on /root/dev failed : No such file or directory
mount : mounting /sys on /root/sys failed : No such file or directory
mount : mounting /proc on /root/proc failed : no such file or directory
Target filesystem doesn't have requested /sbin/init
 
is that pf any help ?

---

### Post by drs305 on 2010-11-29
You would run the boot info script after booting to the Desktop of a LiveCD (Ubuntu installation CD) - sorry I wasn't more specific.

It looks like you are using GPT partitioning. I'm afraid I don't know a lot about how that interacts with G2.

Without seeing the RESULTS.txt and no knowledge of GPT issues, you could try editing your menuentry. From the G2 menu display on boot, highlight the first entry and press "e" to edit. Use the cursors to move to the start of the 'search' line and use the DEL key to completely remove the line.

Next move to the 'linux' line and remove the UUID and replace it with the device name (sda2). I am assuming your Ubuntu install really is on sda2....
I don't know if the "root=/dev/sda2" will work with GPT, but you can try it.

Once you get the menu looking like the following, CTRL-x and see if it boots:
> 
recordfail
insmod part_gpt
insmod ext2
set root='(hd0,gpt2)"
linux /boot/vmlinux-2.6.35-23-generic **[COLOR="DarkRed"]root=/dev/sda2[/COLOR]** ro quiet splash
initrd /boot/initrd.img-2.6.35-23-generic


If it still fails, see if your boot files really are in sda2. From the Grub menu, press "c", then:
```
ls (hd0,2)/boot
```
Are your Ubuntu kernel and initrd image there?

---

### Post by idealistic on 2010-11-29
oh, i dont have a live CD
 
and replacing with sda2 didnt change anything to the results ...
 
i typed ls (hd0,2)/boot :
 
config-2.6.35-23-generic abi-2.6.35-23-generic
System.map-2.6.35-23-generic memtest86+.bin vmcoreinfo-2.6.35-23-generic
initrd.img-2.6.35-23-generic vmlinuz-2.6.35-23-generic
System.map-2.6.35-22-generic config-2.6.35-22-generic abi-2.6.35-22-generic
vmcoreinfo-2.6.35-22-generic memtest86+_multiboot.bin
vmlinuz-2.6.35-22-generic initrd.img-2.6.35-22-generic
 
does that tell you something ?

---

### Post by drs305 on 2010-11-29
You may be able to fix this by running an fsck check on your drives if it's a partition/drive issue. If it's a grub problem, reinstalling G2 may also be the solution. The bottom line though is that these will need to be accomplished from a LiveCD. You can get the ISO to burn from here:
[http://www.ubuntu.com/desktop/get-ubuntu/download]("http://www.ubuntu.com/desktop/get-ubuntu/download")

---

### Post by idealistic on 2010-11-29
alright, is it possible to do it from a usb stick ?
i have a macbook 2.1 and i burnt the iso file on the usb but i dont know how to make it work ...

---

### Post by drs305 on 2010-11-29
You can make a bootable thumb drive. You'd have to google for how to do it. Search for "unetbootin" I think.

You could also try to use this procedure I wrote for booting an ISO from Grub2. Since your Grub files probably aren't corrupt, it may work if Grub can see the thumb drive:
[HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt]("http://ubuntuforums.org/showthread.php?t=1599293")

---

### Post by idealistic on 2010-11-29
hum i have a live cd now.
so could you tell me a bit more about the fsck check and reinstalling G2 ?

i got a strange thing navigating through the command line with ls

i can see my files for example ls (hd0,2)/home/usr/
but if i go further (example ls (hd0,2)/home/usr/Music) the computer instantly restarts.
well im happy because if i can almost see my files i guess they r not lost but i still dont understand how to do anything ...

---

### Post by drs305 on 2010-11-29
First try to fsck the partition. It cannot be mounted. So if you see it in Places, right click and select "unmount". Or from a terminal, run (assuming sda2 is the Ubuntu partition)
```
sudo umount /dev/sda2
```
Then perform an fsck check with this:
```
sudo e2fsck -f -y -v /dev/sda2 
```

Once you have run the check, you might also accomplish this before rebooting. Mount your Ubuntu partition again, then reinstall grub:

```
sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt  /dev/sda
```

Reboot and if you are still having difficulties, boot the LiveCD and completely purge then reinstall G2 using the chroot procedures in this guide:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by idealistic on 2010-11-29
ok,
sorry to bother again but do i need to put on the CD the same ubuntu version than the one i already have ? i have the 10.10 would it work if the cds version is 9.04 for example ?

---

### Post by idealistic on 2010-11-29
and i have another problem now : 
if i put the cd the screen just reamins blank and nothing happens
do u have an idea why ?

---

### Post by drs305 on 2010-11-29
> **idealistic said:**
> ok,
sorry to bother again but do i need to put on the CD the same ubuntu version than the one i already have ? i have the 10.10 would it work if the cds version is 9.04 for example ?

Yes, in this case it should be ok. *e2fsck* would work properly. Since you will be chrooting into your Ubuntu installation, you should get the version of Grub2 from your real Ubuntu sources.list, and even if not the 9.04 version would have a older version of Grub2 that you could use to get your system back up.

---

### Post by idealistic on 2010-11-29
yes so i have a live cd with the 10.10 version, i put it in the computer, start it and nothing happens.

this seems so desperate i cant even reinstall the system ...

---

### Post by drs305 on 2010-11-29
> **idealistic said:**
> yes so i have a live cd with the 10.10 version, i put it in the computer, start it and nothing happens.

this seems so desperate i cant even reinstall the system ...

Is BIOS set to boot first from the CD? (Enter BIOS to change the boot order if not.)

Is the CD spinning?

Do you see the two icons in the middle bottom of the screen? If so, and the CD continues to 'hang', you may need to set certain boot options. You may be able to call up preset options by pressing the F6 key about the time you see those two icons.

Have you had problems booting a LiveCD in the past?

If 10.10 won't work but 9.04 will, it won't hurt to at least boot and run the e2fsck check. If that doesn't work and you still can't boot, I'd do the purge/reinstall even if you need to use the 9.04 CD. 

If you have to boot the 9.04 CD, after you chroot into your real install, open your /mnt/temp/etc/apt/sources.list and change the Ubuntu "main" repository to "maverick". You can leave all the other repositories as they are, since you will only be downloading packages from the 'main' repository. Save the file, then run "apt-get update" before installing grub-pc (and by default, since it's a dependency, grub-common).

---

### Post by idealistic on 2010-11-29
ok i managed to boot from the CD 
actually i just forgot to press'c' at the beginning :)

soooo i tried the things you describe but i seem to fail to chroot into my real system
i mean how long is it supposed to take to mount sd ?
after i type the mount command, i waited for 30 minutes but it was still in process.
do u think there's a problem or shall i just be waiting longer ?

---

### Post by drs305 on 2010-11-29
> **idealistic said:**
> ok i managed to boot from the CD 
actually i just forgot to press'c' at the beginning :)

soooo i tried the things you describe but i seem to fail to chroot into my real system
i mean how long is it supposed to take to mount sd ?
after i type the mount command, i waited for 30 minutes but it was still in process.
do u think there's a problem or shall i just be waiting longer ?

The partition should mount in less than 10 seconds. 

> i mean how long is it supposed to take to mount sd ?
I assume this is a typo and you are trying to mount sda2?

The commands for you should be (I added the unmount command for sda2 in case it's mounted):
```

sudo umount /dev/sda2
sudo mkdir /mnt/temp 
sudo mount /dev/sda2 /mnt/temp  
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf  # May be required to connect to the Internet.
sudo chroot /mnt/temp
```

---

### Post by idealistic on 2010-11-29
ok
i ; sure i follozed your procedure
sda2 is not mounted so i type sudo mkdir /mnt/temp and it creates the dirctory fine
but then : sudo mount /dev/sda2 /mnt/temp
and nothing happens
when i try to quit the terminal it says that there is still a process running

is there a way to fix that ?

---

### Post by drs305 on 2010-11-29
> **idealistic said:**
> 
is there a way to fix that ?

The most sure way is to reboot the LiveCD and start over. It would be better than trying to figure out which processes were mounted and trying to kill them.

---

### Post by idealistic on 2010-11-29
ok i tried burning a new cd and everything i still get the same thing (would not mount sda2)

i tried sudo fdisk -l

```
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           1        2047+  ee  GPT
/dev/sda2   *           1        9328    74920960   83  Linux
/dev/sda3            9328        9730     3227648   82  Linux swap / Solaris

```

does that help ?

---

### Post by drs305 on 2010-11-29
It does help in that the problem seems to be focusing on a GPT issue. You are going to have to await someone more familiar with that partitioning scheme or search for the answer from previous posts.

To be honest, with the number of posts already made in this thread there will probably not be a lot of users reading new entries. You might consider starting a new thread with GPT in the title, since it appears your problem is really more related to what happened to the partition than it is with GRUB2 itself. You can put a reference to this thread in the first post so helpers can review the history should they wish to do so.

I'll monitor any thread you start as well as this one and if I can add anything constructive I will. Sorry I'm not able to get this resolved by myself.

---

### Post by srs5694 on 2010-11-30
Please post the output of "sudo parted /dev/sda print" to display the GPT partitions. (fdisk is just showing the MBR, which neither Linux nor OS X uses.) It's possible that /dev/sda2 isn't a Linux partition at all. You should also try running the [Boot Info Script](http://bootinfoscript.sourceforge.net/) that was referenced in an earlier post; that'll reveal several things that might be diagnostic.

---

### Post by idealistic on 2010-12-01
thanks for helping me but after a check at a store, it turns out that my hard drive was physically damaged so i guess there was nothing to be done !

---

