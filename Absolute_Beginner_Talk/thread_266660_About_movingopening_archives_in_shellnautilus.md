---
title: "About moving/opening archives in shell/nautilus"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by The Tronyx on 2006-09-27
I recently download the xmms media player and I had hoped to add a new skin.  I downloaded the skin (tar.gz) and extracted it to my desktop.  The problem is that the skin directory for xmms is /usr/share/xmms/skins.  I can't drag the archive there via nautilus and I am having a hard time getting the command to put it there.  Any wise words?

---

### Post by annda on 2006-09-27
you can't move the files because as an ordinary user (as opposed to someone with administrator privileges) you don't have the permission to write to a system directory (/usr/share/and_so_on).

run nautilus from terminal ```
gksudo nautilus
``` and enter your user password at prompt

and read more about permissions here:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Metacarpal on 2006-09-27
You have to have root/su privileges to add things to /usr or any of its subdirectories.  There are two ways to do this:

The graphical way:

1. unpack the tar.gz to your Desktop, or in a new folder in your /home directory.

2. Hit Alt+F2 and enter:
```
gksudo nautilus
```
That'll bring up a window asking for your password, then pop open Nautilus.

3. Use that new Nautilus window to copy/paste the unpacked files into /usr/share/xmms/skins


The somewhat faster command-line way:

1. unpack the tar.gz to a new folder on your Desktop or in your /home directory.

2. Open a terminal (Applications > Accessories > Terminal) and enter:
```
sudo cp /home/*username*/Desktop/*foldername*/* /usr/share/xmms/skins/
```
replacing *username* and *foldername* with your username and the folder you created.

---

