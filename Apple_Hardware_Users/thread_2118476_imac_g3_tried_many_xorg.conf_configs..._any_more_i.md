---
title: "imac g3 tried many xorg.conf configs... any more ideas?"
date: 2013-02-21
forum: Apple Hardware Users
---

### Post by imacg3ppc on 2013-02-21
g3 slot loading imac flower power
600mhz
640mb ram
airport card

I'm able to boot to yaboot and to my command line... but i cannot get X to start up. Im checking lightdm it doesnt seem to have any errors in the log. My xorg.0.log file is throwing errors for Bus error at a certain locatation [x0xx000000] for example.
It then says aborting x server signal 7 bus error.
 
I have tried inputting the specs for the imac based on other imac examples. i was able to log in and ```
sudo nano /home/lubuntu/xorg.conf.new
```i edit my setting and hit ctrl+o to save file. I know its saving correctly. i checked the xorg.0.log to see what xorg.conf and it does use 'xorg.conf.new'

I even changed my yaboot parameters to add ```
radeon=modeset.0
``` and tried that... 

I even tried booting using yaboot parameter
```
video=offb:off
``` and all that did was freeze on my open firmware screen before yaboot comes up. 

Any ideas?? I reallly want to get lubuntu up and running.. my kids have projects to do for school coming up and i feel really bad that i cant get this thing runng... i dont want to try fedora..

---

