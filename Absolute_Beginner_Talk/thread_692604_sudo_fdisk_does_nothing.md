---
title: "sudo fdisk does nothing"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by bkelly on 2008-02-09
I have a second hard drive that does not seem to mount correctly.  A search found another thread on this topic.  The recomendation was to run:

sudo fdisk -l

So I tried it to compare responses.  First it asked for a password, which I supplied. (The passwords for my account and for root are the same)  It responded with a prompt and no information.  Then I tried it again and just got the prompt back with no password request.  Using  fdisk -l without the sudo returns only the prompt.  

When I select Places | Computer, the display shows icons for CD-RW drive, CD-RW/DVD+RW Drive (I have a CD and a DVD installed), an drive that looks kind of like a floppy (but I don't have a floppy) icon labled /1 and another ddrive labled Filesystem.  

Clicking Filesystem shows the files I expect on a system drive.  Click the /1 returns the error message:

   Cannot mount volume.
   Error org.freedesktop.Hal.Device.PermissionDeniedByPolicy.

Selecting the Details options returns:
   hal-storage-fixed-mount refused uid 1001

What do I need to do different to:
a) mount the second hard drive
b)  get sudo and fdisk to return some valid information?

Thanks for your time.

---

### Post by spiderbatdad on 2008-02-10
does this user account have administrative privileges? I expected uid=1000

---

### Post by altonbr on 2008-03-04
I often have problems with:
```
$ sudo fdisk -l
$ fdisk -l
$ sudo su
# fdisk -l
```
as it also returns nothing.

Can anyone help me out?

---

### Post by ruy_lopez on 2008-03-04
What about:

```

sudo fdisk -l /dev/hda

```

where /dev/hda is the volume device, from running "df", without the specific partition number.

---

