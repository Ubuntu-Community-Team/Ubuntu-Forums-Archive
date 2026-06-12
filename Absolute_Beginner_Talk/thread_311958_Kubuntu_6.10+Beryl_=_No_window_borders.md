---
title: "Kubuntu 6.10+Beryl = No window borders"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by mesilikas on 2006-12-03
Help
I just installed Beryl and XGL and, whenever I enable it, I have no window borders (no title bar, no borders to click-drag for resizing)? The other effects and everything else work fine? Anyone know what's wrong?

My system:
Kubuntu 6.10 Lang. greek and Beryl Manager 0.1.3 cvn
Celleron 2.66 Ghz
Graphic card: MSI Nvidia FX5200 and beta driver
Ram 768 Mb
Thanks

** sorry no 2.66 Mhz

---

### Post by jordanmthomas on 2006-12-03
How do you start beryl? (beryl-start, beryl-manager, etc)
Did emerald build correctly for you?
Is emerald running?
```
 ps -A | grep emerald
```
Does beryl complain if you start it on a command line?

**oh, and I don't think a 2.66 Mhz computer would run Beryl. :D

---

### Post by kakalaky on 2006-12-03
I had the same problem.  For my install (edgy, aiglx, beryl, nvidia) I had to add 'Option "AddARGBGLXVisuals" "true"' to the Device section in xorg.conf instead of Screen to make it work.

---

### Post by Azakus on 2006-12-03
Get rid of XGL. It causes nothing but problems with Beryl 0.1.2. I'm using Beryl on AIGLX and nVidia 1.09XXX drivers and it works perfectly.
Also, try using a stable version of Beryl and see if you get the same problems. I had issues similar to yours with the 0.1.3 svn code because I couldn't get emerald to compile right.

---

### Post by kakalaky on 2006-12-03
If you want to use svn, just add the repo here:

[http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/SVN_Snapshots_Repository]("http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/SVN_Snapshots_Repository")

---

### Post by Azakus on 2006-12-03
The real issue is that I just want Beryl to work. The SVN code is still very beta, and can cause some "interesting" crashes. I know, because I tried the svn of 0.1.2 and it was rather annoying. I like stable Beryl rather than more-fun-yet-flaky Beryl.

---

### Post by DarkN00b on 2006-12-03
> **jordanmthomas said:**
> *snip*
**oh, and I don't think a 2.66 Mhz computer would run Beryl. :D

Ha! Here's my specs:

Intel Celeron M @ 1.3GHz
256 GB ram
Intel 82852/855GM/GME integrated graphics chipset.

Looks really cool and runs smoothly. :p

---

### Post by jordanmthomas on 2006-12-04
> Intel Celeron M @ 1.3GHz
256 GB ram

1.3 GHz > 2.66 Mhz
Mine is only 1.5 GHz and it's fine, I was just making a joke of a typo.

And that's a lot of ram you have there!  Heh heh

---

### Post by DarkN00b on 2006-12-04
D'oh! Ya got me. I completely missed the first typo and made one of my own. I only wish I had that much ram. LOL.

---

### Post by mesilikas on 2006-12-04
> **kakalaky said:**
> I had the same problem.  For my install (edgy, aiglx, beryl, nvidia) I had to add 'Option "AddARGBGLXVisuals" "true"' to the Device section in xorg.conf instead of Screen to make it work.

I thank for your interest the problem it does not exist anymore thanks to the above command! 
;) Greetings by Greece.

---

### Post by kilou on 2006-12-05
Hi,

I have the exact same problem (no windows border with Beryl) but I don't really understand exactly what command should be added to xorg.conf. Could you please post a screenshot of your xorg.conf file for comparison?

Thanks a lot!

---

### Post by kakalaky on 2006-12-05
I'm not at that comp at the moment, but the section you are looking for will have something like this (you will probably have more lines in this section than I put here, don't worry about that):

```
Section "Device"
    Identifier   "GeForce FX"
    Driver       "nvidia"
EndSection
```

just add the following after driver to what you have and it should work:

```
Option "AddARGBGLXVisuals" "true"
```

It should end up looking something like this:

```
Section "Device"
    Identifier   "GeForce FX"
    Driver       "nvidia"
    Option "AddARGBGLXVisuals" "true"
EndSection
```

---

### Post by kilou on 2006-12-05
Thanks. This did not work on mine probably because I ave an Intel integrated GPU. However I could solve the problem by starting emerald with the command "emerald --replace" (in System/preferences/sessions/startup programs).

---

### Post by qiemem on 2006-12-10
Thanks guys! Had the same problem. This worked perfectly for me.

---

### Post by daller on 2006-12-19
I can't get beryl running right... (the border is missing in Kubuntu)

here is what I did:

Installed beryl from the repos...

added this to xorg.conf:

```
Option "AddARGBGLXVisuals" "true"
```

ran: 

```
emerald --replace
```

and:

```
daniel@dallap:~$ beryl
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
Initiating splash
beryl: water: GL_ARB_fragment_program is missing
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
beryl: No GLXFBConfig for depth 32
No framebuffer_object support! (only simple blur aviable)
No fragment_program support! (only simple blur aviable)
Reloading all options.

```

---

