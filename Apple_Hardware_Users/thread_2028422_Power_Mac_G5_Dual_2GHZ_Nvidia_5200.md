---
title: "Power Mac G5 Dual 2GHZ Nvidia 5200"
date: 2012-07-18
forum: Apple Hardware Users
---

### Post by Seth Mac Fan on 2012-07-18
Hi I have a Power Mac G5 Dual 2GHZ 1GB RAM , Nvidia 5200 video card and I can not install ubuntu power pc 12.04 at all , I boot the live cd and the screen goes into sleep mode . I am using a dvi to vga converter cable too , I did manage to get to a gui by typing live video=TV-1:d but mostly everything was white and I could not see unity at all . But I could seen some menus . Is there anyway to get it to work ? I really want to dual boot leopard and ubuntu 12.04 I am a huge ubuntu fan . Anybody have any help ?

---

### Post by str8bs on 2012-07-18
Hi,

I think you may be seeing the effects of this bug in addition to a phantom port issue the FX5200 has. [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/952101](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/952101) I've played around with it on mine some and the actual display behavior varies depending on your default resolution and what desktop you use. (IE Unity 3d vs 2D or vs. LXDE/ 1280x1024 vs. 1024x768)

Could you try:
```
boot: live nouveau.noaccel=1 video=TV-1:d
```The additional parameter disables acceleration which should cause Unity to default to 2d and is one workaround to the bug. Please let us know if this changes anything.

---

