---
title: "Black Nautilus and Menus"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by ozPATT on 2007-10-18
Hi All, 

Upgraded to gutsy this morning, and st upt he desktop effects. Finding now that i seem to be getting either the main menus totally black, but still work, o maybe black background and black text? but that comes and goes, but at the moment Nautilus is totally black... Any ideas on what could be causing this? Im sure it wasnt black before, so think it is random as well, but any ideas on fixing it would be great :D 

Thanks

Patrick

---

### Post by ozPATT on 2007-10-18
Morning all, this problem actually extends a bit further, this morning I opened a document in OO without any problems, then went to open another, and its just black. 

I also tried to open gphpedit and same thing there... anyone else experiencing this? Im on a compaq presario v3000 laptop. 

Now my thunderbird is the same, and evince.. menu went this morning, but is back now. I have compiz-manager installed, not sure if this has anything to do with it? Everything seems to be working fine otherwise, and when they arent black they are fine, but just this random thing... 

Thanks! :D 

Patrick

---

### Post by wilksm on 2007-10-19
> **ozPATT said:**
> Morning all, this problem actually extends a bit further, this morning I opened a document in OO without any problems, then went to open another, and its just black. 

I also tried to open gphpedit and same thing there... anyone else experiencing this? Im on a compaq presario v3000 laptop. 

Now my thunderbird is the same, and evince.. menu went this morning, but is back now. I have compiz-manager installed, not sure if this has anything to do with it? Everything seems to be working fine otherwise, and when they arent black they are fine, but just this random thing... 

Thanks! :D 

Patrick
Patrick,

I'm having the same trouble with various windows.  Acrobat does this, but only if the window size is over a certain amount.  Also, the gnome-terminal app shows a transparent window contents if I make the window bigger than a certain size as well...

Matt.

---

### Post by ozPATT on 2007-10-20
Hey glad to hear im not the only one, even though it doesnt solve the problem. I have found it only seems to happen after my computer has been on for a bit. If I CTRL+Backspace, then log in again, it is all back to normal for a while. Which makes me wonder if there is some memory issue, or temperature or something? No idea how that might be related, but they are the 2 things that come to mind...

Thanks

Patrick

---

### Post by celticbhoy on 2007-10-20
Should be easy to tell if it memory prob, just run the memtest at boot-up.

---

### Post by ozPATT on 2007-10-21
how do i do that?

alright, the plot thickens, and makes me think it is a memory issue... 

I just tried to compose a new email in thunderbird, and it came up with the black screen. However, if I closed firefox, then tried to compose, there was no issue. 

Similarly, while the compose window was open, if I tried to open firefox, it came up blank. If I closed the compose window, then opened firefox, it worked. 

I have about 4 windows open, email, ftp, text editor and browser, so I am thinking that having them all open is causing some memory error? Which is weird cos I have 2Gb RAM in this baby, with 80Gb HDD, and have never experienced this before.. 

Any help would be really useful as I was restarting X at least once every hour, but now i know i just need to shut down an application or two, that saves restarting, but it is still very much an inconvenience... 

Thanks

Patrick

---

### Post by wilksm on 2007-10-22
> **ozPATT said:**
> alright, the plot thickens, and makes me think it is a memory issue...

Yeah, that makes sense from what I am seeing too.  I'll have a few fairly large (100x56) gnome-terminals open no problem, and then I open a fourth and the new one goes black when I make it the same size as the others.  I have a 2.6 Ghz P4 with 1GB of RAM.

---

### Post by gimmic on 2007-10-22
I've got the same problem. After a while I will start getting blank terminal windows, black menus, or black windows. I'm guessing it's a memory issue, as if I re-launch compiz it works fine for a while.

---

### Post by FuturePilot on 2007-10-22
I'm guessing you have a Nvidia card. This is a bug with the driver.

---

### Post by gimmic on 2007-10-22
> **FuturePilot said:**
> I'm guessing you have a Nvidia card. This is a bug with the driver.

Is there currently a workaround?

---

### Post by T_W on 2007-10-22
I bumped into this.  Here is what I found:

I found the following post:

[http://ubuntuforums.org/showpost.php?p=3520895&postcount=6](http://ubuntuforums.org/showpost.php?p=3520895&postcount=6)

> NVIDIA

After a while, windows begin to go black

This is the infamous Black-Window Bug with the NVIDIA driver. It is caused by the graphics card running out of texture memory, and therefore all remaining windows (which are textures) will be black. If you have less than 128MB of video memory, disabling blur, and launching Compiz with --indirect-rendering will reduce the appearance of the bug.

So I disabled the blur plugin and set compiz to use --indirect-rendering.  To do this I changed the /usr/bin/compiz script to:

```

# Enable indirect to bypass NVidia black window problem
# INDIRECT="no"
INDIRECT="yes"
```

After doing those two things I have been running fine.  Hope this helps.

---

### Post by ozPATT on 2007-10-22
what is the blur plugin? how do i disable that? will i still have cool fancy things working? Always one for a bit of eye candy ;)

hey i think changing indirect to yes may have resolved the issue... it seems to be loading faster now, and i have just opened 11 windows full screen, and have no issues yet... will wait to see if that changes after a while, but hopefully that has fixed it... 

if so, what is that INDIRECT actually doing because it all seems to look and work the same as before i did that?

Thanks

Patrick

---

### Post by T_W on 2007-10-22
System/Preferences/Advanced Desktop Effects Settings

Uncheck Effect/Blur Windows


