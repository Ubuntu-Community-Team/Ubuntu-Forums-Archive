---
title: "sound install help"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by slugworth1987 on 2008-03-31
hello all 

just installed my Ubuntu 7.10 to my Hard drive most works fine and dandy apart from sound card on my Acer Aspire 5720 i have found the driver and the how to page but i have an error on the code i have the CD in my drive as it promted me for it the code i am having issues with is this bit

sudo apt-get install linux-headers-\uname -r\

i dont understand the "uname -r" bit i have changed uname -r to my user name (sean) and still same error

E: Command line option ‘r’ [from -r] is not known.

any idea's/pointers?:guitar:

[https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5720](https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5720) this is the site for my sound card issue

full laptop spec

Acer Aspire 5720.093 model with following upgrades 4GB DDR2, Intel Turbo Memory and 32GB SSD Express 34mm card 

dual boot with vista is still used as gaming and windows config is required for college

cheers all

Slugworth1987

---

### Post by slugworth1987 on 2008-03-31
after more playing i have got another error after changing uname -r to sean:sean-seanlaptoplinux -r still no joy removed the -r and now i have another error

sean@sean-laptoplinux:~$ sudo apt-get install linux-headers- sean:sean-laptoplinux 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is not installed, so not removed
E: Couldn't find package sean:sean-laptoplinux

sean@sean-laptoplinux:~$ sudo apt-get install linux-headers- sean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is not installed, so not removed
E: Couldn't find package sean

so not getting very far :(
_________________________--*EDIT*--________________________________________
sean@sean-laptoplinux:~$ sudo apt-get install linux-headers-\uname tar xjf realtek-linux-audiopack-4.07a.tar.bz2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-uname

---

### Post by Witling on 2008-03-31
Please do not feel yourself alone. I'm new to Linux (and Ubuntu). Everything is honking along fine (if you're not a native English-speaking American, this means "everything is OK") except the sound card. I suspect I'll need a more detailed explanation later.

---

### Post by slugworth1987 on 2008-04-02
still no luck have the newist drivers 5.01 and with no joy.  i have follwed the read me and no changes seem to of happened i even used the script and manual im using 2.6.22-14-generic kernal and i have used the 2nd line of code but the tar file isnt helping im on the area where it is saved and i have run the files as sugested still not working i don't get the config bit but have copied the part and still no sound

anyone wanna help yet??

cheers

---

