---
title: "New Video Card"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by Micro Rotors on 2006-02-28
Ok I have an ATI radeon X300SE Installed and working with the ATI driver and it works ok. I bought an ATI X800 GTO and I get a blank screen after I go through the login. The new ATI driver supports both cards so why is the screen blank?

If I decide to get rid of the card and just go with an Nvidia 6800  Will I be able to use the GUI to install drivers? Will it not work because of the ATI driver being installed?

Any tips here?

Thanks
Bill

---

### Post by Ramses de Norre on 2006-02-28
Maybe a dpkg-reconfigure xserver-xorg is necessary..
For the nvidia: X wont work with the ati drivers, so you'll need to go directly to a shell (ctrl+alt+F1) and change your xorg.conf there. (I don't know the name of the nvidia drivers, I think it's nv).

---

### Post by Micro Rotors on 2006-02-28
Ok well I need to be able to login and see whats going on, (still new) and use gedit. If I switch cards,, I get nothing I am blind then. Do I need to reinstall if I switch over to a Nvidia card after I installed an ati driver for my existing card I use now?

Bill

---

### Post by xmastree on 2006-02-28
No need to reinstall, but before you physically switch cards you should edit your xorg.conf file and change the entry for the ATI card to nv.

Even better, if you change it to vesa it will work with both cards, but won't look so nice. (think windows' safe mode)

---

### Post by poofyhairguy on 2006-02-28
[QUOTE=xmastree]No need to reinstall, but before you physically switch cards you should edit your xorg.conf file and change the entry for the ATI card to nv.
[/QUOTE]

This is good advice. First this command:

sudo gedit /etc/X11/xorg.conf

Then find the "Device" section. Change the driver to "nv." 

Now save and shut down. Add the Nvidia card. Boot up and use Automatix to install the official driver for the Nvidia card. Should work ok.

---

### Post by Micro Rotors on 2006-02-28
Ok guy's

Thanks, man this place is the best!!!!!!!!!!!!!!!!!!!:mrgreen: \\:D/

---

### Post by Micro Rotors on 2006-03-01
OH Man,,,, Ok I did what you told me,,, BTW I bought the 6800. > sudo gedit /etc/X11/xorg.conf I changed were it said ait under device in 2 different places also were it said driver to nv.  Now I have errors that in a blue screen that says > Screens found but have no usable configureation 

Fatal server error
No screans found

I also went to safe mode under root and did > dpkg-reconfigure xserver-xorg

Same thing. I did the etc/X11/xorg.conf on my Breezy but not in my Dapper, but I get the same messages in Dapper.

How do I correct this from command lines in safe mode if I can't get into the GUI. 

[SIZE="4"]**[COLOR="Red"]HELP![/COLOR]**[/SIZE]:confused: 

Thanks
Bill

---

### Post by Micro Rotors on 2006-03-01
Man,, I dont know what else to do but ,,, reinstall breezy and Dapper with the new card in, Hmmm will that work?

---

### Post by Ramses de Norre on 2006-03-01
Did you try sudo dpkg-reconfigure xserver-xorg?
What did you changed in your xorg.conf?
The driver is only mentioned at one place.
The identifiers of your videocard device section and your screen sections need to be the same, if you change just one of them it doesn't works. It doesn't matter if it says ati, it just needs to be the same.

---

### Post by Micro Rotors on 2006-03-01
Yes I did, I posted it above > dpkg-reconfigure xserver-xorg  


There were (2) device sections were it mentioned ATI that I changed to (nv) and the first section also listed driver ATI I also changed it to (nv) so a total (3) (nv)'s

Can I get into the file from the safe mode command line and fix it there? If so --- HOW?

---

