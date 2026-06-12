---
title: "Installing .iso files in Virtual Box?"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by Tom--d on 2008-03-09
How do I install an OS in Virtual Box by using the .iso file from the hard drive? 

I don't want to burn the image onto a disk, just boot the file in the hard drive into Virtual Box.

Can it be done or do I have to burn it on a CD?

Thanks,
Tom

---

### Post by glennric on 2008-03-09
You can mount the iso using
```
sudo mount -o loop -t iso9660 filename.iso /media/iso
```
You will have to create the directory /media/iso with
```
sudo mkdir /media/iso
```

---

### Post by glennric on 2008-03-09
Scratch that last post.  A better way is to go to the settings in Virtual box for the virtual machine, select CD/DVD rom, and select the option to use an iso image.

---

### Post by p_quarles on 2008-03-09
Mounting the disk via Bash is unnecessary, since Virtualbox includes a utility for mounting disk images. Once you have created a virtual machine, various options -- including mounting a CD or .iso image -- will show up.

---

### Post by Tom--d on 2008-03-09
Ah!
Got it.

Thanks :)

---

