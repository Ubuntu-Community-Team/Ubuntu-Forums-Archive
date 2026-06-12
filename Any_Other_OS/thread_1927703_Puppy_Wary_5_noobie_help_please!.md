---
title: "Puppy Wary 5 noobie help please!"
date: 2012-02-18
forum: Any Other OS
---

### Post by Hash_Burnswell on 2012-02-18
I'm honestly not sure if this is the right forum, but i figured this is such a simple question someone here would know. I'm using puppy wary 5 to get files from a broken windows xp system. I can access the internal hard drive but when i plug in an external hard drive and try to copy i get an error: "cp: cannot create regular file `/mnt/sdg1/janece 1979.jpg': Read-only file system"  (sdg1 is the external hard drive)

I'm guessing i just have to set it to not be read only... But I can't figure out how.

Thanks in advance.

---

### Post by cogier on 2012-02-18
I don't know what your issue is but can I suggest that you try an Ubuntu Live CD and see if that works. I would suggest Ubuntu 10.04.

It must be worth a try.

---

### Post by Hash_Burnswell on 2012-02-18
> **cogier said:**
> I don't know what your issue is but can I suggest that you try an Ubuntu Live CD and see if that works. I would suggest Ubuntu 10.04.

It must be worth a try.

That is the first thing i tried. Cd/dvd drive is dead or something. I borrowed this puppy usb  from a friend. The comp wont boot from cd. I can only usb boot =/

---

### Post by Lisiano on 2012-02-18
What is the filesystem on the external HDD? My guess is that Puppy might not have proper NTFS support, I haven't tried Puppy so I don't know.
You can try to do this to remount the HDD as RW
```
sudo mount -o rw,remount /mnt/sdg1/
```

EDIT: Ubuntu boots from USB too. Try [Unetbootin]("http://unetbootin.sourceforge.net/")

---

### Post by Hash_Burnswell on 2012-02-18
> **Lisiano said:**
> What is the filesystem on the external HDD? My guess is that Puppy might not have proper NTFS support, I haven't tried Puppy so I don't know.
You can try to do this to remount the HDD as RW
```
sudo mount -o rw,remount /mnt/sdg1/
```EDIT: Ubuntu boots from USB too. Try [Unetbootin]("http://unetbootin.sourceforge.net/")

So i just paste 
sudo mount -o rw,remount /mnt/sdg1/ 
Into the console?

---

### Post by Lisiano on 2012-02-18
If you are already root then you can omit sudo. But yes, that's all. If Puppy has RW support for the filesystem you have on your external HDD then it should work.

---

### Post by Hash_Burnswell on 2012-02-18
I'm going to get a larger usb and boot ubuntu. Thanks for all the advice.

---

### Post by winh8r on 2012-02-18
Just a thought, you may have tried already but , check that the computer is set to boot from CD/DVD drive in BIOS settings, and choice is saved to CMOS before exiting BIOS settings.

---

### Post by Hash_Burnswell on 2012-02-18
> **winh8r said:**
> Just a thought, you may have tried already but , check that the computer is set to boot from CD/DVD drive in BIOS settings, and choice is saved to CMOS before exiting BIOS settings.

I had to set it to boot from usb. But thanks for the advice.

---

### Post by oldos2er on 2012-02-18
Thread moved to Other OS/Distro Talk.

---

### Post by KosakiHook on 2012-06-17
> **Hash_Burnswell said:**
> I'm honestly not sure if this is the right forum, but i figured this is such a simple question someone here would know. I'm using puppy wary 5 to get files from a broken windows xp system. I can access the internal hard drive but when i plug in an external hard drive and try to copy i get an error: "cp: cannot create regular file `/mnt/sdg1/janece 1979.jpg': Read-only file system"  (sdg1 is the external hard drive)

I'm guessing i just have to set it to not be read only... But I can't figure out how.

Thanks in advance.

Make sure the HD is mounted before attempting to copy over the files. Just because the HD is plugged in, it is not necessary mounted. To do so, you can do it in a couple of different ways. Once the HD is plugged in, there might be an icon of the HD on the bottom left corner of the screen. Click the icon, and there should be a little dot indicating that it's mounted. Alternatively, you can click menu - filesystem - pmount (I'm doing this from memory as I'm not using puppy now). Then, assuming it is a USB HD drive you're using, there should be a usb tab. Click that, and your HD should be listed. Then, click mount.

At this point, should should be able to copy files from the internal HD to the external HD.

---

