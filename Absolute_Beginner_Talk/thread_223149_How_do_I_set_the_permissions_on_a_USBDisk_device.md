---
title: "How do I set the permissions on a USBDisk device?"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by margni on 2006-07-26
](*,) ...bangin my head against the wall...

I have a Samsung USB MP3 player, and I can't get new files copied into it... (this player worked perfect with FC4, but I can't get it to copy files, etc...)

I've tried opening the properties for the /media/usbdisk and tried simply checking the boxes to add more read/write properites to the device...  The checkboxes wouldn't even keep the checks!

Then I tried:  Sudo chmod 755 /media/usbdisk, and again nothing...

What's the correct way to change the permissions on a specific device in Ubuntu 6.06?  I need to re-fill my mp3 player!! :twisted: 

Thanks for any replies in advance!
Margni

---

### Post by aysiu on 2006-07-26
What filesystem is it? FAT32? FAT16? Ext3? Reiserfs?

---

### Post by JerMe on 2006-07-26
This link is for iPods, but the connectivity section should be the same:
[http://www.ubuntuforums.org/showthread.php?t=103071&highlight=ipod](http://www.ubuntuforums.org/showthread.php?t=103071&highlight=ipod)

Hope this helps.

---

### Post by margni on 2006-07-26
> **aysiu said:**
> What filesystem is it? FAT32? FAT16? Ext3? Reiserfs?

I'm not sure of the file system...  I'd bet it's FAT32, since it's recognized as a usb memory stick in both Ubuntu and XP...

---

### Post by margni on 2006-07-26
> **aysiu said:**
> What filesystem is it? FAT32? FAT16? Ext3? Reiserfs?

> **JerMe said:**
> This link is for iPods, but the connectivity section should be the same:
[http://www.ubuntuforums.org/showthread.php?t=103071&highlight=ipod](http://www.ubuntuforums.org/showthread.php?t=103071&highlight=ipod)

Hope this helps.

I'll check it out and reply back... Thanks!  I don't know if I'm going to need all the ipod software that the link has, since the Samsung is recognized like a 1GB stick drive with Ubuntu, and as it was with FC4 (and windows for that matter...)  It just seems like it needs permissions to be written to as I can delete files from it, but can't copy, or drag-n-drop new files into the device folder/window.  Does that make sense?

---

### Post by aysiu on 2006-07-26
Can you plug the drive in and then post back here the output of these three terminal commands? ```
df -h
sudo fdisk -l
cat /etc/fstab
``` Copy and paste--no need to retype anything.

---

### Post by margni on 2006-07-28
Sorry for not getting back sooner...  Work Calleth me!

margni@Memnoch:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdc3              29G  6.5G   21G  25% /
varrun                506M   80K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  132K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   19M  488M   4% /lib/modules/2.6.15-26-386/volatile
/dev/sda1             992M  990M  1.5M 100% /media/usbdisk  <<<<<<HERE'S THE MP3 PLAYER!


margni@Memnoch:~$ sudo fdisk -l
Password:

Disk /dev/hdc: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1         783     6289416    7  HPFS/NTFS
/dev/hdc2             784        3557    22282155    f  W95 Ext'd (LBA)
/dev/hdc3            3558        7296    30033517+  83  Linux
/dev/hdc5             784        2872    16779861    7  HPFS/NTFS
/dev/hdc6            2873        3394     4192933+   7  HPFS/NTFS
/dev/hdc7            3395        3557     1309266   82  Linux swap / Solaris

Disk /dev/sda: 1041 MB, 1041367040 bytes
227 heads, 56 sectors/track, 160 cylinders
Units = cylinders of 12712 * 512 = 6508544 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         160     1016932    b  W95 FAT32   <<< HERE'S' THE MP3 PLAYER


margni@Memnoch:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc7       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by aysiu on 2006-07-28
It looks as if you did ```
sudo fdisk -l
``` twice. Can you post the output of ```
cat /etc/fstab
``` as well?

---

### Post by margni on 2006-07-28
I just edited the /etc/fstab

Looks like the mp3 player isn't even showing up there...
Or should it?

???

---

### Post by aysiu on 2006-07-28
Well, in theory, what should happen is that it should not be in the /etc/fstab but should automount with the correct permissions. That's what happens, for example, when I plug in my USB Sandisk MP3 player (which is FAT16).

Unfortunately (for whatever reason), that's not happening for you, so we may have to add it to the /etc/fstab to force it to mount with the correct permissions. 

Here's how we do it.

Unmount it first: ```
sudo umount /dev/sda1
``` Make sure the mount point still exists (if you get a warning that it already exists, don't worry about it--just go to the next command): ```
sudo mkdir /media/usbdisk
``` Edit your /etc/fstab file: ```
sudo nano -B /etc/fstab
``` Paste this line in at the end of the file: ```
/dev/sda1 /media/usbdisk vfat iocharset=utf8,umask=0222 0 0
``` Save (Control-X, Y, Enter). Then remount: ```
sudo mount -a
```

---

### Post by margni on 2006-07-28
I did what you said, and it worked... BUT....

I plug the unit into a usb port, and then the OS recognizes it as /media/usbdisk with an ipod icon...

I can double click and open it within nautilus file view.  But I look at the properties, and root owns it now, and all other checkboxes for owner/group/user are dis-abled.

So I commented out the line:
/dev/sda1 /media/usbdisk vfat iocharset=utf8,umask=0222 0 0

So I could get back to square one...

the real question is what's wrong with this line?  Because i don't have control - root owns it now instead of me - and I still can't remove folders/files and cant write to the folder/files either...

It's something very simple that we aren't seeing - you know what I mean?

Margni

---

### Post by aysiu on 2006-07-28
Oh, sorry! I gave you the wrong line! That's the NTFS line. This is the FAT32 line: ```
/dev/sda1 /media/usbdisk vfat iocharset=utf8,umask=000 0 0
``` Try that one. FAT32 and NTFS drives will always be owned by root, but it's just a matter of what permissions are involved. This new line I just gave you will still have it owned by root, but it will be read/write access for everyone else, too.

---

### Post by margni on 2006-07-28
> **aysiu said:**
> Oh, sorry! I gave you the wrong line! That's the NTFS line. This is the FAT32 line: ```
/dev/sda1 /media/usbdisk vfat iocharset=utf8,umask=000 0 0
``` Try that one. FAT32 and NTFS drives will always be owned by root, but it's just a matter of what permissions are involved. This new line I just gave you will still have it owned by root, but it will be read/write access for everyone else, too.

It's still making it root...

Good thing you like to bang your head against the wall with me!  :p

---

### Post by aysiu on 2006-07-28
As I said before, root will always appear to own Windows drives (FAT32 and NTFS). The trick is getting read and/or write access for everyone else, regardless of ownership.

That new line I gave you should still give root ownership, but is also should allow read/write access to all other users.

---

### Post by margni on 2006-07-28
> **aysiu said:**
> As I said before, root will always appear to own Windows drives (FAT32 and NTFS). The trick is getting read and/or write access for everyone else, regardless of ownership.

That new line I gave you should still give root ownership, but is also should allow read/write access to all other users.

It says I can do it,,, but when I do, I get an error that says I don't have enough room on the disk (which I know I do...  I have 509mb out of 1GB mp3 playser stick)

???  I can't tell if it works...  Let me see...

I can remove all the files out of the newly-created folder, and the properties say the player is empty - and it is...

So I go and attempt copy to the folder, and I get an OS error that the disk (the mp3 player) is full...

We have the ability to 'modify' the folder by removing files, but we don't have a write priviledge yet...

Is is something in the line where it says umask=000 0 0
Should I try making the umask=755 or as such?

:)

---

### Post by avtolle on 2006-07-28
Margni: the output from the df -h command you posted shows your usb stick to be full.

---

### Post by margni on 2006-07-28
> **avtolle said:**
> Margni: the output from the df -h command you posted shows your usb stick to be full.

I just cleaned it out, and it still won't let me write to it afterwards...
in other words, I removed all the files out of the player - which it let me do...  But now, it won't let me copy back into it...

Here's the df -h now that took the songs out of it...

margni@Memnoch:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdc3              29G  6.6G   21G  25% /
varrun                506M   80K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  132K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   19M  488M   4% /lib/modules/2.6.15-26-386/volatile
/dev/sda1             992M  990M  1.5M 100% /home/ingram/mp3Player


Notice it says used 990m and avail 1.5m   That cant be right...
Maybe I should reset the player itself first...

---

### Post by avtolle on 2006-07-28
How did you move the files, i.e., did you use the file manager, or do it from the terminal? If from the terminal, did you use the cp command or the mv command? I assume from what you said, you are still getting the error message that the disk is full, am I correct? Our posts crossed; the df -h output still shows 100% used.

---

### Post by aysiu on 2006-07-28
When you "delete" files from an external drive or partition, Ubuntu actually doesn't delete those files. It moves those files to a hidden "trash" on that drive or partition. So the files are still there taking up space.

You need to do a hard delete on those. Both KDE and Gnome have options (in Konqueror and Nautilus, respectively) for enabling a delete command that bypasses the trash. Enable that. Then delete those files.

To see hidden files in Gnome, press Control-H. To see them in KDE, press Alt-V, then H.

---

### Post by avtolle on 2006-07-28
Thanks, Aysiu; I was in the process of finding those commands when your post appeared! Margni, please follow the steps in his latest post, and let us know how it went. Thanks.

---

### Post by margni on 2006-07-28
> **avtolle said:**
> Thanks, Aysiu; I was in the process of finding those commands when your post appeared! Margni, please follow the steps in his latest post, and let us know how it went. Thanks.

I 'hard removed' the files...  I saw what aysiu is talking about...  I saw the files in Nautilus, then I deleted the files to the trash can... BUT they were still on the player, so I followed the players instructions to 'format' 

The player has it's own format function, and now I know it has zero files in it...

BUT the computer still thinks it has...

margni@Memnoch:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hdc3              29G  6.6G   21G  25% /
varrun                506M   80K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  132K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   19M  488M   4% /lib/modules/2.6.15-26-386/volatile
/dev/sda1             992M  990M  1.5M 100% /media/usbdisk


Is it going south here?  :?:

---

### Post by avtolle on 2006-07-28
OK, I don't know the answer to your question. Sounds like the USB drive needs to be unmounted and then remounted for the OS to reinitialize the drive and realize it's "empty".

---

### Post by aysiu on 2006-07-28
> **margni said:**
> I 'hard removed' the files...  I saw what aysiu is talking about...  I saw the files in Nautilus, then I deleted the files to the trash can...  See--that's the problem, actually. There are multiple trash cans. When you "delete" a file from your USB drive, it's not going to the trash can on your desktop. It's going to the trash can on the USB drive. Does that make sense?

---

### Post by margni on 2006-07-28
> **avtolle said:**
> Thanks, Aysiu; I was in the process of finding those commands when your post appeared! Margni, please follow the steps in his latest post, and let us know how it went. Thanks.

OK, performed umount then mount and now df -h looks like:

/dev/sda1             992M  990M  1.5M 100% /media/usbdisk


I'm going to back track this step by step and report back...

Thanks to both Aysiu and Avtolle for your help so far...  BRB...

---

### Post by margni on 2006-07-28
> **aysiu said:**
> Oh, sorry! I gave you the wrong line! That's the NTFS line. This is the FAT32 line: ```
/dev/sda1 /media/usbdisk vfat iocharset=utf8,umask=000 0 0
``` Try that one. FAT32 and NTFS drives will always be owned by root, but it's just a matter of what permissions are involved. This new line I just gave you will still have it owned by root, but it will be read/write access for everyone else, too.

The line is definetly owned by root, but I can remove files (but remember the files weren't truly removed, and I cannot copy anything, or drag-n-drop anything into the folder...

Secondly, the player will not automount anymore either... I keep running
 sudo mount /dev/sda1 or sudo mount -a to get the players icon on the desktop.

The folder I made for the mount has a lock on it...

Isn't there a chmod or chown command that would reset the permissions on the folder/unit?

???

---

### Post by aysiu on 2006-07-28
Okay. Try this.

Plug it in.

Then ```
rm -rf /media/usbdisk/*
``` That should delete everything off the drive. To test it out, do ```
df -h
``` again.

Next... automounting. Try manually unmounting it ```
sudo umount /dev/sda1
``` commenting out the /dev/sda1 line from /etc/fstab. Physically remove the drive. Then reboot your computer. Then plug the drive in again.

---

### Post by margni on 2006-07-29
You Ready... ?

IT'S FIXED!   :D 


Once I removed the line from /etc/fstab/

I rebooted, and then plugged the mp3 player in...  So Far So Good... Ubuntu see's the player and puts an icon up on the desktop...

Now for the real test...  I open the mp3 player up in a folder view, and open up my directory with mp3 files, and drag-n-drop a couple of songs into it...

I worked...  Excellent...!!!!

Thanks for all your help Aysiu, and Avtolle...  I guess the best way to pay both of you back is to pay it forward and help someone else!

Thanks!

Margni

---

### Post by aysiu on 2006-07-29
Glad it worked out for you. > **margni said:**
> 
Thanks for all your help Aysiu, and Avtolle...  I guess the best way to pay both of you back is to pay it forward and help someone else! Yes, I would wholeheartedly agree about paying it forward.

---

### Post by TechnoPenguin on 2006-12-16
I had this same probelm and I followed these steps, but still the icon did not appear on my desk.

I then found in Settings -> Removable Media a checkbox in the Multimedia tab:  "Play music files when mounted"  (I'm not sure about it, my system is in Finnish, but it should be something like that). When I unchecked it, the icon appeared.

Just thought to share in case someone's still wondering what to do.

---

