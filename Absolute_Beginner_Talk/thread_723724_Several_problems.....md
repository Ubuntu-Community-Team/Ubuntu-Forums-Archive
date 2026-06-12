---
title: "Several problems...."
date: 2008-03-13
forum: Absolute Beginner Talk
---

### Post by kulotzy on 2008-03-13
Recently just installed Ubuntu however, there is still a lot of issues i have no clue about..... i've tried searching for similar topics but i cannot find the correct one, usually ending up making things worse..

1. First time i installed Ubuntu ALL SCREENSAVERS worked. Upon my second attempt, it wont work any longer. Everytime i select a 3D screensaver, Ubuntu RESTARTS. i Followed advise from another thread, but now i can only open the screensaver menu but it immediately restarts Ubuntu...
 
                    * 2. I installed WINE but everytime i run it, my PC just totally freezes. Even CTRL+ALT+Backspace doesnt work. This also happens with F-Spot..*

3. Im using a Vista-look theme i got from Eyecandy website but texts are in white and it doesnt allow me to change font colors: "Changing font color is disabled for this theme" or something like that.. i cant read anything.. ie. Firefox error (i see no text)

                     *4. Can i run Yahoo Messenger on Ubuntu with WINE because thats one of the main things why im trying to get WINE running.... GAIM doesnt cut it for me, but i may have to be forced to it....*

5. Is there a way to make folders show mini images of pictures inside ala-Windows XP

                    *6. Few questions... what is Gnome and Nautilus?? Are there any other Ubuntu essentials or applications i need or should install?*

Please help. Any assistance is appreciated. (Reminder for myself in case i forget: itilized problems are resolved or you found it out by yourself, good job mate)

 :confused::confused:

---

### Post by Nythain on 2008-03-13
well, the root of your problems sounds like a vid card driver issue, about the only thing that causes lockups/freezes/reboots i've found in linux land... particularly since you are attempting 3d screensavers...

so you can check into that to begin with

as for wine, gaim, and yahoo messenger... do you have other need for wine... because there are alternatives to gaim... personally i love Kopete and centericq/centerim

Kopete = kde messenger client (though now a days loading kde apps in gnome and vice versa isnt a bit deal) its very similar to trillian as far as looks and some what functionality goes

centericq = ncurses console app... tricky to configure since most of it involves those oldschool confs and rc's but it rocks my socks

others im sure know even more alternatives... there's no sense in messing with wine to so something you can already do in linux

---

### Post by kulotzy on 2008-03-13
> **Nythain said:**
> well, the root of your problems sounds like a vid card driver issue, about the only thing that causes lockups/freezes/reboots i've found in linux land... particularly since you are attempting 3d screensavers...

so you can check into that to begin with

as for wine, gaim, and yahoo messenger... do you have other need for wine... because there are alternatives to gaim... personally i love Kopete and centericq/centerim

Kopete = kde messenger client (though now a days loading kde apps in gnome and vice versa isnt a bit deal) its very similar to trillian as far as looks and some what functionality goes

centericq = ncurses console app... tricky to configure since most of it involves those oldschool confs and rc's but it rocks my socks

others im sure know even more alternatives... there's no sense in messing with wine to so something you can already do in linux

Thanks for replying.

well It seems i did something wrong... i used the terminal to download a driver that im not sure of except for that it helped someone else who had the same video card as mine which is "something"(VIA Technologies or something like that) Unichrome.... first time i installed Ubuntu it all worked fine, but now it doesnt... is there a way to fix the "driver"? Im no expert in any of these though i may have an idea of what im doing.

I actually installed Kopete, but i havent had time to try it out. Can i use webcam or use a mic to talk?? If so, then i might abandon WINE altogether though, i need it for iTunes

" there's no sense in messing with wine to so something you can already do in linux" -- im starting to embrace that idea of "finding alternatives"..

---

### Post by ruy_lopez on 2008-03-13
Doesn't pidgin support Yahoo?

---

### Post by kulotzy on 2008-03-13
I decided to just uninstall WINE.

---

### Post by kulotzy on 2008-03-13
> **ruy_lopez said:**
> Doesn't pidgin support Yahoo?

