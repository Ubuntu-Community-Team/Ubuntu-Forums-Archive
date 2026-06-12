---
title: "removing oss-linux"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by rj4 on 2007-03-21
I installed oss-linux v4.0 and it didnt go well. now I cant get it out I keep getting package manage error "The package oss-linux needs to be reinstalled,but can't find an archive for it." and Package Manager wont run. how do I get it out?
this is a HP pavillion dv8330us notebook and this is the only prod. everything elce works fine (wifi usb ect) execpt sound
Thanx

---

### Post by halitech on 2007-03-22
have you tried opening a terminal and running 

```

sudo apt-get -f install oss-linux
```

I think thats the right format for the command

---

### Post by rj4 on 2007-03-23
Thanks, but it didnt work. 

root@rj-laptop:/home/rj# apt-get -f install oss-linux
Reading package lists... Done
Building dependency tree... Done
E: The package oss-linux needs to be reinstalled, but I can't find an archive for it.
If I do any update I get this

E: The package oss-linux needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

and no updates or installs 
is there a way to fix a package manuly or uninstall manuley?
this is making me nuts

---

### Post by rj4 on 2007-03-23
The Fix 
[http://www.4front-tech.com/forum/viewtopic.php?t=2054](http://www.4front-tech.com/forum/viewtopic.php?t=2054)

---

### Post by Pindulet on 2007-04-23
I have the same problem but the linked didn't help. 

> kristian@Pindulet1:/var/lib/dpkg/info$ rm oss-linux*
rm: remove write-protected regular file `oss-linux.conffiles'? y
rm: cannot remove `oss-linux.conffiles': Permission denied
rm: remove write-protected regular file `oss-linux.list'? y
rm: cannot remove `oss-linux.list': Permission denied
rm: remove write-protected regular file `oss-linux.md5sums'? y
rm: cannot remove `oss-linux.md5sums': Permission denied
rm: remove write-protected regular file `oss-linux.postinst'? y
rm: cannot remove `oss-linux.postinst': Permission denied
rm: remove write-protected regular file `oss-linux.postrm'? y
rm: cannot remove `oss-linux.postrm': Permission denied
rm: remove write-protected regular file `oss-linux.prerm'? y
rm: cannot remove `oss-linux.prerm': Permission denied
rm: remove write-protected regular file `oss-linux.shlibs'? y
rm: cannot remove `oss-linux.shlibs': Permission denied

why dont I have permission?

---

### Post by Adamant1988 on 2007-04-23
> **Pindulet said:**
> I have the same problem but the linked didn't help. 



why dont I have permission?

You need to 

```
 sudo rm -f 
```
it.

---

### Post by Pindulet on 2007-04-23
I tried that but it seems I still have some problem with permission

```
kristian@Pindulet1:/var/lib/dpkg/info$ sudo rm oss-linux* -f
kristian@Pindulet1:/var/lib/dpkg/info$ edit /var/lib/dpkg/status
Warning: unknown mime-type for "/var/lib/dpkg/status" -- using "application/*"
Error: no write permission for file "/var/lib/dpkg/status"
kristian@Pindulet1:/var/lib/dpkg/info$  
```

what am I doing wrong?:confused:

---

### Post by Austin_KW on 2007-04-23
I think "edit /var/lib/dpkg/status" mean use your favourite editor (gedit etc) not the edit program

FYI from "apropos edit"
edit (1)             - execute programs via entries in the mailcap file

---

### Post by Delkster on 2007-04-23
> **Pindulet said:**
> I tried that but it seems I still have some problem with permission

```
kristian@Pindulet1:/var/lib/dpkg/info$ edit /var/lib/dpkg/status
```

You also need to use sudo here. You need administrator (root) privileges practically whenever you edit almost anything outside your own home directory.

You probably want "gedit" or something instead of "edit", too.

---

