---
title: "PC hangs at end of installation"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by Oomska on 2006-05-03
Hi, I'm a total noob to linux so be gentle :D. I've just been trying to install Ubuntu on an old computer of mine. I sent away for the CDs so I'm using the official install from boot CD rather than an ISO downloaded from the web. 

Basically, everything appears to install fine up until a point. It gets past the stage where you take the disk out of the drive and Ubuntu starts to configure itself. Then it gets to the end of configuration, says something about starting Gnome, the screen goes black, and a small white cursor appears...then nothing! It just stays like that for hours. I've tried installing twice, only to get the same result.   

The computer is old, being a 700MHz Celeron with 384MB RAM and a 64MB NVidia GF2 card. It works fine with XP (I'm not attempting dual boot alongside XP though), so i'm not sure what I'm doing wrong here.

Any idea what's causing this? Is it a graphics card driver problem or something?

---

### Post by neouser99 on 2006-05-03
is it a small white cursor with a thatched background??

what happens if you press and hold <Ctrl> + <Alt> then press F1?

---

### Post by Oomska on 2006-05-03
No, it's just a flat white line - an underscore, in fact, in the top left hand corner of the screen. Will try pressing those buttons and get back to you.

---

### Post by Oomska on 2006-05-04
Anybody? Should I take out my NVidia Card and try reinstalling using the onboard graphics chip?

---

### Post by Sef on 2006-05-04
It's not going to hurt to take out the card.  Try it and see if it works.

---

### Post by Oomska on 2006-05-04
[QUOTE=Sef]It's not going to hurt to take out the card.  Try it and see if it works.[/QUOTE]

Thanks, will try it later. Here's where I get to according to the install guide.


> #

Go and get something to drink and something nice to eat while the packages install, until the progress bar gets to 100%.

This is the stage I get to 


 > When the packages finish installing, a graphical login screen will appear. 

This doesn't appear. Only a cursor appears and Ican't type anything with my keyboard

---

### Post by meat on 2006-05-04
At the Grub menu, try and run in recovery mode.  This uses a standard video driver.  If that works, you may need to change the driver in your xorg.conf file.  I am a newbie also, so I don't know what you change it to, but if X works in recovery mode, maybe others can help you.  I had the same problem you did

---

### Post by Oomska on 2006-05-04
[QUOTE=meat]At the Grub menu, try and run in recovery mode.  This uses a standard video driver.  If that works, you may need to change the driver in your xorg.conf file.  I am a newbie also, so I don't know what you change it to, but if X works in recovery mode, maybe others can help you.  I had the same problem you did[/QUOTE]

Okay, I ran in recovery mode at the Grub menu as you suggested. When I do this, it loads up stuff then gives me a command prompt:

root@ubuntu: #

I didn't know what to do at this stage so I tried 'login' and it let me enter my username and password. Then the command prompt changed to my username.
I don't know what to do next (is this supposed to bring up a gui?). You say that I should change video driver. Any suggestions on how to do that?

---

### Post by richbarna on 2006-05-04
root@ubuntu: # exit
now type your user name and password and you will get :-
you@ubuntu: # 
now type "startx" eg :-
you@ubuntu: # startx
this will start your gui : )

---

### Post by Chuck_W on 2006-05-04
I had a similar problem with a Dell Optiplex. The onboard video was flaky so I added a PCI card. The install seemed to go ok, just like it did for you, but it also would hang at the cursor. What seemed to be happening was that the installer was fine with the PCI card but the installed OS was trying to use the onboard circuit. When I removed the PCI card it would boot just fine. Try removing the card and see what happens. You may have to start up in GRUB (watch the screen for the prompt) and run :"dpkg-reconfigure -phigh xserver-xorg". Without the quotes :). Also there may be a way of disabling the onboard in BIOS. It was not an option for me.

---

### Post by Oomska on 2006-05-07
[QUOTE=Chuck_W]I had a similar problem with a Dell Optiplex. The onboard video was flaky so I added a PCI card. The install seemed to go ok, just like it did for you, but it also would hang at the cursor. What seemed to be happening was that the installer was fine with the PCI card but the installed OS was trying to use the onboard circuit. When I removed the PCI card it would boot just fine. Try removing the card and see what happens. You may have to start up in GRUB (watch the screen for the prompt) and run :"dpkg-reconfigure -phigh xserver-xorg". Without the quotes :). Also there may be a way of disabling the onboard in BIOS. It was not an option for me.[/QUOTE]

Okay, I've got the gui up and running through recover mode. I had to disable the add on nvidia card in the BIOS and switch to onboard VGA. Now what's my next step to try and ge the NVidia card working? 

OH, and my USB mouse won't work and I also got an error message 'failed to initialise HAL' when the gui started.

---

### Post by Oomska on 2006-05-07
Well it's working finally. Wow, what a great OS. The NVidia card seems to have been the problem when coupled with my onboard VGA. 

I've removed the PCI card for the time being and reverted to the onboard VGA. Will wait and get a feel for Linux/Ubuntu before I attempt to reinstall the card. In the meantime, I'm enjoying using Ubuntu. Thanks for all the help.

---

