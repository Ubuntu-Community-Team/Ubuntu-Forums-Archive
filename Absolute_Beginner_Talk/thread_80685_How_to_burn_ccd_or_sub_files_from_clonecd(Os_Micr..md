---
title: "How to burn ccd or sub files from clonecd(Os Micr.Windows) with Linux-K3b?"
date: 2005-10-22
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-10-22
How to burn ccd or sub files from clonecd(Os Micr.Windows) with Linux-K3b?
After using windows for several yezars and now turned the page ... 
I have to make some backup to pass all my partitions to ext3 

Thank you, 

Best regards,

Patrick

---

### Post by tristangrimaux on 2007-12-12
for ccd, I am using ccd2iso to convert the image file. I tried cdemu but it hangs and does not work well with gutsy.

to install:

sudo apt-get install ccd2iso

The sintax is

ccd2iso image.img image.iso

---

### Post by Brain_of_J on 2008-02-18
I'm attempting to do this as well.
I followed the directions for installing ccd2iso.
The command
ccd2iso imagename.img imagename.iso
produced the result of
"Error: cannot open source file for reading!"

The *.img file is in the directory that i'm located in (I even tried typing in the entire file path...)
I assume ccd2iso installed correctly.
No errors resulted after the apt-get command.
Ideas?

---

### Post by johanneslandin on 2008-02-20
I had the exact same error message "Error: cannot open source file for reading!" on my opensuse 10.3.

The solution was to simply rename the img-file from .img to .iso :KS
After that i could mount it and read it without errors.

$ rm imagename.img imagename.iso
$ sudo mount -o loop imagename.iso /mnt

---

### Post by Brain_of_J on 2008-02-20
I currently have the files on the desktop and when i run the command
sudo mount -o loop imagename.iso /home/name/Desktop
I get the error stating 
'you must specify the filesystem type'

Any ideas?

---

### Post by gator64 on 2008-02-27
I'm puzzled as to why you have indicated "rm" to rename the file, as it will instead simply delete it Perhaps "mv" would be more appropriate ?

---

