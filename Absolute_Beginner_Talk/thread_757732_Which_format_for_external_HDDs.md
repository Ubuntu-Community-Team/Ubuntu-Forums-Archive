---
title: "Which format for external HDDs?"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by Xarok on 2008-04-17
So I keep all my data on 4 external HDDs 
and I want to use them with Windows, OSX, and Linux,

currently I'm using fat32 on them because all three can read it easily
but I don't trust its stability (I've been getting more data corruption now than before when  I was using HTFS)

Is there a better option such as formating them as NTFS and then getting some NTFS reader for OSX (if there is such a thing)?

I also want to be able to use Unison on the HDDs but I'm not sure what formats it supports.

Also, a random question... can malware copy itself on to external HDDs and be spread around that way? If so, is there any measures I can take to prevent this?

Thanks in advance

---

### Post by northern lights on 2008-04-17
Both Ubuntu (any Linux with ntfs-3g) and OSX read from and write to NTFS

---

### Post by northern lights on 2008-04-17
> **Xarok said:**
> Also, a random question... can malware copy itself on to external HDDs and be spread around that way?
Theoretically? Sure.

Practically speaking, what is Windows malware gonna do to a *nix os MacOS system? Exactly - nothing...

[EDIT]Darn. Meant to edit in the first place...[/EDIT]

---

### Post by dca on 2008-04-17
FWIW, I went NTFS, indeed the FAT32 is a good idea but I've run into problems when it's formatted FAT32 and you're trying to move a large file.  It has problems determining how much space is left (or something thereabouts) and says 'not enough disk space'...  Sure enough converting to NTFS solved the issue...

---

### Post by Xarok on 2008-04-17
> **northern lights said:**
> Theoretically? Sure.

Practically speaking, what is Windows malware gonna do to a *nix os MacOS system? Exactly - nothing...

[EDIT]Darn. Meant to edit in the first place...[/EDIT]

I referring to spreading malware from one Windows machine to another.

Also, OSX support for NTFS is still only read (no write capability),
Is there a program for OSX so it can write to NTFS?

How about EXT3?
Is there programs for Windows and OSX that allow them to read & write to EXT3 formated drives?

---

### Post by Traceur-UK on 2008-04-17
I recall a program in Windows that let you copy files from EXT3, but it's quite slow and not very practical. It'd be better if it integrated with Windows, but it's just a standalone app.

Personally, for accessing between *nix and Windows, I use Fat32 but that's due to it not letting me format the partition as NTFS (for whatever reason). I've ran into no problems with it yet and it's working fine (I even resized it, and it still works flawlessly).

---

### Post by alecz20 on 2008-04-17
I don't really like the use of third party programs for such basic disc operations.

On rather different alternative would be to connect all your external HDD's to ones of the machines (or a cheap linux server) and share them with samba through a 100/1000 cable connection.

---

### Post by northern lights on 2008-04-17
> **Xarok said:**
> Also, OSX support for NTFS is still only readYou certain? I've written to an external NTFS HDD from a friends MacBook (Leopard). I'd be surprised if she (History major) figured it out herself, but I'll ask and report back...

---

### Post by bodhi.zazen on 2008-04-17
> **Xarok said:**
> I referring to spreading malware from one Windows machine to another.

Also, OSX support for NTFS is still only read (no write capability),
Is there a program for OSX so it can write to NTFS?

How about EXT3?
Is there programs for Windows and OSX that allow them to read & write to EXT3 formated drives?

NTFS is likely the best bet.

And yes, shared drive = shared malware. If you are mounting the drive on different Windows machines take care you scan the device for malware on a regular basis.

It is unlikely malware will cross platforms (ie windows malware will not affect Linux/OSX).

---

### Post by Traceur-UK on 2008-04-17
But if it was to be accessed on multiple Windows installations, it might spread.. I guess it depends on whereabouts it is situated on the harddrive...

---

### Post by warbread on 2008-04-17
Looks like EXT2 might be a good option.

[Windows]("http://www.fs-driver.org/")
[OSX]("http://fuz2y.blogspot.com/2008/04/how-to-mount-ext3-partition-on-os-x.html")

---

### Post by aeiah on 2008-04-17
there is now seamless drivers (ie, the partitions are treated like any other, not a seperate application) for windows and os x that can read and write to ext2 and (probably) ext3. this will be practical if you're copying to computers that you own or regularly to friends, but if you're going to be using office computers or internet cafe ones etc then i guess you'll have to stick to something more universal.

---

