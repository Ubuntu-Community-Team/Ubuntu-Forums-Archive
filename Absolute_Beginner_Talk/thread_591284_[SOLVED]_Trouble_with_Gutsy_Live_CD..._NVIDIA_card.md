---
title: "[SOLVED] Trouble with Gutsy Live CD... NVIDIA card &amp;amp;more"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Thiera on 2007-10-25
The Gutsy Live cd refuses to work on my PC. Have not been able to try and install it yet. Can't even get to a proper display.

 First I get "Sync out of range" floating all over my screen, and run 
> sudo dpkg-reconfigure xserver-xorg, 

then I select "Vesa" instaed of NV in the drivers, and then worked as instructed [here]("http://ubuntuforums.org/showthread.php?t=455504") - ([http://ubuntuforums.org/showthread.php?t=455504](http://ubuntuforums.org/showthread.php?t=455504) )

I end up at this on the console:

> xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xong.conf.20071025211636

And I have NO clue what to do after that. 
Using 
> 
sudo gedit "/etc/X11/xong.conf.20071025211636" doesn't work.Even without the sudo.  How to edit xorg.conf?

And WHAT do I have to do to even see what Gutsy looks like? 

Am complete, abjectly ignorant noob. :oops: ](*,)

---

### Post by RWC on 2007-10-25
I suggest using the alternate install cd - making sure the computer is connected to a wired network.  Once the install is complete and you're logged in - enable the Nvidia Driver in Restricted Drivers - this should download the most recent driver.  This worked for me.. ..

---

### Post by ed-koala on 2007-10-25
If you are copying and posting, I noticed that you spelled Xorg as Xong.  Also, I get into my Xorg.conf file by using sudo gedit /etc/X11/xorg.conf - without the numbers at the end.

Try that, and if necessary report what is in the file.

---

### Post by fmc6338 on 2007-10-25
> **Thiera said:**
> The Gutsy Live cd refuses to work on my PC. Have not been able to try and install it yet. Can't even get to a proper display.

 First I get "Sync out of range" floating all over my screen, and run 


then I select "Vesa" instaed of NV in the drivers, and then worked as instructed [here]("http://ubuntuforums.org/showthread.php?t=455504") - ([http://ubuntuforums.org/showthread.php?t=455504](http://ubuntuforums.org/showthread.php?t=455504) )

I end up at this on the console:



And I have NO clue what to do after that. 
Using 
 doesn't work.Even without the sudo.  How to edit xorg.conf?

And WHAT do I have to do to even see what Gutsy looks like? 

Am complete, abjectly ignorant noob. :oops: ](*,)

i had similar trouble with graphics.  Mine was stuck in low res.  I reinstalled live cd onto clean partition.  once installed I picked the nvidia driver and now things work fine.  just works dont really know why.  maybe that helps.

---

### Post by lost_poet on 2007-10-25
Theira's basic problem is that she cannot get a display. I guess everything else is working fine.

her integrated GPU has to be the problem. I am no expert, But I have been trying very hard to help her (she's a friend of mine and I egged her on into Ubuntu :P ). If she can get a working display a lot problems can be solved.

Does any one know how to get around this > Sync Out of Range Problem???:confused:

---

### Post by FuturePilot on 2007-10-25
I'm kind of guessing here, but I think the Sync out of range seems to be that Ubuntu isn't getting the refresh rate right or the horizontal or vertical sync rates correct and the monitor doesn't like that. Do you know the recommended refresh rate?

---

### Post by schneider707 on 2007-10-25
Post the model of the monitor and someone should be able to google some specs for ya to use and/or you can visit the manufacturer's website and a quick search for the specs will give you the numbers you are looking for.

---

### Post by Thiera on 2007-10-26
From what I garnered from this link - [http://www.samsung.com/in/products/pcmonitor/homeseries/56v.asp?page=Specifications](http://www.samsung.com/in/products/pcmonitor/homeseries/56v.asp?page=Specifications) , 

I think this is what I'm looking for:
> 
Scanning Frequency (Auto Scanning) 
Horizontal : 30-55 KHz
Vertical : 50-120 Hz

Resolution  	
Recommended Mode
-800 x 600 @ 85Hz
Supportable Refresh Rate
-Max 1024 x 768 @ 60Hz

Will try using those specs tomorrow or tonight(another 11 hours, give or take). Kinda caught up today.
I guess if everything is fine, I'll be able to navigate away from the console and into GUI?

Thank you, folks!

---

### Post by Thiera on 2007-10-26
I used the specs. Guess what? Now I get the postinst warning where you're supposed to enter the colour resolution(is that what it's called?) ... whether it's 16-bit or 24-bit. 

using > sudo gedit /etc/X11/xorg.conf gets me > "Cannot open display. Run gedit --help for..."

EDIT:
I connected to the Net, installed the nvidia driver using > sudo apt-get install nvidia-glx . Worked from there, selecting "nvidia" as a driver. And it STILL gives the postinst warning, although this is at the stage I got it formerly(will update on the exact stage).Even after I entered monitor specs manually in advanced mode.

---

### Post by Thiera on 2007-10-26
Ooohhh... I'm such a noob! 

Didn't know that "gedit" was a GUI, and that I'd have to use "nano" to edit xorg.conf. 

So what I did to get it working was

1. Configure and Connect to Net (sudo pppoeconf)
2. install the driver - > sudo apt-get install nvidia-glx
3. Edit xorg.conf manually - sudo nano /etc/X11/xorg.conf (Entered the horizontal sync and vertical refresh tolerances of my monitor directly)
4. ctrl+alt+F7(switch to GUI)
5. Ctrl+alt+bksp(reload)
Et voila!

Thank you so much, folks! :)

---

### Post by lost_poet on 2007-10-27
I shud've remembered that gedit was a GUI based editor. Anyways, good that it is solved. Bad that she has another problem. Her PPPoE Conenction keeps dropping. I wonder when she wud be able to make a thread on it at this rate or search for it.

---

