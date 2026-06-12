---
title: "Openbox theme gui editor?"
date: 2008-12-23
forum: Arch and derivatives
---

### Post by zephyrus17 on 2008-12-23
I know there's the way to edit it through themerc, but can I edit the themes gui style like emerald?

---

### Post by Rokurosv on 2008-12-23
You could try obconf, you can change styles, fonts and other stuff.

---

### Post by RiceMonster on 2008-12-23
Openbox themes are incredibly simple, just look at the themerc's from different themes, and check out [this](http://icculus.org/openbox/index.php/Help:Themes). Everything is controlled from that one config file, except the button images, but you still assign colors to them in the themerc (I honestly just take button images from other themes). Trust me, it's easy to figure out.

---

### Post by chucky chuckaluck on 2008-12-23
*gedit themerc*

---

### Post by urukrama on 2008-12-23
There is something available somewhere, but it is quite old and doesn't support all the many new themeing options that have been introduced in recent versions of Openbox. If you are interested, I can try and find it again.

As mentioned, though, Openbox themes are very easy to create. Try creating one and you'll be on top of it in no time.

---

### Post by zephyrus17 on 2008-12-23
Do you mean stylebox? Yeah, that's pretty old.

Ok, thanks. :) I guess it's text-based, then..

---

### Post by handy on 2008-12-23
I consider modifying GTK themes to be a pain in the RRRs.

Fiddling around with hex named colours for hours to get it how you want it.

I use [***_Gcolor2_***]("http://gcolor2.sourceforge.net/") to help with the hex to colour, colour to hex translation, it is a huge help.

---

### Post by chucky chuckaluck on 2008-12-24
> **handy said:**
> I use [***_Gcolor2_***]("http://gcolor2.sourceforge.net/") to help with the hex to colour, colour to hex translation, it is a huge help.

one of my very favorite apps. i first started using it a few years ago when i realized gimp's color sampler would not take a sample outside of the current project.

---

### Post by handy on 2008-12-24
> **chucky chuckaluck said:**
> one of my very favorite apps. i first started using it a few years ago when i realized gimp's color sampler would not take a sample outside of the current project.

I'd be lost without Gcolor2 or something else that does the same job.  Changing colours would just be too much of a headache.  How would you do it, with a huge colour chart with hex names under each square of colour?

I don't have GIMP installed, I have no use for it.

One day someone is going to write a little tool that allows us to change the colours of selected parts of our desktops with sliders.

The day I see the release of that will be an historic day for the distros.

Ideally this tool would accept plugins that would enable it to work across other theme environments & not just GTK's.

It is a beautiful dream... :lolflag:

If I new how to program in any of the current languages I'd have a go myself.  But I don't & I'm not interested in learning a new language these days.

---

### Post by urukrama on 2008-12-24
> **zephyrus17 said:**
> Do you mean stylebox? Yeah, that's pretty old.

Yes, that is what I meant.

I always use Agave (instead of gcolor2) when I create or modify Openbox themes.

---

### Post by handy on 2008-12-24
> **urukrama said:**
> 
I always use Agave (instead of gcolor2) when I create or modify Openbox themes.

It was probably you urukrama that told about Agave when I was setting up Openbox. I agree Agave is great too, it is probably even more useful than Gcolor2 for creating theme's. 

I just look at themes created by others until I find one that has colours as close to what my eyes will find relaxing & then spend the time identifying & modifying some of the colour tones until I'm satisfied.  Gcolor2 works well for me in that situation.

---

### Post by K.Mandla on 2008-12-24
+1 to gcolor2, but only a half-hearted +1 to Agave. I resent Gnome implications on such a seemingly simple program.

On the other hand there are lots of web-based color pickers that do the same thing as Agave. So it's no great loss to me. :|

---

### Post by handy on 2008-12-24
I have a vague recollection of dumping Agave due to its dependencies.

---

### Post by zephyrus17 on 2008-12-24
> **handy said:**
> I use [***_Gcolor2_***]("http://gcolor2.sourceforge.net/") to help with the hex to colour, colour to hex translation, it is a huge help.
Isn't it the same if you use the colour thing in the Panel Properties?

---

### Post by handy on 2008-12-25
> **zephyrus17 said:**
> Isn't it the same if you use the colour thing in the Panel Properties?

Dunno' it wasn't part of my Xfce or Openbox installs.

---

### Post by zephyrus17 on 2008-12-25
> **handy said:**
> Dunno' it wasn't part of my Xfce or Openbox installs.
Ahhh... Touche.

---

### Post by handy on 2008-12-25
> **handy said:**
> I have a vague recollection of dumping Agave due to its dependencies.

I just had a look & for me to install Agave on my current setup I would require the following dependencies as well, which would make 34.85Mb total installed size:

