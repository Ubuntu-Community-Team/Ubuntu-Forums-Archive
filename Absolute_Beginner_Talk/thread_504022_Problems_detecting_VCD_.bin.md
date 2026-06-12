---
title: "Problems detecting VCD .bin"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by NeoEIRE on 2007-07-18
hi
i have a vcd that works in other pc's(nasty windows) and in my dvd player but when i put the cd in my PC(Ubuntu 7.04 feisty) nothing happens... usually with other cds and dvds it will appear on my desktop but nothing for VCDs.....? 

is there a way of extracting the info so i can convert it to avi at least or a way of getting to my DVD rom drive?

or can this bug be fixed?

tried using every program on the add/remove list..... just doesnt detect the disk?

thanks

---

### Post by sad_iq on 2007-07-18
Darn...had a page about VCD's ...but I lost the bookmark :(
 Anyway...install vlc...it will play the disk. Also try **sudo mount /cdrom ** (it used to work for me...haven't tried in a while though) I'll try to find an answer soon!!!!

---

### Post by NeoEIRE on 2007-07-18
have vcl....

finally got it to work by going to chapter 1 with vlc but the disk is still not visible for me to put it to my hard drive and convert it to avi. want to use video editin software to clean up and play with it...

---

### Post by sad_iq on 2007-07-18
Ok...found something...hope it helps(It worked for me): [http://ubuntuforums.org/showthread.php?t=165695&highlight=vcd+.dat](http://ubuntuforums.org/showthread.php?t=165695&highlight=vcd+.dat)

---

### Post by NeoEIRE on 2007-07-18
hi mate

i know this sounds stupid but....
i unzipped it and then?

(Next, I unzipped the folder, used "make" and "make install". I had to do an additional step: sudo insmod cdfs.ko This is to activate the filesystem. See the INSTALL file for more details.) **NOT A CLUE WAT THIS MEANS**

Now I mounted the VCD, not using iso9660, but cdfs, like this: sudo mount -t cdfs /dev/dvd /media/cdrom 
[B]OR THIS
[/B]

but i know where its talkin about with /dev/dvd /media/cdrom 

sorry still getting use to how this system work from windows rubbish

thanks for the help m8

---

### Post by sad_iq on 2007-07-18
Ok ...it's easy...download the file to the desktop,extract it then open a terminal and type:
 ```
cd ~/Desktop/cdfs-2.6.19
 make
 sudo make install
 sudo insmod cdfs.ko
```
 That should do it...insert your disk and type ```
sudo mount -t cdfs /cdrom
```
 Also watch for errors when typing make and sudo make install!!!

---

### Post by NeoEIRE on 2007-07-18
hi it installed ok and no errors but...

i cant find where i monted wat? looked in dev/all of them and nothing

and the cdrom file at the base level is emty to

feeling really stupid now....lol

---

### Post by sad_iq on 2007-07-18
Ok...this part can be tricky...my cdrom is /dev/ scd0 so to mount that vcd on my pc should be ```
sudo mount -t cdfs /dev/scd0 /media/cdrom
``` Try inserting a dvd , open vlc, press play, choose DISC and under Device Name you should have the name of your cd (/dev/ scd0 in my case). Once you mount it go to media and open cdrom!!!

---

### Post by NeoEIRE on 2007-07-18
think i get u.... in my case its dev/hdc

ill give it a try thanks a lot m8 but dont dissapear yet...:guitar:

---

### Post by NeoEIRE on 2007-07-18
:):guitar:YIPPIE FINALLY :guitar:

ur a Star mate thanks

1 step closer to understanding this system

thanks again

---