### Post by xmastree on 2006-03-01
Take a look here:
[http://ubuntuforums.org/showthread.php?t=79827](http://ubuntuforums.org/showthread.php?t=79827)
in particular, post#23 which explains a little about xorg.conf and a 'no screens found' error.
since you have an nvidia card, you might try copying that file I posted there, which is my xorg.conf using my GeForce 4. That should work for yours too.

---

### Post by Ramses de Norre on 2006-03-01
Sorry, didn't read that post again.
What are those first two ati's you changed? On what line where they? You should only change the driver.
From recovery mode you can do vi /etc/X11/xorg.conf to change it. 
press i to go into insert mode, esc and shift+q to exit it, wq! to save and exit.
init 6 to reboot.

---

### Post by poofyhairguy on 2006-03-01
[QUOTE=Micro Rotors]Yes I did, I posted it above 

There were (2) device sections were it mentioned ATI that I changed to (nv) and the first section also listed driver ATI I also changed it to (nv) so a total (3) (nv)'s

Can I get into the file from the safe mode command line and fix it there? If so --- HOW?[/QUOTE]

Go into safe mode.

run this command:

```
sudo apt-get install nvidia-glx
```

Now run this command

```
sudo dpkg-reconfigure xserver-xorg
```

and pick the "Nvidia" driver. It all should work then.

---

### Post by Micro Rotors on 2006-03-01
Ok I will try ,, but here is an interesting thing. I decided since I just installed Dapper I would try to install it with the new card in and see what happens. Well I reformated the partitions / and /home and during the install guess were it froze up ,,, 

A) somewere in the begining
B) somewere in the middle
C) configureing xserver.org
D) at the end

Do I really need to say...........   

[SIZE="6"]**C**[/SIZE] Your right! :evil: 

You know,, I cant even install a new ubuntu.. Why is this?

---

### Post by Micro Rotors on 2006-03-02
Ok, here is the latest. 

poofyhairguy, I did exactly that.

1). I tried to install a fresh Dapper and it stalls on the "**configuring xserver.org**" every time.

2). I did install a fresh Breezy but I get vertical lines about 1/8" thick throughout the entire screen.

3). since I did do a complete backup (with the ATI Radeon X300se card) last week I just decided to wipe that entire drive and do a fresh install thinking that since they shared the same swap partition, maybe there was something funny going on there but I don’t think so. I did a fresh install of Breezy. Again vertical lines about 1/8" thick throughout the entire screen.

4).I tried a live Breezy CD and again vertical lines about 1/8" thick throughout the entire screen.

Each time I did something I tried to fire it up as is first then since it didn’t I did > dpkg-reconfigure xserver-xorg  


I am running Breezy i386 and for the dapper I am running the AMD-64 version.

My computer specs:

AMD Athol 3500+
2 gigs ram
PNY NVIDIA 6800 GS (factory over clocked version)

I am just scratching my head over this one. I guess this is the puzzle of the day. :confused: :confused: :confused:

---

### Post by Micro Rotors on 2006-03-02
Does anyone know if this card (PNY NVIDIA 6800 GS ... factory overclocked version)will work with Linux, I know it's not the card it is working fine with XP.

Any help would be great.

---

### Post by xmastree on 2006-03-02
As far as I know, pretty much all nvidia cards work well. You said you're using the AMD-64 version, but your spec doesn't say Athlon 64... :k

Out of interest, and to save time too, have you tried a live CD? If that works, copy the xorg.conf that it uses and try to use that. if it doesn't, have a look at that [thread I mentioned](http://ubuntuforums.org/showthread.php?t=79827) earlier for an idea.

---

### Post by Micro Rotors on 2006-03-02
[QUOTE=xmastree]As far as I know, pretty much all nvidia cards work well. You said you're using the AMD-64 version, but your spec doesn't say Athlon 64... :k [/QUOTE] I run i386 in Breezy and 64 in dapper as the i386 in Dapper was corrupt.

> Out of interest, and to save time too, have you tried a live CD? 
Yup, Bars of blue there also.

> If that works, copy the xorg.conf that it uses and try to use that. if it doesn't, have a look at that [thread I mentioned](http://ubuntuforums.org/showthread.php?t=79827) earlier for an idea.

I will look at the other thread again also.

Thanks a bunch.
Bill

---

### Post by Micro Rotors on 2006-03-06
Problem solved, Thanks

---

### Post by Darkarcher on 2006-03-22
i have also the bug of the veritcal bars and flashy strange colors
i tried these commande to get it work 
you can try to get the nvidia-glx package and install the package 
but i think someone sould really see deep in this bug because every distribution has the same bug except knoppix like i reported the bug in launchpad but it dissapeared

---

