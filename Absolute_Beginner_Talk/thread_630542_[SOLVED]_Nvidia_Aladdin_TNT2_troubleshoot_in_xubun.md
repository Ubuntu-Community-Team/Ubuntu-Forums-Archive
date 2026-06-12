---
title: "[SOLVED] Nvidia Aladdin TNT2 troubleshoot in xubuntu"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by IsraeliHawk on 2007-12-03
hey all,

I  installed xubuntu two days ago hoping my old pc would recieve a good-'ol boost, but i can't enable the Nvidia 3d card. 
after the installion, the resolution sat on 1280*1024 (which was awesome, for a 7 year old pc..) and when i tick my card (Nvidia Aladdin TNT2 32MB) and restart - bam - 800*600.. lovely. and of course, 3d isn't there either, although compiz and emerald are installed..

and suggestions? i am lost already.. (and fed up with this.. really)

i know this can work - i saw it : [http://www.youtube.com/watch?v=_qddueXkD8E](http://www.youtube.com/watch?v=_qddueXkD8E)

thanks in adavnce :)

---

### Post by monktbd on 2007-12-04
i am not sure what driver got installed. but you need quite an old nvidia driver to make a tnt2 card work.

looking at [this](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=nvidia&searchon=names&subword=1&version=gutsy&release=all) and [this](http://www.nvidia.com/object/IO_32667.html) you need to install the nvidia-glx-legacy driver.

what is the output of
```
sudo dpkg -l "nvidia*"
```?

---

### Post by IsraeliHawk on 2007-12-04
i followed this guide.. and it just messed things even more.. 

[http://blog.shevin.info/2007/04/dont-panic-if-you-broke-graphic-in.html](http://blog.shevin.info/2007/04/dont-panic-if-you-broke-graphic-in.html)

and this is the output:

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ &#1513;&#1501;           &#1490;&#1512;&#1505;&#1492;       &#1514;&#1497;&#1488;&#1493;&#1512;
+++-==============-==============-============================================
rc  nvidia-glx     1:1.0.9639+2.6 NVIDIA binary XFree86 4.x/X.Org driver
un  nvidia-glx-dev <&#1500;&#1500;&#1488;>       (&#1488;&#1497;&#1503; &#1514;&#1497;&#1488;&#1493;&#1512; &#1494;&#1502;&#1497;&#1503;)
ii  nvidia-glx-leg 1.0.7185+2.6.2 NVIDIA binary XFree86 4.x/X.Org 'legacy' dri
pn  nvidia-glx-leg <&#1500;&#1500;&#1488;>       (no description available)
un  nvidia-glx-new <&#1500;&#1500;&#1488;>       (no description available)
un  nvidia-glx-src <&#1500;&#1500;&#1488;>       (no description available)
un  nvidia-kernel- <&#1500;&#1500;&#1488;>       (no description available)
un  nvidia-kernel- <&#1500;&#1500;&#1488;>       (no description available)
un  nvidia-kernel- <&#1500;&#1500;&#1488;>       (no description available)
pn  nvidia-kernel- <&#1500;&#1500;&#1488;>       (no description available)
un  nvidia-kernel- <&#1500;&#1500;&#1488;>       (no description available)
ii  nvidia-kernel- 20051028+1ubun NVIDIA binary kernel module common files
un  nvidia-kernel- <&#1500;&#1500;&#1488;>       (&#1488;&#1497;&#1503; &#1514;&#1497;&#1488;&#1493;&#1512; &#1494;&#1502;&#1497;&#1503;)
un  nvidia-kernel- <&#1500;&#1500;&#1488;>       (&#1488;&#1497;&#1503; &#1514;&#1497;&#1488;&#1493;&#1512; &#1494;&#1502;&#1497;&#1503;)
pn  nvidia-legacy- <&#1500;&#1500;&#1488;>       (&#1488;&#1497;&#1503; &#1514;&#1497;&#1488;&#1493;&#1512; &#1494;&#1502;&#1497;&#1503;)
un  nvidia-setting <&#1500;&#1500;&#1488;>       (&#1488;&#1497;&#1503; &#1514;&#1497;&#1488;&#1493;&#1512; &#1494;&#1502;&#1497;&#1503;)
pn  nvidia-xconfig <&#1500;&#1500;&#1488;>       (&#1488;&#1497;&#1503; &#1514;&#1497;&#1488;&#1493;&#1512; &#1494;&#1502;&#1497;&#1503;)

```
and all the hebrew crap means "no description available" and "no" or "without"

what do you think?

---

### Post by IsraeliHawk on 2007-12-04
BTW - i checked and legacy is installed in syneptic ..

---

### Post by monktbd on 2007-12-04
does not look too bad i think.
try to completly remove (not just uninstall) everything regarding the drivers. then reinstall again the legacy driver with synaptic.
you have the nvidia-glx-legacy installed but not the nvidia-settings and nvidia-xconfig, which should be installed as well.

if that all still does not work then you can always try to download the nvidia driver from nvidia directly and try that one (keep in mind to use th 71xx legacy driver).

---

### Post by IsraeliHawk on 2007-12-04
syneptic doesn't want legacy and nvidia settings together.. when i tick 'nvidia settings' it wants me to remove 'legacy'.. well, i'll reboot anyhow. fingers crossed :)

---

### Post by IsraeliHawk on 2007-12-04
didn't work.. any ideas? i looked at this thread 

[http://ubuntuforums.org/showthread.php?t=588735](http://ubuntuforums.org/showthread.php?t=588735)

and installed the "missing" parts (libgl1-mesa-dri..) but still - nada..

i'll try downloading the nvidia "original" drivers.. should i uninstall the legacy one before i install or overwrite?

---

### Post by tak1150 on 2007-12-04
> **IsraeliHawk said:**
> didn't work.. any ideas? i looked at this thread 

[http://ubuntuforums.org/showthread.php?t=588735](http://ubuntuforums.org/showthread.php?t=588735)

and installed the "missing" parts (libgl1-mesa-dri..) but still - nada..

i'll try downloading the nvidia "original" drivers.. should i uninstall the legacy one before i install or overwrite?

Assuming you've already restarted your machine after you installed those packages, can you post the result of "glxinfo"?

---

### Post by IsraeliHawk on 2007-12-05
you know what, i'll reinstall xubuntu today, because i believe i messed it up way to much .. and i'll try everything step by step again.. and then come back here and let you know.. 

wish me luck :)

---

### Post by IsraeliHawk on 2007-12-06
:) i was right..
installation was even smoother this time.. and the driver works fine.. 

now i'll try installing the compiz + your updated "extras" and we'll see how it goes..

---

### Post by tak1150 on 2007-12-06
> **IsraeliHawk said:**
> :) i was right..
installation was even smoother this time.. and the driver works fine.. 

now i'll try installing the compiz + your updated "extras" and we'll see how it goes..

Hi IsraeliHawk,

Before you start installing things, I'd make sure you have 3D acceleration turned on.
In your terminal, type:

```
glxinfo | grep direct
```

Tak

---

### Post by IsraeliHawk on 2007-12-06
everything looks good (i even managed to fix the 800*600 issue..) but i don't know how to enable the effects.. it may sound dumb , but i really don't (i mean, i did pick all the good stuff in the preferences of compiz .. but.. )

any ideas now?

---

### Post by tak1150 on 2007-12-06
> **IsraeliHawk said:**
> everything looks good (i even managed to fix the 800*600 issue..) but i don't know how to enable the effects.. it may sound dumb , but i really don't (i mean, i did pick all the good stuff in the preferences of compiz .. but.. )

any ideas now?

So you have direct rendering?
And you have installed compiz and compiz manager?

---

### Post by IsraeliHawk on 2007-12-06
yes.. according to this thread :

[http://ubuntuforums.org/showthread.php?t=623752&page=2](http://ubuntuforums.org/showthread.php?t=623752&page=2)

oh, and what you asked.. glxinfo | grep direct:
```
israelihawk@israelihawk-desktop:~$ glxinfo | grep direct
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
israelihawk@israelihawk-desktop:~$ 

```

btw, this thread: [http://blog.shevin.info/2007/04/dont-panic-if-you-broke-graphic-in.html](http://blog.shevin.info/2007/04/dont-panic-if-you-broke-graphic-in.html) (which saved me from the 800*600 situation..) says that adding /Option "AllowGLXWithComposite" "1"/ into the xorg.conf file improves the performence for TNT2 cards.. only i don't know if i could use it since there's a difference between my card (aladdin tnt2) and riva tnt2 for instence.. or am i wrong?

---

### Post by tak1150 on 2007-12-06
The command I asked you to issue should give:
```
tak@tak1150:~$ glxinfo | grep direct
direct rendering: Yes
```

I'm pretty sure that your 3D acceleration is not working.
What have you done on your machine since the installation?

I just realized that you were talking about turning on Compiz Fusion.
To do so, press Alt + F2, then type in
```
compiz --replace --disable-gtk
```

If nothing happens, please post the output from the terminal when you issue the command from the terminal rather than "Alt+F2"

Tak

---

### Post by IsraeliHawk on 2007-12-07
ok, this is weird.. i rebooted again and i'm back to square one.. 800*600.. now here what i've done post the installation:

- restricted driver (nvidia-glx-legacy)
*reboot (800*600..)
- 
- step by step - [http://blog.shevin.info/2007/04/dont-panic-if-you-broke-graphic-in.html](http://blog.shevin.info/2007/04/dont-panic-if-you-broke-graphic-in.html) backed up my xorg.conf file and edited the 'monitor' section (i installed gedit since it's not installed by default..)
*reboot - everything works ok (the resolution was up to 1280*1024..) the driver is recognized as nvidia
- amarok, open office, gmail notifier
*reboot - when i pressed the "stand by" mode in the shut down menu my pc went to bed.. so i rebooted
- 800*600 again - the driver is now "vesa" and no matter what i do, i can't change it.. and weirdly, the xorg.conf file changed..

plus: ```
israelihawk@israelihawk-desktop:~$ compiz --replace --disable-gtk
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
no /usr/bin/metacity found, exiting
israelihawk@israelihawk-desktop:~$ 

```

just to let you know, when i had ubuntu 7.10 i remember the i did have the "direct rendering: yes" answer..

:confused:

and now, for some reason, i can't write in hebrew.. i went to the keyboard options, and il-he is gone.. (!) so i added it up, closed, and it didn't save it ..! it's exactly the same story with the graphics card (it shows "vesa" and when i change it, nothing happens and it goes back to vesa..) WTF?!

---

### Post by tak1150 on 2007-12-07
It seems your xorg.conf is profoundly messed up.
If you backed up the original file, use that one instead.
```

sudo cp /etc/X11/xorg.conf.-name-of-your-backed-up-file /etc/X11/xorg.conf

```
Then make sure that the following are installed
```

sudo apt-get install libgl1-mesa-dri libgl1-mesa-glx

```

In fact, after the fresh install of xubuntu, the above (installing libgl1-mesa-dri and libgl1-mesa-glx) is the only thing you should've done

---

### Post by IsraeliHawk on 2007-12-07
but i did install these "lib's" after the fresh install.. and i did back up my xorg.conf file but have no clue where it's located.. :/ and how do i fix these keyboard and graphics issues? 

btw - thanks for all your help so far.. it really cheers me up that i can finally solve this..

Q: should i reinstall (my pc would probably say:AGAIN? you're a madman!) xubuntu again and then the ONLY thing i'll do is install the "lib's", or can i fix this without it?

---

### Post by tgalati4 on 2007-12-07
Your old card can run a 2D desktop at 1280 by 1024, but in 3D mode that resolution drops to either 800by600 or 640by480.  With only 32M of video memory (I'm assuming that's maximum shared) its hard to get 3D with higher resolutions.  You can drop your color bit to 16-bit and that will free up memory for 3D.

Windows games that use 3D take over the display, drop the resolution, and drop the color bit.  It's done in a way to keep the game playable.  When you are finished with the game, the card is returned to higher-resolution 2D mode.

Compiz will only turn itself on if it detects newer, more capable 3D graphics hardware.  Otherwise gutsy will have the desktop effect settings, but they will not be enabled.

---

### Post by IsraeliHawk on 2007-12-07
thanks tgalati4.. i guess i'll have to wait 'till i'll buy a good labtop (for the university..) in apprx. 7 months from now.. :)
still, what do u suggest - return to ubuntu (gnome) or stick around with the xfce of xubuntu..?

---

### Post by tak1150 on 2007-12-07
It seems you could fix your other problems by restoring the xorg.conf file
If you named it something like xorg.conf.backup...
You can find it by
```

sudo find / -name '*xorg.conf*'

```
It will take a while to find everything.

The choice of desktop env. is really just up to your liking, but I'd say stick with XFCE. I have a fairly modern (~4 years old) laptop and I use XFCE. It's faster, and once customized it's visually nice too.

tak

---

### Post by IsraeliHawk on 2007-12-08
thanks, but i tried and in 30 minutes installed a brand new xubuntu.. but now i'm back to square one.. 800*600 although this time it's a little different.. :

```
israelihawk@israelihawk-desktop:~$ glxinfo | grep direct
direct rendering: Yes
israelihawk@israelihawk-desktop:~$ 
```

i haven't installed anything yet, just the "lib's".. how do i take care of 800*600 issue?

update: i fixed it! i simply went to the display config. and change the id of the card from nvidia to "nv - riva tnt, tnt2, ..." and rebooted. 
the only problem (which i had already in windows..) was that the pc sometimes freezes completely, and i most reboot.. (my tech. guy said it's probably the old motherboard..could it be the compiz..? i doubt it, but i'll try removing it from the autostarted apps.) weirdly it didn't happen EVEN ONCE before i did this (but i lived looking at things in 800*600..)

anyway, [COLOR="Red"]**summery: for those who just installed xubuntu and have an nvidia card that used the _Nvidia-glx-legacy package_, follow these steps**[/COLOR]:

step 1:
go to syneptic, and install 
```
nvidia-glx-legacy
```
```
 libgl1-mesa-dri
```
 ```
lib-gl1-mesa-glx 
```

step 2:
reboot 

step 3:
go to "applications" -->"screen and display conf." and in graphic card choose "nv - riva tnt, tnt2..." instead of "nvidia". It should tell you to reboot in order to see the difference. 

step 4:
Reboot 
go back to that same menu (display conf.) and now you'll be able to change the resolution more than 800*600. of course, don't forget to customise your menues so that the font would be big/small as you wish..

good luck :)

---

### Post by tgalati4 on 2007-12-08
The lockups could be how shared video memory is handled.  The legacy driver works for either discrete video cards or on-board video chipsets.  Shared memory is not as fast as dedicated video RAM and can cause timing issues when doing intensive graphics operations.  For 2D desktop its normally not a problem.  When trying anything 3D, if the memory can't keep up, then it becomes corrupted and your machine freezes.

---

### Post by IsraeliHawk on 2007-12-08
so how do u think this can be solved?

---

### Post by tak1150 on 2007-12-08
When I was installing Ubuntu Feisty for my neighbor, I was somehow able to change the amount of RAM shared for the on-board video card. The machine only had 128MB RAM and by default it was going to share ~12MB or something and that was not enough for the regular GNOME (I did this through alternate install CD).

I can't remember how I did this, but somebody else might know.

Tak

---

### Post by IsraeliHawk on 2007-12-08
thanks Tak, but i don't know how, my friend talked to me tonight about his Grandpa that bought a new pc, and that the he took his old one to his "garage" - so i'll get another 256 MB RAM (meaning i'll have 512 MB RAM!!) and the old (still better) Nvidia card - Ge Force 2 MX 32MB - that way i'll disable the shared one.. :lolflag: amazing what an hilarious weekend i had.. !!

but i'll stay with xubuntu - definitelly.. after my friend will drop by my house on Monday i'll finely enjoy the OS..

do you think it'll recognize it automatically?

Uri

---

