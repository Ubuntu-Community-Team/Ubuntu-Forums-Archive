---
title: "HP printer won't print"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by falconisthebest on 2007-01-17
Dear kind pros.

I recenty tried the much argued about OS , i was told to try this release as it was the most stable and user friendy. i do admit it is quite alright, and makes you realize how must of a windoholic i am, i always used windows, only used mac once and hated it, mainly cuz of thier crippled, one bottoned, small creature of a mouse. but anyways ...

my printer is a LaserJet HP 1020 , and when i tried to add it to the system,.  the CD that came with it didnt work of ocurse. and the OS seem to deal with it ok and said it was installed , but it wont print. no thing would come out, not even the test paper.  i dont know must about drivers, or linux , so please help... !

Thank you, 

Falcon

---

### Post by Shatrat on 2007-01-17
If you go into the System -> Administration -> Printing dialogue at the top of the screen is yoru HP 1020 there with a little check mark on it? (the check means its the default printer)

I have an HP 8250 myself, HP hardware is pretty good at working in linux in my experience.

---

### Post by healthpellets on 2007-01-17
you can check out which printers work well with *nix at [Openprinting.org]("http://http://openprinting.org/printer_list.cgi").

Sorry, that's all I can do for you.

---

### Post by Shatrat on 2007-01-17
Broken link in above post.  The entry for your printer is here:
[http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1020](http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_1020)


Looks like it uses a different driver than my photosmart does, foo2zjs, and needs a firmware upload like some wireless adapters do.  the foo2zjs website says that their current version of the foo2zjs driver is > than the one that ships with ubuntu so I guess you should install their version.

---

### Post by Amorphous_Snake on 2007-01-18
Hey Falcon, try this [http://ubuntuforums.org/showthread.php?t=220766&highlight=hp+laserjet+1020](http://ubuntuforums.org/showthread.php?t=220766&highlight=hp+laserjet+1020)

Just copy and paste the commands. I haven't tried it myself but it should work, give it a try!

---

### Post by deadgobby on 2007-01-18
Lets try the KISS method here. One to make sure that the printer port or USB is connected to your box to the printer. The other thing is to make sure the printer is on. The next thing to to go
Adminstration>Printing and see if Ubie see the printer.
Gobby

---

### Post by falconisthebest on 2007-01-20
thanks guys, 

thanks sanke. the link you gave me worked !

---

