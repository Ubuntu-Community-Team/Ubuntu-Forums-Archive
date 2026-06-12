---
title: "Hard Drives"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by sonrise on 2007-01-17
Why are USB and firewire external harddrives easier to work with than internal harddrives

---

### Post by jvc26 on 2007-01-17
I don't know - Ive never had problems with either ;) What is the issue you're having and can we help? :)
Il

---

### Post by taurus on 2007-01-17
Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by jd65pl on 2007-01-17
Can't say this goes for everyone!

---

### Post by bugster on 2007-01-17
> **sonrise said:**
> Why are USB and firewire external harddrives easier to work with than internal harddrives

Same here.  My USB hard drive was found by edgy eft during installation but I'm still looking for the internal drive.  Not complaining though - this is my latest attempt to learn about Linux and I'm very impressed.  It found my display, keyboard, USB drive and printer without any prompt from me.  Far better than a few years ago !!

---

### Post by jvc26 on 2007-01-17
No it doesnt - some of my friends have had horrible problems with either/both of the above two, hence I said could we have the problem, if there is one clarified then we could help :)
Il

---

### Post by jd65pl on 2007-01-17
> Same here. My USB hard drive was found by edgy eft during installation but I'm still looking for the internal drive. Not complaining though - this is my latest attempt to learn about Linux and I'm very impressed. It found my display, keyboard, USB drive and printer without any prompt from me. Far better than a few years ago !!

If the live CD mounted your internal hard drive with your *other Os* install on and lets say it was trashed {not through linux's fault} you would probably also find this function disagreeable. You can mount drives once a system has booted. Search the forum or use the wiki, it is **very  **well documented

---

### Post by sonrise on 2007-01-17
On my latest installthe usb and fire wire harddrives work fine they are readable and writable but the internal drives are read only. All drives are NTFS except the C drive which was formatted to linusx on the install.

---

### Post by taurus on 2007-01-17
Can you please post the outputs of these two commands from a terminal?

```
sudo fdisk -l 
cat /etc/fstab
```

---

### Post by sonrise on 2007-01-17
Not able I am at the library on a library computer. I finally got 6.06 to recognize all my drives.

Problem #1. The C drive has the 6.06 install but is read only on the empty space. The D drive (internal) is NTFS and its read only, Drive E (internal) is NTFS and its read only, Drive F ( internal) is Fat 32 and its read only Drive G (firewire) is NTFS but its read and write, Drive H (usb) is NTFS and its read and write, Drive I (usb) is Fat 32 and its read and write. cantget the internal to the write status.

---

### Post by taurus on 2007-01-17
The C, D, E, or whatever drive is meaningless in Linux.  Can you post this output from a terminal and tell me which partition (/dev/xxx) you want to mount?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

