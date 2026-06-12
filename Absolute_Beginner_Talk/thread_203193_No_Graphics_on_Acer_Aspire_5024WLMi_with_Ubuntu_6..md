---
title: "No Graphics on Acer Aspire 5024WLMi with Ubuntu 6.06"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by ovimunt on 2006-06-24
Hi,

To start with, I'm a COMPLETE BEGINER with Linux. 

I've just installed Ubuntu 6.06 on my Acer Aspire 5024WLMi and I've got no graphics at all. :( 

I've downloaded the DVD version of Ubuntu and first tried it Live. It didn't seem to work or at least I got no graphics whatsoever. I then tried the 'safe graphics mode' and it worked just fine.

After this I decided to try and install Ubuntu on a separate partion. Installation went smoothly (except for the WiFi which I know will need some additional work according to all ste stuff I've read around here), Grub works fine so I can use my Win XP, but I got no graphics at all when trying to start Ubuntu. I did try to edit the boot lines in Grub and add 'xforcevesa' as it appears in the command line on the 'safe graphics mode' of the Live DVD but it still didn't work.

So I guess I'm stuck for now, good thing my Win XP starts just fine.

Anyway, if you've got an idea on how I can get graphics, please let me know.

Thanks

---

### Post by raptros-v76 on 2006-06-24
first. when ubuntu boots up, can you do Ctrl + Alt + F1, and see anything? if so, then you need to install the right graphic card drivers.

---

### Post by ovimunt on 2006-06-24
Thanks for the quick reply. 

Well, based on the stuff I know about computers with Windows, I'm sure it's a driver problem. I'm just hoping I can get it working just as it did in the 'safe graphics mode'.

Anyway, shorlty after the brown startup screen goes blank, I can hear the sound of a drum. I guess this means the system has started and the drum is just the sound of an error window?

I pressed Ctrl+Alt+F1 as sugested and nothing happened. However, as I said, the systems seemed to have actually started but it just won't share with me whatever it was trying to display. So I randomly pressed 'Enter' a couple of times which was acompanied by more drum sounds. Eventualy I did get a text screen asking me for the login. I entered the login and password and I got into the command line mode. 

So, I guess the next question is what drivers do I use and how do I install them.:confused:

---

### Post by raptros-v76 on 2006-06-24
what graphics card does the acer aspire use? nvidia right? a fairly new one? if so, then, 
sudo apt-get nvidia-glx
sudo nvidia-glx-config enable
reboot

---

### Post by ovimunt on 2006-06-24
It uses ATI Mobility Radeon X700. 

Yet, I've got no internet in Ubuntu... WiFi not working (common problem on this model) and this is the only way I can access the internet. Might sound dumb but I got no ethernet cable around so I can't connect my computer straight to the damn router.](*,)

---

### Post by macarrao37 on 2006-06-25
I have a x700 and the same problem.. apears to load the xserver but no image at all.. i can hear the drums sound...
I´ve allready tried to put vesa on the xorg configuration.. but the same problem..

---

### Post by ovimunt on 2006-06-25
Problem solved, d**n it!

I mean, c'mon, this bl***y Linux can't be smarter then I am, right? (or so i hope :D)

The problem is that Xserver tries to display the image on the wrong device! You might know that the Acer Aspire 5024WLMi with ATI Mobility Radeon X700 has also a Standard Monitor connector, TV-Out and dual display capability besides its own screen. What probably happens is that the Xservers is sending the signal to the Standard Monitor connector. To sort this out you just need to tell it to also look for other display devices.

SOLUTION: (NOTE - ALL COMMANDS ARE cAsE sEnSiTiVe!)

1. After the drum sound press Ctrl+Alt+F1 once or several times until you're in text mode. 

2. Now enter your login and password details.

3. You're now in command line mode. Type the following lines:

[I]cd /
cd /etc/X11
sudo nano xorg.conf[/I]

Some of these commands are redundant but they'll get the job done.

4. You've opened the *xorg.conf* file in the Nano text editor. Scroll almost all the way down until you find these lines:

[I]Section "Monitor"
	Identifier	"Generic Monitor"
	Option ...
EndSection[/I]

5. Replace the line

*Option ...*

with

*Option "Monitor Layout" "LVDS,AUTO"*

I'm not 100% sure what this does but someone around here was saying that it tells the Xserver to look for additional display devices.

6. Press Ctrl+X. This will exit the text editor but first you'll be asked if you want to save the changes. Type Y and press Enter until you're back to the command line.

7. Type 

*sudo reboot*

This will reboot the system

That's it, everything should be just fine now. Good luck! ;)

---

