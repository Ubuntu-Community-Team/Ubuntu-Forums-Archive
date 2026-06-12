---
title: "New to Linux, Got some questions: Dual Screens, Mouse Buttons, General Stuff"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by bemymonkey on 2007-05-12
Hi everyone! About 40 minutes ago, Vista started throwing me all sorts of error messages for no apparent reason (along with Cubase crashing every 5 minutes), so I killed it and downloaded a copy of the Ubuntu 7.04 ISO and burned it with my lappy... now after about 30 minutes of (awesomely simple) installation, I've got a simple Ubuntu desktop up and running... yay!

I've still got a TON of questions though... I'll put them in order from most to least important ;)...

Specs (in case they're needed):

A64 X2 3800+ (939)
MSI K8N Plat rev. 4
7800GTX
2x 80 gig IDE drives
a few DVD drives
Logitech Media Keyboard
Logitche MX510
Audigy2 ZS


1. Screen refresh rates - right now only the Sony is working, and it's showing a refresh of 51Hz (@ 1600x1200... actual max is 2048x1536 @ 85Hz)... This is hurting my eyes so... how do I get the refresh up? I'd like to get it up to 1600x1200 @ 100Hz, just liek I had on Windows...

2. I'd like to get my second monitor working... Searching the forums didn't really offer any usable results, because all of the suggestions require some understanding of how Ubuntu works - and being a complete n00b, I have no idea how to do any of the stuff required, heheh... Any suggestions?

3. MX510 - only the main buttons and scroll wheel are working - I'm still missing the quickscroll buttons and thumb buttons... where do I configure more advanced mouse options than in the "System" dialogue?

I tried downloading some drivers from the nVidia home page, but I can't really figure out what to do with 'em - they're in a .run file... no idea how to install it, lol.

Thanks in advance!

-edit- Another question - How do I get my Audigy2 running properly? Right now it's stereo and nothing coming out of the sub...

---

### Post by starcraft.man on 2007-05-12
1) Download and install the drivers for your card, nvidia it is. Go to envy, download the debian, double click on it and let it install. Then go to Applications > System Tools > Envy, click that and select "Automatically install nvidia drivers" Say Yes/y to any prompt for your input, then when you reboot you'll have drivers. 100 Hz is really high, geez, I dunno if it will detect that.

To get that high a rate, you can do this in terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

Follow the prompts and answer yes/ok/keep old if your in doubt, when you get to the refresh rates, enter your monitors numbers, that should do it.

2) Since your using Nvidia, you set up a dual screen a bit easier, using twinview. Its in the settings panel for nvidia, under system tools. The gui should let you configure it easy. Search forums for a bit more info on twinview.

3) I dunno, involves editting your Xorg manually I believe, you'll have to search for it  >.>.

Thats it, have fun.

---

### Post by bemymonkey on 2007-05-12
Hi SCMan... thanks for the reply.

I'm having a bit of a problem installing the nVidia driver - when I follow the instructions on the nVidia page (Type sh NVIDIA-Linux-x86_64-1.0-9755-pkg2.run in the console), it gives me an error message: sh: Can't open NVIDIA-Linux-x86_64-1.0-9755-pkg2.run

Now what? *scratches head*

and where is Envy? :P

---

### Post by starcraft.man on 2007-05-12
> **bemymonkey said:**
> Hi SCMan... thanks for the reply.

I'm having a bit of a problem installing the nVidia driver - when I follow the instructions on the nVidia page (Type sh NVIDIA-Linux-x86_64-1.0-9755-pkg2.run in the console), it gives me an error message: sh: Can't open NVIDIA-Linux-x86_64-1.0-9755-pkg2.run

Now what? *scratches head*

and where is Envy? :P

Forgot the [link.]("http://www.albertomilone.com/nvidia_scripts1.html") Don't bother with the run file, use envy and follow my instructions, your driver will be working in no time :)

---

### Post by bemymonkey on 2007-05-12
Awesome, thanks dude! Now I just need someone else to answer the other junk :D

---

### Post by starcraft.man on 2007-05-12
> **bemymonkey said:**
> Awesome, thanks dude! Now I just need someone else to answer the other junk :D

If you mean the mouse buttons, you might try searching forums I think i passed a how to the other day for em...

---

### Post by bemymonkey on 2007-05-12
Crap! Envy killed my system!

I installed just like you said, installed the nVidia driver using Envy and then rebooted... now it says "Failed to start X Server"... and I don't really get what the X Server output is trying to tell me, lol.

Failed to initialize the NVIDIA Kernel Module - Please ensure that there is a supported NVIDIA GPU in this system and that the NVIDIA Device files have been created properly.

Fatal server error:
no screens found...


Any bright ideas? ;)

---

### Post by st33med on 2007-05-12
Just to be sure, check your video card. I had a person that had his video card loose (and he didn't know it!) and he got so frustrated, he punched and it worked! I'm not saying to punch yours, though! :)

I doubt it is loose, so what is your Nvidia card?

---

### Post by adityakavoor on 2007-05-12
if u hav a backup of your xorg.conf file just restore it to this location 
```

/etc/X11

```
your  xserver will be fine

---

### Post by bemymonkey on 2007-05-12
LOL, I'm a complete n00b, why would I make a backup? :D

A buddy showed me how to get into the xserver config
but i can't figure out how to restart the xserver after reconfiguring... or rather trying to reconfigure it ;)...

---

### Post by bemymonkey on 2007-05-12
OK, typing in Sudo X gives me the same error message... :(

Is there a default Xorg file I could use?

---

### Post by Lucifiel on 2007-05-12
To restart X server, hit these keys:

Alt + Ctrl + Backspace. ;)

Also, a tip: whenever Ubuntu seems like it's "froze"(as in, pressing the keys + moving the mouse doesn't work and nothing is responding), try pressing these keys:

Hold down Print Screen key and press YUIB.

---

### Post by bemymonkey on 2007-05-12
OK, I just reinstalled... seemed to be easier, since I hadn't really done anything worth restoring yet. Now I'm back to my initial questions, and I'm a bit hesitant to try Envy again. Any safer way to get my second monitor working?

---

### Post by seshomaru samma on 2007-05-12
For Nvidia drivers try[ this ]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Graphics_Driver_.28NVIDIA.29")2. I'd like to get my > second monitor working... Searching the forums didn't really offer any usable results, because all of the suggestions require some understanding of how Ubuntu works - and being a complete n00b, I have no idea how to do any of the stuff required, heheh... Any suggestions?
my suggestion is that you follow one of the HOWTOs and if you get stuck or doen't know what to do - post here

---