### Post by rsavage on 2013-02-21
Pretty sure everything you need is in the FAQ and Known Issues (it's the very first thing listed under 12.04) pages.  So this is going to be brief.

Xorg that should work with the live CD (not saying it's the best setup and I've never used an iMac in my life):

```

Section "Device" 
     Identifier "Card0" 
     Driver "r128"       
     Option "UseFBDev" "False" 
     Option "NoInt10" "True"
     Option "ForcePCIMode" "True"        
EndSection

Section "Monitor"       
     Identifier "Monitor0"       
     HorizSync 58-62       
     VertRefresh 75-117 
EndSection 

```

You put it in /etc/X11/xorg.conf .  Not in your home directory.

---

### Post by imacg3ppc on 2013-02-21
/etc/X11/xorg.conf does not exist and i cant load /etc/X11/xorg.conf from that location... i'll have to try maybe i didnt capitalize the X? that would be sweet. 

but yea... for some reason when i ran the install (see thread [http://ubuntuforums.org/showthread.php?t=2117455](http://ubuntuforums.org/showthread.php?t=2117455)) i was forced to manually partition the hd to make a separate /home partition. Only way i could get thru the base system install. So i have 4 partitions instead in of three. 

apple/boot/swap/home

so i did notice that there may be a problem loading conf file from /home.

But what can i do about this? When i try the automatic partitioning, i get drive I/O errors and everything takes forever to boot up. I have never gotten into x on this machine.

I will try mixing and matching more options in the xorg.conf... but i'm tempted to try and get the live cd running to see if i can boot into X and get a graphical install going... i have spent hours on this issue.

---

### Post by imacg3ppc on 2013-02-21
back to the drawing boards.... going to try a fresh install and try to get a standard automatic partition table.. you guys/gals think that if i get rid of the /home mix up that i have a better chance of being able to boot into x?

---

### Post by abtabt on 2013-02-21
if you try this 

[http://ubuntuforums.org/showthread.php?t=2090462](http://ubuntuforums.org/showthread.php?t=2090462)

but use

live video=offb:off radeon.modeset=0 single 

and

modprobe aty128fb mode_option=1024x768-16 

can you get GUI then ?

---

### Post by imacg3ppc on 2013-02-21
i am going to try that tonight, first off the hd then on the live cd. Thanks so much for the tip great to have a helping hand(s) here in the forum and when i get up and running will reciprocate with any help i can provide.

Will update in the AM of 2/22.

Thanks again.

---

### Post by imacg3ppc on 2013-02-25
OK, so it's a no go. No matter what i cannot ```
startx
```
It does tell me no screen configured, but i have edited the xorg.conf many times over with various configurations. I'm going to try an install of straight up wheezy w/ lxde to see if it makes any difference... if anyone else has any ideas... let me know! and thanks for the help if i come up with a solution i will create a new thread with the details.

---

### Post by abtabt on 2013-02-25
> **imacg3ppc said:**
> OK, so it's a no go. No matter what i cannot ```
startx
```
It does tell me no screen configured, but i have edited the xorg.conf many times over with various configurations. I'm going to try an install of straight up wheezy w/ lxde to see if it makes any difference... if anyone else has any ideas... let me know! and thanks for the help if i come up with a solution i will create a new thread with the details.


you mean that livecd with 

this dont work ????

 

[http://ubuntuforums.org/showthread.php?t=2090462](http://ubuntuforums.org/showthread.php?t=2090462)

 but use

 live video=offb:off radeon.modeset=0 single 

 and

 modprobe aty128fb mode_option=1024x768-16

---

### Post by rsavage on 2013-02-25
If I was a betting man I'd say you are not typing things right.  Plus I suspect your frustration is stopping you reading the documentation properly and instead you are following the whacky advice on the internet.  
 
At the yaboot prompt:
 
live single
 
 
Wait for root prompt.
 
sudo nano /etc/X11/xorg.conf
 
Type in what I wrote.
 
Save it
 
Then run
 
sudo start lightdm
 
If it still doesn't work then tell us the errors in
 
nano /var/log/Xorg.0.log
 
The proper way to set up an xorg.conf is in the FAQ.

---

### Post by imacg3ppc on 2013-02-26
i'll have to try it again, i really appreciate you guys checking back and all. I Did try the live cd and had it printed from the links i was given in this thread. I think i may be just overlooking something but I do want to try again. 

I can't even put OS X back on this thing as i have no external hd and no install dvd lol so I'm determined to get this working. Thanks again and i'll let everyone know. Great community here. cheers.

---

### Post by rsavage on 2013-02-28
This [http://mac.linux.be/files/xorg/imac7.txt](http://mac.linux.be/files/xorg/imac7.txt) is the xorg.conf that mintppc9 users have with your machine.  It should be the same as what I've given you.  I've been assuming that those modelines that are listed shouldn't be used because they don't have the same name as those used in the screen section.  If you want to check then download the file to your imac G3 with the wget command.

---

### Post by str8bs on 2013-02-28
Same hardware except no WiFi on 12.04.
Been a while but based on my last here: [http://ubuntuforums.org/showthread.php?t=1952306&page=2&](http://ubuntuforums.org/showthread.php?t=1952306&page=2&) I believe "Option UseFBDev False" will cause a failure. I don't think the NoInt 10 is necessary either.

I would try exactly as rsavage noted xorg.conf without those two lines.

You can also try it with the _driver_ fbdev **This is not the same thing as the "Option UseFBDev."

---

### Post by imacg3ppc on 2013-03-01
so glad you are all still trying to help. Saturday is the day coming up and My goal is to get it x running. I will let you all know how it works out... i believe i tried to load the fbdev driver but maybe it was video=fbdev:only...

---

### Post by imacg3ppc on 2013-04-17
I'm Back! after a hiatus I was able to get x running! However... i only had the top 50% of the monitor operational. the lower half was black and the bottom of screen and task bar was half way. I have changed many settings in xorg.conf

i used ```
cvt 1024 768
``` and it gave me the modeline to use in my xorg.conf. so i put that mode line in and now all i see is the top 50% of screen works.

first of all:
I have to boot into lubuntu with the following yaboot parameters:
```
aty128fb.modeset=0 video=aty128fb:1024x768-16@60 single
```

Then i got root@lubuntu~$

start lightdm gives me black screen from which there is no return. so i skip that, i sudo nano my xorg.conf and edit stuff...
then when i started x with the corrected -hsync +vsync in the modeline... i logged out, restarted and got to lubuntu login, again on top 50% of the screen. Except now, i type my password, and click login... and nothing is happening.

I was able to use lubuntu with xfce and it was nice. color was ok. but only half the screen. I couldnt find a network signal so i couldnt send my log files to this forum. 

Any more ideas guys??? This is killing me, i dropped $85 on this cpu because i had this stupid idea that lubuntu would be a peice of cake, but i need to solve this graphics issue so i can continue to move on to printers, network, scanners, update to 12.10 after thats all said and done. or maybe not.

Thanks for all the help so far and any tips would be great! Any links to apple moitor specs would be nice, having trouble finding this stuff.

edit: also, i should probably ask if there is a way to permanently add boot parameters to yaboot so i can just start up the system and not have to jump at the keyboard the last second haha

---

