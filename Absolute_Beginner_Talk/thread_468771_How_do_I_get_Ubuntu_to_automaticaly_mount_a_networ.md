---
title: "How do I get Ubuntu to automaticaly mount a network folder each log in?"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by Mark Raymond on 2007-06-09
I've finally managed to mount this Windows shared folder: (the original problem was I hadn't got all of Samba installed)
sudo mount //192.168.2.2/Mark /home/markr/mydocs

How do I make this happen every time I log in, without having to type it or enter the root password?

---

### Post by cantormath on 2007-06-09
> **Mark Raymond said:**
> I've finally managed to mount this Windows shared folder: (the original problem was I hadn't got all of Samba installed)
sudo mount //192.168.2.2/Mark /home/markr/mydocs

How do I make this happen every time I log in, without having to type it or enter the root password?

In the menu,  PLACES>Connect to Server

a window will pop up, pick windows share and fill out the info,  a icon will show up on the desktop and will stay there after reboot.  

You can also do this with SSH, FTP and http.....or any other protocol you could probably think of.

Hope this helps.

---

### Post by alex_anthony on 2007-06-09
try [[COLOR="Blue"]_here_[/COLOR]]("https://help.ubuntu.com/community/MountWindowsSharesPermanently")
or 
[_[COLOR="Blue"]here[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=255872")

---

### Post by huygens on 2007-06-16
I would recommend the post of cantormath. It is the easiest way to do so, and with a nice GUI :-)
It will be readily accessible with-in Nautilus and most (if not all) Gnome application.

However, if you are using some application that have custom dialog boxes for opening or saving files, or if you use application not designed specifically for the Gnome desktop, the post alex_anthony is the way to go.
By the way, in the latest two links are provided. Both are using "smbfs" for the file-system type. If you have Windows 2000, XP, 2003, Vista, I would **recommend to use "cifs" instead**.
The syntax is almost similar and if it works for smbfs, it will work even better with cifs. If you are interested, there is a draft wiki [how to mount network disk using cifs]("http://www.berthon.eu/wiki/foss:wikishelf:smb:cifs"). In this article, you have 3 chapters, one about smbfs (rather similar to the resources pointed earlier), one about cifs (that's the one I recommend to you) and finally some a tip if you have spaces in the shares of your drive.

---

