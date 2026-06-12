---
title: "Help with mounting macos9 disk from ubuntu and with yaboot to recognize it"
date: 2005-03-09
forum: Apple PPC Users
---

### Post by Misanthrope on 2005-03-09
hi, i got some serious problem
im noob dudes, please have mercy on my soul =; 
ok this is the problem
i have just installed ubuntu on my G4 400 mhz some days ago, i tried to switch from the macos9.2.2 disk (i have 2 disks, one with macos 9.2.2 and the other with ubuntu installed, no partitions)
but the yaboot menu only had the boot from cd option and the ubuntu's hard disk
seems ubuntu didnt recognized my hd (macos extended format)
well...i can switch from systems by pressind command+option+shift+delete while restarting so thats not the biggest problem

the problem is, from ubuntu i cant see the contents of the macos9 hard disk, i mean, i cant even mount it, the documentation hasnt been of too much help, seems it SHOULD be able to mount the drive by default, since in no faq i have seen this issue

maybe i need a driver?

---

### Post by Nekrataal on 2005-03-12
Come on, some one help this poor soul... :-({|=

---

### Post by Ptero-4 on 2005-03-12
[QUOTE=Nekrataal]Come on, some one help this poor soul... :-({|=[/QUOTE]
 Hi. IIRC you can't mount hfs+ drives under Linux. you can install hputils and use it to access your OS9 drive. And as of your yaboot, that's probably a known problem (older Mac's used to crap up when you had two HDs and one OS in each HD).

Hope it helps.

---

### Post by Misanthrope on 2005-03-13
[QUOTE=Ptero-4]Hi. IIRC you can't mount hfs+ drives under Linux. you can install hputils and use it to access your OS9 drive. And as of your yaboot, that's probably a known problem (older Mac's used to crap up when you had two HDs and one OS in each HD).

Hope it helps.[/QUOTE]

hputils? where i can get this?

---

### Post by val1984 on 2005-03-14
[QUOTE=Ptero-4]IIRC you can't mount hfs+ drives under Linux.[/QUOTE]
Wrong, you can typing for example
```
mount -t hfsplus /dev/hda3 /mnt/mac
```
where hda3 is the third partition of your first IDE disk.

Launch either pdisk and press P or mac-fdisk -L (not sure) to know your partition number.

PS : To launch mol, your Mac partition must not be mounted.

---

### Post by Digsa on 2005-03-22
Hi Misanthrope,

Actually you can get yaboot to recognise your OS 9 drive simply by adding a line to the    /etc/yaboot.conf      file. More info can be obtained here -

[http://penguinppc.org/bootloaders/yaboot/doc/yaboot-howto.shtml/ch6.en.shtml](http://penguinppc.org/bootloaders/yaboot/doc/yaboot-howto.shtml/ch6.en.shtml)

The line you need to add looks something like this -

macos=/dev/hdax 

where x  is your OS 9 partition number. When you reboot, you should see your OS 9 disk in the options.

Hope this helps,


Digsa

---

### Post by Misanthrope on 2005-04-05
dudes, i dont understand anything, im really new, i have never used linux before
whats mol? whats fdisk? how do i open it?

i think i should uninstall ubuntu since my fathers need the macos 9 to work and they are really pushing me off

today when they turned the g4 on, ubuntu loaded instead of macos9 (i didnt used ubuntu for weeks for that reason)

i know this HAS to be a basic question: how do i get yaboot to recognize the macos9 hard drive, its the first disk...wich command do i write? where? pleease, this is the only thing that has stopped me using ubuntu instead of macos9


the problem is....and thats why im here now..that command alt shift delete at restart doesnt work anymore!!!! i dont know why...so i got to use yaboot to get it to work or im dead

---

### Post by Misanthrope on 2005-04-05
where do i write those commands? in terminal i get the message: mount only root can do that
how do i get to root?



damn i cant even uninstall ubuntu !! im stuck!!! and i cant even see the files from the macos9 hard disk from here

---

