---
title: "[SOLVED] Cannot Mount New Volume"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by bscasta on 2008-01-02
My situation is that I have two harddrives one now has been formatted and has ubuntu 7.10 on it but the second was all my files (movies music etc.) my problem is when I try to access it. it says unable to mount new volume. Would somebody please tell me how to get all my info from that disk backed up and then format that drive to be used with linux and put it all back?

---

### Post by iansane on 2008-01-02
> **bscasta said:**
> My situation is that I have two harddrives one now has been formatted and has ubuntu 7.10 on it but the second was all my files (movies music etc.) my problem is when I try to access it. it says unable to mount new volume. Would somebody please tell me how to get all my info from that disk backed up and then format that drive to be used with linux and put it all back?

what file system is it?

if it's FAT usbuntu should be able to read it. If it's NTFS use NTFS configuration tool from add/remove programs or better yet, place an entry in the fstab file. 

Have you already done either of those things?

Oh and are you using sudo mount to mount it?

---

### Post by iansane on 2008-01-02
you can try going into terminal and typing "sudo mount /media/drivename and use "sudo umount" the same way.

I think you have to make an fstab entry (sudo gedit /etc/fstab) to be able to do it that way. Here are two of my entries for seperate harddrives.

[code]/dev/hda1 /media/XP ntfs-3g noauto,locale=en_US.UTF-8 0 0[code]

and

[code]/dev/sde2/media/removable1 ntfs-3g noauto, force 0 0[code]

hda1 is a seperate internal and sde2 is a removeable. You just have to know which drive your is (hda, hdb, or whatever) I don't think the part "locale=en_UTF-8" is important cause only one of them says it.

---

### Post by iansane on 2008-01-02
ok that was embarrasing. Apparently I don't know how you guys get the little boxes around your code so disregard the  " [code]" part..

---

### Post by bscasta on 2008-01-02
Sorry but I am a complete beginner. I dont know what entry to make in the fstab or what that is for that matter or how to sudo or any of that stuff.

---

### Post by ~LoKe on 2008-01-02
First we'll need to know a little bit of information about your hard drive.  Open a terminal II'm assuming you know how) then type the following:
```
sudo fdisk -l
```
It'll ask you for your password, just enter the one you specified when you installed Ubuntu.  Copy and paste the ouput, for me, it would look like this:
> [01:53:23 loke]$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d5340

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29126   233954563+  83  Linux
/dev/sda2           29127       30337     9727357+  83  Linux
/dev/sda3           30338       30401      514080   82  Linux swap / Solaris

---

### Post by ~LoKe on 2008-01-02
> **iansane said:**
> ok that was embarrasing. Apparently I don't know how you guys get the little boxes around your code so disregard the  code part..

Ah, it's easy.  You had it almost right, except the last part has to be [/code].  An example:

[co******de]some text[/co******de] would look like this:
```
some text
```

---

### Post by bscasta on 2008-01-02
how do I copy and paste from the terminal to here. ( I know im really dumb with this stuff)

---

### Post by ~LoKe on 2008-01-02
> **bscasta said:**
> how do I copy and paste from the terminal to here. ( I know im really dumb with this stuff)

Hey, you're in the right section.  You're new, no one expect you to know how to do everything all at once. ;)

Use the mouse to select the output like a block of text, then right click -> copy.  Come here and right click -> paste.

---

### Post by iansane on 2008-01-02
well I'm actually kinda new myself. I can tell you that the ntfs configure tool is in add/remove  under the applications menu. (searh for "ntfs") and that the fstab is a file in /etc.
I think you have to install it first if the drive is ntfs format. If it's plugged in, that tool should detect it and make it easy for you to configure a mount point. (that's the purpose of the fstab entry.)

If you open a terminal (applications>accessories>terminal) and type "sudo gedit /etc/fstab" it will open in the gnome text editor. You'll see any other entries there and can go by them. If the drive is internal it should be "hdb" With more than one drive it uses a,b,c etc. And uses numbers to count the partitions on the drives like "hda1, hda2, hdb1, hdb2" I don't know why the external usb drive I have is "sde" and I don't know much about the "dev" part at the beginning of the lines.


If you try some different ones, I don't think it will crash your system or anything. Just delete the line if it doesn't work. Or you can put a "#" in front of it. That comments it out so the computer doesn't read it.

I hope someone more knowlegable can explain it to you soon. I can do it after playing around for a while but telling someone how is a little different.

Sorry I'm not more help

---

### Post by bscasta on 2008-01-02
Ok   I wasnt able to use the mouse in terminal but i did get gpm to be able to do so   but i can highlight the text but if I right click it it goes crazy    it keeps saying command not found over and over again

---

### Post by bscasta on 2008-01-02
Disk /dev/hdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x76067606

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        4660    37431418+  83  Linux
/dev/hdc2            4661        4865     1646662+   5  Extended
/dev/hdc5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/hdd: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc16e7ad

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        4865    39078081    7  HPFS/NTF



I guess i wasnt using the right terminal?    I was using ctrl alt f1 instead of applications accesories terminal

---

### Post by iansane on 2008-01-02
glad you stepped in ~LoKe. I just learned how to list my harddrives so no more guessing, and how to paste code. I should have known like a closing tag in html.

Thanks :)

---

### Post by ~LoKe on 2008-01-02
> **bscasta said:**
> Ok   I wasnt able to use the mouse in terminal but i did get gpm to be able to do so   but i can highlight the text but if I right click it it goes crazy    it keeps saying command not found over and over again

That sounds...odd.  Which terminal are you using?

Anyways...try ctrl+shift+c instead of right click -> copy.

---

### Post by ~LoKe on 2008-01-02
> **iansane said:**
> glad you stepped in ~LoKe. I just learned how to list my harddrives so no more guessing, and how to paste code. I should have known like a closing tag in html.

Thanks :)

No problem. ;)

---

### Post by ~LoKe on 2008-01-02
Try this in the terminal:
```
sudo mkdir /media/windows
```
Then...
```
gksu gedit /etc/fstab
```
Add this to the bottom:
> /dev/hdd1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
Save it then close.  Now, back in the terminal, type this:
```
sudo mount -a
```

If it all worked, you should be able to type this into the terminal:
```
ls /media/windows
```
And it should list some files/folders.

---

### Post by bscasta on 2008-01-02
> **~LoKe said:**
> That sounds...odd.  Which terminal are you using?

Anyways...try ctrl+shift+c instead of right click -> copy.

Disk /dev/hdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x76067606

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        4660    37431418+  83  Linux
/dev/hdc2            4661        4865     1646662+   5  Extended
/dev/hdc5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/hdd: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc16e7ad

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        4865    39078081    7  HPFS/NTF

I was using ctrl alt f1 instead of applications accessories terminal

---

### Post by bscasta on 2008-01-02
[mntent]: line 12 in /etc/fstab is bad

---

### Post by ~LoKe on 2008-01-02
Crap.  I copied the wrong line.  One second.

Open up fstab again.
```
gksu gedit /etc/fstab
```
Remove the line I told you to paste in.  Replace it with this:
> /dev/hdd1  /media/windows  ntfs  defaults  0 0
Save it, close it, then:
```
sudo mount -a
```
That should work.

---

### Post by bscasta on 2008-01-02
YOU ARE AWESOME     now that thats fixed and its almost 2 in the morning      Im going to bed        Thanks alot man        I really appreciate it.

---

### Post by ~LoKe on 2008-01-02
Glad I could help.  Enjoy. ;)

---

