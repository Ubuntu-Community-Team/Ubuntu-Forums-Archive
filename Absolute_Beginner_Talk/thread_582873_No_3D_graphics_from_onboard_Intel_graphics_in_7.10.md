---
title: "No 3D graphics from onboard Intel graphics in 7.10"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by Charlie Chick on 2007-10-20
Hello Everybody,

Fist of all, may I congratulate the team behind 7.10 for yet another superb release! 

I upgraded both computers straight away and everything went smoothly, but I cannot get any 3D effects on my desktop, a 2 1/2 year old Dell Dimension 3100. When I enable any effects in Appearance, I don't get any buttons in the top right hand corner (minimise, resize and close) which makes it useless. My Dell has onboard Intel graphics. 

Strangely, my Acer Travelmate 2410  laptop, which is a little younger at 1 1/2 years old and also has onboard Intel graphics, has no such problem and I can enjoy the effects in all their glory but I think that it may be using restricted drivers which the Dell is not.

I looked inside the Dell's case and all I have is a single PCI Express x1 slot (and 2 standard PCI slots) for which I can't find a single graphics card on sale in the UK. So, am I stuffed or is there a fix for the Dell which will get the nice 3d effects to work?

Thanks,

Charlie

---

### Post by derred on 2007-10-20
What kind of Intel board is it? {950, 915, 855?}

---

### Post by Charlie Chick on 2007-10-20
Ubuntu's harware info tool says it's a 82915G/GV/910GL Integrated Graphics Controller.

Thanks,

Charlie

---

### Post by Kosimo on 2007-10-20
Did you try enabling restricted drivers?
System > Administration > Restricted Drivers Manager

---

### Post by Charlie Chick on 2007-10-20
> **Kosimo said:**
> Did you try enabling restricted drivers?
System > Administration > Restricted Drivers Manager

Yes, I have. I get a message saying that my hardware does not need any restricted drivers.

Thanks, 

Charlie

---

### Post by Mandibela on 2007-10-21
I've got the same problem, but with (intel -driver) G965 integrated graphics, aka the X3100 -chip. No 3D desktop.

---

### Post by Perfect Storm on 2007-10-21
Try install **libgl1-mesa-dri**

---

### Post by Mandibela on 2007-10-21
> **Artificial Intelligence said:**
> Try install **libgl1-mesa-dri**

Already installed. This is a fresh install of 7.10. Direct rendering is yes/SGI

---

### Post by Perfect Storm on 2007-10-21
How's the driver part in your xorg.conf looks like?

---

### Post by Mandibela on 2007-10-21
> **Artificial Intelligence said:**
> How's the driver part in your xorg.conf looks like?

```

Section "Device"
	Identifier	"Intel Corporation 82G965 Integrated Graphics Controller"
	Boardname	"intel"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	0
EndSection
```

---

### Post by Mandibela on 2007-10-21
```
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
```

---

### Post by Mandibela on 2007-10-21
...and because I didn't mention it already, 3D (beryl/compiz) worked in 7.04, kubuntu 7.04, OpenSUSE 10.3, and Mandriva 2008.1, naturally with this hardware. And of course my old xorg.confs are via the wonder of repartiotioning lost.

---

### Post by Perfect Storm on 2007-10-21
If we can get some people with intel card to post their xorg.conf to compare it. (I'm nvidia user so it's limit how much help I can be).

---

### Post by Mandibela on 2007-10-21
> **Artificial Intelligence said:**
> If we can get some people with intel card to post their xorg.conf to compare it. (I'm nvidia user so it's limit how much help I can be).

Well, until that happens.. I experimented a little. No luck with i810 driver either... i810 also removed high frequencies from my display or didn't support them (I didn't change the config for display). But it displayed the login screen with a better resolution than the 'intel' driver, which gives a wide-screen resolution+low freq that I'd also would like to change.

Perhaps setting the graphics memory to an amount could solve something?

---

### Post by kroenecker on 2007-10-21
[http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)

That'll do it.  Playing video doesn't work though.

---

### Post by Charlie Chick on 2007-10-22
> **Artificial Intelligence said:**
> Try install **libgl1-mesa-dri**

I looked in Synaptic and it's already installed. Do you have any other suggestions please?

