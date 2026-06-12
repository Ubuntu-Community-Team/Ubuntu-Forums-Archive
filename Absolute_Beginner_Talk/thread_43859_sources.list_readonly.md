---
title: "sources.list readonly"
date: 2005-06-23
forum: Absolute Beginner Talk
---

### Post by SWo2005 on 2005-06-23
Hi

Trying to add extra repositories and editing via gnome text editor or vim and I am told it's readonly.

Tried sudo chmod 644 /etc/apt/sources.list. Command was accepted but file is still readonly

Any suggestions

Thanks again

Simon

---

### Post by digby on 2005-06-23
sources.list is owned by root.  To edit it, you need root permissons.  To do this, use 'sudo' before your editor command.

-edit-
To address one other thing, permissions of 644 would still make it writable only for the owner.  The 44 in 644 makes it read-only for the group and other users.

---

### Post by pace_tua on 2005-06-23
Have you tried [color=Sienna]sudo vim /etc/apt/sources.list[/color]

---

### Post by Martin Witte on 2005-06-23
Well 644 translates to rw-r--r--, so the owner can write it. /etc/apt/sources.list is owned by root, so you edit with sudo gedit /etc/apt/sources.list, or set it open for group the worls with chmod 666 (not recommended!)

---

### Post by SWo2005 on 2005-06-23
Thanks everyone

[QUOTE=Martin Witte]Well 644 translates to rw-r--r--, so the owner can write it. /etc/apt/sources.list is owned by root, so you edit with sudo gedit /etc/apt/sources.list, or set it open for group the worls with chmod 666 (not recommended!)[/QUOTE]



When I try sudo gedit /edit/apt/sources.list an error is generated 

"GtK-Warning: Cannot open display"

When I asked about this previously, I was asked "is gnome running". I'm afraid I'm a newbie here so I'm not sure how to stop either gnome running or  to get round it some other way. Again suggestions/info would be gratefully received

S

---

### Post by Ampersand on 2005-06-23
you can't run X applications (ie ones which don't run in the terminal) as a different user from a terminal. It's probably easiest to use 'sudo nano /etc/apt/sources.list' to edit it. Once you've finished editing it, use ctrl-O to save (press eneter to accept the file name to write to), then ctrl-X to exit.
Richard

---

### Post by poofyhairguy on 2005-06-23
please try this command:


> gksudo gedit /etc/apt/sources.list

notice the gksudo.

---

### Post by SWo2005 on 2005-06-24
[QUOTE=poofyhairguy]please try this command:




notice the gksudo.[/QUOTE]


Well I tried that as well and still get  the same warning.

BTW, is it possible to open a remote desktop on another machine without having logged into gnome on the console

---

### Post by estel on 2005-06-24
[QUOTE=SWo2005]Well I tried that as well and still get  the same warning.

BTW, is it possible to open a remote desktop on another machine without having logged into gnome on the console[/QUOTE]

You mean that you want someone to log in remotely?

Yes, you need to use XMDCP.  You can connect easily enough from another Linux computer, but you'll need to install cygwin if you want to login remotely from a Windows machine. Read [here](https://wiki.ubuntu.com/HowToCygwinX?highlight=%28cygwin%29) for a tutorial on the latter.

---

### Post by fdoving on 2005-06-24
[QUOTE=SWo2005]Well I tried that as well and still get  the same warning.

BTW, is it possible to open a remote desktop on another machine without having logged into gnome on the console[/QUOTE]
 Hi.
Try 'sudo xhost +local:' and then 'sudo gedit /etc/apt/sources.list'

---

