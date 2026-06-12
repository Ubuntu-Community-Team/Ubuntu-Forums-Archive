---
title: "sd card reader &amp; program location"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by james.gaede on 2007-05-22
2 Problems:

1) Can't get Feisty to recognize when I insert a sd card into my ACER 5630 card reader.  Device manager shows a card reader...

2) Installed Realplayer 10 by downloading .bin from Real's website...now program is installed in home directory and wont show up in my applications menu.  I would like it to.  On a related note, where are all the other programs stored in Ubuntu?  I'd like to add some to the startup session...

Thanks, 
James

---

### Post by macogw on 2007-05-22
What card reader is it?  Type lspci into the terminal.  If it's a Texas Instruments one, try downloading [http://geocities.com/dollzrgr8/tifm_install.tar.gz](http://geocities.com/dollzrgr8/tifm_install.tar.gz)

They're stored in /usr/bin usually, but that doesn't matter.  Just put the command you use to run it (usually just the name) into your startup tab on the System > Preferences > Sessions thing

---

### Post by Jad on 2007-05-23
Macogw, 
Please elaborate, I installed it but I have no idea how to run it because I don't know what was installed and what its name.

---

### Post by Inxsible on 2007-05-23
> **macogw said:**
> What card reader is it? Type lspci into the terminal. If it's a Texas Instruments one, try downloading [http://geocities.com/dollzrgr8/tifm_install.tar.gz](http://geocities.com/dollzrgr8/tifm_install.tar.gz)
 
They're stored in /usr/bin usually, but that doesn't matter. Just put the command you use to run it (usually just the name) into your startup tab on the System > Preferences > Sessions thing
 
I installed the tifm packages, however my lspci shows the reader to be Ricoh and not TI. Are there drivers / packages available for Ricoh ?
 
I installed this just last night, so I havent thoroughly tested it. Will the memory stick and xD cards be read too ?

---