Thanks,

Charlie

---

### Post by misfitpierce on 2007-10-22
I have heard about the Intel skip check fix posted by kroenecker. Do you think this will be fixed with compiz eventually for 7.10 as my friend has this problem but would like to play videos and have 3d effects... lol :)

---

### Post by shad0w_walker on 2007-10-22
Have you tried adding this to your xorg file? Stick it in the device section.

```
Option "AddARGBGLXVisuals" "True"
Option "AllowGLXWithComposite" "True"
```

---

### Post by crimesaucer on 2007-10-22
I use a 910GML celeron m chipset and when I tried the xubuntu 7.10 tribe 5 and the next 2 beta upgrades, I also ran into this problem.


I had a fully working Compiz Fusion in Feisty using the Trevino repo. I also had Beryl SVN working with AiGLX since Beryl 1.1 - 1.5 -SVN, all the way up until it merged to Compiz Fusion.


My point is that as soon as I did a fresh install of xubuntu 7.10 tribe 5, I was unable to get Compiz 0.5.2 to start... I didn't really work on the problem because I knew it wasn't even a beta yet, so I just used the compositing from xfce4... which worked perfectly.


Then I installed Archlinux and also had problems with AiGLX and Compiz Fusion..... it seems Compiz Fusion wasn't working with my AiGLX. I would get this error:

```

# fusion-icon
 * Detected Session: gnome
 * Searching for installed applications...
Backend     : gconf
Integration : true
Profile     : default
Adding plugin decoration (decoration)
Initializing decoration options...done
 * No GLX_EXT_texture_from_pixmap with direct rendering context
 ... nor with indirect rendering, this isn't going to work!
Traceback (most recent call last):
  File "/usr/bin/fusion-icon", line 57, in <module>
    from FusionIcon import interface
  File "/usr/lib/python2.5/site-packages/FusionIcon/interface.py", line 25, in <module>
    from start import wms, apps, options, decorators, init, env
  File "/usr/lib/python2.5/site-packages/FusionIcon/start.py", line 64, in <module>
    env.set()
  File "/usr/lib/python2.5/site-packages/FusionIcon/environment.py", line 143, in set
    if not self.Xgl and self.glx_vendor == 'NVIDIA Corporation':
AttributeError: Environment instance has no attribute 'glx_vendor'

```


