---
title: "Repositories"
date: 2006-01-25
forum: Absolute Beginner Talk
---

### Post by Icebear on 2006-01-25
Hi.

Unfortunately I can not connect my ubuntu to the net. So is there a way to download selected things from the repositories(for example at my friends), then use my memory stick to transfer it to my computer.

---

### Post by sigge on 2006-01-25
A really ugly hack would be to google for whatever_app_name and add .deb I have done this several time when on machine without net... Save the .deb file to u'r mem-stick and install it manually when on the other machine, like:
sudo dpkg -i packagename.deb

---

### Post by Sutekh on 2006-01-25
A better hack is to go to [Ubuntu Packages]("http://packages.ubuntu.com/")

You can search for all the packages available in the Ubuntu repositories.  Download and copy them across and use
```
sudo dpkg -i packagename.deb
```
as previously suggested

---

### Post by zoran on 2006-01-25
hallo,
how to install anything from CD/DVD
i can not connect net.
zoran

---

### Post by Icebear on 2006-01-25
Thank you for your replies and help. This is what makes ubuntu so great people helping each other:D

---

### Post by Sutekh on 2006-01-25
[QUOTE=zoran]hallo,
how to install anything from CD/DVD
i can not connect net.
zoran[/QUOTE]
Is the CD/DVD a Ubuntu CD?  Or is it one that you've burned?

-If it's an Ubuntu CD, just open Synaptic.  Open the Edit menu and choose 'Add CD-ROM'  Then you should be able to install the packages on the CD.


-If it's a CD that you burned with packages that you've downloaded, it must have the layout in the correct format or the Synaptic method won't work.  You'll just have to copy the packages across.  Install them using the ```
sudo dpkg -i packagename.deb
```command OR copy the .deb files into the apt cache folder```
/var/cache/apt/archives
```Then use
```
sudo apt-get install packagename
```And apt-get will look in this folder when trying to install the package.



-If you are interested in making your own CD that can be used with Synpatic, check these links;

[Ubuntu Wiki - Apt Move Howto]("https://wiki.ubuntu.com/AptMoveHowto")

[How to make own repositories]("http://ubuntuforums.org/showthread.php?t=60130")

[Building Ubuntu DVD Images]("http://cargol.net/~ramon/ubuntu-dvd-en")

---

