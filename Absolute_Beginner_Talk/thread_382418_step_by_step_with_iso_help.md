---
title: "step by step with iso help?"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by tcebak on 2007-03-12
Hello, i'm having a problem with the command line mounting a .iso file. now i've read 
    
    sudo mkdir /media/iso

    sudo modprobe loop

    sudo mount filename.iso /media/iso -t iso9660 -o loop

But i get the menu of it tellling me what to do. for a frist question the .iso file i'm trying to mount is on the desktop do i need to put the iso file in that new folder. thanks!

---

### Post by SishGupta on 2007-03-12
Options come before filenames.

---

### Post by tcebak on 2007-03-12
can you tell me the comman line with the options on. and also does it matter where my .iso file is located?

---

### Post by SishGupta on 2007-03-12
sudo mount -t iso9660 -o loop /any/dir/imagename.iso /media/isoimage

no it doesn't matter where the iso is as long as the command line path is correct

so for you you might want to do

sudo mkdir /media/ISO
sudo mount -t iso9660 -o loop /home/<yourusername>/Desktop/youriso.iso /media/ISO

---

