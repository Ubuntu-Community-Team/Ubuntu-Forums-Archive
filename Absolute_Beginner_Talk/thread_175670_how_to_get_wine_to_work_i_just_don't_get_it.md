---
title: "how to get wine to work i just don't get it"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by shutupimpoor on 2006-05-13
ok i want to get something like pokerstars to run in wine, how do i go about doing that?

i actually really want to use zsnes in wine (i know it has a linux version but it runs crappy for me in linux and much better in windows) how do i go about getting the files and then running in wine

thanks

---

### Post by jazzmuzik on 2006-05-13
A simple way is after you have the wine deb package installed, just do a 'wine install.exe' (install.exe being the windows program you want to install) and it will install the program in /home/yourlogin/.wine/drive_c/Program Files.

Then when you want to run the program just do 'wine pokerstars.exe' or whatever the exe program is. Not all programs are successful running on wine.

---

### Post by shutupimpoor on 2006-05-13
where do i save the file that is .exe? i dont think i can just tell terminal to install and it will find it, do i just specify the location?

---

### Post by mostwanted on 2006-05-13
[QUOTE=shutupimpoor]where do i save the file that is .exe? i dont think i can just tell terminal to install and it will find it, do i just specify the location?[/QUOTE]

Yes of course. Where did you download the exe to? Your home folder?

---

### Post by jazzmuzik on 2006-05-13
Just do 'wine install.exe' and it will put everything where it's supposed to go. Just like in Windows.

Oh, you mean you lost the file you downloaded? It's probably in your user directory (cd ~; ls -l) or your user/Desktop directory.

---

### Post by shutupimpoor on 2006-05-13
zsnes comes in a .zip how do i go about that?

---

### Post by shutupimpoor on 2006-05-13
ok i just took it out of the .zip folder, now it says i need to have 16 or 32 bit color, but i have 24 right now how do i change it? i have a nvidia 5500 fx geforce video card

---

### Post by jazzmuzik on 2006-05-13
I'm not sure about changing the color bit depth. Most of that is controlled from /etc/X11/xorg.conf though.

---

### Post by YokoZar on 2006-05-13
[QUOTE=shutupimpoor]zsnes comes in a .zip how do i go about that?[/QUOTE]
There is a native zsnes for Linux that works perfectly.

Open up Synaptic, enable the universe repositories, then install zsnes by searching for it.

---

