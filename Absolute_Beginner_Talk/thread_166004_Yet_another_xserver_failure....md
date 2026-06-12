---
title: "Yet another xserver failure..."
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by masooga on 2006-04-25
So I'm trying to install dapper on my friend's laptop (HP).  She's not a big gamer so she just has a very basic video card, I'm pretty sure it's just whatever is onboard.  Everything works just fine until you try to boot up, xserver fails to start.  I've tried dpkg-reconfigure xserver-xorg, installing nvidia drivers and searching the forums.  I can't find a single piece of useful information.  Any suggestions?

---

### Post by pbaehr on 2006-04-25
Do you know what kind of video card it is?

You could try setting the type to "vesa" when you run dpkg-reconfigure xserver-xorg and see if that gets you in.

---

### Post by masooga on 2006-04-25
[QUOTE=pbaehr]Do you know what kind of video card it is?

You could try setting the type to "vesa" when you run dpkg-reconfigure xserver-xorg and see if that gets you in.[/QUOTE]

Intel Corporation 82852/855GM Integrated Graphics Device

I don't quite see where you want me to put in vesa.

---

### Post by catlett on 2006-04-25
vesa is a type of setting for your video card. it should come when the reconfigure x asks about your video card. it will try to do an automatic detection and then give you a list of card types, it will ask do you see your card/driver type (or something like that). the point is you get an option during configure x as to what type of video card you have and therefore what driver to use. in that list is vesa. vesa works well with "regular" video cards. most older cards seem to use it no problem and it is used as an almost default choice if you are having trouble with an install. so when the list comes during the setup of the video card choose vesa and see what happens.
Also you should try installing the current stable version Ubuntu Breezy Badger 5.10. Dapper is the unstable version that is still in testing and still has bugs in it. If your having trouble with the install it could be a bug dapper has when it comes to her type of hardware and breezy might not have the problem. Regardless the stable current version is always the best one to use unless you like to try out new stuff that might not work well. The advanced users like being part of the debugging process and enjoy finding out why things don't work on the new version that did  on the old. So if you just want a first try at Linux go for a stable release, it just gives you better odds of having a smooth install.

---

### Post by masooga on 2006-04-25
[QUOTE=catlett]vesa is a type of setting for your video card. it should come when the reconfigure x asks about your video card. it will try to do an automatic detection and then give you a list of card types, it will ask do you see your card/driver type (or something like that). the point is you get an option during configure x as to what type of video card you have and therefore what driver to use. in that list is vesa. vesa works well with "regular" video cards. most older cards seem to use it no problem and it is used as an almost default choice if you are having trouble with an install. so when the list comes during the setup of the video card choose vesa and see what happens.
Also you should try installing the current stable version Ubuntu Breezy Badger 5.10. Dapper is the unstable version that is still in testing and still has bugs in it. If your having trouble with the install it could be a bug dapper has when it comes to her type of hardware and breezy might not have the problem. Regardless the stable current version is always the best one to use unless you like to try out new stuff that might not work well. The advanced users like being part of the debugging process and enjoy finding out why things don't work on the new version that did  on the old. So if you just want a first try at Linux go for a stable release, it just gives you better odds of having a smooth install.[/QUOTE]

Okay, I'll try looking for vesa again... I didn't see it the first couple of times.  And I already tried Breezy, it had the same problem.  I know what I'm doing for the most part, I've just exhausted my resources trying to get X to work.

**EDIT** The options I have are: 

neomagic
nvidia
siliconmotion
voodoo

It's also saying it's failing to load modules synaptics and wacom.

---

### Post by trent dillman on 2006-04-26
Boot into recovery mode, then when you get to the root prompt:

```
vi /etc/X11/xorg.conf
```

Use the down arrow until you get to a section that looks like this:

```

Section "Device"
        Identifier      "Name of your Graphics Card"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
```

Move your cursor to the 'Driver' section, press 'i' (for 'insert'), then change the driver to 'vesa'. Then, hit ESC, then type ```
:wq
```

Now, run

```
init 2
```

---

### Post by masooga on 2006-04-26
[QUOTE=trent dillman]Boot into recovery mode, then when you get to the root prompt:

```
vi /etc/X11/xorg.conf
```

Use the down arrow until you get to a section that looks like this:

```

Section "Device"
        Identifier      "Name of your Graphics Card"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
```

Move your cursor to the 'Driver' section, press 'i' (for 'insert'), then change the driver to 'vesa'. Then, hit ESC, then type ```
:wq
```

Now, run

```
init 2
```[/QUOTE]

I did all of that and now it says it's having trouble parsing the xorg.conf file.

---

### Post by pbaehr on 2006-04-26
vi is very confusing to use if you are new to it. Try editing the file again using nano and see if you can make it look right. The "Driver" line will probably be the problem since that's where you edited. Make it look like:
```
Driver     "vesa"
```

---

### Post by masooga on 2006-04-26
[QUOTE=pbaehr]vi is very confusing to use if you are new to it. Try editing the file again using nano and see if you can make it look right. The "Driver" line will probably be the problem since that's where you edited. Make it look like:
```
Driver     "vesa"
```[/QUOTE]

Okay I did that and now when I try init 2 and startx it tells me that it can't load vesa in addition to wacom and synaptics.  Are there packages that I'm missing or something?

---

