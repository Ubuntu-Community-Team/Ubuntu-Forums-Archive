---
title: "beginer 2 ubuntu in need of some serious technical help  i cant even get it 2 boot"
date: 2005-05-18
forum: Absolute Beginner Talk
---

### Post by doctor_chaotica on 2005-05-18
Hi

i have a copy of the 64bit ubuntu linux but here is the twist
everything seems to go fine untill the gui should load but it just comes up scrambled i can even hear the startup music but my screen is just one multi-colored line.

i have tried it on the Live cd and on the install

has it got somthing 2 do with it not being compatable with ATI cards?

any help in soughting this one out would be an absolute drean i am about ready 2 scream ](*,) and go back 2 windows full time which as everyone knows is a fate worse then death  

 my system is

AMD3000+ 64bit
Lemel 512mb 400mhz ram
80gb Pata HDD
120GB Sata drive
LG DVD burner 
Liteon cd/cdr/cdrw
ATI Radeon 9250 video  card
gigabyte GVA-X motherboard  
with a partridge in a pear tree following close behind 


thanx

---

### Post by kamstrup on 2005-05-18
Ok. There's prolly problems with the ati drivers... When the boot has completed, and you get the screen garbage, follow these steps:

Hit ctrl-alt-f1 to go to a virtual terminal. Log in as your normal user.

Type "sudo nano -w /etc/X11/xorg.conf" and hit enter.

Find the line in the "Device" section that says

Driver "something"

Then change "something" to "vesa", So it says Driver "vesa".

Hit ctrl-x, and hit 'y' to save the file (still as /etc/X11/xorg.conf).

Reboot your machine (type "sudo reboot" and hit enter).


By the way... What exactly did "something" say? If it did not say "ati", you might also want to try that...

Good luck!

---

### Post by doctor_chaotica on 2005-05-19
thanx dude will give that a try :)

---

### Post by poofyhairguy on 2005-05-19
[QUOTE=doctor_chaotica]Hi

i have a copy of the 64bit ubuntu linux [/QUOTE]


I do not recommend this. I pretty sure that ATI doesn't have 64bit drivers and unless you use programs that need more than 4 gigs of RAM (most people don't have that much RAM) then using the 64bit version offers no real speed increases. The 64bit version has more problems, such as not having window media codecs.

The 64 bit version should only be used by experianced users who have BIG 64 bit applications they need to run. Otherwise you are doing it for bragging right and pain....

---

