---
title: "what is this file?"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by yamfox on 2008-04-06
I downloaded a .iso file but when I open it in CD/DVD Creator it tells me it's not a valid iso image. How can I see what this '.iso' file actually is? :confused: I am very confused.

---

### Post by ugm6hr on 2008-04-06
> **yamfox said:**
> I downloaded a .iso file but when I open it in CD/DVD Creator it tells me it's not a valid iso image. How can I see what this '.iso' file actually is? :confused: I am very confused.

You downloaded something without knowing what it is?

Always dangerous.

---

### Post by Hospadar on 2008-04-06
try opening it with "Archive Manager"  Right click the file and "Open->With"
this will let you browse the files on the iso, if indeed it is a valid image file.

---

### Post by Michael.Godawski on 2008-04-06
Where did you downloaded the "iso" file? What is it ?

---

### Post by NightwishFan on 2008-04-06
also try
```
file filename.iso
```

---

### Post by yamfox on 2008-04-06
nope, Hospadar, it gives me this error:
> CD-ROM is NOT in ISO 9660 format

I know what this means, I just don't know what kind of file it actually is. Isn't there a command-line utility that lets you see what type of file it is that isn't fooled be extentions? I've heard about it somewhere....

---

### Post by yamfox on 2008-04-06
i tried the file utility, it gives me this:
> /home/yamfox/Downloads/MACOS9.2.1ISO/macos921.iso: data
yes, it's updates for an old Mac I own.

---

### Post by stroyan on 2008-04-06
You may have downloaded it incorrectly.
Some access methods such as ftp have binary vs. ascii download modes.
Downloading an iso with a non-binary mode will result in a file of junk.

---

### Post by m60dude5 on 2008-04-06
I don't think you can open .iso s all the time. Try burning it to cd as an image and boot from it.

---

### Post by ajgreeny on 2008-04-06
Alternatively, you may be able to mount it with the mount command 
sudo  mount -o loop -t iso9660 path/to/file.iso mount/path which should show you what is in it.  I've no idea about mac file systems, though, so this may not work.

---

### Post by yamfox on 2008-04-06
It was downloaded via torrent, if that helps.

---

### Post by nhandler on 2008-04-06
Try verifying the md5 sum. Most torrent sites post the md5 hash for files. To view the md5 hash for a file in Ubuntu use the following command

```
md5sum /path/to/file
```

If the md5sum you generate does not exactly match the one on the torrent site, it means you have a corrupted download. Try redownloading it.

---

