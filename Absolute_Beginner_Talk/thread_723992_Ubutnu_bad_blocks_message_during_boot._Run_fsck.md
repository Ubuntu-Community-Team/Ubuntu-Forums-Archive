---
title: "Ubutnu bad blocks message during boot. Run fsck"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by chrisdee on 2008-03-14
Hello. For some time now iv had problems with permission denied messages when backing up files with rsync from my IMAC to my Ubuntu 6.0.6 web/mail/samba/ssh server on some directories (not all).

When encountering this problem I have rebooted the system. Then I during boot get messages about bad blocks on disk and that I have to run fsck to fix this. Doing this has resolved the problem, and rsync copying works again.

Today however after rebooting, the system hangs on mounting file system. Iv tried reboting several times and choose the different recovery modes etc, but they all hang while mounting the file system.

I guess this is a bad disk problem ?
Any ideas how I can fix this ?
Reinstall ?
New pc ?

---

### Post by wieman01 on 2008-03-14
So you cannot boot at all even while in recovery mode? I think that's pretty bad news... I had that once and had to reinstall the computer. But before you do so, I would pull backups. Use the Live CD to do so... But wait until others have posted as well.

---

### Post by chrisdee on 2008-03-14
Unfortunately the ubuntu server is my main backup machine
where I run daily backups.

On the bright side I have all my data intact on the IMAC machine +
I have a usb disk with backup of my data in my garage in case
of fire.

But as you say, I will not take any steps befor I get some more
tips and comments from the good people on this forum first.

Anyway, im a bit afraid that reinstall wount solve the problem
if its a bad disk thats causing these messages.

I do have a old shuttle pc I dont use (from 2002) wich I could
install the new Ubuntu 7.10 maby ?

I forsee a lot of work ahead  for me this weekend:(

---

### Post by wieman01 on 2008-03-14
You can still recover data by running LiveCD, mounting the drives in questions, and copying the data. It is worth a shot and should be relatively simple.

---

### Post by chrisdee on 2008-03-14
Im not familiar with Live CD. What is it ?
Is it the Ubuntu installation cd ?

---

### Post by sandysandy on 2008-03-14
> **chrisdee said:**
> Im not familiar with Live CD. What is it ?
Is it the Ubuntu installation cd ?

live CD is the installation CD. 

it is bootable.

u may have used the alternate CD.

---

### Post by wieman01 on 2008-03-14
Yeah, it's the installation CD. You can boot from it, mount the partition and recover your data. If you don't know how to do it, please let us know. It's really simple.

---

### Post by chrisdee on 2008-03-14
Ok. I'll try that. Thanks for your replies:)

---

