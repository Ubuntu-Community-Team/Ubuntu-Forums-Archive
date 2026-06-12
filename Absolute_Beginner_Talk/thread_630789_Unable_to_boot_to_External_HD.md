---
title: "Unable to boot to External HD"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by dualR on 2007-12-03
I installed Ubuntu 7.10 to a 10GB External HD, installation went fine, I followed the instructions closely and unticked these:

Mount removable drives when hot-plugged
Mount Removable Media When Inserted
Browse Removable Media When Inserted

I unplugged all the internal HDs before I booted to the liveCD just incase, and when it came to where it asked me where to install the Boot Loader, I changed "(hd0)" to "dev/sda".

Now whenever I boot to the USB drive on bootup, I get a black screen and
> grub>

At this point I thought I had mistyped the "dev/sda" and proceeded to boot to the livecd and do the whole grub fixing thing "find /boot/grub/stage1", "root (hd0, 0)" etc

But when that didn't work I simply took out the HD from the enclosure and plugged it in internally, it booted fine, ran fine and updated fine.

I asked my friend and he said it was because external enclosures don't have proper MBR or something like that.

Oh and just for closure, I booted to the HD externally again, went to the grub menu and typed in "find /" and got a whole bunch of errors, the only one I remember was error 17: disk not mounted or something like that - but surely if it found whatever files it needs to go into the boot menu it has accessed the external HD right?

Is there anyway you guys know to fix this? If it wasn't clear I want the computer to boot to my normal OS (Windows XP) unless I plug in the external HD where it should boot to Ubuntu.

My only thoughts were to have a floppy disk/usb/cd to tell the computer to look into the external HD and boot Ubuntu, but if grub can't even find the disk its installed on then I think we have some problems.

Thanks in advance for any help.

EDIT: Oh, and I should mention that the computer BIOS CAN boot to USB fine.

---

### Post by diatribe on 2007-12-03
if you have installed on an external drive the drive isn't going to be (hd0,0) anymore

---

### Post by dualR on 2007-12-03
Well after I got to the "grub>" message, I booted to the livecd (with internal drives still unplugged)
I googled how to fix the grub loader because I thought it was broken
Went to terminal typed in "sudo grub" then "find /boot/grub/stage1"
And the output was (hd0, 0)
And in the instructions it said to type in root (hdX, Y) so I typed in (hd0, 0)

Is that why it isn't working? I should've installed the grub to (sd0, 0) instead of (hd0, 0)?
That explains why it only works when plugged internally.

Could someone tell me if this would fix it because I don't really want to mess with it without knowing what exactly will happen just incase I mess it up even more.

---

### Post by meierfra on 2007-12-03
As far as I can see you did everything correct and I don't see what the problem could be. At the  "grub>" prompt at boot-up, what is the output of "find /boot/grub/stage1" ?

---

### Post by meierfra on 2007-12-03
Actually  at the Live CD you should do

```
root (hd0,0)
setup (hd0)
```

You can also try these commands at the "grub>" prompt at  boot-up

---

### Post by dualR on 2007-12-03
> **meierfra said:**
> As far as I can see you did everything correct and I don't see what the problem could be. At the  "grub>" prompt at boot-up, what is the output of "find /boot/grub/stage1" ?
I get Error 15: File not Found, same for "find /"

> **meierfra said:**
> Actually  at the Live CD you should do

```
root (hd0,0)
setup (hd0)
```

You can also try these commands at the "grub>" prompt at  boot-up
Yea I tried that on the live CD as I wrote > and do the whole grub fixing thing "find /boot/grub/stage1", "root (hd0, 0)" etc
I have tried that on the prompt at boot up too, but I can't remember what the error was, I just rebooted to XP after finding the error message for "find"

The point it that it boots fine if I plug it in but it goes to the grub prompt and can't seem to find any other files when I plug it externally.

---

### Post by meierfra on 2007-12-03
Plug in all your hard drives, boot from the LiveCD and post the output of 

```
sudo fdisk -l
```
("l" is a lower case L)

---

### Post by dualR on 2007-12-03
I'm on livecd now, results of sudo fdisk-l

> Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8e898e89

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         653     5245191    7  HPFS/NTFS
/dev/hda2             654        4865    33832890    f  W95 Ext'd (LBA)
/dev/hda5             654         915     2104483+   7  HPFS/NTFS
/dev/hda6             916        4865    31728343+   7  HPFS/NTFS

Disk /dev/hdb: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe301ff21

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1216     9767488+   7  HPFS/NTFS

