---
title: "How do I unzip an encrypted 7z archive with archive manager?"
date: 2013-03-15
forum: Any Other OS
---

### Post by Nerv68 on 2013-03-15
I have an encrypted 7z archive and when I open it with archive manager it says "an error occured while loading the archive". (the file is not corrupt)
Is there something I need to install to get it to work?
What about RAR?

(using Mint 14)

---

### Post by Perfect Storm on 2013-03-15
Moved to Other OS/Distro Talk.

---

### Post by schragge on 2013-03-15
```
sudo apt-get install p7zip{,-full}
``` After that the archive manager will be able to handle 7z archives.

---

### Post by sudodus on 2013-03-15
> **Nerv68 said:**
> I have an encrypted 7z archive and when I open it with archive manager it says "an error occured while loading the archive". (the file is not corrupt)
Is there something I need to install to get it to work?
What about RAR?

(using Mint 14)
I made a small encrypted archive with two text files from the current directory with the following command
```
7z a -mhe=on -p test.7z .
```
(the password is prompted)

It worked without issues to open it with the default archive program in Ubuntu 12.04 LTS
```
file-roller test.7z 
``` Of course it wants the password, but after that I can view the files. (Use your appropriate file name)

I think either your 7z file is corrupt, or your file-roller does not have 7z tools. Install it with the following command and try again
```
sudo apt-get install p7zip-full
```
If still no go with file-roller, try
```
7z e test.7z
```
(Use your appropriate file name)

---

