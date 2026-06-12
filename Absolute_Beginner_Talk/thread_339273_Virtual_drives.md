---
title: "Virtual drives"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by Jkirch on 2007-01-15
Ok, I'm a nebie and I just switched my system over to Ubuntu. I love it so far, and if things keep going this smoothly I might completely switch to Ubuntu. :)  Now I think I've pretty much figured out all the replacements apps in Ubuntu that I used in Windows, but I want to know if you guys have any suggestions on DVD virtual drives. I like to put all my DVD's on hard drive and so in Windows I used Daemon tools for the virtual drives and DVD decrypter for creating the .ISO's. So is their anything like that for Ubuntu?

---

### Post by smartbei on 2007-01-15
If I remember correctly you can just use the mount command to mount images. So:

```
sudo mkdir /media/virtualdrive
sudo mount <path_to_iso> /media/virtualdrive

```
If I understood correctly anyway...

Not sure about creating the .iso though...probably something really simple.

---

### Post by taurus on 2007-01-15
> **smartbei said:**
> If I remember correctly you can just use the mount command to mount images. So:

```
sudo mkdir /media/virtualdrive
sudo mount <path_to_iso> /media/virtualdrive

```
If I understood correctly anyway...

Not sure about creating the .iso though...probably something really simple.

```
sudo mount -t iso9660 -o loop **filename.iso** /media/virtualdrive
```

---

### Post by Oki on 2007-01-15
Or if you want a application with GUI you can install Kiso. Search in Synaptic for kiso. 

Edit; if you are running Edgy you could also install gISOmount.

---

### Post by Jkirch on 2007-01-15
That's awesome that you can just mount the image, man I'm liking Linux more and more. Any suggestions on creating dvd iso's. Thanks everybody!

---

### Post by fakie_flip on 2007-02-17
> **Jkirch said:**
> That's awesome that you can just mount the image, man I'm liking Linux more and more. Any suggestions on creating dvd iso's. Thanks everybody!

Find the dvd or cd device that has the disk you want create an iso from.

e.g. /dev/dvd /dev/cdrom /dev/hda /dev/hdb etc.

Then you can do

dd if=/dev/dvd of=filename.iso

Or you can do

cat /dev/dvd > filename.iso

Replace /dev/dvd with your device file.

---

### Post by mcduck on 2007-02-17
also, if they are movie DVDs you don't even need to mount them, as VLC can play movies directly from the image file..

---