Disk /dev/sda: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00a7a75f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1158     9301603+  83  Linux
/dev/sda2            1159        1216      465885    5  Extended
/dev/sda5            1159        1216      465853+  82  Linux swap / Solaris

hda1-hda6 is my IDE Master, it has Win XP on it. hdb1 is just an extra HD i put in there for storage (No OS)
sda1-sda5 were made by the Ubuntu Guided Install.

---

### Post by meierfra on 2007-12-03
I think, you enclosure is the problem (but  my reasoning is not very scientific: I don't see any wrong, I don't know anything about enclosure, so it must be the enclosures fault) 

Here is something you could try:

Install Grub to the MBR of your second internal hard drive. (There is  potential problem:  If you boot from the second internal drive with the external drive unplugged, you might get an error message. But I think that after it failed to boot from the second drive,  it will try to boot from the first drive)

If you want to give this a try, here are the instructions.

In a terminal in the Live CD with all the drive plugged in:

Install grub to the second internal drive:

```
sudo grub
find /boot/grub/stage1   #this is just for double checking: it should return (hd2,0)
root (hd2,0)
setup (hd1)
quit

```


Edit menu.lst to reflect the new setup:
```
sudo mkdir /ubuntu
sudo mount -t ext3 /dev/sda1 /ubuntu
cd /ubuntu/boot/grub
sudo cp menu.lst menu.lst.backup
gksudo gedit menu.lst
```


Change "#groot (hd0,0)" to "#groot (hd2,0)"

Change  all  "root (hd0,0)" to "root (hd2,0)" (there should be three of them)

Save the file and reboot  from the second internal drive,
(edit: The boot order need to be 
2nd internal drive, 1st internal drive, external drive)

---

### Post by dualR on 2007-12-03
meierfra: Just finished doing all the editing, am going to reboot now. You are probably right about the enclosure being at fault, it is a Generic Brand, next post should hopefully be from the externally installed Ubuntu, wish me luck :D.

---

### Post by dualR on 2007-12-03
Nope it didn't work :(
I booted to the second HD and it said it was loading GRUB stage 1.5 then it said error 22.

And after re-reading your instructions, I just want to get something straight, when I boot to the second internal HD, the MBR of that HD tells the computer to look in the external HD folder "/ubuntu/boot/grub/menu.lst"? Is that right?

---

### Post by meierfra on 2007-12-03
I forgot to tell that the boot order needs to be  

second internal drive, first internal drive, external drive


> look in the external HD folder "/ubuntu/boot/grub/menu.lst"?

It will look for /boot/grub/menu.lst on (hd2,0)

That's why  the external drive needs to be last in the boot order.

---

### Post by dualR on 2007-12-03
I didn't edit the boot order, I just press F8 when the BIOS tells me to and I boot the 2nd internal HD. But the boot order right now is HD1, HD2, EHD, so the external drive should still be (hd2,0) to grub, it doesn't explain the error though.

---

### Post by meierfra on 2007-12-03
OK. Try this


(from the LIVE CD, all drives plugged in)

```

gedit device.map 
```

This opens an empty file. Add this lines

(hd0) /dev/hdb
(hd1) /dev/hda
(hd2) /dev/sda

Save the file.

```
sudo grub --device-map=device.map
root (hd2,0)
setup (hd0)
quit

```


Reboot, (but check on the boot order)

---

### Post by dualR on 2007-12-03
I did that, and now when I boot to the second internal it goes to the black screen with the "grub>" prompt, just like if I boot to the external HD directly :P

Any ideas?

---

### Post by meierfra on 2007-12-03
> Any ideas?

Well,  it seems that grub is not able to read the external drive at boot-up.  Did you try "find /boot/grub/menu.lst" at the "grub>" prompt again?  Did you change the boot order in the bios or did  you just use "F8"? 


Other things one could try:

1) Use a different boot loader (Windows, lilo, grub for windows, gag, ...

This would be fairly easy to carry out. But I have no idea whether it would work..


2)  Create a boot partition for ubuntu on one of the internal drives.

This probably has the  better chance to succeed, But I'm hesitant to recommend it, mostly because I don't know whether it would work. I just don't have any experience with enclosures.  


Well, I'm on my way to bed. I'll check back in tomorrow. Maybe somebody else in the forums with some knowledge about  enclosures comes along and shed some light on the whole situation.

---

### Post by dualR on 2007-12-03
Yep, "find" anything turns up error 15 at the grub> prompt.
Thanks for all your help so far anyway.

I will look into other boot loaders.

EDIT: Oh yeah, I did change the boot order.

---

