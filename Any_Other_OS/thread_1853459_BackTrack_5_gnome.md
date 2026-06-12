---
title: "BackTrack 5 gnome"
date: 2011-10-02
forum: Any Other OS
---

### Post by alcapony007 on 2011-10-02
Hi guys, I have a big problem with Linux BackTrack 5 GNOME 32 bit.
First of all I installed windows 7 and than on the same partition C I installed backtrack 5. I have many files on both systems. Few days after I was doing something with partitions and after reeboot I didn't have grub ... I had only:
"Error unknown file system
grub rescue>"

I read about grub and I tried to reinstall grub. No sucssess cause I can't mount my partition and i dont know why...
I tried everything: do this manually, Timos rescue CD set, boot repair disk and that last one repaired my Windows 7 MBR so now when i restart computer it load windows. 
Help me to reisntall/rebuild grub or just tell me how to copy few files from linux partition. I need only few text files. Please help me. It's very important to me. Have any ideas?
Sorry if thread not in correct place.

---

### Post by Dangertux on 2011-10-02
My suggestion boot to the Back Track 5 LiveDVD or Ubuntu LiveCD either will work then do the following

Open terminal and type the folllowing

```

mount /dev/sda1 /mnt

```

*this assumes Back Track is on /dev/sda1 modify this appropriately for your partitions

Then

```

grub-install --root-directory /mnt /dev/sda

```

Reboot system you should be presented with the grub bootloader (however it probably only has backtrack)

Then in Back Track open a terminal and do the following

```

mount /dev/sda3 /mnt
update-grub

```

*This assumes your windows is on sda3 change as appropriate

Reboot and your Windows 7 and Back Track should be available in the bootloader.

Hope that helps.

---

### Post by uRock on 2011-10-02
Moved to "*Other OS/Distro Talk*"

---

### Post by alcapony007 on 2011-10-03
Hi guys,
I typed:
mount /dev/sda2 /mnt
It giaves me:
you must specify the filesystem type
so I typed:
mount -t ext3 /dev/sda2 /mnt

here is the image:
[http://imageshack.us/photo/my-images/508/backtrack5.jpg/](http://imageshack.us/photo/my-images/508/backtrack5.jpg/)
[IMG]http://imageshack.us/photo/my-images/508/backtrack5.jpg/[/IMG]

---

### Post by alcapony007 on 2011-10-05
Can anyone help me ?

---

