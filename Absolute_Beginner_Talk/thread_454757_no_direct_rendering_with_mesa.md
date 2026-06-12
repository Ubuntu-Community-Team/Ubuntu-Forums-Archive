---
title: "no direct rendering with mesa"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by lordcrimmeh on 2007-05-25
Alright, i took the plunge and installed unbuntu and beryl once again (was itching for some nice visual effects). I loved how it turned out, and would like to get it working again.  

Last night, when i had beryl working, when i used

glxinfo | grep vendor

it displayed:

server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.

(and direct rendering: Yes)

and beryl worked fine. Now, i get a white screen (no desktop, yet i can switch around cube) whenever i load on beryl. Ubuntu works fine on gnome (using it now). Now, when i do

glxinfo | grep vendor

it displays

server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)

and when i use

glxinfo | grep "direct rendering"

i get

direct rendering: No

... Needless to say, my card works with Tungsten, but not with mesa (on my previous, noncompatible with beryl installation it always loaded mesa as well, and no direct rendering/beryl)

i love beryl, but if the driver vendor is going to change at random i'm not going to use ubuntu...

Notes: using ati radeon x800pro with Radeon driver (will post xorg.conf if needed)

---

### Post by overdrank on 2007-05-25
> **lordcrimmeh said:**
> Alright, i took the plunge and installed unbuntu and beryl once again (was itching for some nice visual effects). I loved how it turned out, and would like to get it working again.  

Last night, when i had beryl working, when i used

glxinfo | grep vendor

it displayed:

server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.

(and direct rendering: Yes)

and beryl worked fine. Now, i get a white screen (no desktop, yet i can switch around cube) whenever i load on beryl. Ubuntu works fine on gnome (using it now). Now, when i do

glxinfo | grep vendor

it displays

server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)

and when i use

glxinfo | grep "direct rendering"

i get

direct rendering: No

... Needless to say, my card works with Tungsten, but not with mesa (on my previous, noncompatible with beryl installation it always loaded mesa as well, and no direct rendering/beryl)

i love beryl, but if the driver vendor is going to change at random i'm not going to use ubuntu...

Notes: using ati radeon x800pro with Radeon driver (will post xorg.conf if needed)

Hi and welcome I am assuming that you are using feisty 7.10 so if you follow this thread
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)
It should get your drivers installed. Good luck! ;)

---

### Post by icechen1 on 2007-05-25
> **overdrank said:**
> Hi and welcome I am assuming that you are using feisty 7.10 so if you follow this thread
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)
It should get your drivers installed. Good luck! ;)
Follow that guide f you have an ati card.
BTW:You mean 7.04?7.10 is not out yet.

---

### Post by lordcrimmeh on 2007-05-25
most tutorials i have read on ati cards say to uninstall fglrx (closed driver doesnt support beryl/direct rendering well) and that tutorial is telling me to install that driver. 

So what should i do, follow those directions to install/update the fglrx driver, then uninstall and procede with beryl? i am a little confused as to why it worked last night, but not now.... is there any way to force it to use Tungsten instead of Mesa as vendor?

---

### Post by overdrank on 2007-05-26
> **lordcrimmeh said:**
> most tutorials i have read on ati cards say to uninstall fglrx (closed driver doesnt support beryl/direct rendering well) and that tutorial is telling me to install that driver. 

So what should i do, follow those directions to install/update the fglrx driver, then uninstall and procede with beryl? i am a little confused as to why it worked last night, but not now.... is there any way to force it to use Tungsten instead of Mesa as vendor?

Hi I wish I was able to help more on feisty but as you can see I can not even get the numbers right ( 7,04 instead of 7.10) ;). I can offer you this link I found to maybe help you
[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)
There is a couple of ways to use beryl with the ati cards one is both are mention in the link and it tell you how to install AIGLX. I myself use the XGL in edgy and I like it so it is up to you it which works for you. Hope this helps and Good luck!:popcorn:

---

### Post by lordcrimmeh on 2007-05-26
That is actually the tutorial i used. Problem is, i turned off the computer that night, and when i went back on in the morning, the vendor displayed for the graphics (and the status of direct rendering) changed overnight, leaving me without beryl...

---

### Post by Kubunteando on 2007-05-27
Can you post the file /var/log/Xorg.0.log ?
That should give some idea what is wrong...

---

### Post by lordcrimmeh on 2007-05-28
Sorry for the zipped attachment, but the character limit and the .txt size limit was in my way. Zip will have to do...

Anyway, when i logged on today, the vendor had switched back to tungsten (and i had Direct Rendering: Yes again)... I launched beryl after login and it worked again, but it isnt permanent, so it wont do...

---

### Post by lordcrimmeh on 2007-06-09
From what I've read, what it comes down to is this:

Many newer Radeon cards fail to work with direct rendering due to issues with Mesa rendering using only indirect rendering. Older cards have success with direct rendering with Mesa and/or Tungsten rendering.

My card is just new enough that it doesn't work with Mesa (well) but it DOES work with Tungsten.

The problem here is that each time i start up, i don't know which one it will choose. Sometimes I end up with Mesa (no direct rendering, no beryl) and sometimes I end up with Tungsten (Direct Rendering: Yes, beryl yes).
...
...
I have heard bad things about using fglrx with beryl, so i am wanting to stick with aiglx, but i need a way to fix the render-er as Tungsten, so i don't to restart multiple times every time I get unlucky and end up with Mesa.

---

