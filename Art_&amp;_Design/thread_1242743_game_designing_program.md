---
title: "game designing program?"
date: 2009-08-17
forum: Art &amp; Design
---

### Post by publicladykilla on 2009-08-17
Is there any program for ubuntu that i can design and play a game?

---

### Post by dlmarti on 2009-08-17
You will need to be a lot more specific.
They're are hundreds if not thousands of developer tools for Linux.
Please spell out exactly what you need.

---

### Post by publicladykilla on 2009-08-17
ok well i found what i need... im using blender.. but everytime i start i up it looks all laggy i took a screenshot ....

---

### Post by mcduck on 2009-08-17
> **publicladykilla said:**
> ok well i found what i need... im using blender.. but everytime i start i up it looks all laggy i took a screenshot ....

Make sure you have drivers for your graphics card installed & working correctly, and if Blender is still lagging then disable desktop effects.

Running Blender in full-screen mode might also help a bit.

---

### Post by hessiess on 2009-08-17
Blender requires a decent graphics card with the proper drivers installed. What card do you have?
If you want to create games, you are going to have to learn to program, and have a decent understanding of 3D/2D vector math, 'gui' game builders can only do so much, if you want to do anything specific you will need to implement it yourself.

---

### Post by coldReactive on 2009-08-17
And if Flash 4 Linux was more stable, then you could make flash games.

But no, the last update was in like, 2002.

---

### Post by JustMegawatt on 2009-08-18
You can also install Flash 8 by downloading a program called PlayonLinux and install it from there, it has the file you need to install it from that one program, just saying, flash is probably the most convenient way to program a game,

you can play it on your browser,
games are coded inside flash,
graphics are drawn in flash, 
very convenient, but full screen games are different since they take up more space and are always better than the best flash games

public computers though, (library, etc) can only play games on the browser, and that's what you use flash for!

---

### Post by s.vladimir on 2009-08-18
You probably need to update your graphics card drivers, or you just have a crappy one.
Blender >:guitar:
See if there is one for Linux.
I still have no hard solution for the reason why Blender is laggy. Never happened to me, but I run blender on a mac. :(
Sorry I could not be of great help.

--
Vladimir.

---

### Post by s.vladimir on 2009-08-18
> **mcduck said:**
>   if Blender is still lagging then disable desktop effects.

Yes. Seems that that would help.:KS

---

### Post by publicladykilla on 2009-08-18
im relatively new to ubuntu.. so how do i figure out which graphics card i have and if the drivers are installed properly.....

---

### Post by Fzang on 2009-08-18
If you use the default panel menu it's in System -> Preferences -> Hardware Information

---

### Post by hessiess on 2009-08-18
> **Fzang said:**
> If you use the default panel menu it's in System -> Preferences -> Hardware Information

or open a terminal and run

```

lspci

```

---

### Post by publicladykilla on 2009-08-19
alright i think this is my graphics card. 00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
does that help?

---

### Post by hessiess on 2009-08-19
> **publicladykilla said:**
> alright i think this is my graphics card. 00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
does that help?

Yes that's the problem, Integrated cards suck for 3D performance, If possable buy a dedicated card, preferably Nvidia. Eaven the low-end ones are multiple orders of magnitude faster than any integrated chip.

---

### Post by publicladykilla on 2009-08-19
okay... how much would one of these run?

---

### Post by hessiess on 2009-08-19
> **publicladykilla said:**
> okay... how much would one of these run?

My £50 (couple of years ago) 7600gs will run about 400,000 polygons(quads) in Blender at a usable speed (10-20 FPS), which is plenty unless you are doing very high detailed sculpting.

---

### Post by publicladykilla on 2009-08-19
ok thankss.. is this something i could install myself?

---

### Post by hessiess on 2009-08-19
> **publicladykilla said:**
> ok thankss.. is this something i could install myself?

Asuming you are on a desktop, yes. do you have a PCIE or AGP mobo?

---

### Post by publicladykilla on 2009-08-19
im thinking PCIE

---

### Post by hessiess on 2009-08-19
> **publicladykilla said:**
> im thinking PCIE

Then look for a pcie card, again preferably nvidia ;)

---

### Post by Repgahroll on 2009-08-19
It's a Blender problem; the older versions works well, but you can easily fix this:

Download Blender binary from the oficial website (tar file), and run the "blender-softwaregl" file.

Or, you can add:

Option 		"DRI" 				"off"

to the Device section on xorg.conf, but it's a little bit unstable, it's better to use the first option, the file is a script, so you can make it work with your Blender installation also.

Blender 2.5 will be very GPU-friendly, so we'll be able to run even in some crazy hardware :).

Sorry mine english.

---

### Post by publicladykilla on 2009-08-19
will do

---

### Post by juancarlospaco on 2009-08-19
Don't forget OpenSIM, 
you can build a 3D Game Desing things, without hard to learn skills.
*Its a Open Source Server Side Second Life Clone to run it locally.*

---

### Post by publicladykilla on 2009-08-19
ill look into it thanks

---

