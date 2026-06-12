---
title: "OS for slow PC's - very confused"
date: 2006-04-19
forum: Absolute Beginner Talk
---

### Post by linuxnoobtothemax on 2006-04-19
Yeh iam completly new to linux i have never used it before, and at my local church we have some old computer which we want to fix up and give away to the church community, but me not wanting to get into trouble i dont want to set them up with pirated windows XP and Office, however these computers could barely run XP anyway. The next solution seemed to be windows 98, having used that before, i will never ever go back to it because of its terrible reliability. Now i remeber that i can install linux on these computers for free and maybe could find a linux version thats designed for slow computers. 

Ive read a post saying IceWM and XFCE are the way to go but i have no idea where to go from there. Do i just download these programs and install them/? whats the deal, do i need to install Ubuntu first? lol im so confused :rolleyes:

By slow pcs, i mean 300Mhz AMD and 96 - 128RAM

---

### Post by Stone123 on 2006-04-19
Xubuntu will work on that with no problem. As somone else in forum reported on p2 300 AMD processors. 
ANyway take a look at :
[https://wiki.ubuntu.com/Xubuntu](https://wiki.ubuntu.com/Xubuntu)

---

### Post by az on 2006-04-19
[QUOTE=linuxnoobtothemax]
Ive read a post saying IceWM and XFCE are the way to go but i have no idea where to go from there. Do i just download these programs and install them/? whats the deal, do i need to install Ubuntu first? lol im so confused :rolleyes:

By slow pcs, i mean 300Mhz AMD and 96 - 128RAM[/QUOTE]

Here is a gudeline:

-  If they have more than 5 gigs of hard drive space, install the default ubuntu system, and then add the universe repositories and add on the lightwieght desktop.   Then make the light desktop the default session in the login manager.
-  If they have less that 5 gigs of hard drive space, just install the base system (type "server" when you boot the installer) and then just install the lightweight desktop
  ->You need to boot into your base system and edit the /etc/apt/sources.list file and remove the # at the beginning of hte universe line to do that.

sudo vi /etc/apt/sources.list
(press x to delete a character, press :wq to save and exit.
sudo apt-get update
sudo apt-get install x-window-system-core xterm icewm menu synaptic gdm mozilla-firefox
and/or
sudo apt-get install xubuntu-desktop


Use xubuntu for a pentium (not celeron) and icewm for anything less (celeron, amd duron...)

---

### Post by jason.b.c on 2006-04-19
;) Thats the worst picture of *William Shatner* a.k.a "The shatman" that i've ever seen.;) 

:rolleyes:

---

