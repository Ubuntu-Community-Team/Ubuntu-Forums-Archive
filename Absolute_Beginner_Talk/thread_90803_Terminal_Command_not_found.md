---
title: "Terminal: Command not found"
date: 2005-11-15
forum: Absolute Beginner Talk
---

### Post by ajfgrogan on 2005-11-15
Hello Folks,

New recruit here! I am following the instructions from another web page to install a wireless driver.
And basically everything works fine until I am told to type "make" into the treminal. It then says make: command not found.
I am led to believe make is used all the time for installing programs etc.

Ta Aidan

---

### Post by kruz on 2005-11-15
sudo apt-get install make

even though i dont know why 
your would need make to get ur wireless up
i got my pci dlink g card up without any drivers

maybe we can try a different approach??

but ya try that command first, even though i thought ubuntu came make preinstalled maybe i just didnt check before i apt-get upgrade updated

---

### Post by ajfgrogan on 2005-11-15
Its a Netopia USB Wireless Lan Card that I am trying to install.

Your first idea worked but I am at a loss now!

The card is detected but Ubuntu has no idea what it is

---

### Post by kruz on 2005-11-15
okay try this
go to the top of ur screen where u have ur lil ubuntu toolbar
go to
system>Administration>networking
then itll prompt u for a password
enter ur normal username password

now look and see if its there, if it is
deactivate all other devices
and activate that one and then click 
properties
and set it up accordingly
also set default gateway to ur wlan adaptor
prolly ath0 in this case

tell me how that works
if it doesnt

go back into that terminal when u were using the command make
and try again, that apt-get install make worked, now u DO have the make command
see if htis works bro

---

### Post by ajfgrogan on 2005-11-15
The device was not there just the eternet card.

It tried the rest of the instrutions in order but no good.
I'll connect the PC via the ethernet cable tomorrow and at least get connected to the internet. I seem to be missing some files.

Thanks for help anyway. I might need you yet!

---

### Post by kruz on 2005-11-15
if make installed correctly you can go back to that first program yo uwere doing
and use the 

make command
./configure
then make
then make install

or try to find a modprobe for ur usb
im not sure what it is on the top of my head

---

