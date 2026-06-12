---
title: "Sharing a Printer on Xubuntu"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by dragonflyseven on 2006-08-02
I am trying to share a printer that is set up on Xubuntu with the rest of the home network (which includes Windows computers), but I can not find a way to make the computer shared. Is there a folder I can add to the the shared documents that will allow other computers to use the printer? Also, when I try to access the computer over the nextwork, it asks for a password and username, and the administrator username and password don't help. Thanks in advance...

---

### Post by FooAtari on 2006-08-02
I havent tried to do this yet.  But have also been wondering how I go about sharing folders and the printer with my Laptop, which is running XP, while the PC runs Ubuntu.

---

### Post by dannyboy79 on 2006-08-03
dragonflyseven: For the printer issue, (assuming you have cups installed because I have xubuntu 6.06 and I didn't have to install cups) you need to type [http://localhost:163/printers](http://localhost:163/printers) and then set up your printer for cups then within this browser based config you'll be bale to share the printer with everyone. In order to be able to browse your computer from a windows pc you need to set up a smb user on your xubuntu machine, that smb user needs to be a user htat already exists within your xubuntu setup. it's been awhile since I set it up but after I googled it I found this excellent wiki which will help you get it setup. [http://gentoo-wiki.com/HOWTO_Setup_Samba#Adding_a_Valid_User](http://gentoo-wiki.com/HOWTO_Setup_Samba#Adding_a_Valid_User).
If you can ping your windows box and vis versa you should be able to share files.


FooAtari: As far as sharing folder within ubuntu, you go to administration, then sharing, then just select the folders you want to share on your ubuntu box, of course this is assuming you have samba configured already. If you can ping your windows box and vis versa you should be able to share files. the printer sharing is the same as above. I am not at home right now, I am at work so I can't really be super specific, but if you try to do what I have suggested and you still have questions just post back and I'll probably be at home by hten and can probabl help you out more.

---

### Post by carlosqueso on 2006-08-03
installing gnome-cups-manager also helps with printer sharing.  I couldn't have done it without it.

---

### Post by TFX360 on 2006-08-07
Hi All,

Correction on previous post by dannyboy: The url should be [http://localhost:631/printers/]("http://localhost:631/printers/")

The **gnome-cups-manager** is to be found under ***System -> Administration -> Printing*** and from there to enable CUPS website ***Global Settings -> Detect LAN Printers***.

Kind regards,

TFX

---

### Post by tarclee on 2006-08-28
i have try go to the url to add a share printer but what should i type in the URI?should i chose ipp?now the network user can't use the printer to print.pls help.

---

### Post by TFX360 on 2006-08-29
> **tarclee said:**
> i have try go to the url to add a share printer but what should i type in the URI?should i chose ipp?now the network user can't use the printer to print.pls help.

Dear Tarclee,

Check [here]("http://www.ubuntuforums.org/showthread.php?t=213060&highlight=cups+printing").

It's about CUPS network printing.


Kind regards,


TFX

---

