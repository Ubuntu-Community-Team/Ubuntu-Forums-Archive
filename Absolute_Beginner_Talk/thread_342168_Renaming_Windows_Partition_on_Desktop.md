---
title: "Renaming Windows Partition on Desktop"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by Jamesbowden on 2007-01-19
My Windows Partition is on my desktop named "Hda1" I would like to rename it. But do not now how, i know you can pick what it is mounted as when you installed ubuntu, but didnt bother to name it properly at the time.

how can i rename it now?

thanks

james

---

### Post by meng on 2007-01-19
you could do this in terminal:

sudo umount /media/hda1
sudo mv /media/hda1 /media/newname

then
sudo nano -B /etc/fstab
(and replace the occurrence of /media/hda1 with /media/newname)

sudo mount -a

---

### Post by Jamesbowden on 2007-01-19
Alright i did that.

Only got up to the second step because i get this:

```
james@hackers-dojo:~$ sudo umount /media/hda1
Password:
james@hackers-dojo:~$ sudo mv media/hda1 /media/Windows
mv: cannot stat `media/hda1': No such file or directory
james@hackers-dojo:~$ 

```

so now i have just unmounted it.

---

### Post by meng on 2007-01-19
sudo mv /media/hda1 /media/Windows
You didn't copy the command correctly, you're missing a /

---

### Post by Jamesbowden on 2007-01-19
> **meng said:**
> sudo mv /media/hda1 /media/Windows
You didn't copy the command correctly, you're missing a /


Oh that you, sorry i was being an idiot, i'll try again now

---

### Post by Jamesbowden on 2007-01-19
Alright i did it, i didn't get any error messages, but now the partition is'nt showing on my desktop, but it is showing up under "/media"

any idea what the problem is? Or is there anyway to just create a launcher to open it on the desktop?

---

### Post by meng on 2007-01-19
What if you log back out and in again? Or perhaps reboot? I'm surprised it doesn't show on the desktop.

---

### Post by oni5115 on 2007-10-27
Using Gutsy, I had the same issue with them not showing back up.  So I followed your directions, but before rebooting or anything I added:

sudo mount -a /media/Windows

This mounted the drive, causing it to show up on my screen.  Rebooted after to make sure the changes stuck, and it worked fine.  Hopefully, that works for you too.

---

### Post by robert_ps88 on 2008-03-24
hi, i have the similar problem but for me i have already rename the mounting folder but now the name changed to the partition's ntfs label which is "local disk" for c drive  and  "local disk (2)"  for d drive.
is there anyway to rename this?

---

