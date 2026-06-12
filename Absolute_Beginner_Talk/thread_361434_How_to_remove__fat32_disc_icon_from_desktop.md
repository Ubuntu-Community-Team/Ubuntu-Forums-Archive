---
title: "How to remove  fat32 disc icon from desktop?"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by kramer65 on 2007-02-14
Hello,

I have partitioned my disc now into a linux and a fat32 partition with all my data (so it can also be accessed from windows). Now I always see the icon for the fat 32 partition on my desktop. How can I remove that from my desktop so that the disc is only appearing in the 'places' menu on top? It's not for any specific reason, just that I want to have my desktop clean..

Does anybody know?

---

### Post by dbbolton on 2007-02-14
change the mount point in your fstab to something like "/windows"

---

### Post by kramer65 on 2007-02-14
Ehm....  what?

What does that mean? How do I do that?

---

### Post by Sqwishy on 2007-02-14
@ dbbolton
Are you sure that's a solution to his problem? He doesn't wana change the mount point he wants to rid his desktop of the shortcut to the partition.

---

### Post by kramer65 on 2007-02-14
I think Sqwishy is right. I indeed just want to remove the launcher from the desktop. But I do want to be able to access the fat32 partition trhourh 'Places'..

Is there any sollution for that?

---

### Post by kakalaky on 2007-02-14
use gconf-editor and go to /apps/nautilus/desktop and uncheck volumes_visible

if you dont have gconf-editor installed, install it like this:

```
sudo apt-get install gconf-editor
```

it will show up under Applications, System Tools as Configuration Editor

---

### Post by kramer65 on 2007-02-14
Initially I couldn't find the gconf editor, so I looked in Applications > System tools, but there was nothing there.

So I tried installing it with your code (sudo apt-get install gconf-editor). It says "gconf-editor is already the newest version", but it still doesn't show up in the applications menu.. 

Where else could it be?

---

### Post by kakalaky on 2007-02-14
I keep forgetting that I installed it 2 releases ago, so it could be different now.  Just open a terminal and type gconf-editor

Edit:  You could also try right clicking Applications and click Edit menu.  Check in this app to see if Configuration Editor is checked, otherwise it won't show up in the menu.

---

### Post by Patrick K on 2007-02-14
Why not just send the icons to the trash bin? They are only links to /media. Deleting the icon links won't delete the mount points. Or, if you like, create a directory in your /home folder and move them there.

---

### Post by bapoumba on 2007-02-14
Unchecking the volume_visible key wil work indeed, but you will not see any other mounted devices like usb keys or CDroms on your desktop either. If this is not okay with you, please let us know and we can walk you through mounting the fat32 partition some place else (you will still have access in Places menu).

You can add gconf-editor to your menu in > System > Preferences > Menu Layout.

---

### Post by kakalaky on 2007-02-14
> **Patrick K said:**
> Why not just send the icons to the trash bin? They are only links to /media. Deleting the icon links won't delete the mount points. Or, if you like, create a directory in your /home folder and move them there.

You can't send the icon he is talking about to the trash bin.

---

### Post by housam on 2007-02-14
Open up gconf-editor ( hit alt+f2 and type : gconf-editor )

Now go down to apps >> nautilus >>desktop, and check the boxes next to the appropriate icons...

---

### Post by kramer65 on 2007-02-14
Thanks kakalaky. Found it now. I just unchecked it. It is still available under Places now and also when i click in another volume it will open automatically and also be available in places. I like it better like this.. :D

@ Bapoumba. Thanks a lot for the friendly offer of walking me trough the other process! However as said, not needed anymore.

ps. I just start liking ubuntu more and more. I just love it that you can adjust everything to your own whishes. Now I only need beryl to start working and it's finished!

---

### Post by Cody Krodle on 2007-02-14
I'm having the same problem, but i would like to keep it to where my cd-roms and others will show up! Could you help ME?

---

### Post by bapoumba on 2007-02-14
@ Cody Krodle: please open a terminal (> Accessories > Terminal) and paste the complete output to **cat /etc/fstab**.

If talking about your windows partition, you should see a line that has vfat in it:
```
# /dev/hda2
UUID=0A2A-1AD4  /mnt/Windows     vfat    defaults,utf8,umask=007,gid=46 0       1

```
You see mine is mounted in /mnt/Windows, because I have other partitions in it too. Currently yours should be in /media. The /dev/hd* and UUID should be different for you. Do not change that.

Make up a mount point:
```
sudo mkdir /mnt
sudo mkdir /mnt/Windows
```
(you can choose not to make the second file if you do not have other partitions to mount there, just let us know).

Backup your fstab:
```
sudo cp /etc/fstab /etc/fstab.bak
```

Edit fstab to change the vfat mount point:
```
sudo nano /etc/fstab
```
go to your vfat line, and change the /media mount point to /mnt/Windows. CTRL-O (like in ocean) to save the file (with same name), CTRL-X to close.
Will take effect next reboot ;)

---

