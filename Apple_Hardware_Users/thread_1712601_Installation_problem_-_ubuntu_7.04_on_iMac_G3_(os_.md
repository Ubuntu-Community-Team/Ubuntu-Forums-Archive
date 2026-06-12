---
title: "Installation problem - ubuntu 7.04 on iMac G3 (os 9.2.2)"
date: 2011-03-22
forum: Apple Hardware Users
---

### Post by shiann82 on 2011-03-22
Basically, my partner and I have been trying to wipe the mac os 9.2.2 (UK version) and replace with ubuntu 7.04 (previous forums have mentioned this is the most stable version of ubuntu for the G3).

We bought this iMac G3 the other day, cheap, for our sons room... homework, research, music etc.  He's used to the windows system that the Mac os looks both boring and confusing to him. so we thought we'd go in between and use the ubuntu os.

Any who! downloaded the iso for ubuntu 7.04, burned the iso image, alternate cd install of course.  the only problem we are having is getting the disc to boot at start up on the iMac.  (cd rom doesn't have a tray, I've seen this question asked before).  the cd burned fine, the disc works on other systems. but when it comes to boot up on the iMac, nothing happens. press and hold down c, cd drive turns the discs a few times then carries on with the original mac os 9 start up.

any help would be greatly apreaciated! :) I personally haven't used Macs for about 11 yrs, so a little rusty with the content and different functions compared to windows.

---

### Post by snafu006 on 2011-03-23
start the computer hold option till a screen come's up stick in cd till it reads you may have to eject and place back in a few times

---

### Post by nevius on 2011-03-23
Ubuntu 7.04 stopped being supported almost 3 years ago. You should probably try installing 10.04 or 10.10. You may want to use a lightweight desktop manager rather than the standard gnome. You may also want to take a look at debian.

---

### Post by Bucky Ball on 2011-03-23
> **nevius said:**
> Ubuntu 7.04 stopped being supported almost 3 years ago. You should probably try installing 10.04 or 10.10. You may want to use a lightweight desktop manager rather than the standard gnome. You may also want to take a look at debian.

+1. 7.04 is long gone. I would try Xubuntu 10.04 LTS perhaps.

---

### Post by shiann82 on 2011-03-23
Other forums that I checked before making this post stated that the G3 wasn't stable enough for the 10.04 or 10.10... although the post was a couple of years old... is that not the case any more?

I was wondering if I should've gone with a newer version in the first place, but I was unsure if there would be an hardware incompatibility... anyone know for sure?

Also, there isn't a key labelled option on the keyboard that came with this G3, the related "alt" key has another symbol on it, would that still be the same? it looks like a mirror image of a "J" or a wonky T lol.  I'll try it any way.  Thanks for the help so far guys :) much appreciated!

---

### Post by shiann82 on 2011-03-23
I've uTubed for other iMac G3 users have put on their systems... Debian 5.04 looks like a favourite.  Which version would you recommend?

I also tried the option key and the disc wasn't in the options to boot from even though it was burner directly as an iso image. odd! As I said before, I'm more of a windows user so unsure of any command promt types I should be using to get this iMac formatted! Arrrgghh frustrating lol

---

### Post by snafu006 on 2011-03-23
I have a Imac G3 600mhz running 10.04 just fine.

---

### Post by shiann82 on 2011-03-23
just checked system specs on this model, it's only got 350mhz so that's going to be a challenge!

---

### Post by snafu006 on 2011-03-23
Go linux-mint PowerPc it going to run better because you have you slow prosser:popcorn:

---

### Post by shiann82 on 2011-03-23
which version would be compatible with my system? I've done some looking around but I've not found a definite answer.

I have been looking into **mac os x 10.3.9** as that is apparently the newest version that can be used with iMac G3 350mhz.

**Debian 5.04** has popped up a few times in forums but the iso images I've found so far has been for a DVD and this iMac only has a CD Rom drive... obviously I'd need a USB DVD drive to continue on this route and I don't have one.

**Ubuntu 7.04 & 10.04** discs wouldn't even load with the option key, only the HD was shown to choose from. tried rebooting with the disc still in then pressing option on boot up AND also starting up without the disc, pressing option key then putting the disc in and refreshing the list and neither worked so couldn't even start a format. (looked at the disc files on the iMac and none of the files had file type association?!)

I'm wondering if the **RW drive** I'm using to create these discs is the problem? I'm using **windows 7** on the other system.  I created an audio disc for my son to use on the iMac and it will only play the first track on the iMac system and then crash.  other audio discs created with old laptop (**windows xp home**) works fine on the iMac. wondering if the problems running the ubuntu disc is related to this fact?

sorry to be such a pain guys! it's probably something simple that needs to be done but as I said previously, I'm rusty with Macs :)

---

