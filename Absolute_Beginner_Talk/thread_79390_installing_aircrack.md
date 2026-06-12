---
title: "installing aircrack"
date: 2005-10-20
forum: Absolute Beginner Talk
---

### Post by TeleTommy on 2005-10-20
hi,

the aircrack package provided via apt-get is very old.
that's why i want to install the .tgz file manually. how do I do this?
I decompressed it via tar and installed
apt-get install make
apt-get install gcc

Typing make install results in hundreds of warnings like "incompatible implicit declaration of built-in function 'memcpy'" and many errors.

what can i do?

thank you!

---

### Post by BoyOfDestiny on 2005-10-20
[QUOTE=TeleTommy]hi,

the aircrack package provided via apt-get is very old.
that's why i want to install the .tgz file manually. how do I do this?
I decompressed it via tar and installed
apt-get install make
apt-get install gcc

Typing make install results in hundreds of warnings like "incompatible implicit declaration of built-in function 'memcpy'" and many errors.

what can i do?

thank you![/QUOTE]


sudo apt-get install build-essential

That will give you all the compiler stuff you need

I also recommend sudo apt-get install checkinstall

That program allows you to make a .deb so you can easily remove it with dpkg or synaptic...

Anyway uncompress your .tar (or whatever)
and in that directory type
./configure
make
If any errors occur at this step, usually it tells you what is missing, try and grab that from synaptic.

If all went well
do a sudo make install
or sudo checkinstall
(note the spacing)

Best of luck!

Also I'm not sure what aircrack is... Is it similar to airsnort?

---

### Post by TeleTommy on 2005-10-20
great! it worked!

aircrack is a wep/wpa capture, crack und decrypt tool.
 thank you very much!

---

### Post by spikes2020 on 2006-01-05
i could not   get "apt-get install checkinstall" to work, but everything else seems ok.. is there anyother basic programs that ill need to install other programs like apt-get install build-essential that you recommended ?


thanx 

spikes2020

---