### Post by pbaehr on 2006-04-26
I'm not sure. I was under the (possibly mistaken) impression that the vesa driver was a generic driver included in the distribution by default. Perhaps someone with slightly more expertise in the matter will shed light on this. I've always had the vesa driver available with no additional installation.

---

### Post by masooga on 2006-04-26
I installed some drivers that I found on the package manager, one for vesa, synaptics and wacom.  Now when I reboot I get a very distorted gateway boot screen but then x fails to launch.  I get the error:

Failed to initialize glx extension (Compatible NVIDIA X driver not found)

---

### Post by pbaehr on 2006-04-26
Try commenting out (put a "#" in front of) the line in your xorg.config file that reads:
```
Load      "glx"
```

---

### Post by pbaehr on 2006-04-26
You may have on there that says
```
Load      "dri"
```
in there, too. I think you can comment that out, too if you still have problems.

---

### Post by masooga on 2006-04-26
Okay, I did all of that and it says 

error in locking authority file /home/dtrippel/.Xauthority

---

### Post by pbaehr on 2006-04-26
I'm not positive so BACK IT UP FIRST but I believe deleting that file and running startx again will fix that. I think it's a permissions issue.

Actually, rather than backing it up and deleting it, let's just rename it:
```
sudo mv /home/dtrippel/.Xauthority /home/dtrippel/.Xauthority_backup
```

You probably don't need the sudo since it's in your home directory, but just to be safe I threw it in.

---

### Post by masooga on 2006-04-26
That took away that error message but it's still telling me wacom can't be reached and now it says

could not open default font 'fixed'

Even though it's not fixed, thank you for spending your time helping me :)

---

### Post by pbaehr on 2006-04-26
Well, we're getting through one problem at a time. New ones just keep coming. Do you have a wacom device? If not then that section can probably just be removed (or commented) from xorg.conf entirely. That should make it stop complaining about that. I don't think that will halt the x-server, though, so there's another problem, too. I'm pretty sure that's just a warning, not a full blown error.

I found another thread with the font issue and the suggestion was to run sudo dpkg-reconfigure xserver-xorg. There's not other replies after that so it either worked or the original poster gave up (or died while trying it). So I'd give that a shot and see what happens. Be careful, though, it seems it may be fatal for the user.

Edit: By the way, I know you've run that command many times during the course of this so I'm skeptical, but maybe now that the other issues are resolved it will help with that. I have no idea, really.

---

### Post by masooga on 2006-04-26
Okay, now it just says

No valid FontPath could be found

We're getting somewhere!

---

### Post by pbaehr on 2006-04-26
Well, there's a fontpath section of xorg.conf, this is what mine looks like. I'm running Dapper, but it should be similar, I would think. Does yours look anything like this? Is this section in your xorg.conf at all?

```

Section "Files"

        # path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

```

---

### Post by masooga on 2006-04-26
It's not in there at all, should I go ahead and copy your's in?

---

### Post by pbaehr on 2006-04-26
Also, I'm at work now and it's quitting time. I'll check up on your progress when I'm home, though. Good luck for now.

---

### Post by pbaehr on 2006-04-26
Seems like it would be worth a shot. It may have some extra stuff in it on mine, though. Try it and see if it gets you anywhere, though. Worst case we'll take it back out.

I'm at work now and it's quitting time. I'll check back in on your progress when I get home though. Good luck for now.

---

### Post by masooga on 2006-04-26
I put that in and it said it couldn't find any of those files so I commented them out.

The error still reads

No valid FontPath could be found

---

### Post by pbaehr on 2006-04-26
Hm, looks like I posted twice without realizing it worked. ubuntuforums started acting a little funny for me before I left. At least the one I wanted to go through worked.

Maybe the font files are in a different location? I've seen some people report them to be in /usr/share/fonts which is different from what my file shows.

Someone else said something about running sudo dpkg-reconfigure fontconfig but I don't know exactly what that does.

It seems like you need that section of xorg but my fonts are in a different place than yours. I've never really had to mess around with my font files (as opposed to the video drivers which I played with extensively) so I'm not much of an expert in this area.

---

### Post by pbaehr on 2006-04-26
Also, since we've fixed many of the problems you were having and now it's specifically a font problem, I wonder if it would be appropriate to start a new thread with that specifically in the title to try and drum up support specific to that issue. I don't know the "rules" about that per se, but it seems appropriate to me.

---

### Post by masooga on 2006-04-26
[QUOTE=pbaehr]Also, since we've fixed many of the problems you were having and now it's specifically a font problem, I wonder if it would be appropriate to start a new thread with that specifically in the title to try and drum up support specific to that issue. I don't know the "rules" about that per se, but it seems appropriate to me.[/QUOTE]

Thank you so much for your help, I'll take a look later today :)

---

### Post by pbaehr on 2006-04-26
No problem. I just hope it wasn't the sort of thing that a real expert could have given you one command and fixed. Best of luck!

---

### Post by Damanther on 2007-09-05
I just ran across this looking for something else. I dunno if you have found a resolution yet, but it looks like maybe you just dont have the X11 misc fonts installed.

try
sudo apt-get install xorg-X11-fonts-misc

Or use synaptic or adept and search for the X11 misc fonts.

I think this will get at least the default font path that it is looking for installed.

---

### Post by pleasant88 on 2008-05-29
Yeah I had the same problem but used aptitude to see what I had installed  I didnt have xorg installed so try 
sudo apt-get install xorg 

hope this helps

---

