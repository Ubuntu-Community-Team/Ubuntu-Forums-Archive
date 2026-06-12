---
title: "Best all around medi player for Linux?"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by Endow on 2006-07-09
So I want to play .wmv files.I installed VLC player but for some reason I only get sound and no video....


What's the best all around media player for Linux?Or is VLC a good choice? - if so what can i do to enable video (PS:If i go to "Video" on VLC I see that it is disable to i select track 1 but I still get nothing...)


Oh and btw possible related : how can I know if I have graphic acceleration enabled or not?I'm using Dapper Drake 64bit and I have nVidia 6600GT graphic card.


Thanks :)

---

### Post by woedend on 2006-07-09
did you install an nvidia driver?  if not, you do not have accelleration as ubuntu by default does not use it.
my vote goes to mplayer, by the way.

---

### Post by siccness on 2006-07-09
I'm a fan of VLC over here, although mpg321 for music.

---

### Post by Endow on 2006-07-09
What's the simplest way for me to install the driver then? (from what I understand the video problem IS realted to the lack of nvidia driver right?)...


But that reminds me (im not much of a computre expert) :how can I have graphics then if my graphic card isn't beeing recognized by Ubuntu?Is the CPu doing all the calculations??

---

### Post by IrishGangsta on 2006-07-09
I have a similiar problem.
I have the totem xine enabled i beleive. 
I have Dapper 6.06 and i can see video but do not heaer it.
I do know that my sound card works b/c i hear songs.

Any suggestions?

---

### Post by siccness on 2006-07-09
> **Endow said:**
> What's the simplest way for me to install the driver then? (from what I understand the video problem IS realted to the lack of nvidia driver right?)...


Simplest way? Probably using EasyUbuntu ([http://easyubuntu.freecontrib.org/get.html](http://easyubuntu.freecontrib.org/get.html))

---

### Post by woedend on 2006-07-09
i like tseliots script
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html)

youll want to scroll down to the dapper drake section and get the 64 version of the latest driver.  Its a script, you kill gdm/X, run it, it does all the work for you (except, I think, in your /etc/X11/xorg.conf you must change driver to "nvidia" if i'm not mistaking!)

---

### Post by Endow on 2006-07-09
Well according to Easy Ubuntu my nvidia dirver is installed (I had already ran easyubuntu once) so what might be my problem?

---

### Post by richbarna on 2006-07-09
> **woedend said:**
> 
my vote goes to mplayer, by the way.

Lol, just like the poll in the cafe ;), and who won that ?................
AMAROK !! yay!

No but seriously, for videos I use MPlayer and it works sweet as long as you have got the restricted format codecs installed.

And as woedend said, get the nVidia acceleration sorted out.

---

### Post by woedend on 2006-07-09
i am convinced that you fixed the amarok poll in desperation...and thats fine if you need it that bad I figured i'd let it go.  Everyone knows xmms is superior.

---

### Post by Endow on 2006-07-09
> **richbarna said:**
> And as woedend said, get the nVidia acceleration sorted out.

I AM asking for help :p

---

### Post by -deadcats on 2006-07-09
> **Endow said:**
> Well according to Easy Ubuntu my nvidia dirver is installed (I had already ran easyubuntu once) so what might be my problem?

Well, if the driver is installed, let's see if direct rendering is implemented.

Pull up a terminal and type "glxinfo | grep direct"

If it's implemented, it will say yes. If not, then type "glxinfo" and give us a copy of your output. We can help you from there.

regards,
-dc

---

### Post by Endow on 2006-07-09
When I typed "glxinfo | grep direct" I got  > Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".



When I type "glxinfo" I get... > name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None


---

### Post by -deadcats on 2006-07-09
So it appears your Nvidia driver may not be installed after all?

Here's what I'd do:
1. Open up Synaptic
2. Search for "linux" and make sure I had the restricted modules kernel installed for my processor.
3. Search for "nvidia" and select the nvidia-glx, nvidia-kernel-source and nvidia-kernel-common for installation.
4. As a matter of course (though I don't think they're needed with this type of install), I also install gcc and g++ along with make.
5. After installing any needed files, I'd open up xorg.conf, "sudo gedit /etc/X11/xorg.conf" and delete the line under Section "Module" that says "dri". Or at least comment it out.
6. Change the line for my Nvidia 6600GT card that says Driver from "nv" to "nvidia".
7. Save the file, reboot, and look for an Nvidia splash screen.

THEN I'd type "glxinfo | grep direct" and the response should be "yes." THEN I'd know the drivers for my card were fully installed, and I should have full hardware rendering.

The problems I've seen with some scripts--Automatix, as an example--is that they offer to install the Nvidia driver, but do so for only the 386 modules. And to do that, they also have to install the 386 kernel. Well fooey-on-that, I use the 686-SMP kernel! So I always have to install the Nvidia driver from Synaptic or hand-install it in a terminal. Anyway, not having used the script you are, I can't say for certain that this is part of your problem with your x64 cpu, but it likely is. Nonetheless, the solution I gave you should get you up and running! :)

regards,
-dc

P.S. My vote goes to MPlayer, in ANY distro. :)

---

