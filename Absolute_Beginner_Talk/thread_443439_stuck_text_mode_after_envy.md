---
title: "stuck text mode after envy"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by merobertd on 2007-05-14
Hi
I have an old Dell 2350 desktop with pentium 4 2.5 Ghz 
528 mb ram 
built in graphic card ( gforce FX 5500 pci) 
60 Gig HDD
xp and ubuntu 6.10
32 inch samsung LCD screen 
maxtor external hard drive

i have tried to install the drive for the fx 5500 from the sea of posts on the web (envy don't what i think it should have) but when i reboot i get a error message about the x server fail and it lets me login in text mode, but when i login i don't know what to do to get the GUI back.

if i disable the fx 5500 in the bios i can run ubuntu on my LCD but the only resolution i can get is 640 x 480.

if i could get better resolution on the built in graphics card i would be happy not to use the fx 5500 (i would like to run beryl at some time in the future and it would be better to have the fx 5500)

any help would be great
Thanks

---

### Post by starcraft.man on 2007-05-14
Easy fix to get your gui back. Run this command after you log in to the text mode.

```
sudo dpkg-reconfigure xserver-xorg
```

Keep pushing ok and selecting default until you get to the drivers for graphics, make sure you select "nv" instead of "nvidia" then when its done it will save and you can log out and reboot :).

Easy fix, do make sure to re-enable your card.

---

### Post by kvonb on 2007-05-14
I've NEVER had envy fail on me yet, and I've used it several times on many machines!

Having said that, I would suggest that the problem is that your card is built onboard the mainboard.

To get the standard driver back, boot the computer, and quit from those error boxes.

Now type this:

```
 sudo dpkg-reconfigure -phigh xserver-xorg
```

That should get the "vesa" driver back for now.

Have a look at Alberto's web page, and ask him a question about your card and tell him the problem you had.  I'm sure you will get some help.

---

### Post by starcraft.man on 2007-05-14
> **kvonb said:**
> I've NEVER had envy fail on me yet, and I've used it several times on many machines!

Having said that, I would suggest that the problem is that your card is built onboard the mainboard.

To get the standard driver back, boot the computer, and quit from those error boxes.

Now type this:

sudo dpkg-reconfigure -phigh xserver-xorg

That should get the "vesa" driver back for now.

Have a look at Alberto's web page, and ask him a question about your card and tell him the problem you had.  I'm sure you will get some help.

I agree with ya, I've never had a problem with Envy, or anyone I've sent to it. And I even think another person I helped by sending em to envy had the fx 5500, and it worked. Weird, file a report with albert and do it manually with the guide from [Feisty.]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Graphics_Driver_.28NVIDIA.29") If you want beta drivers manually, scroll down one.

Pick whichever way you want to get your gui back, both commands work, mine just is the general way to reconfigure xorg :)

---

### Post by kvonb on 2007-05-14
> **starcraft.man said:**
> I agree with ya, I've never had a problem with Envy, or anyone I've sent to it. And I even think another person I helped by sending em to envy had the fx 5500, and it worked. Weird, file a report with albert and do it manually with the guide from Feisty.

Pick whichever way you want to get your gui back, both commands work, mine just is the general way to reconfigure xorg :)

Them's fightin' words! ;)

Actually I tell a lie, I tried to use the Edgy version of Envy on the beta release of Feisty, it wasn't a pretty sight :D.

But that was my stupidity, and inquisitive nature, "of course it will work on Feisty!"

Hahahah

---

### Post by merobertd on 2007-05-14
Hi
thanks for your help but it didnt work. i enabled the fx 5500 on the reboot and it froze on the splash screen then i tried it in safe mode and i got loads of code ending in 

Kernel panic not syncing: fatal excption

i disabled the fx 5500 and tried

sudo dpkg-reconfigure x server-xorg

emabled me to apply some settings like you said i sellected the nv. i went through all the options got to colour depth. default was 24 i hit enter and a few lines of text poped up like in the terminal and then it just sat there doing nothing. i rebooted and the setting are in the x server code that came out but no joy.

---

### Post by kvonb on 2007-05-14
I would enable your 5500 in BIOS, give it at least 64 megs of memory, boot into recovery mode, do the configure again and select "vesa" this time, reboot and see if that works.

---

### Post by merobertd on 2007-05-14
if i enable it and go to Saft mode i get

"Kernel panic not syncing: fatal excption" 

and it takes a hard boot to get out of it

and if i just go to standerd mode i get the ubuntu sign and a loading bar that gets stuck about 1/5 of the way full so i cant in put any thing.

---

### Post by merobertd on 2007-05-14
when i tried  

sudo dpkg-reconfigure -phigh xserver-xorg

it said i didnt have phigh installed

---

### Post by kvonb on 2007-05-15
> **merobertd said:**
> when i tried  

sudo dpkg-reconfigure -phigh xserver-xorg

it said i didnt have phigh installed

Hmm, very odd!  Oh well, just leave the -phigh out.

Your original post leads me to believe that you are using Ubuntu Edgy (6.10).  Have you been running it long or just recently installed it?

If it is a recent install, as it seems that you have not much to lose at this point, may I suggest that you download Ubuntu Feisty (7.04) the i386 version (NOT the 64 bit version!!!) and install that.  You might find that the problems vanish.

Make sure that your video card is enabled and working properly first though, boot inti Windows to make sure all is OK.

Oh, and DO NOT use Envy with Feisty!!!!

---

