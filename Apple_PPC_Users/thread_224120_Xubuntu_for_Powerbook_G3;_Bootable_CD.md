---
title: "Xubuntu for Powerbook G3; Bootable CD?"
date: 2006-07-27
forum: Apple PPC Users
---

### Post by Youssef Alaoui on 2006-07-27
I would like to load xubuntu on my old '98 mac powerbook ppc g3  
233mhz w/ 128megs ram.

I downloaded the live cd from the web via my ibook g4 with os 10.4  
and burned it, following the directions written on the ubuntu site,  
using "disk utility."

but my powerbook isn't reading it.  I'm getting a floppy disk icon  
with a flashing question mark over it.

does this mean I burned it wrong?

or,

is it neccessary to "seed" my computer with a bit of linux so it can  
read the installer?

thanks!

---

### Post by avtolle on 2006-07-27
Sorry for the perhaps ignorant question: when you burned the CD, did you burn it as an image?

---

### Post by Youssef Alaoui on 2006-07-27
yes, as far as I know...  

the instructions said that, once the complete image downloads on to the desktop, to open up disk utility and simply drag the icon into the column at the left.  then put in a blank non-rw cd and press "burn."

I did not, however, select "create new image" from the top.

I think my powerbook falls right in the middle between new world and old world macs.

I don't think its a wallstreet or a pismo.  or a kanga.  it could be that infamous dog: "main street."  I am so not sure about this.

but I'm thinking I maybe have to use bootX in order to "seed"

---

### Post by avtolle on 2006-07-27
I am not familiar w/Disk Utility, but I believe you should have selected the create new image option. Hopefully, someone with more knowledge and experience can answer this for both of us with some certainty.

---

### Post by Youssef Alaoui on 2006-07-27
thanks, I hope so.

---

### Post by avtolle on 2006-07-27
OK, I think I was wrong. See: [http://psychocats.net/ubuntu/maciso.html](http://psychocats.net/ubuntu/maciso.html) 

One other thing, sometimes when the iso is burned, it becomes corrupted unless burned at a slow speed, e.g., 4x. Hope this is helpful to you.

---

### Post by Youssef Alaoui on 2006-07-27
indeed!

I have seen the psychocats instruction.  very good. that's part of what convinced me this would be easy.

perhaps if I re-burned the disk at a slower speed... if I have that option... I'll have to look.

also, I might try toast.  

but my question is, if I'm getting the floppy w/ "?" on it, does this mean that I've burned the CD wrong or that my computer needs to be seeded with bootX?

it could be both...
is there not an online guide to what these symbols mean?

my feeling is that the powerbook isn't reading the xubuntu cd because it needs to have a small amount of info in order to read all the new info.

  unless all that is supposed to already be on the disk...  is that what I'm not getting?

thanks for any and all input.

---

### Post by iamhugeinjapan on 2006-07-27
I installed Xubuntu on my G3 Powerbook (Lombard) with the Alternate iso flawlessly so don't give up hope. If you're sure you want to install it maybe that's the best one to use anyway since you have low RAM.

---

### Post by Youssef Alaoui on 2006-07-28
totally! that's exactly what I had planned.

so  you have a g3 233 pb also?  great.  I thought I'd need that alternate install.  that's what I'd read in the forums anyway...

so I downloaded that one too and tried to install it, but still that little icon with the question mark.

okay then, if you're saying that I won't need to use bootX, then I'm relieved.

I'll try to burn the disk again.

right?

thx

---

### Post by Youssef Alaoui on 2006-07-28
uh, wait.

you said "lombard"?

is that the one with usb and bronze keyboard?

my pb has adb and... nothing too interesting.  its black.  the first one they made after the kanga I think.  before the bronze keyboard.

is that it?

---

### Post by iamhugeinjapan on 2006-07-29
Yes I have the bronze keyboard model. I have never needed BootX with an Ubuntu distribution on here (Hoary to Dapper). Only time I've needed BootX is with Mandrake Linux 10.1 PPC...

My PB is a 400 MHz model though so yours might be just slightly too old to use the more modern stuff without BootX?

---

### Post by streetlightpoet on 2006-08-01
the question marks means it's not finding the proper file systems. Unfortunately that's what I get when I try to boot my powerbook g3 266 "wallstreet" since there is currently no OS installed on it. I just bought this machine yesterday thinking I could put Ubuntu on it and give it to the gf, however the PPC install disc has failed to boot, but I am downloading the alternate disc as I type this. To the OP: Did you ever get your install to work? Any tips?

---

### Post by avtolle on 2006-08-01
From [http://ubuntuforums.org/showthread.php?t=178823&highlight=Wallstreet](http://ubuntuforums.org/showthread.php?t=178823&highlight=Wallstreet), I hypothesize you will need to get some type of macos to install, and then use BootX. HTH.

---

