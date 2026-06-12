---
title: "Installed Windows Vista, now no more Ubuntu..."
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by TR3GO on 2007-02-15
Hello,

         I just installed Windows Vista and it wiped out my Ubuntu grub loader of course. I need a way to get it back. I tried (sudo grub, find /boot/grub/stage1 , root (hd?,? , setup (hd0), quit) and it showed it was successful but the GRUB loader did not appear. Does anyone have any other solutions?

-Thanks! :-D

---

### Post by rsambuca on 2007-02-15
How many drives, and how are they partitioned?

What happens when you boot up after trying to reinstall grub?

What were the exact entries you used to try and restore grub?

---

### Post by SoggyCornflake on 2007-02-15
> **TR3GO said:**
> Hello,

         I just installed Windows Vista and it wiped out my Ubuntu grub loader of course.

Maybe the Windows Installer remapped the Boot drive.

I would try taking an Ubuntu Installl CD and the install program.  It should detect the Windows Vista and your existing ubuntu installation and re-install the Grub files.

---

### Post by jml on 2007-02-15
I've read that Windows Vista handles the MBR differently than previous versions of Windows.  I've read online that this makes repairing the MBR difficult.  I don't remember where I read this, but I just did a Google search and came up with this post that may help you.  

[http://www.cyberciti.biz/tips/howto-fix-dual-boot-windows-vista-linux.html](http://www.cyberciti.biz/tips/howto-fix-dual-boot-windows-vista-linux.html)

Good luck

Joe

---

### Post by vloris on 2007-02-15
What I do in that situation is as follows:

[LIST]
[*]Boot from install-cdrom
[*]Open up a terminal and become root:
```
sudo -s
```
[*]Mount the root-filesystem of your installed Ubuntu, in my case this is /dev/hda2
```
mount /dev/hda2 /mnt
```
[*]Run grub-install to put its files in the master boot record (MBR) of the same disk (/dev/hda here) and the rest of its files in /boot on your installed partition (that is /mnt/boot in this case)
```
grub-install --root-directory=/mnt/boot /dev/hda
```
You only need to restore the MBR, but I haven't found a simple way to do just that. Above command works and does leave your menu.lst intact.
[/LIST]

---

### Post by TR3GO on 2007-02-15
I have two Hard Drives and on...

HARD DRIVE 0:

Vista - 29.29 GB (NTFS)
MP3s - 29.29 GB (NTFS)
Game Disc - 15.93 GB (NTFS)

HARD DRIVE 1:

Video Disk - 24.41 GB (NTFS
Documents - 1 GB (NTFS
Game Disc 2 - 23.48 (NTFS)

UBUNTU - 27.36 GB (Ext. 2)
SWAP - 518 MB (NTFS)

- When I boot up I go directly into Windows Vista.

- (In Ubuntu 6.10 Live CD Terminal) I used the HD entry that it gave me when I entered the "find /boot/grub/stage1" command. I believe it was "HD1, 0". Not positive...

---

### Post by TR3GO on 2007-02-15
Hmm... Nothing has worked so far... Myabe I'll have to reinstall Ubuntu

---

### Post by rsambuca on 2007-02-15
Whoa, no need to re-install!  What type of drives do you have? Both IDE?  Master and slave, or one IDE and one SATA?

From your very first post, if you indeed did the grub command: setup (hd0) and your machine still boots straight into Vista, then grub is guessing the order of the drives incorrectly.

Enter your system Bios and see what the boot order of the hard drives is.  Post the results and we should have you up and dual booting in no time.

---

### Post by dralaroc on 2007-02-15
I came across this article "Living With Vista" in Linux Pro Mag, perhaps it might help ya out.

[http://www.linux-magazine.com/issue/75/Microsoft_Vista_With_Linux_Interoperability.pdf](http://www.linux-magazine.com/issue/75/Microsoft_Vista_With_Linux_Interoperability.pdf)

---

### Post by TR3GO on 2007-02-15
> **rsambuca said:**
> Whoa, no need to re-install!  What type of drives do you have? Both IDE?  Master and slave, or one IDE and one SATA?

From your very first post, if you indeed did the grub command: setup (hd0) and your machine still boots straight into Vista, then grub is guessing the order of the drives incorrectly.

Enter your system Bios and see what the boot order of the hard drives is.  Post the results and we should have you up and dual booting in no time.

I have both IDE Drives, and when I did the grub location command it told me grub was on (HD1,4). My boot order is "HARD DRIVE (MASTER), CD-ROM, Floppy". Still no luck! :-(

---

### Post by dtg on 2007-02-15
vista? blashempy!

they ripped off os x so bad.

os x is tight though.

---

### Post by newbsaucer on 2007-02-15
good article to read that explains this and a good approcah to fixing it is below:

[http://desktoplinux.com/articles/AT2094892904.html](http://desktoplinux.com/articles/AT2094892904.html)

---

### Post by rsambuca on 2007-02-15
Could you please post what your menu.lst file and fstab please?

Use the live CD, and mount the linux partition using this command in a terminal```
sudo mount /dev/hdb5 /mnt
```
then ```
then sudo mount -a
```
then```
gksudo gedit /mnt/boot/grub/menu.lst
```and paste the results here

---

