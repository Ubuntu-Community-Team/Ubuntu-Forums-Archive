---
title: "[SOLVED] Can't access HDA"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by Goldpin on 2006-04-05
This has probably been asked a thousand times before, but I need to know how to access my windows drive.

I'm dual booting with Windows XP on HDA and Ubuntu on HDB.  The HDA icon appears on my Ubuntu desktop, but when I try to browse the files on it, I'm told I don't have permission do do so.  ](*,) 

How can I change or obtain permissions to do this?  I'd like to be able to access HDA without having to obtain permissions every time.

HDA is formatted as NTFS so I know I can't write to it, but I'd like to be able to read the files and save them on the Ubuntu drive.

Any suggestions?

Please answer in words of one syllable telling me what to do and how to do it.  I'm completely new to all this.

Thanks in advance

---

### Post by meborc on 2006-04-05
it seems to be a permission problem in fstab

in terminal type

**sudo cp /etc/fstab /etc/fstab_backup**
then
**sudo gedit /etc/fstab**

now gedit will open the file... go to the line which points to your windows partition... probably a line with ntfs in it... make the line look like this:

**/dev/hda[COLOR="Red"]x[/COLOR]    /media/[COLOR="red"]windows[/COLOR] ntfs  nls=utf8,umask=0222  0    0**

change the red parts to whatever is your configuration (hda1, hda2, hda3 or whatever is your win partition nr; and the folder where it gets mounted)... the most important part is the umask=0222 in your case... this is the part of permissions... if it is 0222 the it should be fine

EDIT: if anything goes wrong you can save the situation by typing:
**sudo cp /etc/fstab_backup /etc/fstab**
this will restore the original file from the backup

EDIT2: oh, and check out the breezy guide from my sig for further help!

---

### Post by millol on 2006-04-05
Code:
> sudo gedit /etc/fstab
Then search for the line corresponding to your hda for instance:
> /dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
and make sure the umask value is: 0222

---

### Post by Ric95 on 2006-04-10
In Dapper, I just tried 'sudo nautilus' and it seemed to work fine :)
Is there any hazard to doing it that way?

---

### Post by chizzt on 2006-04-11
After you edit and save /etc/fstab, you may need to restart the machine ( or rerun init!). It's one of the few places where you need to think like a windows user!

---

### Post by Goldpin on 2006-04-15
[QUOTE=meborc]it seems to be a permission problem in fstab

in terminal type

**sudo cp /etc/fstab /etc/fstab_backup**
then
**sudo gedit /etc/fstab**

now gedit will open the file... go to the line which points to your windows partition... probably a line with ntfs in it... make the line look like this:

**/dev/hda[COLOR="Red"]x[/COLOR]    /media/[COLOR="red"]windows[/COLOR] ntfs  nls=utf8,umask=0222  0    0**

change the red parts to whatever is your configuration (hda1, hda2, hda3 or whatever is your win partition nr; and the folder where it gets mounted)... the most important part is the umask=0222 in your case... this is the part of permissions... if it is 0222 the it should be fine

EDIT: if anything goes wrong you can save the situation by typing:
**sudo cp /etc/fstab_backup /etc/fstab**
this will restore the original file from the backup

EDIT2: oh, and check out the breezy guide from my sig for further help![/QUOTE]

After much tinkering I finally got it to work (looks like I had to install nls or something).  However I did a few reinstalls before it worked.  At the moment I have a FAT32 partition on my linux drive (hdb) which is hdb5.  I'd like to be able to access this from linux, but I'm told I don't have the necessary permissions to write to it.  Will this fix work for hdb5 as well?

Thanks

---

### Post by xenmax on 2006-04-15
To enable write access to a FAT32 partiotion, you need umask=0000.
Read this thread - it might help
[http://www.ubuntuforums.org/showthread.php?t=144321](http://www.ubuntuforums.org/showthread.php?t=144321)

---

