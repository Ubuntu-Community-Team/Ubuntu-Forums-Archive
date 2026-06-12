---
title: "ubuntu gutsy on sony vaio PLEASE HELP!"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by racgus on 2008-03-16
so i'm brand new to linux, and my first exposure to it is ubuntu gutsy gibbon. i must say i'm very happy with this os. it only took me an entire day to figure out the terminal setup process, and at first i hated it but now i kind of prefer cmd prompts to the graphical setup process as it is much faster and gives you a better understanding and appreciation. anyways, i've pretty much figured everything out. BUT the one thing that has got me pulling my hair out is the fact that on initial start up of ubuntu on my Sony Vaio VGN-FS640/w I am able to use desktop effects, but after installing updates, apps, etc. i'm unable to use even the lowest settings for desktop effects. going into restricted drivers manager is a dead end  as there is apparently no restricted drivers available for this laptop, which i find hard to believe. as much as i love this os, i really want the eyecandy that goes along with it. this laptop was running vista prior to ubuntu and was able to support aero. while beryl, i feel, is far superior i should at least be able to make a window wobble! anyways, for a new member and first post i really hope this can be answered and possibly help some others as to figuring out how to get the desktop effects to work with this class of laptop.
thanks in advance,
Gus:)

---

### Post by A4006 on 2008-03-16
If your laptop has a nVidia or ATI graphics card, then you'll be able to use Envy [http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html")
to install the proper drivers for it.  By the way, congratulations on switching over from Vista, it's nice not to have to put up with User Account Control and all of Vistas other "helpful" features :).

---

### Post by racgus on 2008-03-17
worked like a charm...thanks so much. although, i've noticed a few problems with the extra effects. these may be do to the laptops limited abilities but maybe not. the cube for example really isn't a cube at all. it is just a desktop that flips to the next desktop...there is no "cube" not like what is shown by other users. this is the biggest thing i've seen so far but there are more things. either way, the os is still fantastic. starting my next project of getting osXleopard on my vista machine as a dual boot os. we'll see.

---

### Post by jan quark on 2008-03-17
you have to add additional workspaces
so you have 4
to view the cube

---

### Post by racgus on 2008-03-20
that was the first thing i did when i loaded the effects. that was the only thing that made since, but still no cube...:(

---

### Post by billgoldberg on 2008-03-20
> **racgus said:**
> that was the first thing i did when i loaded the effects. that was the only thing that made since, but still no cube...:(

First install the compizconfig effects manager (use system->administration -> synaptic package management).

Then go to "system -> preferences -> advanced desktop effects setting".

Go to "general options".

Go to the "desktop size" tab.

change the "horizontal virtual size" to 4 (don't use the slider for that just type it)

Also enable these effects (besides desktop cube):
 
- rotate desktop
- cube caps
- cube reflection (optional, but it looks better)

(using the cube: hold the scroll wheel on your mouse and move the mouse, or use "ctrl+alt+left click" or use "ctrl+alt+down arrow" or use "ctrl+alt+left or right button".)

That will do the trick.

note:

If you are into eye candy, you might want to enable these effects:

- expo (enabled by default, but you should set a "screen edge" for it under it's action tab).
- animations 
- trailfocus (makes non used windows transparent after a while)
- wobbly windows (this will also enable you to drag your windows to other desktops in the "expo" plugin).
- shift switcher (this will either give you the vista aero switcher or the mac osx coverflow switcher if you use "super+tab" (super is the meta key aka the key where the windows logo is on on most keyboards).

And you might want to consider using emerald to give you windows borders (download it using synaptic, and access it under "system -> preferences -> emerald manager").

You can download allot of emerald themes on gnome-look.org under "beryl or compiz".

To use them, import them in the emerald manager, double click them, press "alt+f2" and type "compiz --reconfigure" (or log out and back in).

---

