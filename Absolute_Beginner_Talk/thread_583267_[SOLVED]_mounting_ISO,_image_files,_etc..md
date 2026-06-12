---
title: "[SOLVED] mounting ISO, image files, etc."
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by linux.convert on 2007-10-20
I have a game in ISO form, and I don't know how to go about mounting it/what to download/etc.

---

### Post by Linux_Man on 2007-10-20
What is the game? Because some MMORPGs have downloads at their sites

---

### Post by James7 on 2007-10-20
There are straightforward ways to do this on the terminal. But I use a graphical program called gmount-iso. It's in the Synaptics Package Manager (System --> Administration), just open that and do a search and install it. :D

---

### Post by anaconda on 2007-10-20
you can mount isos with
sudo mount -o loop /path/to/isofile.iso /path/to/where/you/want/to/mount/it

---

### Post by Sockerdrickan on 2007-10-20
mount -o loop -t iso9660 file.iso /mnt/test

---

### Post by linux.convert on 2007-10-20
fallout 2

i downloaded gmount, but it was in french! wth? I attempted to use it anyway but it gave me some error message.

---

### Post by VON_CAPO on 2007-10-20
Take a look to this one ----> [http://www.acetoneteam.org/](http://www.acetoneteam.org/)

---

### Post by linux.convert on 2007-10-20
when i used...

sudo mount -o loop /path/to/isofile.iso /path/to/where/you/want/to/mount/it

it asked for my password which i gave, then said no such directory

further more, i have found that i can use wine to play fallout 2, any ideas as to how i go about that?

---

### Post by linux.convert on 2007-10-21
new update, i am now attempting to wine daemon tools so the OS will recognize the ISO as a cd, because otherwise i run the game and it tells me i have to have a disk. but im not sure what command to use. while in the home directory i used...

wine daemon410-x64.exe SETUP
wine daemon410-x64.exe INSTALL
and
wine daemon410-x64.exe

and got nothing.

---

### Post by BackwardsDown on 2007-10-21
Running deamon tools in wine is problably not going to work.

But with the command "sudo mount -o loop /path/to/isofile.iso /path/to/where/you/want/to/mount/it"
you need to see if both directory-'s accually exist. So dont just copy paste the command to the command line but do this:

sudo mount -o loop <fill in where the iso is> <fill in an empty folder>

---

### Post by meighty on 2007-10-23
I've been searching all over and i'm having a hard time finding my answer. I'm trying to mount an img/iso over a network. I have a local server here in my home that holds most of my stuff and want to remotely mount some images and just run them over the local network. I can mount anything that is located on my gutsy box. My storage box is running 7.04 server and has samba installed so i can use it with windows as well. I've mounted the network share and have the via the places/connect to server. I can't get the command line or gmount to work. 

thoughts?

Thanks
Adam

---

