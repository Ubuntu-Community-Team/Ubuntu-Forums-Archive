---
title: "Nero .nrg images"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by Deived on 2007-08-21
Question.  I know you can mount .iso images in Linux/Ubunto.  Is it possible to mount a nero disk image (.nrg).

---

### Post by TeaSwigger on 2007-08-21
Yes. :)

By converting the .nrg to an .iso format then mount it. It's easy to do. If I recall correctly you can just enter:

```
sudo apt-get install nrg2iso
```

to install the converter. To see the simple instructions, enter:

> man nrg2iso

Also if you like, you can install a GUI to mount the iso, like GISOMount. 

Enjoy. :guitar:

---

### Post by Deived on 2007-08-21
w00t!  Thanks dude.  That really helps.  I have a bunch of audible.com audio books that I burned to nero image so that I can mount and reimport into iTunes as mp3 to get past the DRM when I move to Ubuntu.  I still have a bunch of images to reimport but I'm eager to get Ubuntu as my main OS on my laptop.  I was hoping I would just be able to do it once Im in ubuntu, rather than before I move.

---

### Post by Divan Santana on 2007-08-23
did u come right?
I'm trying to do the same...
But downloaded the audible.com book burnt to nrg files and converted to .iso but when I try mount it it says I must specify the filesystem...
strange.
I tried iso9660 and udf and nothing works. I will try burn the iso with k3b now...

---

### Post by Deived on 2007-08-23
I was able to convert all the .nrg to .iso with no problem.  I haven't tried mounting them yet.  I was looking around and there are some scripts you can use to mount iso's with a right-click menu option in nautilus but was too busy last night with stuff to try it out.  I have a bunch of images to rip so I wanted to make it simple to go through them all.  Here's a link...
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_Image_.28ISO.29_files_without_burning](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_Image_.28ISO.29_files_without_burning)

There are some others if you search google.

---

### Post by amb.physis on 2007-09-04
Well... I'm having an issue here... I tried to convert the nrg file into iso (with nrg2iso) and I get the error 

```

alex@laptop:~/Desktop$ nrg2iso Riff\ Interactive\ -\ Blues\ Legends\ Ii.nrg Riff\ Interactive\ -\ Blues\ Legends\ Ii.iso
It seems that Riff Interactive - Blues Legends Ii.nrg is already an ISO 9660 image 
[Aborting conversion]

```

then I just renamed the .nrg file into .iso and I can open it nicely with the file roller (still didn't go through the step of mounting it...) but ALAS! all the files end with a ";1" ...

```

alex@laptop:~/Desktop/Blues Legends$ ls -l
total 648
drwx------ 2 alex alex   4096 2007-09-05 01:40 03-15-01
drwx------ 2 alex alex   4096 2007-09-05 01:40 08-03-00
drwx------ 2 alex alex   4096 2007-09-05 01:40 08-10-00
drwx------ 2 alex alex   4096 2007-09-05 01:40 09-13-01
-rw-r--r-- 1 alex alex   8706 2007-09-05 01:40 about.htm;1
-rw-r--r-- 1 alex alex  14261 2007-09-05 01:40 ANIMATE.JS;1
-rw-r--r-- 1 alex alex   1509 2007-09-05 01:40 ARCHIVE1.HTM;1
-rw-r--r-- 1 alex alex   1509 2007-09-05 01:40 ARCHIVE2.HTM;1

```

and so on... so it doesn't actually seem to be a proper iso image... but nrg2iso doesn't recognize it as nrg either... off course I could rename all the files, but it doesn't seem to be a clean solution to me...

any idea??

Thanks for any help in advance

---

