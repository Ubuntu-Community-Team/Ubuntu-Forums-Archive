---
title: "installing programs"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by djsoss on 2007-07-28
Okay, I went to the ubuntu pakages site to download some programs. the programs I downloaded were gnome-ppp & tkmixer. I downloaded the to my usb drive via a windows box, I then inserted the memory stick in to the linux box and went add and remove programs. It opens and shows me a list of stuff from with in the program that I'm trying to install but that's as far as I get and don't know what to do from there :confused: Please help.

---

### Post by felicity on 2007-07-28
I haven't used Dapper, but as far as I know, you should be able to double-click the deb's you downloaded on your stick to open up the installer, without having to go through Add/Remove programs.

---

### Post by Mark_in_Hollywood on 2007-07-28
I'm no expert, so wait for another post or two, please. If you have 'net access an easier way is System/Administraion/Synaptic Package Manger. Search for those files by name that you mentioned in your post. The search returned will show all the files associated. You may want some more. but don't worry synaptic will find, download and install the necessary dependencies.

Otherwise, move the files from the memory stick onto your desktop. Highlight one and right click, if the GDebi installer is at the top of the list, use it. Otherwise you may have to untar which is beyond where I'm able to help.

The GDebi installer knows where to put the files. A window will come up asking (radio button) INSTALL. Click it and wait.

---

### Post by Mornedhel on 2007-07-28
felicity is right, it works under Dapper. However, gnome-ppp requires some other packages not found in a default install of Ubuntu. You've stumbled across the greatest problem of all Debian-based OSes : no net access, no APT super powers.

---

### Post by djsoss on 2007-07-30
> **felicity said:**
> I haven't used Dapper, but as far as I know, you should be able to double-click the deb's you downloaded on your stick to open up the installer, without having to go through Add/Remove programs.

Wow!! I tried right clicking it and openin it with and and remove programs and I even tried doulbe clicking it. At first it just opend up a list of files and yestereday when I did the same thing, it asked me for my admin password and after that it didn't do any thing.

---

### Post by aysiu on 2007-07-30
Double-clicking the .deb file should usually open it with gDebi for installation, but if that's not working, make sure the .deb file is on your desktop and then type this command into [the terminal](http://www.psychocats.net/ubuntu/terminal) (case matters): ```
cd ~/Desktop
sudo dpkg -i *.deb
```

---

### Post by djsoss on 2007-07-30
> **aysiu said:**
> Double-clicking the .deb file should usually open it with gDebi for installation, but if that's not working, make sure the .deb file is on your desktop and then type this command into [the terminal](http://www.psychocats.net/ubuntu/terminal) (case matters): ```
cd ~/Desktop
sudo dpkg -i *.deb
```
Thanks, will try.:)

---

### Post by frotzed on 2007-07-30
> **aysiu said:**
> Double-clicking the .deb file should usually open it with gDebi for installation, but if that's not working, make sure the .deb file is on your desktop and then type this command into [the terminal](http://www.psychocats.net/ubuntu/terminal) (case matters): ```
cd ~/Desktop
sudo dpkg -i *.deb
```

OK, this is may be a little off topic.  I know that *.deb means any .deb file on the Desktop.  But what does dpkg mean?  And why do you have to put that -i in there?

I apologize for the n00b question, but it's something I've wondered and just wanted a simple answer to.

---

### Post by Paul820 on 2007-07-30
dpkg is debian package the -i is for install

---

### Post by frotzed on 2007-07-30
Thanks.

---

### Post by djsoss on 2007-08-06
Dose it matter that the programs that I am trying to install end with a trg extension?

---

### Post by aysiu on 2007-08-06
> **djsoss said:**
> Dose it matter that the programs that I am trying to install end with a trg extension?
Yes, it matters.

They should have the .deb extension.

You can find the proper packages here:
[http://packages.ubuntu.com](http://packages.ubuntu.com)

---

