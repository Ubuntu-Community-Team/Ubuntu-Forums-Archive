---
title: "How can I automatically mount removable drive and allow read/write to every one?"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by Knitter on 2007-01-02
Hi,

I've been using ubuntu for quite some time now, but I still use my Windows installation more so there are things that, even after a full year, I have not tried...
I bought today an external 2.5" HDD, I formated it leaving a 100GB NTFS partition and a 20GB ext3 partition, rounded up values. 
The drive shows up correctly in my desktop, I can see and read the NTFS, I don't need the write access, but I can't write to the ext3 partition. I understand that the partition was created with root access and therefor the files are owned by root.
What I need is a way to make the disk always have the same label and allow me to have write access without having to mount the disk manually.

I have found some threads about how to make labels and add entries to the fstab file but I can't find how to allow write access to a disk that mounts at boot.

What I don't understand is how to make the disk boot up allowing me to write to it without having to open a console and type some commands. I would like it to be has straightforward has any pen drive that I plug into my usb



I've searched the forums but have failed to find any answer to what I need, if there is a thread about this please just post the link. I'll be happy to follow it :D

---

### Post by taurus on 2007-01-02
Where do you mount that ext3 partition.  You can change the permission to mount point with the chmod command!!!  If you are not sure what the mount point for that ext3 is, this command should tell you...

Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by Knitter on 2007-01-02
I don't mount it, well not manually. It is mounted when I plug the drive into the usb port, and I really want it to continue that way :D

I know how to use the mount command, and how to change the file permissions and how to find the mounting point, it actually shows in my desktop with a nice icon ;)

Those "normal" things are not the problem. The problem is that I want Ubuntu to mount the drive when I plug it, I know that that is set up in the fstab, or so I think it is. But what I don't know is how to make every user allowed to write to the ext3 partition... is it a fstab option?

I'm starting to think that it is just a fstab option... going to google for it...

---

### Post by konst88 on 2007-01-02
I think if you chmod this partiton recursively, to 777, it will do the trick.

---

### Post by taurus on 2007-01-02
> **Knitter said:**
> I don't mount it, well not manually. It is mounted when I plug the drive into the usb port, and I really want it to continue that way :D

I know how to use the mount command, and how to change the file permissions and how to find the mounting point, it actually shows in my desktop with a nice icon ;)

Those "normal" things are not the problem. The problem is that I want Ubuntu to mount the drive when I plug it, I know that that is set up in the fstab, or so I think it is. But what I don't know is how to make every user allowed to write to the ext3 partition... is it a fstab option?

I'm starting to think that it is just a fstab option... going to google for it...

And that's why I asked for the output of that command, df -h, so I would know what the mount point it.  Then, I can show you how to change the permissions so you can read and write to it!!!

```
sudo chmod -R 777 **<mount point>**
```

---

### Post by Frank Golden on 2007-01-02
> **konst88 said:**
> I think if you chmod this partiton recursively, to 777, it will do the trick.
Or change to Fat32. Is there any special reason to use ext3? If you change to Fat32
you can access it from XP.

---

### Post by taurus on 2007-01-02
> **Frank Golden said:**
> Or change to Fat32. Is there any special reason to use ext3? If you change to Fat32
you can access it from XP.

You can access ext2/ext3 from XP with [http://fs-driver.org](http://fs-driver.org)!!!

---

### Post by Frank Golden on 2007-01-02
> **taurus said:**
> You can access ext2/ext3 from XP with [http://fs-driver.org](http://fs-driver.org)!!! This is still an "experimental"  program correct. Wouldn't changing the ro flag in the fstab
entry for the partition to rw accomplish the desired actions.

---