Targets (11): libart-lgpl-2.3.20-1  libgnomecanvas-2.20.1.1-2  gnome-mime-data-2.18.0-3  
              gnome-vfs-2.24.0-2  libbonobo-2.24.0-1  libgnome-2.24.1-1  libbonoboui-2.24.0-1  
              libgnomeui-2.24.0-1  libglademm-2.6.7-1  gconfmm-2.24.0-1  agave-0.4.4-2

That would have been why I removed Agave.  

Gcolor2 weighs in at 0.07Mb total installed size & has no added dependencies when installed on my Arch/Xfce system, if I remove Gcolor2 using -Rsn it is the only thing that is deleted as gtk2 is its only dependency.

---

### Post by zephyrus17 on 2008-12-25
I don't have as much problems as you. ;) I use Arch/Gnome.

---

### Post by handy on 2008-12-25
> **zephyrus17 said:**
> I don't have as much problems as you. ;) I use Arch/Gnome.

Which problems are you referring to?

My system is vastly more simple since I rid it of Gnome.

It became so light I had to screw it down to the desktop. ;-)

---

### Post by zephyrus17 on 2008-12-25
> **handy said:**
> Which problems are you referring to?

My system is vastly more simple since I rid it of Gnome.

It became so light I had to screw it down to the desktop. ;-)
hahahaha! That may be, but I think it wouldn't matter much on my computer. Since it's hardware is quite capable of handling gnome with much to spare

---

### Post by mips on 2008-12-25
> **handy said:**
> 
It became so light I had to screw it down to the desktop. ;-)

lol, I just pictured that in my mind :)

---

### Post by handy on 2008-12-25
> **zephyrus17 said:**
> hahahaha! That may be, but I think it wouldn't matter much on my computer. Since it's hardware is quite capable of handling gnome with much to spare

It makes a difference, believe me.

I prefer to run all my machines *light* though my two working machines (apart from those I have  dedicated to running the super light installs - IPCop & FreeNAS) are strong:

One is a dual core intel chipped thing, with 1Gb of RAM & 256Mb on the strong GPU, the other also has a 64bit CPU, single core this time - Athlon 3500+ with a strong nVidia graphic card with 512Mb of RAM on it.

The reason I like to run a lighter than KDE or Gnome GUI interface on top of Arch or whatever, is that it makes it more reliable, it makes is so much simpler to configure or fix if the need arises, it makes it so much easier for me to be more familiar with the files on my computer, which of course works in very well with the points I have already just stated.

& these fairly powerful machines that I run are quite noticeably snappier in their responses than when using either of the two BIG DE's.

I personally don't care what other people use on their computers, just so long as I can use what I choose to. :-)

---

### Post by zephyrus17 on 2008-12-25
Hmm.. That is true. I'll try Xfce next time and see how it is. :)

---

### Post by handy on 2008-12-25
> **zephyrus17 said:**
> Hmm.. That is true. I'll try Xfce next time and see how it is. :)

You can install Xfce on your Arch box now, it will take you about 2 minutes. You can have multiple DE's & WM's installed on a distro.  Try it out, if you decide you do like it & want to get rid of Gnome you can.  I did :) it doesn't create an unstable machine, the pacman system does an excellent job.

***_[http://wiki.archlinux.org/index.php/Xfce](http://wiki.archlinux.org/index.php/Xfce)_***

---

### Post by zephyrus17 on 2008-12-25
Aye. I know. I installed gnome with kde together. But somehow it ruined my gnome main menu. The applications won't appear there. I think I have a thread in Notebookreview.com as well. It's driving me nuts.

---

### Post by Dr Small on 2008-12-26
> **urukrama said:**
> Yes, that is what I meant.

I always use Agave (instead of gcolor2) when I create or modify Openbox themes.
My sister uses Gimp for all her theming. Unfortunately, I can't get her interested in any of the Window managers like IceWM or Openbox. If it doesn't have a menu to easily access her Home Folder, she has no clue how to get to it. :|

I, on the other hand,  have absolutely no artistic touch. Currently, I'm using your theme *Mythos* and think it is beautiful. I love dark themes :D

---

### Post by urukrama on 2008-12-27
> **K.Mandla said:**
> only a half-hearted +1 to Agave. I resent Gnome implications on such a seemingly simple program.

There are several gnome-ish applications I use anyway (gedit with the Latex plugin is probably the most important one), so I have most of these dependencies installed anyway.

Though I'll admit I'm somewhat proud that on my old and slow Dell Inspiron 2500 I don't have any Gnomes :-)

> **Dr Small said:**
> I, on the other hand,  have absolutely no artistic touch. Currently, I'm using your theme *Mythos* and think it is beautiful. I love dark themes :D

Thank you. It is one of my favourite dark themes as well.

---

