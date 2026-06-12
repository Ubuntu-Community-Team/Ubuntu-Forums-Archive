---
title: "can't change file permissions even as sudo - please help"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by Cippa Lippa on 2007-05-23
Hi all

I have recently copied all my data from an external hard drive (probably FAT or NTFS) on my data partition (ext3). Now I can't change the permissions in Linux and in win (I am using FS-drive).
I tried sudo chmod -Rv +rw but it says something like "mode retained". In windows it simply doesn't do anything

In the properties panel it says that the folders are "locked"

Is there a way to get these files to change the permissions. That would be great!

Thanks in advance

Cippa

---

### Post by atoponce on 2007-05-23
Are you trying to change the permissions of your Linux filesystem or the Windows filesystem?  If the Windows filesystem, then chances are you are using NTFS, at which, you can't change those permissions.

---

### Post by taurus on 2007-05-23
Where exactly is that data partition located?

---

### Post by Cippa Lippa on 2007-05-23
I am trying to change permissions on files that are in a ext3 partition and that are accessible by both operating systems and in both operating systems I can't. I decided to use ext3 instead of Fat as a share partition, since there is fs-driver which allow to read and write ext3 files from windows.

---

### Post by Cippa Lippa on 2007-05-23
the data partition is my second partition on a Toshiba 120GB IDE laptop drive.

---

### Post by taurus on 2007-05-23
What command did you run to change permissions on those files?

---

### Post by Cippa Lippa on 2007-05-23
I used chmod -Rv +rw

---

### Post by wpshooter on 2007-05-23
I had something similar to this happen to me recently and what I did to get rid of the files that I could not even get rid of using SUDO, was that I marked the admin. GUI logon box in Login windows/security and then I did a GUI log on as ROOT user and then I was able to get rid of those files.  I, of course, went back and remove the ability to login as ROOT user once I was finished.

Good luck.

---

### Post by taurus on 2007-05-23
> **Cippa Lippa said:**
> I used **chmod -Rv +rw**

That was the whole command?

---

### Post by Cippa Lippa on 2007-05-23
no it was chmod -Rv +rw "directory name"

actually I could change the permissions on a single file but not on a directory!

---

### Post by Cippa Lippa on 2007-05-23
I found this in a forum. I think they were talking about debian

---The man page wasn't clear to me about the "minus are":

"Change the file flags for the file hierarchies rooted in the files instead of just the files themselves."

Huh?!

But I took a gamble that "-R" meant recursive, and it worked. So the two commands:

sudo chflags -R john
sudo chown -R john.staff john

solved my problems! Woot!

Thanks for the link. That was a very helpful explanation, and the bit about Super-Duper-User just might come in handy one of these days.

Thanks everyone!

---

but I can't find the command chflags in ubuntu

---

### Post by Cippa Lippa on 2007-05-23
I could change ownership... I selected my account... It is sort of ok since they are only data and not system files....
BNow I have to check if windows liked the change

any idea on how to change the permissions?

---

### Post by Cippa Lippa on 2007-05-23
ok it seems it is working.

Now, as the owner of the folder I can change permissions. And it seems I can change ownership back too

I'll keep you posted

---

### Post by Cippa Lippa on 2007-05-23
everything seems fine now...

this might be a good reference for people using FS-drive and having problems with file permissions.

All the best to all of you guys

Cheers

Cippa

---

