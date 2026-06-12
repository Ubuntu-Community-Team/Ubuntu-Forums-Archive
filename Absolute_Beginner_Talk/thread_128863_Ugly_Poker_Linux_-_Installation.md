---
title: "Ugly Poker Linux - Installation?"
date: 2006-02-12
forum: Absolute Beginner Talk
---

### Post by darkblue1893 on 2006-02-12
I have downloaded a free video poker game for Linux and have no idea about how to install it. The download is in the form of a file called Uglypokerlinux.tgz. 

Can this file be installed in Ubuntu, if so, how? Thanks for any help given.

---

### Post by christhemonkey on 2006-02-12
sudo tar -xvf Uglypokerlinux.tgz
then 
cd Uglypokerlinux/
then probably
sudo ./configure
sudo ./make

Something like that!

---

### Post by darkblue1893 on 2006-02-12
Did that and received the following message "sudo: ./configure: command not found"

Had previously installed build-essential.

---

### Post by christhemonkey on 2006-02-12
Maybe it doesn't need configuring,
Go to the directory(in a terminal)
cd /directory/of/ugly/pokerthing
then do a 
ls -ah
and see if it mentions config or anything.
If not, just skip this step and do install.
(Plus if there are any Readme documents, they often have generic install instructions)

---

### Post by Perfect Storm on 2006-02-12
Ugly poker is a static binary package. The only thing you need is to unpack it and click UglyPokerLinux icon and you can play right away.

Enjoy ^^

---

### Post by darkblue1893 on 2006-02-14
HI thanks for the help but, i think i made a mistake and should have posted this on the kubuntu forms. I unpacked it and clicked on the icon and a window pops up asking me to pick the program to run it with.

---

### Post by claydoh on 2006-02-14
[quote=darkblue1893]HI thanks for the help but, i think i made a mistake and should have posted this on the kubuntu forms.[/quote]

Not really, this is not a KDE/Gnome issue at all. Once you have extracted the tgz file, you will need to open a konsole and type 

> cd /the/full/path-to/UglyPokerLinux. then type

> ./UglyPokerLinux

---

### Post by darkblue1893 on 2006-02-14
Hi, tried that, it did not work, the poker folder contains these files/folders - 

data (folder)
libfmod-3.74.so 
libptk.so 
UglyPokerLinux ( exe file)

When i click on the exe file nothing happens, when i go into a terminal and type   ./uglypokerlinux , i get the following message-

 bash: ./uglypokerlinux: No such file or directory

---

### Post by claydoh on 2006-02-14
Remember it is CaSe SeNsItIvE:
                             ./UglyPokerLinux is not the same as ./uglypokerlinux

Also, to make sure you are in the correct directory, run 'ls' to see the files
I think you can use Konqueror to open the directory, then right-click an empty space there and go to "Actions" then "Open Terminal Here"

I tried creating a shortcut to it on my desktop, but it would not close on its own (which it would not do from a terminal window either - but closing the terminal killes the game anyway) so if that happens for you, use ctrl-alt-escape to bring up the skull-and-bones app killer cursor and use it to kill the game that way.

---

### Post by darkblue1893 on 2006-02-15
Hi , thanks for the help. You are correct i was not entering the name as case sensitive. Still does not work though as it seems i must have problems with my ATI rage pro graphics card as i get the following error message:

libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x30
Selected OSS Output
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 111 requests (110 known processed) with 2 events remaining.

I then have to use ctr/alt/esc to shut  poker window down.

---

