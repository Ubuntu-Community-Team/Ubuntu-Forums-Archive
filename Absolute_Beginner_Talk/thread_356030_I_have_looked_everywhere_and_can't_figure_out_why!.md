---
title: "I have looked everywhere and can't figure out why!"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by ohmycar on 2007-02-07
hey everyone, i am super new to this scene and am excited. i recently installed ubuntu 6.06 on my dell inspiron e1405 laptop . everything seems to be runnning smoothly except that i can't seem to up my resolution to the wide-screen resolution it should be up. it doesnt go past 1024 x 768 and it is a little bothersome. i have looked through other posts and such but i havent really been able to understand was was going on. sorry if this is annoying or anything. i just need help with this one problem. i tried looking for the intel gma950 drivers for linux but i had no luck. i hope someone can help me, if not, then thats ok. thanks.


- Ash

---

### Post by john.nicholls on 2007-02-07
```
sudo dpkg-reconfigure xserver-xorg
```
Accept the defaults for any questions you're unsure about.

---

### Post by ohmycar on 2007-02-08
do i need to restart or anything afterwards? it still says i cant go past 1024x768 , im restarting it now, so hopefully it works now?

edit: k i restarted, and it still cant go past it. so i dont know

---

### Post by Loki57701 on 2007-02-08
Did u configure the drivers for your graphics card? You can goto the ubuntu wiki and theres instruction for just about every graphics card on how to setup your drives. After that you should have more option in screen resolution.

---

### Post by john.nicholls on 2007-02-08
You don't need to restart the computer, just the X server (Ctrl-Alt-Backspace).
When you were doing the reconfigure, did the resolution you want appear and did you select it? Perhaps it would help if you deselect all resolutions except the one you want (which should be the native resolution of your laptop.

If that doesn't work, I'm at a loss.
John

---

### Post by ohmycar on 2007-02-08
ah i see, not to sound like a mega noob, but what is ubuntu wiki? is it the wikipedia page for ubuntu?

and im going to try that config but only picking the resolution i want

---

### Post by Loki57701 on 2007-02-08
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)


If your not using 6.10 theres links to the other version on there too

---

### Post by ohmycar on 2007-02-08
well since i have a 945gm intel video adaptor
i followed these directions:

 How to Correct the Graphics Resolution (Intel)

    * Read #How to enable Large Widescreen Support if you have a larger (>20") monitor 

    * Intel 915g, 945g, etc. graphics chipsets only have a limited set of resolutions initially installed, despite the correct driver being detected.
    * Install the resolution altering tool: 

sudo apt-get install 915resolution



so i type in the above code and i got this:
Reading package lists... Done
building dependency tree...Done
E: Couldn't find package 915resolution

so now i am lost again, not quite sure what to do from here

---

### Post by bodhi.zazen on 2007-02-08
Enable your repositories:
915resolution
[http://ubuntuguide.org/wiki/Dapper#Repositories](http://ubuntuguide.org/wiki/Dapper#Repositories)

Then: ```
sudo aptitude update && aptitude install 915resolution
```

---

### Post by Loki57701 on 2007-02-08
I have an old desktop that has an onboard intel media accelerator or something and I also could never get the resolution to work right. But I had a spare ati 9200 sitting around and after alittle configuration got it working.

---

### Post by ohmycar on 2007-02-08
ok so i tired this

915resolution -1
915resolution 5c 1440x900

then i get this error
unable to obtain the proper IO permissions: operation not permitted

i was only follow the steps from that one wiki website which tells me this:
 How to Correct the Graphics Resolution (Intel)

    * Read #How to enable Large Widescreen Support if you have a larger (>20") monitor 

    * Intel 915g, 945g, etc. graphics chipsets only have a limited set of resolutions initially installed, despite the correct driver being detected.
    * Install the resolution altering tool: 

sudo apt-get install 915resolution

    * Run the following to see the availible modes: 

915resolution -l

    * Choose a resolution you don't need and replace, for example the following changes 1920x1440 to 1920x1200 

915resolution 5c 1920 1200

    * This should add the option for that resolution to the "System>Preferences>Screen Resolution" tool.

---

### Post by bodhi.zazen on 2007-02-08
First, I think that is a small "L" and not the number 1 ...

If that fails, run it with sudo ...

---

### Post by ohmycar on 2007-02-08
yeah the lowercase L didnt make a difference, but what do you mean by run it with sudo?

edit: ah nvm i got it :)

---

### Post by bodhi.zazen on 2007-02-08
And ... the suspense is killing me :p

---

### Post by ohmycar on 2007-02-08
haha allright so this is what happened

the resolution worked, i got it to run at 1440 x 900

and i followed the steps to make it stay permanent (gedit)

but it doesnt stay permanent.

so now i don't know how to keep it permanent.

---

### Post by bodhi.zazen on 2007-02-08
Should be ...

```
gksudo gedit /etc/rc.local
```

Add 

> 915resolution 5c 1280 800 24

above the "exit 0" line

Use the same command you used to set your resolution without sudo ...

---

### Post by ohmycar on 2007-02-08
yeah it still diodnt work, i restart and its still set at 1024 x 768 :(

---

### Post by ohmycar on 2007-02-08
ill just go back to windows

---

### Post by shareMenaPeace on 2007-02-08
Hi, 
just wondering did you check this GUIDE
#
The Painless Way to Set-Up Widescreen Laptops
that have the Intel® 845-945 Graphics Chipets,
Using 915resolution.
[http://ubuntuforums.org/showthread.php?t=351647&highlight=945gm+intel+resolution](http://ubuntuforums.org/showthread.php?t=351647&highlight=945gm+intel+resolution)

Cheers

---

### Post by ohmycar on 2007-02-08
still no luck with that, i am going to try and reinstall ubuntu and start it all over from scratch

---

