---
title: "Clean Rewritable disc"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by gwoodard on 2008-01-11
How do you erase data on a CD-RW? I know plenty around Ubuntu but never cleaned a CDRW except on Windows can anyone help?

---

### Post by phidia on 2008-01-11
In GnomeBaker Tools> Clean CD RW  for  DVD it's Format DVD+-RW. Hope that helps.

---

### Post by jcwmoore on 2008-01-11
[http://ubuntuforums.org/showthread.php?t=172388]("http://ubuntuforums.org/showthread.php?t=172388")

Try this Thread

---

### Post by Shazaam on 2008-01-11
I don't know the cli command right off but I use gnomebaker for cdrw's and such. There is a section in the program that will let you erase disks. There are quite a few other programs out there that you might like better like k3b.

---

### Post by nikoPSK on 2008-01-12
Now I know too, thanks all.

---

### Post by bharadwaj on 2008-01-12
just start off writing dvds or cds normally the way you do it in gnome baker but for rw it automatically erases rws before writing

---

### Post by nikoPSK on 2008-01-12
> **bharadwaj said:**
> just start off writing dvds or cds normally the way you do it in gnome baker but for rw it automatically erases rws before writing

Ooh? So it erases automatically like in nero?

---

### Post by Whiffle on 2008-01-12
k3b does it automagically as well

---

### Post by nikoPSK on 2008-01-12
> **Whiffle said:**
> k3b does it automagically as well

Ah, well I stopped using K3B for awhile. I need to try gnomebaker apparently.

---

### Post by Cannaregio on 2008-01-12
> **gwoodard said:**
> How do you erase data on a CD-RW? I know plenty around Ubuntu but never cleaned a CDRW except on Windows can anyone help?

```
sudo cdrecord dev=/dev/cdrom blank=all
```

This did the job for me.
Note that it will "seem" as if the disk hasn't been blanked, if you just open the disk icon, but it is blanked allright: eject and reinsert and then check again and everything will be dandy.

Note that the same problem appears for dvd + RW, where you have to use
```
sudo dvd+rw-format -force  /dev/dvd
```

I still believe these problems are mainly due to the low quality DVD writers we use, in my case an Hewlett Packard HP dvd writer 740b.

---

