---
title: "Mounting DVD-ROM"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by milad on 2007-04-26
This is the error message I get when I insert some of my DVDs:

cannot mount volume.
Invalid mount option when attempting to mount the volume

and when i try to mount it manually: 

milad@milad-linux:~$ sudo mount /dev/hdc
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I never had this problem with Edgy!

Does anybody know a solution?

---

### Post by LaRoza on 2007-04-27
What kind of DVDs are these?

It may be that you had a tool on Edgy that is not yet installed on Feisty.

---

### Post by dervis on 2007-04-30
I just have the same problem. But I was guessing something was wrong with my drive... Maybe not. Now it looks funny, because in the early morning mounting was okay, now it's the same error again. And it's the same disk  and it worked with Feisty... But before Fesity it worked everytime. :lolflag:

---

### Post by milad on 2007-05-01
Are you using an LG DVD-Rom?

---

### Post by toddward on 2007-05-01
The last time I had to get my DVD drive mounted, I needed to download general DVD drivers.  Since I'm fairly new to Ubuntu, I'm not sure if you have to locate / download them.

---

### Post by dervis on 2007-05-04
I use _NEC_DVD_/_RW_ND_6650A drive...

---

