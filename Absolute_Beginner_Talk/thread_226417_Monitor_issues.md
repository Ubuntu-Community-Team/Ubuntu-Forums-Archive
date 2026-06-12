---
title: "Monitor issues?"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by buythe2ndglance on 2006-07-31
I am having trouble using my E551a Dell monitor.  The monitor works great in the start.  It makes it through bios and it even works when starting to load ubuntu in but when the computer trys to reboot the monitor just flashes all of Its LED's over and over again.  I was able to finish loading Ubuntu using a newer Dell monitor but even with this monitor about an inch was cut off from the left and right side of the screen.  Adjusting the monitor didn't work.  I am guessing it is thinking that I am using a widescreen monitor.  I would just like to get my old Dell monitor to work since it is my spare.  I am working with the relatively new CN10000 mini-itx mother board from VIA.  It has an on board video card.  To be specific it uses an Integrated VIA UniChrome™ Pro AGP graphics with MPEG-2 decoding acceleration.  I am very new to Linux I am still kinda lost.  Do I need some sort of driver or do I need to type something into the terminal window (This is what they are talking about when talking about command lines right?).  I don't consider my self completely a newbie when it comes to computers.  I own both Windows and Mac PC's and I am an electrical Technician by trade.  I just don't know how different Linux is yet.

Thanks for any help or information anyone can add.

---

### Post by zxee on 2006-07-31
Welcome to linux & ubuntu! Chances are you need to select the correct driver for your onboard video card. I'm pretty sure that that specific video you listed is supported. Make sure you have your system's hardware info and then from a shell (to open a shell do Alt+Ctrl+F1 or is you have a somewhat functioning desktop you can open it from Applications>Acessories>Terminal) in the shell type 
> dpkg-reconfigure xserver-xorg This will open up a interactive program (non-mouse driven) that will ask for your input and you'll get to select the video driver most applicable to your system.

---

### Post by Paerez on 2006-07-31
first off, you are correct when you say command line = terminal. A terminal is a command line interface. It is also called a shell, if you ever hear that.

The best way to set up your graphics is to run:
```
sudo dpkg-reconfigure xserver-xorg
```
Dont be scared! It will ask you some pretty confusing questions, but if you don't know what the answer is, just hit Enter and it will use the default.

When you get to the monitor part, near the end, it will ask you if you want "Beginner", "Medium", or "Advanced". Choose "Medium" and you can select your screen resolution. Then log out, and press CTRL+ALT+BACKSPACE to restart the screen and use the new configuration. Good luck!

---

### Post by buythe2ndglance on 2006-07-31
:( Okay so I tried that and it sent me into a different screen and now I am stuck in "username"@LINUX:~$ 

What should I have entered for the video card's bus identifier if the card is on the mother board itself?  

I even tried reinstalling ubuntu and doing it again.

Please help!!

---

### Post by Paerez on 2006-07-31
just keep hitting enter when you don't know the answer. If you leave it blank, ubuntu does it for you. The only thing you want to change from the defaults is the monitor settings.

---

### Post by buythe2ndglance on 2006-07-31
:p Part of my problem was actually in the Bios.  In the Advanced Chipset Features menu under Select Display Device I had to change it to CRT instead of CRT/TV in the Advanced Chipset Features menu.  This fixed the problem with the current CRT.

---

### Post by buythe2ndglance on 2006-07-31
That change also fixed my issue with my old E551 Dell monitor.

Thanks for everyones help  :lol:

---

