---
title: "moto4lin?"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by Niklas Schröder on 2007-08-07
i'm getting a Motorola Razr V3 soon (my first cell phone) and i want to be able to mod it with custom wallpapers, ringtones, and external picture.  my question is, is moto4lin reliable and safe?  what i REALLY don't want to do is screw up my phone as soon as i get it...

EDIT: i've done modding on an ipod nano before (successfully i might add), but it was a little less risky then because i could just re-install the firmware if i screwed up.  i'd be fine messing with my new gadget if i knew i wasn't gonna fry it permanently...  is it possible to just put the firmware back on there if it messes up and have it functional again?

---

### Post by FleetAdmiral74 on 2007-08-07
Well, first thing to check would be if it is listed as compatible or not with the program. If it is...your probably good to go. I would wait for others though, if possible someone who has used the same model phone.

---

### Post by Niklas Schröder on 2007-08-07
yeah.  good idea.  i don't think i'll be putting the phone into too much danger.  all i want is a custom mp3 as a ringtone and a background.

the only thing bugging me about the mp3 file transfer is that the guides i've read say to...

> 
delete the “MyToneDB.db” and “TempToneDB.db” files


to get it to work.  does anyone know what these do?  the file names imply that they're just temporary files...  but i'm not sure...

so the deletion of those files and the trustworthiness of the moto4lin program is what i need to know about at the moment.  thanks for any help.  ;)

p.s.  here's a link to a wiki for the program.  [http://moto4lin.sourceforge.net/wiki/Main_Page](http://moto4lin.sourceforge.net/wiki/Main_Page)

---

### Post by Niklas Schröder on 2007-08-07
ok.  i've learned alot since i first posted.  what i want to do (add wallpapers, change the image on the front of the phone, and add ringtones) is entirely safe.  all it is is data transfer and file replacement.  you just add the wallpaper in the image directory, stick the properly encoded mp3 file (see here, [http://veinhammer.wordpress.com/2006/05/18/motorola-razr-ubuntu-linux/](http://veinhammer.wordpress.com/2006/05/18/motorola-razr-ubuntu-linux/) , for encoding) and the replacement cl.gif in the proper places and you're ready to go.

the only way you can screw up your phone is by changing the firmware or other more high-end mods.  maybe i'll post a how-to later on (once i actually get the phone).

---

### Post by rexxxlo on 2007-11-18
i like this thread but i am to green to understand th lingo for the termnal

can someone explain what these commands mean on this page???

[http://veinhammer.wordpress.com/2006/05/18/motorola-razr-ubuntu-linux/](http://veinhammer.wordpress.com/2006/05/18/motorola-razr-ubuntu-linux/)

it says 

> Compile and install p2kmoto and moto4lin. I like to compile using my home directory as the prefix so when my OS goes haywire I can recover the files I've custom compiled.:



then it gives the command/s> $ cd p2kmoto-0.1
$ ./configure --prefix=$HOME/local && make && make install
$ cd moto4lin-0.3
$ ./configure --prefix=$HOME/local && make && make install

what does this do ?

if i copy and paste it in the the terminal it tells me command not found,im lost after this !

---

### Post by rexxxlo on 2007-11-18
i have read about the 64bit version but have no idea how to implement it (i have 64bit ubuntu)

---

### Post by Niklas Schröder on 2007-11-18
you actually don't need to use the terminal to install those programs (and i only ever installed moto4lin to my knowledge).  do you know how to use the synaptic package manager?

(and which razr do you have exactly?  we kinda need to know which model it is...)

---

