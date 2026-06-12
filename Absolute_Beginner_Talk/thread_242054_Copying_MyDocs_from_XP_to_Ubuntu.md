---
title: "Copying MyDocs from XP to Ubuntu"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by James0044 on 2006-08-23
Hi, 

I'm a total newcommer to Ubuntu, and could use a bit of help.
I have a laptop running XP which contains all my doccuments, I've just set up a desktop to run Ubuntu (Dapper). 

I have copied my docs to a cdrw and tried to copy these to Ubuntu, but it tells me it can't mount the CD drive. 

I know this is something to do with the different file systems used by XP and Ubuntu, but i don't know any more than that.

Any help would be great, i am a complete beginner though.

Thanks
James

---

### Post by mssever on 2006-08-23
Do other CDs work? If so, than you probably have a bad burn. Otherwise, Ubuntu's having trouble talking to your CD drive.

If you're dual booting, there's an easier solution. If you go to the /media folder, you'll see a folder for your Windows partition. It's probably hda1 or something similar. You can navigate to your My Documents folder there and copy across to your Linux partition.

Note: You may already know this, but if you're using WinXP, your My Documents folder is in C:\Documents and Settings\Your User\My Documents. Translate this to Linux and you're all set.

---

### Post by mssever on 2006-08-23
Sorry...didn't read your post carefully enough...You've got two computers.

If you have them networked together, you can also try sharing your My Documents folder on the Win box. Then use Nautilus from Linux  and go to Go > Network and navigate to your Windowx box.

---

### Post by Rhubarb on 2006-08-23
Also, make sure that the session is closed on the CD that you've burnt.

---

### Post by mozetti on 2006-08-23
Sounds like a bad burn to me. 

FYI - the problem of:> the different file systems used by XP and Ubuntu doesn't apply here. CDs have their own file system, too. CDFS, or Compact Disc File System, which both Windows and Linux can read/write -- they have to, in order to use CD-Rs.

---

### Post by James0044 on 2006-08-23
Thanks all!

Your were right, bad burn on the CD, went out and got some new CDR's and it worked fine.

Thanks for the quick response too!

James

---

### Post by jeremy on 2006-08-23
If you copy you docs from the cd to you Linux system, you will have to change the permissions to make them writable.

---

