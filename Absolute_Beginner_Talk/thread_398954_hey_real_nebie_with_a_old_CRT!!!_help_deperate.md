---
title: "hey real nebie with a old CRT!!! help deperate"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by sorcerer11 on 2007-04-01
hi a few days ago i heard about ubuntu and linux, and how its free and its  like the natural and pure of coding in the OS world compared to monopolies like shitty windows. i just soo intrested init .. neways .. i got the live cd and while botting it up .. to the part where .. gnome loads up .. my old crt flickers! 
         i rebooted .. then at the menu applied different resoloutions .. by pressing the f4 key.. but had no luck, the flickering continues. i know in windows the monitor used to do it as well but when i changed the reoloution to 800 by 600 it works fine.
         please i would like yor feedback as i wanna give ubuntu a go and see what its all about before i try to install it on my machine . 

thanks in advance

---

### Post by Spr0k3t on 2007-04-01
What graphics card are you using.  From the sound of it, you need to increase your refresh rate.  Based on the graphics card you have, you can adjust the refresh rate in the board drivers.

---

### Post by sorcerer11 on 2007-04-01
i have a gforce 6800 nvidia card 1024 ram 80 gig hdd and a p4 3.2 

so how do i adjust my refresh rate using the live cd ?

thanks in advance

---

### Post by Spr0k3t on 2007-04-01
On the LiveCD I'm not sure.  I've not used the LiveCD with the exception to install and partition drives.  So, anyone want to chime in on this one?

---

### Post by Dual Cortex on 2007-04-01
I'll try to chime in (it's weird that the refresh rate is the problem since the default is always OK...probably just changing to the vesa driver will work until he installs the nvidia binary drivers):
When 'you're in gnome' press CTRL + ALT + F1 then just type 
sudo dpkg-reconfigure xserver-xorg
Go through all the steps selecting all the choices (not hard to follow), then at the end, after selecting the driver you want to use (I recommend you to simply select 'vesa') it will give you some options on configuring monitor settings select medium, (if you don't see the monitor refresh option, select advanced/hard) and finally make your selection. Then when it's done and you're allowed to enter commands in the console type:
startx
If it still flickers than ... post back.

---

### Post by sorcerer11 on 2007-04-01
hey.. 
well see the thing is when iam in  "gnome"  the screen is slickering and horizontal lines everywher and its hard to see the command line or anything for that mater of face should i just anway blidnly type it in lol .. 

please aiticipation your feed back 

thanks in advance

---

### Post by Dual Cortex on 2007-04-01
Ah, something similar happens to me and my 7300LE... just doesn't flicker but there is a buch of horizontal lines.
Give me a sec. and I'll give you some exact instructions on being able to clearly see the console.

---

### Post by sorcerer11 on 2007-04-01
thanks a heap man .. iam going to get some dinner will be back in half hour .. 

thanks again mate 
reallt appreciate it 

cheers

---

### Post by Dual Cortex on 2007-04-01
Well, I tried it out on my PC and remembered what my problem had been: setting anything other than VGA worked (by pressing F4), but I got those lines after having installed Ubuntu.
There I would boot in 'safe mode' or something similar using GRUB, which would not boot up X, and would manually edit the xorg.conf file to use the VESA driver.

See if this works:
At the menu with boot options in the liveCD select the 'Boot with safe graphics line' (but don't press Enter yet) then press F6. Find the part in the line that says > xforcevesa and replace it with> vga = 771

---

### Post by sorcerer11 on 2007-04-01
hey mate i did .. do what you directed me to do .. but iam still outta luck man .. it still flickers .. and nothing has changed please .. i would really like yourhelp ... iam jusyt done with work and still havent seen ubuntu how sad .. :(...


thanks in advance

---

### Post by Dual Cortex on 2007-04-01
Well... seems like your best bet is to use the alternate CD, then install ubuntu-destop from the complete CD, or from the repos.

---

### Post by sorcerer11 on 2007-04-01
alternate cd .. whats that iam pretty new to it .. what do i need to do .. i download .. and is it a must that i have to download it on my machine that already has windows running on it? do i have to dual boot? cant i run it from the live cd just to check it out? my windows machine has two partition both NTFS. i havent back up anything is that a problem 

looking forward for your reply 

cheers

---

### Post by sorcerer11 on 2007-04-02
hey .. well gues what after messing around googling and stuff i figured to go to comand by pressing ctrl+alt+f1 and .. i typed=  sudo dgkg-reconfigure xserver-xorg......

and i used the settings vesa .. and chose .advance ... and input 50 and 60 for my refresh rates .. and then when it was done; i typed in startx .. and it gave me an error saying there is a server already running .. 

well then i pressed ctrl+alt+f7 and then pressed .. ctrl+alt+bckspce and .. then types .. startx ... and it gave me wierd errors .. 


well as you cn see iam iam still trying to get this to work iam that desperate ... 

would like your openion on this 

cheers !

---

### Post by Dual Cortex on 2007-04-02
> **sorcerer11 said:**
> hey .. well gues what after messing around googling and stuff i figured to go to comand by pressing ctrl+alt+f1 and .. i typed=  sudo dgkg-reconfigure xserver-xorg......

and i used the settings vesa .. and chose .advance ... and input 50 and 60 for my refresh rates .. and then when it was done; i typed in startx .. and it gave me an error saying there is a server already running .. 

well then i pressed ctrl+alt+f7 and then pressed .. ctrl+alt+bckspce and .. then types .. startx ... and it gave me wierd errors .. 


well as you cn see iam iam still trying to get this to work iam that desperate ... 

would like your openion on this 

cheers !

:) I had told you to do that in post #5. Anyway, just turn off and back on your computer. Again, press CTRL+ALT+F1 and then type
sudo /etc/init,d/gdm stop
then issue
sudo dpgk-reconfigure xserver-xorg
Go through everything again, choose the vesa driver, a resolution that you know works in your monitor, refresh rates, etc. Then type startx. If X does not start, can you post the errors? More specifically, can you post the ouput after it shows the locations of the log.

---

### Post by sorcerer11 on 2007-04-02
well i did it and it gave me this error :

fatal error:
    server is already active for display 0
    if this server is no longer running remove /tmp/xo-lock
    and start again.



i got this error before as well ..

---

