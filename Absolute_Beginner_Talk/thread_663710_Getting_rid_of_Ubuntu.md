---
title: "Getting rid of Ubuntu"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by sbussy89 on 2008-01-10
I am currently dual-booting windows vista and ubuntu.  In the month since I put ubuntu on my machine I have had nothing but problems, so how can I get rid of ubuntu and the boot selector without having to reformat my hdd and lose everything I have in windows?  I was going to just delete the ubuntu partition and extend the windows partition into it but i didnt know if that would take care of the boot selector.

---

### Post by Saint Angeles on 2008-01-10
the microsoft install disc should have no problem writing to your boot sector... they LOVE doing that.

---

### Post by dgray_from_dc on 2008-01-10
Some of the Windows install CDs don't have the ability to fix the MBR.  I found out that  (if you have one) an old Windows 9x boot floppy can do it.

```
format c: /mbr
```

This command will only rewrite the MBR and nothing else.

---

### Post by Golem XIV on 2008-01-10
> **dgray_from_dc said:**
> Some of the Windows install CDs don't have the ability to fix the MBR.  I found out that  (if you have one) an old Windows 9x boot floppy can do it.

```
format c: /mbr
```

This command will only rewrite the MBR and nothing else.

Um...  I'm pretty certain that the command is NOT format but fdisk:
```
fdisk /mbr
```

---

### Post by dgray_from_dc on 2008-01-10
You're right.  My mistake.

---

### Post by hakan69 on 2008-01-10
Hello!
Quite a few options of how to fix your mbr at this site:
[http://users.bigpond.net.au/hermanzone/p18.htm](http://users.bigpond.net.au/hermanzone/p18.htm)
I used MbrFix. It worked like a charm!

Regards/Hakan

---

### Post by GavinZac on 2008-01-10
lokking at your posts
[http://ubuntuforums.org/search.php?searchid=34441581&pp=25](http://ubuntuforums.org/search.php?searchid=34441581&pp=25)

it seems like the problems you're having are pretty trivial. At one point you called them "embarressing". Give it time, its an entirely new operating system to you, why do you expect to be knowledgable about it right away?

---

### Post by sbussy89 on 2008-01-10
The problem is that I spend more time fixing compatibility problems in ubuntu than actually getting work done.  So after these posts what I'll try to do is hide the bot menu so that it boots into vista automatically, and if i want to i can hit [esc] during boot to get to the bot menu... could someone get me to a walkthrough on how to do that?  I am a super-beginner so even something as simple as editing the GRUB I would need help with.

---

### Post by GavinZac on 2008-01-10
run the command:

sudo gedit /boot/grub/grub.conf

change in the text editor:

default=0 to default=X 
(X is the number of windows, on the grub loading list, e.g. in mine, its 5th, so I would put in 5)

timeout=10 to timeout=X
(X is however long I want to have to be able to switch to ubuntu during boot, e.g. 2 seconds is short enough to ignore but long enough to press a button should you want to switch)

and then save, and reboot to se the effects.

Theres a graphical way of doing this but this is really fast, honest.

---

### Post by sbussy89 on 2008-01-14
> **GavinZac said:**
> 
sudo gedit /boot/grub/grub.conf


I ran the command but there is no file "grub.conf" in the folder.  It contains the files default, device.map, e2fs_stage1_5, fat_stage1_5, installed-version, jfs_stage1_5, menu.lst, minix_stage1_5, reiserfs_stage1_5, stage1, stage2, and xfs_stage1_5.

---

### Post by Linuxratty on 2008-01-14
You can always try other flavors of Linux...I'm using Mepis7 and i've had no problems with it whatsoever.

---

### Post by sbussy89 on 2008-01-14
> **sbussy89 said:**
> I ran the command but there is no file "grub.conf" in the folder.  It contains the files default, device.map, e2fs_stage1_5, fat_stage1_5, installed-version, jfs_stage1_5, menu.lst, minix_stage1_5, reiserfs_stage1_5, stage1, stage2, and xfs_stage1_5.

Quick fix - the file I was looking for was (obvious now) menu.lst  Thanks for the help, worked like a charm :)

---

### Post by apothecaryaaron on 2008-01-14
> **sbussy89 said:**
> I ran the command but there is no file "grub.conf" in the folder.  It contains the files default, device.map, e2fs_stage1_5, fat_stage1_5, installed-version, jfs_stage1_5, menu.lst, minix_stage1_5, reiserfs_stage1_5, stage1, stage2, and xfs_stage1_5.


Before you do anything, make a backup copy.  Always make a backup copy.

```
 sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_bak

```The file you should edit is menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```You will need to edit 3 lines.  Look for the line where it says:
```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```You need to uncomment (remove the '#') from the bottom 'hiddenmenu' so it will look like:

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
```That will take care of the hiding menu/hit ESC part.

Next you will need to edit your default.  Look for:
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0
```Change to number after default to the number corresponding to Vista.  Notice, as it says in the code, that numbering starts at 0, so if Vista is 4th on your list, the number you put in is 3.

The final thing is optional to edit.  I recommend a change so you will have time to hit ESC if you want.  Look for:

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10
```Set the number after timeout for the number of seconds you want it to pause.  I recommend 10, but if you are paying attention 5 will be ok.

Save the file when you are done and when you reboot it should be fine.

---

### Post by apothecaryaaron on 2008-01-14
Just as an example of how slow I type my posts, notice that the problem is solved *BEFORE* my post.  Glad it works for ya.

---

