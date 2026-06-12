---
title: "a bit OT: compiz fusion on macbook?"
date: 2007-06-24
forum: Apple Intel Users
---

### Post by kzm. on 2007-06-24
hey, you guys aware of this [thread]("this: http://ubuntuforums.org/showthread.php?t=480377")??
anybody tried this on his/her macbook?

---

### Post by david_edmundson on 2007-06-24
I have, it's a little big sluggish on my machine. Probably the fault of the GMA950 graphic card. Other than that it's all good, looks very very shiny. Someone posted in this forum about speeds up for the older compiz/bery, I'm sure they'll still apply.

---

### Post by ivesjd on 2007-06-24
First off, could you edit your link so that "this:" isnt in it? :P 
Now, I have installed Compiz Fusion, and it works pretty well, although I'm having problems getting it to run right. They are mostly my fault. What I think would work better is if you arent running beryl have it all uninstalled (if it was) and then start over. Although, I have been told that you need emerald for compiz fusion to run.

---

### Post by adityakavoor on 2007-06-24
> **ivesjd said:**
> First off, could you edit your link so that "this:" isnt in it? :P 
Now, I have installed Compiz Fusion, and it works pretty well, although I'm having problems getting it to run right. They are mostly my fault. What I think would work better is if you arent running beryl have it all uninstalled (if it was) and then start over. Although, I have been told that you need emerald for compiz fusion to run.

Did you get the cube working in compiz-fusion ?? 
can you please paste the install instructions and cube enable instructions ..:confused:

---

### Post by ivesjd on 2007-06-24
[http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)
that is the how to I used, and the cube works out of the box for me.

---

### Post by Gen2ly on 2007-06-24
Friday I tried to compile from sources without success, it's still very very much an alpha or beta state.  The progress on it is incredible.

---

### Post by ivesjd on 2007-06-24
I give up on trying to get it to start on boot. I just run the command ```
compiz --replace -c emerald & 
``` so that works for now, I guess

---

### Post by adityakavoor on 2007-06-24
> **ivesjd said:**
> [http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)
that is the how to I used, and the cube works out of the box for me.

