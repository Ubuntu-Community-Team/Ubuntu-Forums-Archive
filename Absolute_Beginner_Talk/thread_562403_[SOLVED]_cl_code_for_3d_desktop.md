---
title: "[SOLVED] cl code for 3d desktop"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by Wolfie Lee on 2007-09-28
:confused:WELL...have to give up on Beryl. Decided to install and try 3ddesktop from the synaptic repositories. Now, I can not find it anywhere...can't launch from APP menu, and can't find any folders in search of file system. I am running Feisty and a Dell Optiplex GX400 with 256MB ecc RAM, and an Nvidia Riva TNT2/TNT2 Pro (with automatix install of driver). Pentium IV 1.4 GHZ.  Should I just give up on even getting a cube desktop running? SHOULD Beryl work, and if so what am I missing? If Beryl won't, and the 3ddesktop SHOULD, what is the command line to find/launch it?](*,)

---

### Post by overdrank on 2007-09-28
> **Wolfie Lee said:**
> :confused:WELL...have to give up on Beryl. Decided to install and try 3ddesktop from the synaptic repositories. Now, I can not find it anywhere...can't launch from APP menu, and can't find any folders in search of file system. I am running Feisty and a Dell Optiplex GX400 with 256MB ecc RAM, and an Nvidia Riva TNT2/TNT2 Pro (with automatix install of driver). Pentium III 1.4 GHZ.  Should I just give up on even getting a cube desktop running? SHOULD Beryl work, and if so what am I missing? If Beryl won't, and the 3ddesktop SHOULD, what is the command line to find/launch it?](*,)

Hi I have heard of trying to run beryl on that video card but I can not confirm it. With that amount of memory and that card I would say it would be unlikely at best. :(

---

### Post by aktiwers on 2007-09-28
Isnt it in System > System Tools > Beryl ?

Else typing 
 ```
beryl-manager
``` 

in terminal should work.

---

### Post by jordanmthomas on 2007-09-28
3ddesktop is a commandline application:
[http://linuxreviews.org/features/3ddesktop/](http://linuxreviews.org/features/3ddesktop/) (ignore the emerge stuff and probably the stuff about fluxbox that's in the link)

You'd run it like so:
```
3ddeskd &
3ddesk --acquire
```

And then look at 
```
3ddesk --help
```
for more options.

```
   usage: 3ddesk [ OPTIONS ]
  
  Activates the 3d Desktop.  3ddeskd daemon must be running.
  Where OPTIONS are:
       --view=xxx        Uses the options from the view in 3ddesktop.conf
       --mode=xxx        Sets the arrangement mode 
                          (one of carousel, cylinder, linear, viewmaster,
                           priceisright, flip, or random)
       --acquire[=#]     Grab images for all the desktops by cycling thru
                          (sleep for x millisecs at each screen for refresh)
       --acquirecurrent  Grab image for current desktop
       --nozoom          Disable the zoom out
       --gotoright       Goto the desktop to the right
       --gotoleft        Goto the desktop to the left
       --gotoup          Goto the desktop to the up
       --gotodown        Goto the desktop to the down
       --goto=#          Goto specified column (deprecated)
       --gotocolumn=#    Goto specified column
       --gotorow=#       Goto specified row
       --dontexit        Don't exit after a goto
       --stop            Stop 3ddesktop (kill 3ddeskd daemon)
       --reload          Force a reload of 3ddesktop.conf
       --noautofun       Don't Automatically turn on Fun Mode
       --revmousewheel   Reverse the mousewheel
       --swapmousebuttons Swap the mousebuttons
       --altmousebuttons Use alternate mousebuttons scheme
```
You'll probably want to bind keys to run certain things like 3ddesk --gotoleft

---

### Post by Wolfie Lee on 2007-09-29
> **aktiwers said:**
> Isnt it in System > System Tools > Beryl ?

Else typing 
 ```
beryl-manager
``` 

in terminal should work.

...LOL, yeah, same thing happens when I do that as when I try to launch beryl from the app tab...FREEZE! That is why I pretty much gave up on Beryl. Thanx, anyway...will be trying Jordanthomas' CL posts for 3ddesktop, now, not really expecting too much out of this system, though. Thanx guys!!!

---

### Post by Wolfie Lee on 2007-09-29
O.K. I see...you can"t operate it from using mouse, or keystrokes, just IN TERMIAL? Not that kind of a user....installed this for it's functioality snd SPEED. I don't mind  doodling around in terminal (in fact it's kinda fun) but I don't want to have to USE an application soley by typing in lines of code (or copy-pasting, since that is what usually happens..LOL) I just wanted to find and LAUNCH the application from there, if that is what it took....LOL...again, Thanks a million for the help...

---

### Post by overdrank on 2007-09-29
> **Wolfie Lee said:**
> O.K. I see...you can"t operate it from using mouse, or keystrokes, just IN TERMIAL? Not that kind of a user....installed this for it's functioality snd SPEED. I don't mind  doodling around in terminal (in fact it's kinda fun) but I don't want to have to USE an application soley by typing in lines of code (or copy-pasting, since that is what usually happens..LOL) I just wanted to find and LAUNCH the application from there, if that is what it took....LOL...again, Thanks a million for the help...

Well good luck and maybe you can find a nvidia card cheap that will let you run beryl and CF good luck! :)

---

### Post by Wolfie Lee on 2007-09-29
> **overdrank said:**
> Well good luck and maybe you can find a nvidia card cheap that will let you run bery and CF good luck! :)

thanks, but Dell saw fit to go proprietary with the AGP slot....IT IS INSTALLED 180 DEGREES BASS-ACKWARDS!

---

### Post by Wolfie Lee on 2007-09-30
Another thought, Going  back to the memory thing...how much memory would someone reccomend with this card? And, since I can't find it in hardware manager, does anyone KNOW what size (MB) the Riva TNT2/TNT2 Pro is?

---

### Post by overdrank on 2007-10-01
> **Wolfie Lee said:**
> Another thought, Going  back to the memory thing...how much memory would someone reccomend with this card? And, since I can't find it in hardware manager, does anyone KNOW what size (MB) the Riva TNT2/TNT2 Pro is?


How much memory is totally up to you, and how feasible it is to add memory to the system. As vor the video memory it is 32mb according to this link
[http://en.wikipedia.org/wiki/RIVA_TNT2](http://en.wikipedia.org/wiki/RIVA_TNT2)

---

### Post by Wolfie Lee on 2007-10-01
Many thanks to all the help...this one is not solved, but closed...apparently have inadiquate Rig to go 3d, so far...

---

### Post by Wolfie Lee on 2007-10-01
ok

---

