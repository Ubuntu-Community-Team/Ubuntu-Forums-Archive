---
title: "GRUB question /hdb1"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by MadsRH on 2008-01-05
How do I add my XP harddrive in the GRUB menu?

I've tried this, with no luck:

```
sudo update-grub
```

The harddrive is /dev/hdb1
[http://ubuntuforums.org/showthread.php?t=659312]("http://ubuntuforums.org/showthread.php?t=659312")

---

### Post by MadsRH on 2008-01-05
Can no one help me???

I'm thinking that maybe something like this could work:

```
title WindowsXP
map (hd1) (hd0)
map (hd0) (hd1)
rootnoverify (hd1,0)
makeactive
chainloader +1
```

---

### Post by spydon on 2008-01-05
```

title           Microsoft Windoze XP Professional
root            (hd1,0)
savedefault
makeactive
chainloader     +1

```

This one should work for you :).

---

### Post by MadsRH on 2008-01-05
Thanks for your reply. Sadly it didn't work :(
After selecting XP in the GRUB menu, I just returned to the black screen with a blinking cursor!

---

### Post by spydon on 2008-01-05
> **MadsRH said:**
> Thanks for your reply. Sadly it didn't work :(
After selecting XP in the GRUB menu, I just returned to the black screen with a blinking cursor!

Weird... Did you say that your windows partition was hdb1?

---

### Post by MadsRH on 2008-01-05
Yes. I acts a little funny after the mount problem (check the #1 post). It makes a DISK icon on the desktop.
Anyway, could there be something wrong with the XP boot files aften mounting with linux?

---

### Post by spydon on 2008-01-05
there shouldn't be anything wrong with your boot files unless you accidently wrote over some of them when you partitioned...

---

### Post by MadsRH on 2008-01-05
Okay. Have you got any idea what I should try next???

---

### Post by spydon on 2008-01-05
Hmm well idk maybe make sure that the windows partition really is hdb1...
you can do that by ```
fdisk -l
```

Edit: ah now i saw it in your link :P...

---

### Post by spydon on 2008-01-05
Try to unmount it before reboot and use the code that I postes above...
Maybe a checkdisk or something can solve this.

---

### Post by MadsRH on 2008-01-05
HHmmm, I get this:

```
 fdisk -l

Disk /dev/sda: 2063 Mb, 2063073280 byte
16 heads, 32 sectors/track, 7870 cylinders
Units = cylindre of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

    Enhed Opstart   Start         Slut     Blokke   Id  System
/dev/sda1               1        7870     2014704    b  W95 FAT32

```

---

### Post by spydon on 2008-01-05
Okay... you don't happend to have a windows cd somewhere so yuo can get the windows repair console and run a checkdisk from there?

---

### Post by MadsRH on 2008-01-05
I have it, but It will take some time. I will return tomorrow. Thanks for your help so far :)

Oh, and I got "Invalid device request..." with the (0.1)

---

### Post by spydon on 2008-01-05
> **MadsRH said:**
> I have it, but It will take some time. I will return tomorrow. Thanks for your help so far :)

Oh, and I got "Invalid device request..." with the (0.1)

Well, do ```
chkdsk volume:/r
``` so it fixes stuff too and not just checks...
See you tomorrow then :).

---

### Post by MadsRH on 2008-01-06
Hi again
So I disconnected the Linux drive and made the XP harddrive Master, and it booted just fine. Everything was running as it should. Anyway, I ran **chkdsk /r**, shutdown and installed the harddrives as before (Linux pri.master and XP pri.slave)
Still nothing has changed when I booted Ubuntu.

What strikes me as odd is that the XP harddrive is NOT visible on the desktop (like to USB icon) or in the "Places" menu. I can access it from "This Machine" (Don't know what it's called in the English version) but I can only read from it!

---

### Post by MadsRH on 2008-01-06
Has anyone got any suggestions??? :confused:

---

### Post by bumanie on 2008-01-06
I am not sure that this will help much, but a preferable setup it is considered to have windows as the primary and linux as the slave. Apparently windows is much happier this way.
You could try to make windows master and ubuntu slave and then direct grub to boot from the slave drive. But you really need someone more expert than myself to fully answer your problem.
Did you load windows first or second. Did you both drives connected when each install was done?

---

### Post by MadsRH on 2008-01-06
I don't understand what you mean be "load windows first or second"?

> 
Did you both drives connected when each install was done? No, I made each drive run as master with no slave.

---

### Post by bumanie on 2008-01-06
> **MadsRH said:**
> I don't understand what you mean be "load windows first or second"?

By this I meant, if you had both drives plugged in together, did you install windows before ubuntu or the other way around. 

 No, I made each drive run as master with no slave.

Were both drives connected when you installed the OSes or did you plug one drive whilst installing the OS and then change the drives over once the first OS was installed. (I am unable to understand how you had both drives set to master at the same time), unless you had them plugged in separately eg drive one - plug in - install OS - unplug
     drive two - plug in - install OS - unplug

Is this how you did it? If not, please explain the procedure you used to install the OSes and how you managed to have both drives set to master.

---

### Post by MadsRH on 2008-01-06
Not at the same time. I ran Ubuntu on one, disconnected it and connected the XP harddrive. Witch means that every time I want to boot into the other OS, I have to unplug/plug in the cables to that drive.

So, two harddrives, two different OS and only one running at a time.

---

