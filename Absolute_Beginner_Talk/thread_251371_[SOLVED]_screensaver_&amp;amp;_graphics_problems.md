---
title: "[SOLVED] screensaver &amp;amp; graphics problems"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by Alien260 on 2006-09-05
hello, 

i installed ubuntu form a few month everything is working fine the only problem i am getting and it is really annoying is that fact that when a screensaver or any app that uses graphical power (ie google earth) the computer freezes, the only thing i can so it reboot. 

Alien

---

### Post by tatimmer on 2006-09-05
My computer has on-board graphics, no seperate graphics card, it does not support opengl except thru software emulation, so any program such as a game etc which requires 3d graphics support will slow your system to a crawl.  Thats been my experience and I have a Pentium II 350 mhz with 256k ram. My solution has been to avoid running such programs until I get the necessary graphics hdwre.

---

### Post by davebgimp on 2006-09-05
Google Earth and several screensavers that come default with Ubuntu  use OpenGL and require a graphics card to run properly.

---

### Post by Alien260 on 2006-09-05
hello, 

yea i know that you need a graphics card and infact i have one its a Radeon R300 [Radeon 9700 Pro] from ATI Technologies.

so why do i still get these problems??

Alien

---

### Post by davebgimp on 2006-09-05
Did you install the proper drivers for the card?

---

### Post by stuoolong on 2006-09-05
> **Alien260 said:**
> hello, 

yea i know that you need a graphics card and infact i have one its a Radeon R300 [Radeon 9700 Pro] from ATI Technologies.

so why do i still get these problems??

Alien

I wanted Google Earth till I discovered it recommended a faster processor than I have and more RAM (512 MB I seem to remember). My graphics card is pretty poor so I use the same strategy as tatimmer, and many games I've randomly downloaded cause crashes because of graphics issues.

---

### Post by Alien260 on 2006-09-06
well when i go into the comp specs it tells me that i have that graphics card installed, buti didnt do anything special so maybe i didnt install it. 

How do i install my Radeon 9700 Pro card? :confused: 

and stuoolong

i have a good processor so i dont think that is the problem (32bit AMD) and 1GB Ram 

Thanks
Alien

---

### Post by davebgimp on 2006-09-06
You definitely need to install some drivers to get full use of your card. This wiki page should have all the information you need:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Hope that works for you.

---

### Post by Alien260 on 2006-09-07
hi, 

yes it worked fine everything is working perfectly now thanks, the only thing is that i still cant get the little game to work in wine. 

it launches it but then after 5 sec it just closes with no error message? 

any help there? ](*,) 
Alien

---

### Post by davebgimp on 2006-09-07
> **Alien260 said:**
> hi, 

yes it worked fine everything is working perfectly now thanks, the only thing is that i still cant get the little game to work in wine. 

it launches it but then after 5 sec it just closes with no error message? 

any help there? ](*,) 
Alien

Try opening a terminal and typing **winecfg**. Save and then launch the game from the terminal:
**wine .wine/path/to/programs/game.exe**

See if that fixes it and if it does not, look back at the terminal output and post the errors, if any.

---

### Post by Alien260 on 2006-09-07
this is what i get when i try to launch it from wine (i dont know if i m doing the correct thing thoug

alien@alien:~$ wine .wineC:\Programs Files\Team6 game studios\Scooter War3z Demo\Scooter.exe
wine: could not load L"c:\\windows\\system32\\.wineC:Programs": Module not found

thanks 
Alien

---

### Post by davebgimp on 2006-09-07
yeah, something's wrong with that command you entered.

Try from a terminal in your home folder (the folder with your user name):
**wine .wine/drive_c/Program\ Files/programname.exe**

---

