---
title: "[SOLVED] Now that ive installed Ubuntu, how do i get compiz fusion up and running"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by AeThEr777 on 2008-04-15
Im writing this from my new Ubuntu OS YEAH!!!!! Finally Aneways its already so much better then windows and its just the regular version without any extras so now how do I get compiz up and running. Also how do i troubleshoot the system to see if everything is in working order? 

AeThEr777

---

### Post by waggingwabbit on 2008-04-15
i think you just go applications>add/remove and search for and downlaod advanced desktop effects settings. then you go to system>preference>advanced desktop effects settings and play around with that.

---

### Post by ethoxyethaan on 2008-04-15
system > adminitration > synaptic packet manager > make it look for "compiz-fusion",

install both plugins main and extra.

also this tutorial was usefull to me:

[http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-ati-mobility-radeon-9200](http://www.howtoforge.com/compiz-fusion-ubuntu-gutsy-gibbon-ati-mobility-radeon-9200)

---

### Post by mbadawi23 on 2008-04-15
Just keep in mind that your graphics driver may be disabled by default (as a restricted driver); so you need to enable that.

Also, you may want to verify that you have proper repositories enabled  so you can download dependencies.

have fun!

---

### Post by AeThEr777 on 2008-04-15
I just searched for them but when i right click on main and extra to install, the option for mark for install is greyed out. what do i do now?

---

### Post by tvtech on 2008-04-15
go to 

SYSTEMS>ADMINISTRATION>UBUNTU SOFTWARE
check the proprietary drivers for devices(restricted)  box.

---

### Post by AeThEr777 on 2008-04-15
ok i went to system administration but ubuntu software did not show up as a choice. any other way to enable my video card driver and check my reposiories thing. Sorry Im a complete newbie

---

### Post by AeThEr777 on 2008-04-15
Anyone?

---

### Post by mbadawi23 on 2008-04-15
I'm sorry but I'm still at work and not in front of my home pc.
but again from System->Admin->"Software Sources"
 you should be able to include repos.

But first you may want to view "System->Administeration->Hardware Drivers"
or
"System->Preferences->Hardware Drivers"

I don't remember which. But I think you need to install the proper graphics driver first.

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NVidia_Driver]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NVidia_Driver")

---

### Post by Inxsible on 2008-04-15
Three Steps:
1) System>>Administration>>Restricted Driver Manager

2) Enable the restricted drivers for your graphics card and then reboot

3) After reboot, go to System>>Preferences>>Appearances>>Visual Effecta tab. Select Extra or Custom to enable the effects.

---

### Post by AeThEr777 on 2008-04-15
Sry again, the lingo is throwing me off, Repos? Under software sources is there actually a check box for Repos or what am i looking for exactly? Also the previous link is that for all nvidia graphics chips or is it specific for a certain one? Thanks

AeThEr777

---

### Post by mbadawi23 on 2008-04-15
> **Inxsible said:**
> Three Steps:
1) System>>Administration>>Restricted Driver Manager

2) Enable the restricted drivers for your graphics card and then reboot

3) After reboot, go to System>>Preferences>>Appearances>>Visual Effecta tab. Select Extra or Custom to enable the effects.

Exactly!

---

### Post by AeThEr777 on 2008-04-15
Inxsible.....for the first step the only restricted driver that shows up is the "PRO/wireless 3945" Im assuming thats my wirelss card. There is nothing else shown on that screen. So i cant go further into your steps

AeThEr777

---

### Post by Inxsible on 2008-04-15
> **AeThEr777 said:**
> Inxsible.....for the first step the only restricted driver that shows up is the "PRO/wireless 3945" Im assuming thats my wirelss card. There is nothing else shown on that screen. So i cant go further into your steps