### Post by bumanie on 2008-01-06
OK, I was beginning to suspect that is how you must have done it.
Having done it that way, as the windows drive was not connected when you installed ubuntu, when grub checks the system, it can't tell that you have a windows install, grub therefore believes ubuntu is the only OS it has to boot.
One way around this is to go into bios each time you boot and choose which drive you want ie windows or ubuntu. This can be a drag if you switch between the two often, but if you use windows rarely, it should not be too much of a hassle.
Another way is to edit the /boot/grub/menu.lst 
It would be best for you to have the windows drive as the master drive and set the ubuntu drive as slave - but editing the /boot/grub/menu.lst is a procedure I am not confident enough with. I would try it on my own computer, but don't want to muck your system up. (I can try if you want, but there would be no guarantee of success).
The other thing you can do is plug both drives in (Windows master) and reinstall ubuntu to the slave. This way, grub will see windows and should then give the choice of which OS to boot without the need to go into bios.
Sorry I can't be of more help.

---

### Post by MadsRH on 2008-01-06
Okay, thanks - I think I will try to make XP master and Ubuntu slave. Hopefully I will return with good results.

---

### Post by bumanie on 2008-01-06
> **MadsRH said:**
> Okay, thanks - I think I will try to make XP master and Ubuntu slave. Hopefully I will return with good results.

Just plugging them in that way won't solve anything, unless you are going with the choose which OS from bios option. You will either need to edit the grub menu.lst or reinstall ubuntu whilst both drives are plugged in.

---

### Post by logos34 on 2008-01-06
try this:

linux drive first
xp second

tweak the windows entry:

> title Windows XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

add the windows drive to device.map:

gksudo gedit /boot/grub/device.map

> (hd0) /dev/hda
**(hd1) /dev/hdb**

Also, as far as this goes:
> What strikes me as odd is that the XP harddrive is NOT visible on the desktop (like to USB icon) or in the "Places" menu. I can access it from "This Machine" (Don't know what it's called in the English version) but I can only read from it!

did you add hdb to fstab?  If you do it with [ntfs-config]("https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28windows%29#head-c067eb7e3cd4107cc08cdf30a9e1aed8adb02971") it will automount at boot with read+write access

---

### Post by MadsRH on 2008-01-06
****, okay. I've just changed the jumpers. Now I've got XP as pri.master og Linux as pri.slave.

So if it's okay with you **logos34**, I would like to try this approach now. Xp boot's just fine, but how to install GRUB on the XP drive? or how do I do it?

As for your last question about fstab. I did a > sudo mount -t ntfs-3g /dev/hdb1 /media/hdb1 -o force
df -h (see my #1 post)

---

### Post by logos34 on 2008-01-06
> **MadsRH said:**
> ****, okay. I've just changed the jumpers. Now I've got XP as pri.master og Linux as pri.slave.

So if it's okay with you **logos34**, I would like to try this approach now. Xp boot's just fine, but how to install GRUB on the XP drive? or how do I do it?

As for your last question about fstab. I did a  (see my #1 post)

The mount command is a** manual** mount--you have to do that each time you boot.  So it's not in fstab.

Are you sure you want to install grub to XP disk?  Because it will overwrite the windows bootloader on the MBR?

---

### Post by MadsRH on 2008-01-06
No I'm not. If the Windows bootloader can do the same I would like to try that.

---

### Post by logos34 on 2008-01-06
> **MadsRH said:**
> No I'm not. If the Windows bootloader can do the same I would like to try that.

Yep, we can do that too.

One quick question: why aren't you just going into the Bios at startup and switching the hard disk boot order that way rather than physically swapping master and slave?

---

### Post by MadsRH on 2008-01-06
Yes that is maybe a little dumb.
Anyway, the bootloader will solve the problem, but I don't know what to write! I've removed the attribute and the boot.ini looks like this:

```

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

```

Will the GRUB pop-up when I have chosen Ubuntu?

---

### Post by logos34 on 2008-01-06
boot.ini is only half of it.  Add this:
> 
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
[COLOR="Red"]c:\ubuntu.mbr="Ubuntu Linux"[/COLOR]

Now go back into ubuntu and copy the bootsector of the linux partition:
(using [this guide]("http://gentoo-wiki.com/HOWTO_Dual_Boot_from_Windows_Bootloader_(NTLDR)_and_why#Fooling_Windows") as an example)

> sudo dd if=/dev/hda1 of=ubuntu.mbr bs=512 count=1

Look for 'ubuntu.mbr' in home folder and copy it to hdb1, i.e. windows c: directory
(obviously windows will have to be mounted with write permission). Alternatively, copy it to usb flash and transfer it over that way.

Before you leave ubuntu change the ubuntu entry in menu.lst because it will be in second place:

'groot' and root line need to show **(hd1,0)**

---

### Post by MadsRH on 2008-01-06
Okay, I seem to finally have got it working! Thank you :)

Just one last thing. Could someone tell me what to do with the fstab vs. mount problem?

---

### Post by logos34 on 2008-01-06
Did you try the link I gave you?  Just do:

sudo apt-get install ntfs-config

sudo ntfs-config

>enable write support internal device

It will edit fstab for you.  Hopefully that will automount the volume.  If you keep getting errors and you can only manually mount with 'force' option, then I'm not sure what to to tell you.

---

### Post by MadsRH on 2008-01-06
It's not working. There was an error just like in my last thread:

```
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/hda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/hda1 /media/Samsung -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/hda1 /media/Samsung ntfs-3g defaults,force 0 0
```

---

### Post by MadsRH on 2008-01-06
Now I can't access the drive at all! :confused:

---

### Post by logos34 on 2008-01-06
taurus is the best one to help in such matters

---

### Post by spydon on 2008-01-06
Do the chkdsk /r again and it will probably be fixed.

---

