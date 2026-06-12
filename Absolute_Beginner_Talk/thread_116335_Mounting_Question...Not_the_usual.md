---
title: "Mounting Question...Not the usual"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by David Grove on 2006-01-12
I have a machine that is dedicated to Ubuntu (5.10)
It does NOT dual boot, and there are NO MS Windows filesystems in the box.

How do / Can I 'Mount' these Ubuntu filesystems from another machine on my network that is WinXP based?
For Example : I have MP3's (of my own ripped originals) that I would like to access with iTunes on a WinXP machine in my son's room.

Is this a Samba based solution.

Thanks!

---

### Post by Arktis on 2006-01-12
First it's just a matter of sharing the folder with the mp3's over your local network and then accessing the shares from your son's windows xp box.  Right click the folder with the mp3's in it and select "Share Folder", enter your sudo password and it will prompt you to install sharing services and then you can set up the share via a GUI.

This can be troubling once it comes time to access the shares though... I've often had problems sharing files over the network between xp and ubuntu.  Mainly they never show up in the network browser for some reason.  The solution for me after trying common troubleshooting steps (such as making sure it's not being blocked by a firewall) is manually typing in the local network address of the computer you're trying to get that shares from into explorer (if trying to access ubuntu from xp) or nautilus (if trying to access xp from ubuntu).  You can find the local network address of your ubuntu machine by opening a terminal and typing the command 'ifconfig'.  The address you are looking for should be something like 192.168.1.100.  Then on your sons PC, acces your mp3's by typing your ubuntu machine's local address into explorer.  You should see the folder you shared.

Open command prompt on the xp machine.

use the command 'net use drive: \\computername\sharename'

Replace drive with an unused drive letter, like Z or something.  replace computername with the ubuntu box's hostname (local address of the ubuntu box will probably work too), and replace sharename with the network name of the folder you shared with the mp3's in it.  Your network share should now be mounted in xp.

---

