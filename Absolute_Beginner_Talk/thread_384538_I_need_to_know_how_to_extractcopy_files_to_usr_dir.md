---
title: "I need to know how to extract/copy files to usr directory"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by jerseyboy91 on 2007-03-14
I've been trying to get Xarchiver to extract files needed to get my laptop's internet connection working. I know what to do, but I need to know how to get the .tar.bz2 archive from my home folder to my /usr/linux-kernel/... folder. Since I can't do it with Xarchiver (since it doesn't ask for my password), I have to do it with Terminal, but I don't know how!

So can someone give me the command for extracting .tar files from one folder to the usr folder?

---

### Post by dannyboy79 on 2007-03-14
> **jerseyboy91 said:**
> I've been trying to get Xarchiver to extract files needed to get my laptop's internet connection working. I know what to do, but I need to know how to get the .tar.bz2 archive from my home folder to my /usr/linux-kernel/... folder. Since I can't do it with Xarchiver (since it doesn't ask for my password), I have to do it with Terminal, but I don't know how!

So can someone give me the command for extracting .tar files from one folder to the usr folder?

you can run xarchiver from the terminal with root privalages. you would do
gksudo xarchiver

or you can learn how to untar stuff by reading the linux man pages, do 
man tar

man gzip

man bzip2

---

### Post by jerseyboy91 on 2007-03-14
Thanks, I'll try that right now!

---

### Post by aysiu on 2007-03-14
A variation on what dannyboy79 suggested:

Extract them to your home directory.

Then press Alt-F2 and type ```
gksudo nautilus
``` This will open a file browser as root. Browse to the appropriate /usr directory and drag and drop the extracted files there.

---