... then I read on digg.com that others were having problems: [http://digg.com/linux_unix/Ubuntu_7_10_Gutsy_Gibbon_Release_Candidate](http://digg.com/linux_unix/Ubuntu_7_10_Gutsy_Gibbon_Release_Candidate)


.... just click on that digg.com link and the do a ctrl+f search for "AIGLX", and then read what people are saying about AIGLX and XGL and FGLRX... that might help a little. I'm just giving them a little time to sort all of the errors out since the new stable Compiz 0.6.0 is out now.

---

### Post by loganm10 on 2007-10-22
the problem is that most intel onboard graphics have been blacklisted because video doesnt work, that is my problem, you can skip the blacklist check by doing this:

create a file called:
/home/logan/.config/compiz/compiz-manager (replace logan with your name obviously)

inside that file put this line:
SKIP_CHECKS=yes

that will make compiz run, but again, video is crippled

if you want to watch a video, open a terminal and run: metacity --replace

that will kill compiz and run the default window manager, you can watch a video, and just log out and back in to reenable compiz, or run: compiz --replace

again this isnt ideal and I hope the compiz team fixes this

---

### Post by crimesaucer on 2007-10-22
I found this out while researching the Intel GMA problem: [http://wiki.compiz-fusion.org/Troubleshooting](http://wiki.compiz-fusion.org/Troubleshooting)


Scroll a few paragraphs down to the "Common Mistakes" section with the Intel GMA CArds section.


I haven't tried it yet, I'm going to wait until Compiz Fusion 0.6.0 is in my Arch testing or AUR repos before I try to install Compiz again.

---

### Post by Mandibela on 2007-10-22
> **shad0w_walker said:**
> Have you tried adding this to your xorg file? Stick it in the device section.

```
Option "AddARGBGLXVisuals" "True"
Option "AllowGLXWithComposite" "True"
```

I'll try those in a moment, but mind I remind ya'll that these problems should not exist on a fresh install. If those switches should do the job, they should have been there in the first place...

---

### Post by crimesaucer on 2007-10-22
-EDITED-

I also found this in the Compiz Forum: [http://forum.compiz-fusion.org/showthread.php?t=1985](http://forum.compiz-fusion.org/showthread.php?t=1985)

Maybe try starting it this way with the code prepended in front of the normal way you start it: ```
LIBGL_ALWAYS_INDIRECT=1 compiz --replace &
```


I got that from reading this tip from STEP #4 of that link above: ```
LIBGL_ALWAYS_INDIRECT=1 compiz --replace --indirect-rendering --sm-disable ccp &
```


and this tip from the troubleshooting page: 
> 
"Intel GMA Cards

    *

      If you are using an Intel GMA card with AIGLX, you will need to start Compiz Fusion with LIBGL_ALWAYS_INDIRECT=1 prepended."


-from the trouble shooting page: [http://wiki.compiz-fusion.org/Troubleshooting](http://wiki.compiz-fusion.org/Troubleshooting)
- and here: [http://wiki.archlinux.org/index.php/Compiz_Fusion#Second_solution](http://wiki.archlinux.org/index.php/Compiz_Fusion#Second_solution)


!!!!!!! BUT I HAVEN'T TRIED THIS YET... and ... I'M NOT SURE IF THIS IS CORRECT... I just found these pages and am researching it.

---

### Post by Mandibela on 2007-10-22
> **Mandibela said:**
> I'll try those in a moment, but mind I remind ya'll that these problems should not exist on a fresh install. If those switches should do the job, they should have been there in the first place...

Well, well... got compiz to work, my GPU was balcklisted, intel G965. I used the "SKIP_CHECKS=yes" -method. And I got around the choppy video with forcing VLC Player to use X11 as output. It's not smoothed or anything, but works.

But I don't like this, GLXGEARS has the same good fps it used to have, but it wont go behind other windows, Super+Tab works at first, but if I leave the super key down and wait for the windows to stop, they disappear (maybe backgroundblur or something doesn't work).

Not pretty/functional enough for me. Atleast, yet.

---

### Post by Charlie Chick on 2007-10-22
It's interesting reading other people's experiences. Like Mandibela, Compiz worked, after a fashion, in 7.04 and that's with the same hardware. So the only thing that changed was the upgrade to 7.10. That suggests to me that the hardware is capable of rendering the effects, but is just not working for some reason. As I mentioned in my original post, my laptop also has integrated Intel graphics and worked perfectly after the upgrade to 7.10. I wonder why one and not the other?

---

### Post by crimesaucer on 2007-10-23
> **Charlie Chick said:**
> It's interesting reading other people's experiences. Like Mandibela, Compiz worked, after a fashion, in 7.04 and that's with the same hardware. So the only thing that changed was the upgrade to 7.10. That suggests to me that the hardware is capable of rendering the effects, but is just not working for some reason. As I mentioned in my original post, my laptop also has integrated Intel graphics and worked perfectly after the upgrade to 7.10. I wonder why one and not the other?

I read somewhere that they changed something in Compiz while writing an icon into the beta (I could be wrong)... I'm wondering if 0.6.0 will even have the problem with Intel GMA and AIGLX.


Did you try that appended start code from the Compiz trouble shooting page?

---

### Post by crimesaucer on 2007-10-23
> **Charlie Chick said:**
> It's interesting reading other people's experiences. Like Mandibela, Compiz worked, after a fashion, in 7.04 and that's with the same hardware. So the only thing that changed was the upgrade to 7.10. That suggests to me that the hardware is capable of rendering the effects, but is just not working for some reason. As I mentioned in my original post, my laptop also has integrated Intel graphics and worked perfectly after the upgrade to 7.10. I wonder why one and not the other?


I just reinstalled Compiz Fusion on my Archlinux with Intel GMA card, and I used that command in Terminal:

```
LIBGL_ALWAYS_INDIRECT=1 fusion-icon
```


...and it worked perfectly. You would probably use the code:

```
LIBGL_ALWAYS_INDIRECT=1 compiz --replace
```

---

### Post by Charlie Chick on 2007-10-24
> **crimesaucer said:**
> I just reinstalled Compiz Fusion on my Archlinux with Intel GMA card, and I used that command in Terminal:

```
LIBGL_ALWAYS_INDIRECT=1 fusion-icon
```


...and it worked perfectly. You would probably use the code:

```
LIBGL_ALWAYS_INDIRECT=1 compiz --replace
```

As a beginner to Ubuntu and Linux I don't quite understand what you've done. Did you open Synaptic and re-install Compiz from there? Where and when do I open a terminal and use the code? Sorry to be so thick, but I don't have much experience. Would you mind spelling out exactly what I need to do?

Thanks,

Charlie

---

### Post by crimesaucer on 2007-10-24
Hello, I re-read your original question (quoted below), and when you say you this:  "When I enable any effects in Appearance, I don't get any buttons in the top right hand corner (minimise, resize and close) which makes it useless. "....


> **Charlie Chick said:**
> Hello Everybody,

Fist of all, may I congratulate the team behind 7.10 for yet another superb release! 

I upgraded both computers straight away and everything went smoothly, but I cannot get any 3D effects on my desktop, a 2 1/2 year old Dell Dimension 3100. When I enable any effects in Appearance, I don't get any buttons in the top right hand corner (minimise, resize and close) which makes it useless. My Dell has onboard Intel graphics. 

Strangely, my Acer Travelmate 2410  laptop, which is a little younger at 1 1/2 years old and also has onboard Intel graphics, has no such problem and I can enjoy the effects in all their glory but I think that it may be using restricted drivers which the Dell is not.

I looked inside the Dell's case and all I have is a single PCI Express x1 slot (and 2 standard PCI slots) for which I can't find a single graphics card on sale in the UK. So, am I stuffed or is there a fix for the Dell which will get the nice 3d effects to work?

Thanks,

Charlie


... do you mean that you have no window borders at all, just the windows that can't be closed?


I also have not tried Ubuntu 7.10 with the new default Compiz... so I might not be the correct guy to ask about this.


The way I fixed my Compiz Fusion was for the Compiz-git available in the distro called Archlinux... and it had to do with the fact that I have an embedded Intel GMA graphics card in my HP Pavilion notebook.


I think ubuntu and xubuntu both use AiGLX, so I would think this shouldn't be the problem... so you should be able to have window borders and the effects of the cube and wobbliness.


I would ask someone else, or start a new thread with a better description of the problem... because it sounds like your losing your metacity window borders when you enable effects.

---

### Post by crimesaucer on 2007-10-24
> **loganm10 said:**
> the problem is that most intel onboard graphics have been blacklisted because video doesnt work, that is my problem, you can skip the blacklist check by doing this:

create a file called:
/home/logan/.config/compiz/compiz-manager (replace logan with your name obviously)

inside that file put this line:
SKIP_CHECKS=yes

that will make compiz run, but again, video is crippled

if you want to watch a video, open a terminal and run: metacity --replace

that will kill compiz and run the default window manager, you can watch a video, and just log out and back in to reenable compiz, or run: compiz --replace

again this isnt ideal and I hope the compiz team fixes this

...as for people with the video problems and xf86-video-intel... I got my video to work with Compiz Fusion with the media player "xine-ui" and changing the video driver to the xshm driver.


I found that the video quality is not as good, but it works so you don't have to start metacity just to watch a quick 20 second video... and if you're going to watch a movie or many video clips, then just change back to metacity for better video quality with a movie player like Totem.


I am also using the latest testing xorg-server 1.4-4 in Arch, with the newest xf86-video-intel 2.1.1-2 for the 910GML, 915 chipsets... I wish they would fix this in Compiz because my video when using Totem in metacity was the best picture quality I've seen on my Linux.

---

### Post by Bannor on 2007-10-24
Intel Graphics Media Accelerator 900 
do you have this gma or gma 850

---

### Post by crimesaucer on 2007-10-24
My Computer: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00495183&lc=en&cc=us&dlc=en&product=1136372&os=228&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00495183&lc=en&cc=us&dlc=en&product=1136372&os=228&lang=en)

Using the Intel Graphics Media Accelerator 900 on a 1.6 GHz Intel® Celeron® M Processor 380.

---

### Post by Bannor on 2007-10-24
this processing unit has some serious issues I had gma 950 and could n't use it for most 3d things

[http://support.intel.com/support/graphics/intel945gm/sb/CS-021400.htm](http://support.intel.com/support/graphics/intel945gm/sb/CS-021400.htm)

this link is obviously for windows based games but you want 3d rendering for linux I bet the limitation of the card could be causing part of the problem

---

### Post by crimesaucer on 2007-10-24
> **Bannor said:**
> this processing unit has some serious issues I had gma 950 and could n't use it for most 3d things

[http://support.intel.com/support/graphics/intel945gm/sb/CS-021400.htm](http://support.intel.com/support/graphics/intel945gm/sb/CS-021400.htm)

this link is obviously for windows based games but you want 3d rendering for linux I bet the limitation of the card could be causing part of the problem

My 3D rendering works perfectly once I used the bit of code from the Compiz Fusion troubleshooting page: [http://wiki.compiz-fusion.org/Troubleshooting](http://wiki.compiz-fusion.org/Troubleshooting)


I also am able to play video, just not at it's best quality because I have to use the xshm video driver with xine-ui... I wish there was a way around that.


But I agree, it's a low end card on a low end machine, so I guess I'm happy with the Compiz Effects I am able to use, and as for the videos crashing, I think they are working on the xf86-video-intel video driver, I'm actually using this in it's testing version... so I hope they add some sort of patch to make the video quality work while using Compiz... instead of having to use the xshm video driver in xine.


Oh yeah, one more tip for xshm video in Compiz. I found that if I set a few more things in the xine-ui "alt+s" settings, that I can make the video quality better. What I do is I set the video section to "disable all video scaling" and  higher the value of the MPEG-4 postprocessing. The scaling keeps the video original 1:1 size.

---

### Post by Charlie Chick on 2007-10-25
Having looked again, it is the entire window border that is missing as well as the 3 buttons in the top right hand corner.

Thanks,

Charlie

---

### Post by crimesaucer on 2007-10-25
> **Charlie Chick said:**
> Having looked again, it is the entire window border that is missing as well as the 3 buttons in the top right hand corner.

Thanks,

Charlie

Do you have Emerald installed?

usually the command that should work for your window borders is written below (if you have Emerald installed, and if there is no other problems):

```
emerlad --replace &
```

... other than that, I'm not sure what else to suggest.

---

### Post by Mandibela on 2007-10-26
> **crimesaucer said:**
> Do you have Emerald installed?

usually the command that should work for your window borders is written below (if you have Emerald installed, and if there is no other problems):

```
emerlad --replace &
```

... other than that, I'm not sure what else to suggest.

Emerald (or whatever) does have some problems on my h/w too, the window decorations ( =borders) are too large after enabling compiz and then shutting down and booting up, aka after a reboot. I'm searching for solutions still. DPI in xorg.conf or elsewhere seems to be the problem. Temporarily I can remedy the situation with disabling and enabling compiz via the menu. Also, I remember, even if the borders are not visible, the buttons (that you can't see) are still functional. I had some of that earlier.

---

### Post by Flying caveman on 2007-10-26
window border buttons not working? open a terminal and restart your window manager.  

```
metacity
```

I understand your trying to get your 3D stuff working, but isn't it better to have a working 2D desktop than a not working 3D desktop.

I eventually get bored with the 3D desktop and end up going back to the 2D desktop.

---

### Post by Mandibela on 2007-10-26
My opinion is that 7.10 **is** 2D, not 3D. The exposé-esque functionality and other visual and fuctional perks are the main reason for enabling compiz on ubuntu in the first place, most people are not intrested in the effectry. On ubuntu desktop the 2D is the same as in windows (slow, painful), and as my other computer is a OSX mac that has that extra usability, my preferred way of getting things done is the way with that "3D stuff" stuff. This 2D vs 3D, of course, has been wildly speculated over the years..

---

### Post by crimesaucer on 2007-10-26
> **Mandibela said:**
> Emerald (or whatever) does have some problems on my h/w too, the window decorations ( =borders) are too large after enabling compiz and then shutting down and booting up, aka after a reboot. I'm searching for solutions still. DPI in xorg.conf or elsewhere seems to be the problem. Temporarily I can remedy the situation with disabling and enabling compiz via the menu. Also, I remember, even if the borders are not visible, the buttons (that you can't see) are still functional. I had some of that earlier.

You can edit the size of the Emerald window theme like this:

System-->--Preferences-->--Emerald Theme Manager

... then ... select your theme that you are using in the "Theme Settings", then click: 

Themes Settings-->-Edit Themes-->--Titlebar

... then ... goto the "Title Bar" section on the right, and adjust the "Minimum Title-bar Height". mine is set to 21 with my Vertical button at 4, and the Horizontal button at 2.



--- you can also adjust the size of all 4 sides of the window theme by going to the:



Themes Settings-->--Edit Themes-->--Frame/Shadows

... then ... goto the "Frame Borders" section on the right, and adjust the top, bottom, left, and right sides of your windows theme. Mine are set to 4 each....

---

### Post by Charlie Chick on 2007-10-27
> **crimesaucer said:**
> Do you have Emerald installed?

usually the command that should work for your window borders is written below (if you have Emerald installed, and if there is no other problems):

```
emerlad --replace &
```

... other than that, I'm not sure what else to suggest.

No, I don't but I have just installed it via Synaptic. I'm sorry to say that it hasn't made any difference.

Thanks, Charlie

---

### Post by Charlie Chick on 2007-10-27
Postscript: I got fed up fighting this, backed up all my personal files and re-installed from scratch. Guess what? It all works, 3D and all so my Intel graphics can handle all the Compiz stuff. I've just wasted 80 quid on a Matrox graphics card which I don't need and couldn't get to work with Ubuntu anyway, but I'm happy.

So it appears that the problem lies in the upgrade from 7.04 to 7.10. This has never happened to me before as I've upgraded without problem from 6.10 to 7.04 but there's always a first time for everything!

Thanks to everybody for your help,

Charlie

---

### Post by crimesaucer on 2007-10-27
> **Charlie Chick said:**
> Postscript: I got fed up fighting this, backed up all my personal files and re-installed from scratch. Guess what? It all works, 3D and all so my Intel graphics can handle all the Compiz stuff. I've just wasted 80 quid on a Matrox graphics card which I don't need and couldn't get to work with Ubuntu anyway, but I'm happy.

So it appears that the problem lies in the upgrade from 7.04 to 7.10. This has never happened to me before as I've upgraded without problem from 6.10 to 7.04 but there's always a first time for everything!

Thanks to everybody for your help,

Charlie

That sucks that you even bought a new graphics card... did you install Emerald with your new system, there are some really nice window themes using Emerald.


I've heard that a fresh clean install is always best for upgrades... especially when there are a lot of changes.

---

### Post by hellmanns on 2007-10-27
> **crimesaucer said:**
> Do you have Emerald installed?

usually the command that should work for your window borders is written below (if you have Emerald installed, and if there is no other problems):

```
emerlad --replace &
```

... other than that, I'm not sure what else to suggest.

I had that installed here and it didn't work out that great...
but the weird stuff is that the rest (compiz) 3D worked great, withou any kind of modding on my SF.

now I'm just using the original theme...



Ps.: GMA900 here... :mad:

---

### Post by bigred1 on 2008-02-05
I have the same problem -- No 3D graphics from  Intel G33 (GMA 3100)  graphics, which means no Compiz or Google Earth. I have tried everything describd here, and in some other threads on this Forum. 

Even reinstalling Ubuntu didn't help.

Any suggestions?

---

### Post by bigred1 on 2008-02-29
In fact, with this  graphics card (GMA 3100)  problem, I cannot watch movies either -- video comes out grainy .Everything is dark and made of huge pixels.

---

### Post by adityakavoor on 2008-03-04
GMA 3100 is blacklisted

refer [this]("http://wiki.compiz-fusion.org/Hardware/Blacklist") for 3D to work

---

### Post by bigred1 on 2008-04-29
Upgrading to Ubuntu 8.04 TLS (Hardy Heron) did the trick -- the onboard GMA 3100 chip is not recognized, and Compiz works, along with certain 3D programs (like Alien Arena) which failed on an xorg program beforehand. The graininess of video seems to have also been fixed.

---