AeThEr777
Are you sure you have a NVidia card then, or maybe you don't need restricted drivers? post the output of the following command```
lspci | grep VGA
```

---

### Post by AeThEr777 on 2008-04-15
Lol dont laugh ummm how do i get the terminal up so that i can type that in! lol sry once again

AeThEr777

---

### Post by Tyke91 on 2008-04-15
easy :)

Applications>Accessories>Terminal

OR

alt+F2 and type in Terminal

---

### Post by AeThEr777 on 2008-04-15
THis is the output of that command

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

AeThEr777

---

### Post by AeThEr777 on 2008-04-15
So it looks like it is a Nvidia chipset

---

### Post by Inxsible on 2008-04-15
> **AeThEr777 said:**
> THis is the output of that command

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

AeThEr777

> **AeThEr777 said:**
> So it looks like it is a Nvidia chipsetUmmm No. It means that you have an integrated Intel graphics card.

---

### Post by AeThEr777 on 2008-04-15
You definetly know better then I lol. So what now? does this mean I cant have Compiz fusion :( or is there another way? Thanx

AeThEr777

---

### Post by Inxsible on 2008-04-15
> **AeThEr777 said:**
> You definetly know better then I lol. So what now? does this mean I cant have Compiz fusion :( or is there another way? Thanx

AeThEr777
You can have compiz. Did you try enabling them yet? System>>Preferences>>Appearances>>Visual Effects tab. Select Extra or Custom in there and the restart X by hitting Ctrl + Alt + Backspace.

---

### Post by AeThEr777 on 2008-04-15
Wow ive got wobbly windows!! Awesome thans so much Inxsible. So much work and thats all we had to do lol. Ummm last thing could you link me to the key commands to get some  of those effects to work or just an overal compiz how to lol thanks for all the help on this one. Your still helping on the other thread lol. 

AeThEr777

---

### Post by Inxsible on 2008-04-15
To change settings you will need ccsm (Compiz config settings manager). You can install it by```
sudo aptitude install compizconfig-settings-manager
```Once installed, you can find it under System>>Preferences>>Advanced Desktop Effects.

Play around in it with different plugins there :D

Enjoy !!!

---

### Post by AeThEr777 on 2008-04-15
How do i mark this as solved?

---

### Post by Inxsible on 2008-04-15
> **AeThEr777 said:**
> How do i mark this as solved? Top right of this page....Thread Tools>>Mark thread as solved

---

### Post by waggingwabbit on 2008-04-15
ok man...i got curious and tried that system>admin>restricted hardware drivers and enabled my graphics card "ATI accelerated graphics driver" my computers all jacked up now!! first my screen was all black, it said it cant read my grpahics card or show graphics or something so i restarted and now im stuck at 800x600 resolution (this is the highest it goes now) i cant enable the wobly windows or anything now also. even though it says it cant read my video card i can still see it at system>admin>screen and graphics....HELP!!!

---

### Post by ethoxyethaan on 2008-04-15
> **waggingwabbit said:**
> ok man...i got curious and tried that system>admin>restricted hardware drivers and enabled my graphics card "ATI accelerated graphics driver" my computers all jacked up now!! first my screen was all black, it said it cant read my grpahics card or show graphics or something so i restarted and now im stuck at 800x600 resolution (this is the highest it goes now) i cant enable the wobly windows or anything now also. even though it says it cant read my video card i can still see it at system>admin>screen and graphics....HELP!!!

i had this problem aswell, and i solved it the hard way, 

format everything and reinstall it correctly from the first time.

---

### Post by Inxsible on 2008-04-15
> **waggingwabbit said:**
> ok man...i got curious and tried that system>admin>restricted hardware drivers and enabled my graphics card "ATI accelerated graphics driver" my computers all jacked up now!! first my screen was all black, it said it cant read my grpahics card or show graphics or something so i restarted and now im stuck at 800x600 resolution (this is the highest it goes now) i cant enable the wobly windows or anything now also. even though it says it cant read my video card i can still see it at system>admin>screen and graphics....HELP!!!ATI cards have not been known to work well with Linux. There are a lot of threads that deal with low res. You could try and see if one of those work for you.

To get back to the original state you can reconfigure your xorg by```
**sudo dpkg-reconfigure -phigh xserver-xorg**           
```

---

### Post by Inxsible on 2008-04-15
> **ethoxyethaan said:**
> i had this problem aswell, and i solved it the hard way, 

format everything and reinstall it correctly from the first time.No you dont have to do anything that drastic !

---

### Post by waggingwabbit on 2008-04-15
maybe i should get my brothers nvidia card? will that require reformatting? he is parting his system.

i did what you said inxisble, but i dont think it brought it back to its original state. i have a wacom tablet and it used to work when ubuntu installed, but when i typed in that code my tablet wasn't working. graphic wise things seemed to have been back to normal, but i decided to edit xorg to fix my talbet, i only typed in tablet related stuff, but now im getting more graphics problems...like the "greeting" screen crashing. (maybe thats not graphic actually...i dunno) but i only did tablet stuff! =[ 

also, i was never able to get the rain effect for compiz working, and probably the reflection too... and the chess in 3D mode...are these ATI related too?

---

### Post by Inxsible on 2008-04-15
when you perform the dpkg-reconfigure command, it brings down your xorg.conf to the basic level so that you can atleast log in and work around. You will have to re-enable all the additional features like tablet and stylus in the xorg

---