### Post by rsavage on 2012-07-18
This your bug [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/902670](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/902670) ? Compiz (unity-3d is basically compiz) also mention a white screen as a common problem [http://wiki.compiz.org/Troubleshooting#White_Screen](http://wiki.compiz.org/Troubleshooting#White_Screen) .

---

### Post by str8bs on 2012-07-18
rsavage-

I'm wondering if these(and others) are symptoms of a bug further up, or all separate. GNOME 3 does the same. Not sure how to verify, but I get what looks REALLY close with GNome on an AMD64 with ATI. Changing monitors (default display resolution) changes it too. Changing to Cinnamon-symptoms would be described completely differently, but the same workarounds apply. I put a couple pictures in the Debian report and asked the question. No answers yet.

noaccell throws out several variables all at once. I'm not sure how to go about isolating it down to one thing.
IE: EXA,compositing,themes,...  Any suggestions?


seth - If you have the time:
Does your screen look like the first picture in this thread?: [http://ubuntuforums.org/showthread.php?t=2019042](http://ubuntuforums.org/showthread.php?t=2019042)
Does noaccel/unity 2 load OK?

---

### Post by rsavage on 2012-07-20
I think you are probably seeing two problems. The Firefox corruption is possibly an EXA problem? Whereas, unity 3d is a problem with opengl support?
 
From memory, it is unclear what noaccel disables. I think it stops both 2D and 3D acceleration. You can probably be a bit more selective by specifying what EXA options you want to turn off [http://manpages.ubuntu.com/manpages/precise/en/man4/exa.4.html](http://manpages.ubuntu.com/manpages/precise/en/man4/exa.4.html) . 
 
It maybe something else like colour tiling causing the problem. Increasing the virtual desktop size may disable this.
 
You could also turn off AIGLX like in the r128 instructions in the PowerPC FAQ. This will revert to the software rasterizer for the desktop environment, but applications still can use hardware acceleration. I'm not really sure how AIGLX works and fits into it all to be honest.
 
With my radeon card I have to use indirect rendering for compiz and opengl kwin. From unity-2d use:
 
LIBGL_ALWAYS_INDIRECT=1 compiz ccp --replace
 
This overcomes a problem with GLX_EXT_texture_from_pixmap . You could also use compiz config setting manager to try and solve the white screen. There are various options you can toggle - e.g. 'copy to texture' ?
 
I've compiled my own compiz - version 0.8.8, since this works (like lucid and maverick) much much better on my old radeon card. It uses less CPU than openbox and you can use emerald themes n stuff.
 
Gwjvan maybe able to help you more with compiz since he/she uses it with their radeon card and I think they also had problems with missing icons.
 
Raising a bug directly with dri/nouveau people or on their mailing list would also be a good idea. You'd probably be able to speak to somebody who will be able to put their finger on the problem straightaway.

---

### Post by str8bs on 2012-07-20
Thanks rsavage.  Scouring the various bug systems, EXA options which appear to work around the same issue for ATI users don't seem to work for nouveau users. I am not sure if "Firefox" corruption is really specific to Firefox. Similar issues have been associated in terminal and corrupt menus in KDE and Libre office.  This is an interesting read and _may be_ at least partly related to one of these issues. (The title is misleading. See comment 135)[https://bugs.freedesktop.org/show_bug.cgi?id=47266]("https://bugs.freedesktop.org/show_bug.cgi?id=47266") As far as how that translates to 3d and AIGLX, no idea. Hence, my previous question.

> Raising a bug directly with dri/nouveau people or on their mailing list would also be a good idea. Good idea. A picture is worth a thousand words. Since I have no idea what words are appropriate, I might spend a day creating a photo montage with logs and hopefully someone there can parse/link what is related and get it to the proper place.

**Specific to Unity and OP Seth reported issue.**
It would be great if someone could confirm so known issues could be updated. I prefer not to claim things as "known" unless someone else confirms it.
On my FX5200, the exact issue described by Seth can be worked around on the live desktop boot by:```
boot: live nouveau.noaccel=1 video=TV-1:d
``` (The TV-1 part is only relevant to a phantom port issue with this FX5200 card. Omit that if just booting "live" yields a screen described by the OP.)```
boot: live nouveau.noaccel=1
```
If anyone is seeing the same in ATI, please test:
```
boot: live radeon.accel=0
```

From there, the install can be performed and then one can use Unity 2D.

It pains me a bit see people going through the trouble of downloading new/different ISO's just to work around a graphics bug. Or worse, abandoning their attempt.
If one is not a Unity 2D fan, they could simply use software manager,apt, or tasksel to install other desktops. IE: Lubuntu, Xubuntu, etc.

---

### Post by rsavage on 2012-07-20
> **str8bs said:**
>  (The title is misleading. See comment 135)[https://bugs.freedesktop.org/show_bug.cgi?id=47266](https://bugs.freedesktop.org/show_bug.cgi?id=47266) 
 
That's an interesting bug report you've found there. I'm not sure it is what I'm seeing. I'll look into maybe compiling a newer version of radeon though. Thanks, I bet it took some time to find that.
 
> 
I prefer not to claim things as "known" unless someone else confirms it.

I clung to the same ideals, but now I just write what I want.
 
> 
It pains me a bit see people going through the trouble of downloading new/different ISO's just to work around a graphics bug. Or worse, abandoning their attempt.
If one is not a Unity 2D fan, they could simply use software manager,apt, or tasksel to install other desktops. IE: Lubuntu, Xubuntu, etc.
Agreed.

---

### Post by Seth Mac Fan on 2012-07-22
> **str8bs said:**
> Hi,

I think you may be seeing the effects of this bug in addition to a phantom port issue the FX5200 has. [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/952101](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/952101) I've played around with it on mine some and the actual display behavior varies depending on your default resolution and what desktop you use. (IE Unity 3d vs 2D or vs. LXDE/ 1280x1024 vs. 1024x768)

Could you try:
```
boot: live nouveau.noaccel=1 video=TV-1:d
```The additional parameter disables acceleration which should cause Unity to default to 2d and is one workaround to the bug. Please let us know if this changes anything.

Sorry about taking so long to reply,  I will test it and let you know later today . Thanks again .

---

### Post by Seth Mac Fan on 2012-07-22
> **str8bs said:**
> rsavage-

I'm wondering if these(and others) are symptoms of a bug further up, or  all separate. GNOME 3 does the same. Not sure how to verify, but I get  what looks REALLY close with GNome on an AMD64 with ATI. Changing  monitors (default display resolution) changes it too. Changing to  Cinnamon-symptoms would be described completely differently, but the  same workarounds apply. I put a couple pictures in the Debian report and  asked the question. No answers yet.

noaccell throws out several variables all at once. I'm not sure how to go about isolating it down to one thing.
IE: EXA,compositing,themes,...  Any suggestions?


seth - If you have the time:
Does your screen look like the first picture in this thread?: [http://ubuntuforums.org/showthread.php?t=2019042](http://ubuntuforums.org/showthread.php?t=2019042)
Does noaccel/unity 2 load OK?

Ok well I just tried again . Yes my screen does look like that when entering the stuff you told me too , and no I could not get it to work 
I have successfully ran lubuntu but the problem with that is I can not get the resolution any higher than 1024x768 and firefox is choppy and all messed up .

---

### Post by str8bs on 2012-07-22
Seth - I hope my comments didn't imply "What's the hold up?" as that was not my intent. No apologies necessary. Thanks for persisting.

The symptoms you are describing with LXDE have also been reported to be avoided by noaccel. The better long term work around to that is a little more painful, but possible.
See this thread--[http://ubuntuforums.org/showthread.php?t=1937940](http://ubuntuforums.org/showthread.php?t=1937940)

Since you are already running LXDE, could you try the same again?
```
live nouveau.noaccel=1
``` Be weary of type-o's.  If you can see well enough, could you post your /var/log/Xorg.0.log or look in the first few lines and you can see what was passed from kernel parameters.

Edit: Clarify boot params. Since we know yours does have a phantom port issue, always add that TV-1 disable to any boot parameters you try. Just put a space between any other parameters. Upper vs Lower case letters "d" does matter.
```
live nouveau.noaccel=1 video=TV-1:d
```

Once we get it going, we can set that TV disable permanent so you won't have to type it every time using yaboot.conf.

---

### Post by Seth Mac Fan on 2012-07-23
> **str8bs said:**
> Seth - I hope my comments didn't imply "What's the hold up?" as that was not my intent. No apologies necessary. Thanks for persisting.

The symptoms you are describing with LXDE have also been reported to be avoided by noaccel. The better long term work around to that is a little more painful, but possible.
See this thread--[http://ubuntuforums.org/showthread.php?t=1937940](http://ubuntuforums.org/showthread.php?t=1937940)

Since you are already running LXDE, could you try the same again?
```
live nouveau.noaccel=1
``` Be weary of type-o's.  If you can see well enough, could you post your /var/log/Xorg.0.log or look in the first few lines and you can see what was passed from kernel parameters.

Edit: Clarify boot params. Since we know yours does have a phantom port issue, always add that TV-1 disable to any boot parameters you try. Just put a space between any other parameters. Upper vs Lower case letters "d" does matter.
```
live nouveau.noaccel=1 video=TV-1:d
```Once we get it going, we can set that TV disable permanent so you won't have to type it every time using yaboot.conf.

**[COLOR=Black]str8bs PLEASE HELP ME [/COLOR]**

ok so here is the deal , I got kubuntu 12.04 LTS Power pc to work perfectly on the live cd with your steps and I even got my prefered resolution with your steps . But after I installed and logged in I could not see anything start menu or icons but I saw the mouse . So I restarted and logged in failsafe mode and it worked but the firefox issues are there again after installing and running in failsafe mode , which I think is because those commands you gave me are not saved How do I make your steps work on a full install not a live cd ? Are those commands not saved ?**[COLOR=Black]If they are not saved how do I save them because like I said everything was working perfect on the live cd with those commands but does not work after installing ? [/COLOR]**[B][COLOR=Black] 

Also I can not seem to get my audio to work it  says dummy output and I cannot hear anything it works fine in mac os x  and yellow dog linux [/COLOR][/B][B][COLOR=Black]Please help me .
[/COLOR][/B]

---

### Post by str8bs on 2012-07-23
Seth- you will probably want a combination of two workarounds.
noaccel works but has some side effects.

For now, whatever boot parameters worked: replace "live" with "Linux"

Sound: check the FAQ, you probably just need to add some lines in etc/modules.  Someone else will chime to help with that I'm sure.

 No time now, but if you can attach /var/log/Xorg.0.log , I'll see if I can create a xorg.conf for you that works around these issues.

 PS: Good work! You will find the effort well worth it in the long run.

---

### Post by Seth Mac Fan on 2012-07-23
> **str8bs said:**
> Seth- you will probably want a combination of two workarounds.
noaccel works but has some side effects.

For now, whatever boot parameters worked: replace "live" with "Linux"

Sound: check the FAQ, you probably just need to add some lines in etc/modules.  Someone else will chime to help with that I'm sure.

 No time now, but if you can attach /var/log/Xorg.0.log , I'll see if I can create a xorg.conf for you that works around these issues.

 PS: Good work! You will find the effort well worth it in the long run.

Sure thing I will get that information for you , also I have tried typing linux but it basically tells me that linux command cannot not be found or something  , and that the command wont work for whatever reason . But I will get you that xorg.conf in the next couple hours and post it [B]thanks again for helping the ubuntu community is very helpful and I am really grateful for the time you guys take out of your day to help people like me .
[/B]

---

### Post by str8bs on 2012-07-23
Seth - I don't recall if you are dual booting, but you should get to a prompt that has ```
boot:
``` when you power on. hit the tab key.
You should see some "Linux"  and "Linux-old"

Type just like it shows there with your parameters.
```
boot: Linux nouveau.noaccel=1 video=TV-1:d
```It should be the same as the live cd.

Also, could you post output of xrandr -q ?

---

### Post by Seth Mac Fan on 2012-07-23
> **str8bs said:**
> Seth - I don't recall if you are dual booting, but you should get to a prompt that has ```
boot:
``` when you power on. hit the tab key.
You should see some "Linux"  and "Linux-old"

Type just like it shows there with your parameters.
```
boot: Linux nouveau.noaccel=1 video=TV-1:d
```It should be the same as the live cd.

I will try I am currently not dual booting at the moment .

---

### Post by Seth Mac Fan on 2012-07-27
well I got my audio working and I got ubuntu to work in 2d using the no.accel=1 video=TV-1:d but the problem is now I can not watch any videos and I know it is probably because of the no.accel command .

---

### Post by Seth Mac Fan on 2012-07-28
Ok quick **UPDATE **on my progress 

 I got ubuntu working in 2d using no.accell=1 video=TV-1:d and I figured out how to enable it to be permanent . I also know how to turn it off again too if need be .

Now it works good but there is **one major drawback I can not watch videos at all** .

**I can watch videos when nouveau.noaccel=1 is turned off **but the problem with  that is the screen is messed up when I do that so I have to use  no.accell to see my full desktop correctly . I got all of the resolutions that my  monitor supports so that is good at least .

**Is there anything else I can do to get video to work ?** Not having video support is kind of a deal breaker for me when wanting to run ubuntu .

I have tried installing the NV driver using this**[[COLOR=Black] [COLOR=Blue]LINK [/COLOR][/COLOR]]("http://ubuntuforums.org/showpost.php?p=11493049&postcount=27")**but I got no where because the instructions I think are outdated because they are for natty 11.04 on the Power PC FAQ . Either that or the nv driver no longer works with ubuntu 12.04 , or you have to recompile it for 12.04 which I do not know how to do , I am not that advanced with linux yet .

I have also tried downloading a xorg.conf file from this [[COLOR=Blue]_**LINK**_[/COLOR]]("http://mac.linux.be/content/xorgconf-g5-ppc-tower")
 I followed the instructions on the power pc FAQ on how to move it to the  right place . I also turned off no.accel command when I used the  xorg.conf file and that xorg.conf did nothing for me and did not work .

[B]I am totally clueless right now on what to do . I really want video playback . If anybody can help please let me know . I have wanted to give up a lot doing this but I am determined to get this working correctly because I really like ubuntu and the ubuntu community .
[/B]

---

### Post by str8bs on 2012-07-28
Hey Seth - Well done.

noaccel is a good quick workaround for the live, but it will affect other things like video playback.

Best option depends on how the acceleration related bug affects your card.
In 2d or when you were in LXDE, would you describe the corrupt Firefox graphics as appearing on only half or the lower/bottom parts of your display? Or, is it the whole screen. (I'm just talking about in 2d now, not the "white" screen you see in 3d desktops.

Can you post output of xrandr -q ?

---

### Post by Seth Mac Fan on 2012-07-28
> **str8bs said:**
> Hey Seth - Well done.

noaccel is a good quick workaround for the live, but it will affect other things like video playback.

Best option depends on how the acceleration related bug affects your card.
In 2d or when you were in LXDE, would you describe the corrupt Firefox graphics as appearing on only half or the lower/bottom parts of your display? Or, is it the whole screen. (I'm just talking about in 2d now, not the "white" screen you see in 3d desktops.

Can you post output of xrandr -a ?

Yes , when I am not using noaccel Firefox is messed up on the lower half of whatever page I am looking at and yes this is in ubuntu 2d . When I switch resolutions it goes away for a while but comes back eventually , I also cant see the trash can or the bottom half of the unity dock bar .

---

### Post by Seth Mac Fan on 2012-07-28
Ok I am going to try something else , I will tell you guys about my progress when I am done .

---

### Post by Seth Mac Fan on 2012-07-29
> **str8bs said:**
> Hey Seth - Well done.

noaccel is a good quick workaround for the live, but it will affect other things like video playback.

Best option depends on how the acceleration related bug affects your card.
In 2d or when you were in LXDE, would you describe the corrupt Firefox graphics as appearing on only half or the lower/bottom parts of your display? Or, is it the whole screen. (I'm just talking about in 2d now, not the "white" screen you see in 3d desktops.

Can you post output of xrandr -a ?

Ok after a little more testing I have **officially solved my video problem** , firefox and ubuntu work fine when I set my resolution to 1280x1024 . The problems only start if I lower my resolution , its weird but all seems good with the resolution is set correctly . Everything works fine including firefox . The problems only start really when I have my resolution set to 1024x768 or lower . **Thanks everyone for all of the help especially str8bs  .**

---

### Post by str8bs on 2012-07-29
Sounds like you are definitely experiencing the bug I linked in my first post then.

xrandr -q should just show what modes your display supports and what it is currently set at.

If you want a different resolution, the workaround is to create a simple /etc/X11/xorg.conf like at the bottom of [ _this_ ]("http://ubuntuforums.org/showthread.php?t=1937940&page=2") page.
Just change the numbers next to Virtual to match your resolution and then up ydim (the second number) until you don't see the problem. Normally those numbers would be the same as your resolution, but increasing ydim works around the [_ bug _]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/952101").

---

### Post by Seth Mac Fan on 2012-07-29
> **str8bs said:**
> Sounds like you are definitely experiencing the bug I linked in my first post then.

xrandr -a should just show what modes your display supports and what it is currently set at.

If you want a different resolution, the workaround is to create a simple /etc/X11/xorg.conf like at the bottom of [ _this_ ]("http://ubuntuforums.org/showthread.php?t=1937940&page=2") page.
Just change the numbers next to Virtual to match your resolution and then up ydim (the second number) until you don't see the problem. Normally those numbers would be the same as your resolution, but increasing ydim works around the [_ bug _]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/952101").

Ok thanks .

---

### Post by str8bs on 2012-07-29
just realized I've been telling you the WRONG switch.  it is ```
xrandr -q
```
not a.  SORRY!

I went back and edited so as not to confuse others reading this.

---

### Post by Seth Mac Fan on 2012-07-29
> **str8bs said:**
> just realized I've been telling you the WRONG switch.  it is ```
xrandr -q
```not a.  SORRY!

I went back and edited so as not to confuse others reading this.

good job .

---

### Post by gwjvan on 2012-08-05
> **rsavage said:**
> Gwjvan maybe able to help you more with compiz since he/she uses it with their radeon card and I think they also had problems with missing icons.

I was never able to get Unity 3D to display correctly, and I think I lucked out with compiz+a mixture of gui components (and messing with the the "workaround" settings in Compiz Settings). I don't have access to the G4 PowerBook at the moment, but if I am able to get it back/keep it for longer I would like to see Unity fixed on PowerPC.

---

