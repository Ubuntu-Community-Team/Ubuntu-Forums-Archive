---
title: "please help!! already bunch of problems"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by initialxy on 2006-05-22
i just installed ubuntu and i already have whole bunch of problems
i looked around on google and i did the best i could

first of all i didn't have much idea how to set up dialup internet connection
i used pppconfig and hopefully set the numbers, id and password up. i also went to network config and setup modem. but i have no idea how i was supposed to dial and connect. so every time i have problem, i have to switch to windows and go online.

then i tried change the permission of my partition using
sudo -su
sudo chmod a+w /media/hda7/
but that didn't work.

now i'm trying to install sheepshaver (mac emulator) thorugh rpm. so i install alien and used
sudo -su
alien -i media/hda7/sheepshaver.rpm
it looked fine, but when i try to run it, it says missing shared file!
then i try to use the source file to install. but it needs automake so i downloaded automake then it needs autoconf so i downloaded autoconf then it wants gnu m4!!

please help me!!
thank you!

---

### Post by mlind on 2006-05-22
don't change file permissions outside your home folder if you don't know what you're
doing, or you may render the whole system unusable!

why do you want to change permissions of certain partition?

Ubuntu has Mac emlator called basilisk2 already available from apt repositories,
but no sheepshaver. Could you post the output message, so it's more easy to
determine where the problem is.

To install basilisk2, you need to have **multiverse** repository enabled.
then type 

```

sudo apt-get update && sudo apt-get install basilisk2

```

---

### Post by initialxy on 2006-05-22
thanks for your reply!

sheepshaver supports up to mac os 9.04 and mine's mac os 9.0, therefore only sheepshaver can run my version of mac os. when i run sheepshaver the error message says:

/usr/bin/SheepShaver: error while loading shared libraries: libgtk -1.2.90.0: can not open shared object file: no such file or directory

i need the permission to my partition because i allocated 4 partitions in my hard drive:

C, hda1 (NTFS): windows xp, master boot
---------------------------
swap: swap drive
linux, file system (EXT3): ubuntu installation
D, hda7 (FAT32): personaly files

i wanted D: to hold my personal files and can be read and write from both linux and window. now both os can access it, but linux can not write data on it because of the permission problem.

---

### Post by phil66 on 2006-05-22
For the dial-up internet I use gnome ppp you can find it in the synpatic file manager 
After installing you can find it in menu>internet>gnome ppp
Open and configure if you have a compatible modem and not a winmodem it should start -up 
To place an icon in the panel right click on gnome ppp under internet and choose to add a launcher
Activate the log from the gnome ppp panel to have a recording of an errors incured

---

### Post by initialxy on 2006-05-22
i tried 
sudo apt-get install gnome-ppp
but it can't find that package!
then i tried to install through source but it says it's missing c compiler in PATH

please help

---

### Post by mlind on 2006-05-22
[QUOTE=initialxy]
sheepshaver supports up to mac os 9.04 and mine's mac os 9.0, therefore only sheepshaver can run my version of mac os. when i run sheepshaver the error message says:

/usr/bin/SheepShaver: error while loading shared libraries: libgtk -1.2.90.0: can not open shared object file: no such file or directory
[/QUOTE]

You're missing some required libraries, try installing libgtk-x11 or similar.
You can search libraries with similar name using **synaptic** for example

[QUOTE=initialxy]
i need the permission to my partition because i allocated 4 partitions in my hard drive:

C, hda1 (NTFS): windows xp, master boot
---------------------------
swap: swap drive
linux, file system (EXT3): ubuntu installation
D, hda7 (FAT32): personaly files

i wanted D: to hold my personal files and can be read and write from both linux and window. now both os can access it, but linux can not write data on it because of the permission problem.[/QUOTE]

You're supposed to define access rules when mounting a certain parition,
so you need to modify* /etc/fstab*

[https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)

---

### Post by Mustard on 2006-05-22
If you have set up dial up with pppconfig, you type 'pon' to connect and 'poff' to disconnect, btw.

---

### Post by s_h_a_d_o_w_s on 2006-05-22
I thought it was  sudo ppp**oe**co**nf** ! It works just fine, I recommend It.

---

### Post by phil66 on 2006-05-22
[QUOTE=initialxy]i tried 
sudo apt-get install gnome-ppp
but it can't find that package!
then i tried to install through source but it says it's missing c compiler in PATH

please help[/QUOTE]

Did you look in synaptic? If it is not there then you need to update your repositories.

---

### Post by Mustard on 2006-05-23
[QUOTE=s_h_a_d_o_w_s]I thought it was  sudo ppp**oe**co**nf** ! It works just fine, I recommend It.[/QUOTE]
Thats for an adsl connection I believe, not a dialup connection (56k modem).

---

### Post by Mustard on 2006-05-23
[QUOTE=phil66]Did you look in synaptic? If it is not there then you need to update your repositories.[/QUOTE]
You would need to be online and connected with the modem to do that.

---

### Post by phil66 on 2006-05-23
My mistake
pppconfig>pon then gnome ppp

I never could get full 56K by using pppconfig>pon
6K with pppconfig now with gnome ppp 44k

---