### Post by MikB on 2007-02-15
> **bapoumba said:**
> @ Cody Krodle: please open a terminal (> Accessories > Terminal) and paste the complete output to **cat /etc/fstab**.

If talking about your windows partition, you should see a line that has vfat in it:
```
# /dev/hda2
UUID=0A2A-1AD4  /mnt/Windows     vfat    defaults,utf8,umask=007,gid=46 0       1

```
You see mine is mounted in /mnt/Windows, because I have other partitions in it too. Currently yours should be in /media. The /dev/hd* and UUID should be different for you. Do not change that.

Make up a mount point:
```
sudo mkdir /mnt
sudo mkdir /mnt/Windows
```
(you can choose not to make the second file if you do not have other partitions to mount there, just let us know).

Backup your fstab:
```
sudo cp /etc/fstab /etc/fstab.bak
```

Edit fstab to change the vfat mount point:
```
sudo nano /etc/fstab
```
go to your vfat line, and change the /media mount point to /mnt/Windows. CTRL-O (like in ocean) to save the file (with same name), CTRL-X to close.
Will take effect next reboot ;)


I also want to remove the mounted windows partition icon from the desktop but leave it in places. At the mo ubuntu is installed on the slave drive (hdb) and xp is on the master (hda), so I suspect the code i need to change in fstab will be different?

Could you help me out configuring this?

---

### Post by bapoumba on 2007-02-15
Okay, please post the output to **cat /etc/fstab**.

---

### Post by dbbolton on 2007-02-16
> **Sqwishy said:**
> @ dbbolton
Are you sure that's a solution to his problem? He doesn't wana change the mount point he wants to rid his desktop of the shortcut to the partition.
it worked for me. 

i hate desktop icons.

---

### Post by MikB on 2007-02-16
> **bapoumba said:**
> Okay, please post the output to **cat /etc/fstab**.

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/hdb1 :
UUID=e00914fe-dcbc-4334-a975-9ac76c4f44ce / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hdb5 :
UUID=aad67787-2029-49b2-bbe8-d9e4e2b438d0 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/hda1 /media/MIKR_LOCAL ntfs-3g defaults,locale=en_US.UTF-8 0 0

hda1 is the Windows Partition icon which is on the desktop.

Thanks.

---

### Post by bapoumba on 2007-02-17
> **MikB said:**
> 
/dev/hda1 /media/MIKR_LOCAL ntfs-3g defaults,locale=en_US.UTF-8 0 0

So you can make a /mnt/MIKR_LOCAL if you whish:
```
sudo mkdir /mnt
sudo mkdir /mnt/MIKR_LOCAL
```

and edit the fstab file (see my previous post for backup instructions and editing with nano, a terminal editor) to make the above quoted line:
```
/dev/hda1 /mnt/MIKR_LOCAL ntfs-3g defaults,locale=en_US.UTF-8 0 0
```

Will take effect next reboot, and you will be able to browse your partition in > Places > Computer (or File System, I do not remember what is the default name for it, I changed it a long time ago ;))

---

### Post by MikB on 2007-02-19
Sorted. Merci.

---

### Post by bapoumba on 2007-02-19
> **MikB said:**
> Merci.
De rien ;)

---

### Post by pmendham on 2007-02-21
Erm... I tried moving my ntfs-3g mount from /media/windows to /mnt/windows.  Well, I sure lost the "windows" icon on my desktop... but now I have one labelled "/mnt/windows".  I would rather not have an icon at all for this mount, and especially not one with the rather off-putting name of "/mnt/windows".  Ideas anyone?

-- Peter

---

### Post by bapoumba on 2007-02-21
> **pmendham said:**
> Erm... I tried moving my ntfs-3g mount from /media/windows to /mnt/windows.  Well, I sure lost the "windows" icon on my desktop... but now I have one labelled "/mnt/windows".  I would rather not have an icon at all for this mount, and especially not one with the rather off-putting name of "/mnt/windows".  Ideas anyone?

-- Peter
What is the output to **cat /etc/fstab** and **sudo fdisk -l** ?

---

### Post by pmendham on 2007-02-21
:oops: I'll tell you what I did, I'm sure you can spot the bit where I should have waited before posting...

I set up my mount for my ntfs drive by following a tutorial, which told me to do it in /media.  I didn't like the desktop icon (as the drive is a permanent feature) so after a few seconds of googling I found this thread.  I created the new mount point under /mnt, executed "sudo umount /media/windows", edited fstab and then executed "sudo mount /mnt/windows".  The icon the appeared on my desktop.  When I reboot, however, it's not there.

:oops: Sorry.  Crisis over.  Lesson #329: If making major changes, try rebooting before posting.

-- Peter

---

### Post by Snookered on 2007-02-22
> **kakalaky said:**
> I keep forgetting that I installed it 2 releases ago, so it could be different now.  Just open a terminal and type gconf-editor

Edit:  You could also try right clicking Applications and click Edit menu.  Check in this app to see if Configuration Editor is checked, otherwise it won't show up in the menu.

Didn't know that was there?1?!  Thanks, man!

Learn something GNU every day.

---