[http://dri.freedesktop.org/wiki/IndirectRendering](http://dri.freedesktop.org/wiki/IndirectRendering)

Indirect Rendering

> When OpenGL commands are packaged up with the GLX library and transported across a network pipe (even if that network pipe is local) it is termed Indirect Rendering.

In essence, I think we are telling compiz to use the *indirect* part of AIGLX (Accelerated **Indirect** GLX), which causes OpenGL to be sent via the X11 protocol.

In my reading, this seems to relax the memory stress places upon the NVidia graphics card.

In reality, the only difference is some compiz plugins (like Water), may not work.

---

### Post by nchase on 2007-10-22
This bug has totally disappeared for me since I got the latest version of nvidia's drivers.

I could swear that the bug doesn't exist in the nvidia driver included in the restricted drivers manager in ubuntu 7.10.

---

### Post by Endolith on 2007-10-23
> **nchase said:**
> This bug has totally disappeared for me since I got the latest version of nvidia's drivers.

I could swear that the bug doesn't exist in the nvidia driver included in the restricted drivers manager in ubuntu 7.10.

It's still there.  :-)  I am going to see about the indirect rendering.

...

Seems to fix the black windows, but other things still have issues.  I'll see what I can find.

Here's a whole bunch of stuff.

[http://forum.compiz-fusion.org/showthread.php?t=1762](http://forum.compiz-fusion.org/showthread.php?t=1762)

---

### Post by ozPATT on 2007-10-23
it seems to have fixed things for me... how do you use plugins with compiz?

---

### Post by T_W on 2007-10-23
The plugins should be automatically installed.

If you have not already done so, install the "CompizConfig Settings Manager"

```
sudo apt-get install compizconfig-settings-manager
```

This will add an "Advanced Desktop Effects Settings" control panel under System/Preferences.

You can disable/configure plugins here.

---

### Post by ozPATT on 2007-10-23
wow thats pretty crazy... are there any instructions on using these things? like water effect and/or flames etc, it doesnt say exactly what they do or if i have to do anything or hold any buttons to make them work?

sorry thats a bit off topic... last post on it :D

---

### Post by Endolith on 2007-10-23
> **ozPATT said:**
> wow thats pretty crazy... are there any instructions on using these things? like water effect and/or flames etc, it doesnt say exactly what they do or if i have to do anything or hold any buttons to make them work?

sorry thats a bit off topic... last post on it :D

There is some information on the wiki, but even that is weak on documentation.  I wish there were more.

[http://wiki.compiz-fusion.org/Plugins](http://wiki.compiz-fusion.org/Plugins)

---

### Post by ozPATT on 2007-10-23
actually i found the actions thing in the settngs manager, so had a look at that, and all seems to be sorted now. :D I love ubuntu :D haha its so cool... thanks for your help with all this, so I guess now if i get black screen its cos i have enabled too many things!! haha

---

### Post by gimmic on 2007-10-23
The problem with indirect rendering is you seem to take quite a performance hit. I wish nvidia would just fix whatever bug there is with the drivers..

---

### Post by Endolith on 2007-10-23
> **gimmic said:**
> The problem with indirect rendering is you seem to take quite a performance hit.

Mine has never really been great performing in the first place.  You would think that offloading graphics to a dedicated graphics processor would make the GUI respond more smoothly, but it actually slows things down.  I don't get it.

> I wish nvidia would just fix whatever bug there is with the drivers..

Are you sure it's a bug with the drivers?  I know the black windows are caused by the graphics card running out of memory.

---

### Post by FuturePilot on 2007-10-23
Yes, it's a bug with the driver. Specifically how it handles the GLX_EXT_texture_from_pixmap extension. As VRAM starts to run low, textures don't get redrawn and result in black windows. However the 100.14.19 driver has almost fixed this problem entirely. But if your card isn't supported by this driver, you're kind of out of luck as of now as the 96xx driver still has this problem.

---

### Post by Endolith on 2007-10-23
> **FuturePilot said:**
> Yes, it's a bug with the driver. Specifically how it handles the GLX_EXT_texture_from_pixmap extension. As VRAM starts to run low, textures don't get redrawn and result in black windows. However the 100.14.19 driver has almost fixed this problem entirely. But if your card isn't supported by this driver, you're kind of out of luck as of now as the 96xx driver still has this problem.

Is that the nvidia-glx-new?  I have that installed and I'm still seeing the black windows without indirect rendering.

---

### Post by FuturePilot on 2007-10-23
> **Endolith said:**
> Is that the nvidia-glx-new?  I have that installed and I'm still seeing the black windows without indirect rendering.

If you're using Feisty, no. If you're using Gutsy yes.
Feisty has the 9755 driver as nvidia-glx-new
Gutsy has 100.14.19 as nvidia-glx-new

---

### Post by T_W on 2007-10-23
I was getting black rectangles rather quickly with Gutsy.  Sometimes just a handful of windows.

---

### Post by T_W on 2007-11-07
This problem has gotten dramatically worse on my system.   In some cases, with only two windows, I am getting black rectangles.

I have disabled compiz.

I did recently install the recent compiz upgrades FWIW.

Anyone else having issues?

---

### Post by Endolith on 2007-11-07
> **FuturePilot said:**
> If you're using Feisty, no. If you're using Gutsy yes.
Feisty has the 9755 driver as nvidia-glx-new
Gutsy has 100.14.19 as nvidia-glx-new

Yes, Gutsy, and it still has the problem.

---

### Post by T_W on 2007-11-07
I found the source of my regression.

The compiz update rewrote the /usr/bin/compiz script and turned indirect rendering back off.

---

### Post by T_W on 2008-03-31
Update:  The hard drive on my laptop crashed and I had to reinstall.  After the reinstall, I simply left the compiz settings on "Normal" visual effects (Appearance Control Panel/Visual Effects/Normal).

At this level of visual effects, I do not get the black rectangle problem.

---

