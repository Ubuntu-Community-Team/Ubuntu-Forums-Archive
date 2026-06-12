---
title: "How to install .iso disk"
date: 2005-05-11
forum: Absolute Beginner Talk
---

### Post by leslier on 2005-05-11
I'm trying hard to install ubuntu. I have 1 burned cd rom with the ubuntu-5.04.iso image on it and nothing else. My pc does boot from the cdrom but the disk does not work. Error message - No Operating System replace disk and try again.

Should there be any more files on the cdrom? 

I have had a look at the Smart Boot Manager which I am using, but I have no idea what to do with rawwrite?

The rawwrite web site does not give simple enough step by step instructions. Can someone please help as I'm desperate to get ubuntu to install. Thanks

---

### Post by Jace on 2005-05-11
Make sure in your BIOS that the cdrom is the first boot device. F10 on most systems.

---

### Post by leslier on 2005-05-11
Thanks for that but it still does not work. on the first disk I burned I get No Operating System replace disk and try again. and on the second disk I get disk error!!!

There must be something I'm missing here?????

---

### Post by spd106 on 2005-05-11
[QUOTE=][/QUOTE]
 Hi, You need to make sure that when you burn the disk image you downloaded to disk that you use software capable of writing iso images. You can't just drag and drop.

Follow the instructions on this wiki page [http://www.ubuntulinux.org/wiki/BurningIsoHowto](http://www.ubuntulinux.org/wiki/BurningIsoHowto).
It should tell you what you need to know.
Nero will also let you do this.

Hope this helps

---

### Post by poofyhairguy on 2005-05-11
[QUOTE=spd106]Hi, You need to make sure that when you burn the disk image you downloaded to disk that you use software capable of writing iso images. You can't just drag and drop.

Follow the instructions on this wiki page [http://www.ubuntulinux.org/wiki/BurningIsoHowto](http://www.ubuntulinux.org/wiki/BurningIsoHowto).
It should tell you what you need to know.
Nero will also let you do this.

Hope this helps[/QUOTE]

Also:

Be sure to burn at lower speeds


and make sure you are burning this file:

[http://us.releases.ubuntu.com/releases/5.04/ubuntu-5.04-install-i386.iso](http://us.releases.ubuntu.com/releases/5.04/ubuntu-5.04-install-i386.iso)

---

### Post by Nu-Buntu on 2005-05-13
Just to elaborate a bit, an ISO file is a single file that is a digital image of the disk. It is NOT the disk in standard file format. Therefore, if you just burn the ISO file to a CD like you would any other file, you have only made a copy of the ISO, and have not recreated the disk from the image.

You can use a tool like NERO or the full version of Roxio under Windows to burn an image to a CD and actually recreate the disk. You can also get a copy of a live Linux CD from a friend and use K3B or some other tool capable of making a disk from the ISO image.

Hope that helps.

---

### Post by jagger on 2006-01-04
Also if you don't want to buy a copy of Nero or Roxio you can use the ISO Recoder power toy available at no cost from [http://isorecorder.alexfeinman.com/isorecorder.htm]("http://isorecorder.alexfeinman.com/isorecorder.htm")

---

