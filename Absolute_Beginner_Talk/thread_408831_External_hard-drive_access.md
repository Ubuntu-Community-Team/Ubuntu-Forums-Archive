---
title: "External hard-drive access?"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by AgelessDrifter on 2007-04-13
I have a SimpleTech 250G external hard-drive that plugs into my USB. The system requirements on the box only have the info about Windows and Mac, but I don't get the impression that Windows and Mac themselves are requirements. Any one know how I might access this drive from ubuntu?

edit: Actually (stupid me) I just turned it on and it pops right up in a file browser window. The thing is, when you back things up on this drive, it compacts everything and gives you a "quickrestore.exe" file in order to restore it. Since Linux apparently doesn't run .exes, is there any way I can use this drive from Linux, or am I hosed?

---

### Post by taurus on 2007-04-13
When you plug it in, does it automout?  Otherwise, try something like

```
sudo mkdir /media/windows
sudo mount -t vfat /dev/sda1 /media/windows -o iocharset=utf8,umask=000
df -h
```

---

### Post by AgelessDrifter on 2007-04-13
Yeah, now that I've plugged it in (I didn't realize it was unplugged when I made the first post), it's auto-mounted and has an icon on the desktop, but I can't write anything to it, or do anything with the files that are in there (backed up when I was still running windows)

---

### Post by Ptero-4 on 2007-04-13
He said that the drive does automount, but that it automatically compresses the files you put in it (in a secret, propietary format I guess) and gives you a windoze app to uncompress the contents. The solution I think is to format the drive (any linux filesystem will do), the reason is b/c the drive might contain a sort of function in it`s firmware that compresses the files and puts the windoze decompressor, but by changing the partition type to a linux one the firmware function will become non-operational and the drive will become just a mass-storage device.

---

### Post by AgelessDrifter on 2007-04-13
I hadn't even considered that. Do you think things will take up more space on the drive that way (no compression)? What should I use to format it? I have partition magic on my windows partition, but is there an app on ubuntu I can use?

---

### Post by RealG187 on 2007-04-13
USB HDs show up automatically [I love my USB HD, all my docs arfe there in case I need to reinatall and I can use it in any OS!]

Use Wine for run most .exe!

---

### Post by Ptero-4 on 2007-04-14
to format use:
```
sudo mkfs -t ext3 /dev/yourusbdisk
```

In the terminal
(Applications>Accesories>Terminal).

---

### Post by RealG187 on 2007-04-14
> **Ptero-4 said:**
> to format use:
```
sudo mkfs -t ext3 /dev/yourusbdisk
```

In the terminal
(Applications>Accesories>Terminal).
But then Windozr won't read it, I a  keeping FAT32, cuz Linux don't read NTFS...

---

### Post by taurus on 2007-04-14
> **RealG187 said:**
> But then Windozr won't read it, I a  keeping FAT32, cuz Linux don't read NTFS...

Actually, Linux can read NTFS just fine but if you want to write to it, then you need to use ntfs-3g driver.

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

In the meantime, you can read ext2/ext3 filesystem fine in Windows if you install fs-driver.

[http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by Treasure Trooper on 2007-04-14
Spam...

---

### Post by RealG187 on 2007-04-15
> **taurus said:**
> Actually, Linux can read NTFS just fine but if you want to write to it, then you need to use ntfs-3g driver.

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)



i tried and it does read[heard it doesnt]

ill try da links, r they safe would it use ntfs compression? any good backup software, my files r outdated and i dont wanna manually recopy all files when lots are unchanged, is there a way to only copy new/updated files and leave unchanged alone, it slows it down!

---

