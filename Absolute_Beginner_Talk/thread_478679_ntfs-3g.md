---
title: "ntfs-3g"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by mrsempai on 2007-06-19
i've been trying to set up my ntfs partition in ubuntu 7.04 but i need to know its UUID for it to work since it doesnt appear on my /etc/fstab... can someone help me? ive searched google and couldnt find anything...

---

### Post by meborc on 2007-06-19
what you need is a "ntfs-config" package... it is a simple program allowing you to mount ntfs correctly... no uuid needed to insert...

you can get it by "sudo apt-get install ntfs-config"

[http://flomertens.free.fr/ntfs-config/screen.html](http://flomertens.free.fr/ntfs-config/screen.html)

---

### Post by 5-HT on 2007-06-19
To find out UUIDs:```
ls -l /dev/disk/by-uuid
```

---

### Post by gn2 on 2007-06-19
> **mrsempai said:**
> i've been trying to set up my ntfs partition in ubuntu 7.04 but i need to know its UUID for it to work since it doesnt appear on my /etc/fstab... can someone help me? ive searched google and couldnt find anything...

Just cheat and do it through [www.getautomatix.com](www.getautomatix.com).

It has an NTFS auto-mounter available in the "Miscellaneous" category once you've got it installed.

As with all Linux software there's no guarantees of reliability.....

But it works flawlessly in my experience.

---

### Post by dunklegend on 2007-06-19
I've used automatix and ntfs-3g config and they work fine for me.
ntfs-3g config is more simple but automatix lets you setup a bunch of stuff at once.

Good luck

---

### Post by mrsempai on 2007-07-03
the ntfs config and the automatix ntfs application dont seem to work for me... can someone help me set up ntfs-3g?

found a guide here in the forum, but its kind of old and its for edgy... any help would be more than welcome

---

### Post by Beatbreaker on 2007-07-05
> **gn2 said:**
> Just cheat and do it through [www.getautomatix.com](www.getautomatix.com).

It has an NTFS auto-mounter available in the "Miscellaneous" category once you've got it installed.

As with all Linux software there's no guarantees of reliability.....

But it works flawlessly in my experience.

I'm seriously considering getting the Automatix -3g NTFS auto mount stuff on my system too - i do know there's no gurantees that it will work but really i'm wondering how risky is it?

I haven't found any theads with people saying that it's stuffed their HDDs up just yet and i also read that GG will be using 3G too for automounting NTFS partitions.

should i take the plundge? I've got all my NTFS drives in read mode only, it would be nice to write to them too (well atleast to a few of them, read access on my windows drive can remain the same)

so yeah, any horror stories to tell?

---

### Post by Songwind on 2007-07-05
I set up my NTFS partition without knowing the UUID

Just FYI

---

### Post by taisao on 2007-07-05
> **mrsempai said:**
> the ntfs config and the automatix ntfs application dont seem to work for me... can someone help me set up ntfs-3g?

found a guide here in the forum, but its kind of old and its for edgy... any help would be more than welcome

you could try this here:

[https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite)

---

### Post by stchman on 2007-07-05
> **mrsempai said:**
> i've been trying to set up my ntfs partition in ubuntu 7.04 but i need to know its UUID for it to work since it doesnt appear on my /etc/fstab... can someone help me? ive searched google and couldnt find anything...

So what you are wnating is for Ubuntu to mount the NTFS partition for read/write.

No problem.  Make sure you have ntfs-3g installed and then add the following to your fstab.

/dev/hda1       /media/windows ntfs-3g  defaults  0   0

This assumes your NTFS partition is hda1.  You need to make a folder called /media/windows as a mount point.

After reboot you will be see and icon on your desktop called windows.  No UUID is required.  Refer to my page for more info.

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

---

