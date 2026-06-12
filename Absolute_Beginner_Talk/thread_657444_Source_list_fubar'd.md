---
title: "Source list fubar'd"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by mobi on 2008-01-03
Hello,
I think I've messed up my source list somehow.  When I try to do a apt-get update I get the following:

W: GPG error: [http://ftp.debian.org](http://ftp.debian.org) sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277
W: You may want to run apt-get update to correct these problems

I tried to run it again like it suggests but get the same result.  Is there a way to recreate the source list?  If so can someone give detailed how-to?

Thanks,
mobi

---

### Post by aysiu on 2008-01-03
You shouldn't really have Debian repositories in Ubuntu.

To get a new sources.list, try this:
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by lamalex on 2008-01-03
Did you add the debian repo to your system? it looks like you just need their GPG key, although Aysiu is right, you shouldn't have Debian repos in your Ubuntu source list.

---

### Post by mobi on 2008-01-04
Thanks for the replies guys.  I'm not sure what I did.  I may have added the debian, not sure.  I would just like to get it back to default so I can update the box.

---

### Post by shifty2 on 2008-01-04
To get it back to a "default" go to the link that aysiu posted and complete the form that is on the website.

ie, for me with gutsy I would choose the following options:
Country I live in: UK
Ubuntu release: Gutsy Gibbon
Architecture of computer: i386
*click send and go to next page*
Underneath "Default Repositories" there should be two options both with checked boxes next to them. underneath that is a "create sources.list button". Click on it.

A load of text should appear on the screen, this is your new sources.list. Select all, right click and copy

To get the computer to use this new source list:
back-up the old sources.list and create a new one (paste these two lines in separately):
```
sudo mv /etc/apt/sources.list  /etc/apt/sources.list.old
sudo touch /etc/apt/sources.list
```

Then we need create our new sources.list:
```
gksudo gedit /etc/apt/sources.list
``` 
This opens a text editor window. Paste in the text that you copied earlier and save your file. Then to tell your computer to use this and not the old one:
```
sudo apt-get update
```

---

### Post by mobi on 2008-01-04
Thanks so much shifty...your instructions worked perfectly.  Thanks to all who replied!

---

