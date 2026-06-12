---
title: "Deciding to give linux a try!"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by Malachi30040 on 2007-11-21
Hi, I've decided i want to give linux a try, so i downloaded Unubuntu, both the 64bit and 32 bit versions, burnt them to a cd and it reads the cd but then when i click install it just has the yellow bar moving back and forth then my computer freezes. I've also tried LinuxMInt and it did the exact same thing. Could it be a hardware problem? I did the md5sum and it matched. I also checked the CD's for anything wrong with them and they are all fine, I've even tried on all the different write speeds and still nothing.Only thing i can think of is the hardware, is any of this hardware not compatable with linux?:

ECS PT890T-A Socket 775 motherboard.
Intel Core 2 Duo E6600 2.4Ghz.
2GB's DDR2.
Nvidia GeForce 7600GT.
160GB Maxtor Internal HDD.. - This one has windows on it.
320GB WD External HDD .. - Was hoping to install linux on it, but couldnt even get to the screen to select it before crashing :(.

If it is because of the hardware is it just because of the distributions i was choosing or is it just that i cant put any linux on it? Thanks for any help! and sorry if this is not the right forum but im kinda lost.

---

### Post by jken146 on 2007-11-21
Welcome.  Sorry, I don't know what might be causing your problem but I would give the alternate installer CD a go.  Go to [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) and tick the box that says 'Check here if you need the alternate desktop CD.'

Hopefully you'll be ably to get Ubuntu to work, but if you really can't then by all means have a look at another distro.  Mint is a derviative of Ubuntu so I would suggest openSuse perhaps.

---

### Post by DutyDuty on 2007-11-21
You can also partition the inside hard drive. I think it would make you miserable to boot from an external hard drive.

---

### Post by Incense on 2007-11-21
Your system should run ubuntu just fine. I would also suggest the alt CD. It's really odd though that the disc would run fine until you ran the installer. Did the installer even start up? If so how far did you get?

---

### Post by Malachi30040 on 2007-11-21
Allright Thx for the help, ill try the alt installer. I didnt get very far, what happend was i clicked on the setup/install button (I cant remember exactly what it said) then it said "Ubuntu" and had a yellow bar going back and forth. I waited about 5 mins then suddenly the bar froze, my screen bugged out a little bit and i had to power down and re power on my pc. 

What i said above happend like 6 times, but one time it just went to a black screen completely covered in white text that kept flashing really quick but it was flashing too fast between 2 different error sentances so i could not make out what it was saying.

---

### Post by mike555 on 2007-11-21
it may not like your video card , you might try " safe graphics " mode ....  or you could try PCLinuxOS , it has graphic drivers ......... ( though I hate to steer anyone away from Ubuntu )

---

### Post by Incense on 2007-11-21
> **mike555 said:**
> it may not like your video card , you might try " safe graphics " mode ....  or you could try PCLinuxOS , it has graphic drivers ......... ( though I hate to steer anyone away from Ubuntu )

Yeah, I would also suggest another live disc (non Ubuntu based) to see if you have the same result. PCLinux OS, Fedora, and OpenSUSE all have live install discs. You could also try the alternate install CD from Ubuntu. It's text based but it should work.

---

### Post by Malachi30040 on 2007-11-22
Ok, so i gave fedora live CD a try and it booted up fine, i got to the desktop and everything worked perfect. So i decided to give the alt cd for unbuntu a try. I hit the install from text and it went to a black screen that just kept repeating this error message:

"buffer I/O error on device SDA, logical block 4"
"buffer I/O error on device SDA, logical block 5"
"buffer I/O error on device SDA, logical block 6"
"buffer I/O error on device SDA, logical block 7"
"buffer I/O error on device SDA, logical block 8"
"buffer I/O error on device SDA, logical block 9"

it did that all the way to logical block 14 then it restarted at logical block 4 and kept doing that in an endless circle. Anyone know why? If nobody knows a fix for this is there a big difference between Fedora and Ubuntu? I would like Ubuntu because ive been told its the best but i cannot seem to get it to work on either CD. Ive checked the cd for errors and it said there was no errors.


EDIT: NVM I just realized thats what i got when i was CD checking not when i was installing >_< Sorry about that.

---

### Post by Malachi30040 on 2007-11-22
Alright i think im just gonna have to give up on Ubuntu for now. I tried rewriting the cd at 16x speed and i still get the same error message both when checking the cd for errors and when trying to install from text. When i use the live cd I still get the same problem as before, it keeps just freezing in the same exact spot. If anyone has a solution that would be great, otherwise are there any major differences between Fedora and Ubuntu?

---

### Post by wolfen69 on 2007-11-22
why not resize your 160gb partition and dual boot?

---

### Post by philinux on 2007-11-22
Those errors dont sound good is it a new drive?

---

### Post by Malachi30040 on 2007-11-22
Sorry i couldnt get back to you earlier, but anyway... the 320 external drive is new, and the internal is about 6 months old. The internal drive runs windows fine, and the external seems to work fine also for storing videos ect on it. I thought about portioning the 160 gb, and im still not sure what i want to do. But i havent even been able to make it to that part. Those error msg's just start appearing right after i click the "Install by text" button. 

On the live CD i get to the splash screen that says "ubuntu" on it with the orange bar moving accross the screen, then it just crashes after about 5 mins of sitting on that screen. It looks like it was a graphics problem on the live cd just like the above posters said, but i have no idea what it could be on the alt cd that is causing it.

---