### Post by linuxopjemac on 2011-03-23
First Debian Squeeze and then MintPPC 9.
Follow Installation Instructions in [http://mintppc.org](http://mintppc.org). Success.

---

### Post by shiann82 on 2011-03-24
I've burned a number of different iso images of OS' compatible with my G3 model but it's still not booting up from the discs at start up.
  
This is getting a bit silly now! I've had people asking me to try C, Option and Alt buttons but it still won't boot from disc.

I only have 2 questions floating around ... 
1, are the iso images burned with windows 7 compatible with iMac? 
and 2, maybe the discs burned so far arent for the correct speed of the cd rom drive?

---

### Post by nevius on 2011-03-25
> **shiann82 said:**
> I've burned a number of different iso images of OS' compatible with my G3 model but it's still not booting up from the discs at start up.
  
This is getting a bit silly now! I've had people asking me to try C, Option and Alt buttons but it still won't boot from disc.

I only have 2 questions floating around ... 
1, are the iso images burned with windows 7 compatible with iMac? 
and 2, maybe the discs burned so far arent for the correct speed of the cd rom drive?

Boot into the Mac OS then stick the CD in the drive. Are you able to navigate the CD and see the folders on the CD?

---

### Post by snafu006 on 2011-03-25
> **shiann82 said:**
> I've burned a number of different iso images of OS' compatible with my G3 model but it's still not booting up from the discs at start up.
  
This is getting a bit silly now! I've had people asking me to try C, Option and Alt buttons but it still won't boot from disc.

I only have 2 questions floating around ... 
1, are the iso images burned with windows 7 compatible with iMac? 
and 2, maybe the discs burned so far arent for the correct speed of the cd rom drive?

You can burn a iso cd from windows to use on a imac the brun software i use is Infra from ubuntu.com.

and no thos Imac Cd-drivers where RW-drivers so they where good back in there hayday.

---

### Post by linuxopjemac on 2011-03-26
Reset your pram and then try to start from the CD. At boot hold down these keys:
option+command+p+r
wait until your hear the chime, then release the key combination and then you hear another chime. 
Then try booting from CD by holding down c during boot.

---

### Post by shiann82 on 2011-03-26
I have a question:
If I format another IDE HD with Ubuntu 10.04 and put it into the iMac G3, will it boot from it? Or does the iMac need other system files to boot from a different IDE in the first place?


Thanks again guys for your help.  Tried everything you have said so far. Yes, I can browse the disc from the desktop and it boots on my windows laptop fine.  I tried the resetting prams, that didn't seem to be useful. I think everything would be ok if I could get the darn discs to boot at start up! nothing seems to be working.  

I've decided to stick with trying Ubuntu 10.04 and if that doesn't work, I'm just going to have to buy the discs for Mac X Panther, as that's apparently the latest compatible Mac OS for my system.  Unless there's anything else I could try?

---

### Post by linuxopjemac on 2011-03-27
You might to want to start it from open firmware:
Boot with holding keys
option+command+o+f
held down. Then type the following:
```
boot cd:,\\:tbxi
```
enjoy.
[http://mac.linux.be/content/booting-open-firmware](http://mac.linux.be/content/booting-open-firmware)

---

### Post by shiann82 on 2011-03-27
I've just tried that boot cd code and each time I get:

"load size too small"

---

### Post by snafu006 on 2011-03-27
> **shiann82 said:**
> I can browse the disc from the desktop and it boots on my windows laptop fine.

Are you downloading ubuntu the one for windows?@ ubuntu.com thos do not work on apples computers you Need to down load the PowerPC ver. this link [http://cdimage.ubuntu.com/ports/releases/10.04/release/](http://cdimage.ubuntu.com/ports/releases/10.04/release/) If you are going to burn from windows use Infra Bruning software and burn the Cd @ 2x. The link is right here [http://infrarecorder.org/?page_id=5](http://infrarecorder.org/?page_id=5)

---

### Post by snafu006 on 2011-03-27
If you are download the ubuntu OS and are able to boot it on a windows computer you do not have the right software. Remember the apple computers that are PowerPc base cpu you need the right Version of linux os. 

Please Use the link the i posted redownload, reburn the Cd @ 2x or 4x 2x is better. Turn on the imac hold down option till you see a screen come's up place the cd in till you see a icon come up click it you will start to see a black screen on the first or second press Tab and type in the one that shows install-powerpc, or even better expert install-powerpc.

---

### Post by snafu006 on 2011-03-27
> cd rom doesn't have a tray, I've seen this question asked before

And from your first post does your imac have a Tray Loading cd-drive, or slot loading cd-drive. I need to know this please.

---

### Post by snafu006 on 2011-03-27
Ok yep you have the wrong Ubuntu vers. From the start so please use the two link i posted on the second page and down load one that says Mac (PowerPC) and IBM-PPC (POWER5) desktop CD and you can use Alternate, or Desktop I use desktop its up to you

---

