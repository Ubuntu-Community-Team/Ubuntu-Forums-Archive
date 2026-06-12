---
title: "Grub didn't recognize my Windows 2000 after reinstall"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by PoseidonOSU on 2008-03-27
I usually try to search and do my research before posting on forums but this morning I am running out of time! I have a Supra security Key that connects through a USB that I probably have to use windows for to update. 
I was using Ubuntu 7.10 successfully for several months. I had it on its own hard drive in my system. For some reason last night it decided to not work with my graphics card(Radeon 9600). 

Anyway I decided to simply remove and reinstall Ubuntu. I reinstalled Ubuntu 7.10 from the same disk I used before. After installation Grub does not have my windows 2000 as an option on the menu. 
I cant figure out how to get the win2k option back. I can use ubuntu and see that the windows drive is still there with all the files on it, i just can't boot from it. 

Unfortunately I need windows so I can update my security key. Any ideas?

thanks
E

---

### Post by paradoxni on 2008-03-27
You need to add the following to the bottom of /boot/grub/menu.lst

```
title Microsoft Windows 2000
root (hd0,1)
savedefault
makeactive
chainloader +1
```

where hd0,1 is the harddisk and partition number for the 2000 installation. e.g. drive 1 partition 2 in the example above. The correct numbering depends on the location of your windows installation.

hd0,0 - first drive first partition
hd0,1 - first drive second partition
hd1,0 - second drive first partition

---

### Post by PoseidonOSU on 2008-03-28
How do I know which hard drive it is on? I am going ot just try 0,0 and see if that works.

Also for beginers looking over my shoulder I used: 

sudo gedit /boot/grub/menu.lst

in the terminal window to bring it up in gedit and have root power to save changes.

E

---

### Post by Duck2006 on 2008-03-28
From the terminal type,

sudo fdisk -l

and post the output here.

---

### Post by bumanie on 2008-03-28
Provide output of sudo fdisk -lu (that's a small L), that will tell us what drive designation windows in on.

---

### Post by PoseidonOSU on 2008-03-29
Well as luck would have it 0,0 was just the ticket and my windows is up and running so I can update my Security Key. 

Thanks folks

E

---