Installation went on smooth but .. I can find only 1 workspace :( .. How can increacse them to 4 ??

---

### Post by ivesjd on 2007-06-25
Type ccsm in terminal. Then go to general options. Then Desktop Size and increase the horizontal size slider. DO NOT INCREASE NUMBER OF DESKTOPS

---

### Post by pveith on 2007-06-25
just installed compiz fusion on macbook with Ubuntu 64Bit. Works quite well, but one thing is quite annoying. The gnome-applet to switch Desktops displays 2 frames, if used them i get the next 4 Cube Desktops for both frames. With pure Beryl i had one wide display for all four virtual-cubed desktops. Is this normal for compiz or do i have to configure it somewhere?

Additionally here is how i start compiz with emerald:
```

LIBGL_ALWAYS_INDIRECT=1 compiz --replace --indirect-rendering --sm-disable ccp &
emerald --replace &

```

---

### Post by ivesjd on 2007-06-25
> **pveith said:**
> just installed compiz fusion on macbook with Ubuntu 64Bit. Works quite well, but one thing is quite annoying. The gnome-applet to switch Desktops displays 2 frames, if used them i get the next 4 Cube Desktops for both frames. With pure Beryl i had one wide display for all four virtual-cubed desktops. Is this normal for compiz or do i have to configure it somewhere?

Additionally here is how i start compiz with emerald:
```

LIBGL_ALWAYS_INDIRECT=1 compiz --replace --indirect-rendering --sm-disable ccp &
emerald --replace &

```

You got Fusion running on 64bit? From what I had heard that it didnt work. 

Go into the config manager, and go to general, and then desktop size, set the horizontal size to 4 (if you want a cube) and then the number of desktops to one.

How did you figure out to use that code to start it?

edit/ I tried you code as a start-up option and it booted into metacity. \edit

---

### Post by adityakavoor on 2007-06-26
> **ivesjd said:**
> Type ccsm in terminal. Then go to general options. Then Desktop Size and increase the horizontal size slider. DO NOT INCREASE NUMBER OF DESKTOPS

thanks

---

### Post by pveith on 2007-06-26
> **ivesjd said:**
> You got Fusion running on 64bit? From what I had heard that it didnt work. 

Go into the config manager, and go to general, and then desktop size, set the horizontal size to 4 (if you want a cube) and then the number of desktops to one.

How did you figure out to use that code to start it?

edit/ I tried you code as a start-up option and it booted into metacity. \edit


How i did it: use this site: [http://forums.opencompositing.org/viewtopic.php?f=51&t=758](http://forums.opencompositing.org/viewtopic.php?f=51&t=758)

First build the compile environment:
```
sudo apt-get install git-core automake build-essential intltool libtool python-pyrex python2.5-dev checkinstall

sudo apt-get build-dep compiz

sudo apt-get remove emerald

```

Second let'e get the sources (got to a sane directory either in you home or in /usr/src/) and get all sources as described below:
```
git clone git://git.freedesktop.org/git/xorg/app/compiz
git clone git://anongit.opencompositing.org/fusion/libraries/bcop
git clone git://anongit.opencompositing.org/fusion/compizconfig/ccsm
git clone git://anongit.opencompositing.org/fusion/compizconfig/libcompizconfig
git clone git://anongit.opencompositing.org/fusion/compizconfig/compizconfig-python
git clone git://anongit.opencompositing.org/fusion/plugins-main
git clone git://anongit.opencompositing.org/fusion/decorators/emerald
git clone git://anongit.opencompositing.org/fusion/decorators/emerald-themes

```

Go into all Subdirs and configure and build them. You find lots of dirs in your directory so here is what has to be done for compiz.
```
cd compiz
./autogen.sh --prefix=/usr/local --enable-librsvg --disable-kde
sudo checkinstall

```
During Checkinstall you will have to change the version-number to a sane value. For the compiz package use 1:X.X.X to make sure that is won't be overwriten by the updatemanager. For all other packages use the given number (which will already be present, but unfortunetaly multiple time).
[If this is to adventourous for you then simply use "sudo make install" instead of checkinstall.]

Do the same for all directories in a logical order (e.g. emerald before its plugins). I have problem with compiz-icon...

forth: create a CompizStart file
```
LIBGL_ALWAYS_INDIRECT=1 compiz --replace --indirect-rendering --sm-disable ccp &
emerald --replace &

```
And make this file executable (chmod +x <filename>) and voila you should be able to start compiz-fusion on macbook (with intel graphicadapters).

That's is allready. 

Please keep in mind that this is for advanced user, who can cope with compile failures and life on with some break downs.

@ivesjd: Here ist the source for all my action: [http://forums.opencompositing.org/viewtopic.php?f=51&t=758](http://forums.opencompositing.org/viewtopic.php?f=51&t=758) . See step 4 for the startup.

So that's what i did to get it running. For some strage reason the Desktopswitcher continues to annoy me. Alle settings in ccsm are correct (Cube works like a charm), but the applet just displays the metacity Desktop i suppose...

---

### Post by ivesjd on 2007-06-26
@pveith: Do you have more the one desktop set in CCSM? Horzitontal size can be any, but the desktop number has to be one. That is also a very nice guide for 64bit.

---

### Post by pveith on 2007-06-27
@ivesjd: No cssm says that the destop is set to 4 horizontal, 1 vertical and 1 # of Desks. It seems that the applet is not updated correctly.

Solved: Saved a new profile and switched back to the default profile. This seems to repair the applet somehow. Had to redo the profile-switching after reboot.

---

### Post by ivesjd on 2007-06-27
Sometimes things make no sense.

---

### Post by Gen2ly on 2007-06-27
Nice post complete and detailed.  I always prefer compiling when I get to it.  Course, I'm having one of those, failure uses, is as when working directly from source.  I'd say this could be one of those post we put in the Stickies but I am afraid it wouldn't last long.

---

### Post by pveith on 2007-06-28
Actually i like compiling from source, too (used to build my own kernels to keep them as small as possible, but that was a too time consuming hobby). But keeping self-compiled programs up to date is a mayor pain in the backside. So if there are good repositories for the programs need, i use them. Compiz-Fusion on 64Bit lacks these repos and therefore i used the chance to get into my old hobby. I was even too lasy to enter all dependencies for the packages into checkinstall...

Another good example is the madwifi driver, just yesterday i though "Is my madwifi installation up to date?" and went to their website. And voila there was a new version with lots of fixes and now my wireless works a little better (better connection-range). This could have been automated by a good repro...

This post is just intended to be a hint for those who just want their programs to work: Use repositories you trust and let them take care of the updates / compiling.

---

### Post by luisbg on 2007-06-29
I run compcomm (aka compiz fusion) very happily in my macbook, it runs very smooth.

I just added a source in my apt and apt-get installed a few packages as explained in...
[http://forums.opencompositing.org/viewtopic.php?f=14&t=131&hilit](http://forums.opencompositing.org/viewtopic.php?f=14&t=131&hilit)

The good thing about this method is that the packages are updated every now and then, so they appear in your apt upgrades.

luis

---