hey, sir, you're right... i just checked however, there doesnt seem to be webcam/mic function. i use the messenger solely to communicate with my family who are in a different country as i am.

---

### Post by kulotzy on 2008-03-14
Bump?

---

### Post by swudee on 2008-03-15
No Pidgin (formerly called Gaim) does not support webcams, at least in the foreseeable future, Try Kopete, although sound is still experimental at this stage, It didn't work for me with Gutsy, though I haven't got around to playing with it to try and make it work. (My wifes computer!!) AMSN does do webcams, but I think it only does MSN protcol, but I am not sure about that. It didn't like my webcam. Maybe in Hardy:)

---

### Post by kulotzy on 2008-03-15
> **swudee said:**
> No Pidgin (formerly called Gaim) does not support webcams, at least in the foreseeable future, Try Kopete, although sound is still experimental at this stage, It didn't work for me with Gutsy, though I haven't got around to playing with it to try and make it work. (My wifes computer!!) AMSN does do webcams, but I think it only does MSN protcol, but I am not sure about that. It didn't like my webcam. Maybe in Hardy:)

Thank you for the input. I think i might have to settle with Gaim or newly installed Kopete for now. Im still trying to grasp Ubuntu and such. Im still having problems with screensaver and graphics though...

---

### Post by mimada on 2008-03-15
Regarding your problem with the graphics. You might want to check the xorg.conf file against the graphics card you have installed. Be sure to back it up if you need to make changes.

To back up xorg.conf:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorgOLD.conf
```

To open xorg.conf in gedit:

```
gksudo gedit /etc/X11/xorg.conf
```

Look for the "Device" section and check to see if the driver is for your graphics card. Be careful about making changes to xorg.conf file.

Regarding the thumbnails of pictures, that's the default for Nautilus. Open up your Pictures folder and press CNTL+1.

---

### Post by forrestcupp on 2008-03-15
About your gaim problems.  The Linux version of Skype now supports webcams & sound.  It's cross platform.  Maybe that's an option for you.

About wine.  How did you install it?  Try going to [Wine's site](http://www.winehq.org/site/download-deb) that explains how to set up your repositories so you can get the latest version.

About your video card.  You don't know what kind of card you have?  in a terminal, type
```
lspci | grep VGA
```
to find out what kind of video chip you have.  Then we can go from there and figure out how to get it working right.

Gnome is your desktop environment (DE).  It is what makes Linux graphical with windows and everything.

Nautilus is your file browser, like Windows Explorer in Windows.

---

### Post by kulotzy on 2008-03-16
> **forrestcupp said:**
> About your gaim problems.  The Linux version of Skype now supports webcams & sound.  It's cross platform.  Maybe that's an option for you.

About wine.  How did you install it?  Try going to [Wine's site](http://www.winehq.org/site/download-deb) that explains how to set up your repositories so you can get the latest version.

About your video card.  You don't know what kind of card you have?  in a terminal, type
```
lspci | grep VGA
```
to find out what kind of video chip you have.  Then we can go from there and figure out how to get it working right.

Gnome is your desktop environment (DE).  It is what makes Linux graphical with windows and everything.

Nautilus is your file browser, like Windows Explorer in Windows.

I see now, thank you.

Im going to try to be accustomed to Gaim instead.

About WINE, i tried downloading from the internet and through the Terminal. Both times resulted in freezing the system when attempting to run it. I might have to live without that as well....

---

### Post by kulotzy on 2008-03-16
> **mimada said:**
> Regarding your problem with the graphics. You might want to check the xorg.conf file against the graphics card you have installed. Be sure to back it up if you need to make changes.

To back up xorg.conf:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorgOLD.conf
```

To open xorg.conf in gedit:

```
gksudo gedit /etc/X11/xorg.conf
```

Look for the "Device" section and check to see if the driver is for your graphics card. Be careful about making changes to xorg.conf file.

Regarding the thumbnails of pictures, that's the default for Nautilus. Open up your Pictures folder and press CNTL+1.

I did a fresh install of Ubuntu after trying several other distros. Fortunately, the process fixed the graphics problem. Bizarre eh, but it worked so im satisfied. Thanks for the reply.

---

