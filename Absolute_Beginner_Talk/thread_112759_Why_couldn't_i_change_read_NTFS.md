---
title: "Why couldn't i change read NTFS"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by kurei on 2006-01-05
My hda9 is NTFS
When I use command: CD /media/hda9.It prompt that i have no permission
So,I use command: sudo kurei.
Next,password is require .
I enter password,then use chmod 777 /hda9 but not successful.
What must do now?
thanks

---

### Post by Lord Illidan on 2006-01-05
Give us your /etc/fstab

---

### Post by jimrz on 2006-01-05
Take a look [**[COLOR="Sienna"]here[/COLOR]**]("http://www.ubuntuguide.org/#automountntfs") for a guide to mounting your win partions (both FAT and ntfs). Be sure to continue down the page to the section where you edit fstab, as this will setup your win partitions to where they auto mount each time you boot up. Be SURE to backup your current fstab before editing to desired changes.

Welcome and good luck.

---

### Post by bluefrog on 2006-01-05
change in /etc/fstab:

the line with ntfs    change   defaults by user,umask=0222

sudo umount your-ntfs-drives
sudo mount -a

james

---

### Post by kurei on 2006-01-07
To bluefrog:
:) I did finish. 
To jimrz:
The page which you give me is very useful for me.The information which bluefrog 
guide me is also in it

Ubuntu is new to me,i don't know thanks how.and again,thank you

---

