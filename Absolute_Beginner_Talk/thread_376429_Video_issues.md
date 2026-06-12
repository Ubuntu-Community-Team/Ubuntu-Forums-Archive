---
title: "Video issues"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by SvenGB on 2007-03-04
i just saw a video for this version of linux and thought i would give it a try.  i am also realy new to useing any linux os.

specs:
Amd barton 2500+
1 gig ram
220 gig HD
dvd-ram drive
nvidia Geforce fx 5600 256mb

ok now the porblem...


i get the os intalled every thing looks good duel boot works great, but after i get past the Ubuntu splash screan i get nothing but a nice display of block colours. i am guessing it is a conflect with my video card, and was woundering if any one has an idea how to get rid of it so i can seethe gue?

---

### Post by j.miller565 on 2007-03-04
Does that happen on your other OS too (Windows I suspect)?

---

### Post by Jacobey000 on 2007-03-04
I'm having the similar problems with my 7600GT. My ubuntu wont even load. :(

---

### Post by SvenGB on 2007-03-05
no it does not happen in windows... sorry i missed some info... i am running windows xp pro as my other boot, and no problems just slow so looking for a less bloated os.

i am thinking it is drivers plus monitor support i tryed it on both my 17" lcd and my 40" lcd tv... on vga and both did the same thing so i am going to try a reinstall of it and dissable diffrent res. settings and give it a higher natur resolution and see what that does...

---

### Post by SvenGB on 2007-03-05
ok so i just did a fresh install and i am still haveing the same issues... is there a way to install the video card drivers out side of the system, or reconfigure it to a higher resolution befor you get into the system becaue i have the boot from cd on as well and i can get into it but the video settings are a littel bit messed up but i can still get into it.

---

### Post by aberry5555 on 2007-03-05
yes there is, alot of people seem to have problems like this on a fairly regular basis, I had to do the following to get mine working:

when you get to the block-colours screen press Ctrl+alt+F1, this will give you a command line. First of all it will ask you to log on, do this and then, when it gives you a command prompt, type in 

```
sudo nano /etc/X11/xorg.conf
```

this will bring up your graphics card settings file. Using the arrow keys scroll down until you find a heading named "Device" if you scroll down a bit more it should have a sub-heading under Device called "Driver", with the driver being used to the right of it. I'm guessing the drivers being used currently are "nv" which are the open source drivers for you graphics card. Change the driver from "nv" (or whatever it is) to "vesa". Now you've made this change press ctrl+O and ctrl+x to save and exit the file. This will bring you back to a command line, in here type in "reboot" and, hopefully, once it's restarted, you should have a gui. The gui WILL be slow and quite bad graphics but the "vesa" driver is the most basic driver available but it will still give you a gui. 

Post back and, if it works, I'll tell you have to get some proper drivers :)

---

### Post by SvenGB on 2007-03-05
i have tryed that meny diffrent ways and it doesnt bring up any file... i can get into the editor but if i try just giving it a file name it sez that paticuler one does not exist
><

nix above... i got into it change the device to vesa and rebooted... 

it gave me an error but most of the other stuffin the dos like promp was working better... go figure... 

so when i couldnt get a gue i changed it back to nv and got the same colour blocks...

---

### Post by aberry5555 on 2007-03-05
Sorry I don't think I understand you :S. Did you manage to edit the xorg.conf file? and, if you did, what error came up when the vesa drivers were used? 

If the vesa drivers don't work (make sure you check your use of capital letters, copy the stuff above exactly as it is written because Linux is completely case-sensitive, it might have been why you got an error) then you can do it another way, by downloading the proper nvidia drivers in the command prompt.

---

### Post by SvenGB on 2007-03-05
i found that out about the case sensative part after an hour of fighting with it saying bump- <comand name>

so i got into it and i did change it to vesa.

when i rebooted it gave me an error saying no such driver excisted... i am going to try it again once i get home for lunch. and see what happens. now that i know that linux is extreamly case sensative... 

but if you could explain or point out where to learn how to install drivers in the command promps that would be great... i havent had to learn this much since i started with dos... oh so meny years ago... lol

and thanks for the help :D

---

### Post by nudnik on 2007-03-05
I get this sort of thing frequently. On a modern machine (old integrated graphics system such as the Presario motherboards are nearly hopeless) boot to the command line by pressing Ctrl-Alt-F1 and type the following:

sudo -s
(password)
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure -phigh xserver-xorg
(choose your resolution) 

When back to the CL, type the following:

sudo /etc/init.d/gdm start

That might do the trick. We will sacrifice a goat on your behalf to the great god Torvald to ensure success.

---

### Post by SvenGB on 2007-03-05
ok i am going to try that when i get home from work... on my lunch brake i retryed it again and my screen just went blank and went into sleep mode on the nmonitor with is a resolution issue most of the time and that is what  co-worker said it also could be so i think this might help out as well...

i think we will get this figured out... last option is installing the newest linux drivers...

---

### Post by SvenGB on 2007-03-05
ok so i have done everything that has been suggested to me to do. no one problem with the last sugestion is that i have edited my xorg.conf file so it will not let me do what you are asking me to do when it comes to changing the resolustion.  i have also changed the "nv" to "vesa" but i get a blank screan, and i can only get it back by doing the alt+ctrl+f1.  so i am guessing my last option is to install the drivers from a cd into the kernal or what ever it is called for linux and see if that works. i am open to suggestions.

i am also guessing the easyest thing to do would to be install a new video card... but i am getting a new computer once i get this business up and running that i am starting.

so i want to try and get this going and learn it on this computer first... and man is it putting up a fight

thanks again for all the help

---

### Post by aberry5555 on 2007-03-07
if you want to install the nvidia drivers from your pc it's easier than running it from a CD. If you get a command prompt by pressing ctrl+alt+f1 and you have a dhcp internet connection you can type in 

```
sudo apt-get install nvidia-glx
```

this will download and install from the Ubuntu repositories.

---

### Post by SvenGB on 2007-03-08
hey thanks for all the help... but after meny and i do mean meny installs it just finaly started to wrok...


now for the fun part figuring out linux :D

---

### Post by SvenGB on 2007-03-09
ha ha i figured it out... my dvi port witch is hooked up to my 40"lcd tv was the cause of the issue...

---

