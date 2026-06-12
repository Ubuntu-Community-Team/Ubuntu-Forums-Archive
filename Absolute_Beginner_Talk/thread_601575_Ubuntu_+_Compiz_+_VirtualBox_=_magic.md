---
title: "Ubuntu + Compiz + VirtualBox = magic"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by P4man on 2007-11-03
Made a little video to show off the combination of ubuntu, compiz (with a nice custom theme), and VirtualBox Windows integration in a way many of you haven't seen before:

[http://p4mansubuntublog.blogspot.com/](http://p4mansubuntublog.blogspot.com/)

3 Ubuntu viewports, 1 windows viewport, on 1 cube. Added a how-to, parts 1 and 2 online, 3 will follow in a few days.

---

### Post by P4man on 2007-11-03
oops, just noticed the sound isnt there.. oh well, you can watch at least :)

---

### Post by Hendrixski on 2007-11-03
You've got a nice setup, and you show it off very well.  Have you looked into maybe helping the screencasting team with making great video tutorials?  They can teach you a lot, like how to make those kinds of videos just in higher res, and to add voice over it, edit, etc. etc.

It's a great way of not only showing off your setup, but helping others make their setups great as well.  :-)

---

### Post by P4man on 2007-11-03
Actually, I wanted to do some sort of how-to video, this was a first attempt.  I figured showing it off and having a written how-to makes more sense.

BTW, its horrible how google messed up the quality, it was very high res (1440x900), perfect quality. video.  Looks like I better do the scaling and recoding myself :(

---

### Post by Jose Catre-Vandis on 2007-11-03
How did you get a different background/wallpaper on the "Windows" viewport?

---

### Post by P4man on 2007-11-03
Its a little trick, you have to disable gnome rendering the desktop

gconf-editor

apps>nautilus>preferences untick "show_desktop"

A side effect is that you lose desktop icons :(

Then you go into Compiz settings,  desktop cube, appearance, and define the background images. I used 3x the orange ubuntu dragon, and once the blueish windows dragon.

---

### Post by saj0577 on 2007-11-03
How did you get the one windows viewpoint?

Saj

---

### Post by MarshallClan on 2007-11-03
Nice Work P4man!... 
 I, for one, am awaiting the full post on how to get VirtualBox configured so nicely in Gutsy. Like I said... I'll be waiting!

---

### Post by P4man on 2007-11-03
Install virtualbox (virtual machine). Install windows on the virtual machine  (any flavour you have, XP or even Vista). Once it is up and running, press control+L to get the" seamless" mode. It has some minor issues, like when you minimize everything in windows, but works wonderfully. 3D stuff in windows apps is not support though.

If you need more info, google around, or wait until I made a how-to.

---

### Post by pjones0404 on 2007-11-03
i eagerly await the how to as well. i have played around w/ virtualbox before but never really got it to work he way i liked.

this is really cool w/ it being on one side of the cube like that.

---

### Post by P4man on 2007-11-03
I'll write a detailed step-by-step guide to get "my desktop" and I will post the wallpapers and stuff on gnome-look.org (where I got the originals). But where would be the most appropriate place to post stuff like that ? Here, in this forum ?

---

### Post by MarshallClan on 2007-11-03
P4man... Maybe go ahead and post it to the "Tutorials and Tips" section. Maybe even use the same header so the awaiting masses can track it from there. Hopefully you can include the guide you used to get your Compiz to that "Magic" state! Thanks!

---

### Post by akiratheoni on 2007-11-03
Wow! Looks really cool, I can't wait to see the tutorial! :P

---

### Post by mdpalow on 2007-11-03
Pretty impressive display you made there. :)

I wasn't even considering the use of Compiz Fusion on my desktop, but now I think I just might have to.

damn... you're nice little demo is going to cause me some problems for sure... LOL

Just when I had everything perfect too.

...

---

### Post by rickycodie on 2007-11-03
did you use the new virtual box? 

it enters seamless mode just by pressing rt ctrl+L!!!

---

### Post by Jose Catre-Vandis on 2007-11-03
> **P4man said:**
> Its a little trick, you have to disable gnome rendering the desktop

gconf-editor

apps>nautilus>preferences untick "show_desktop"

A side effect is that you lose desktop icons :(

Then you go into Compiz settings,  desktop cube, appearance, and define the background images. I used 3x the orange ubuntu dragon, and once the blueish windows dragon.


Thanks, yes, I sorted it that way. There is a more tricky route installing wallpapers for compiz which i steered clear of!

---

### Post by jake16424 on 2007-11-03
> **P4man said:**
> Made a little video to show off the combination of ubuntu, compiz (with a nice custom theme), and VirtualBox Windows integration in a way many of you haven't seen before:

[http://video.google.com/videoplay?docid=4190016296458685340&hl=en](http://video.google.com/videoplay?docid=4190016296458685340&hl=en)

3 Ubuntu viewports, 1 windows viewport, on 1 cube. If anyone is interested in the wallpapers, theme or how to configure Ubuntu and virtualbox to get this effect, I'll post links later.

how did you do such a thing. O_O

---

### Post by bdamon on 2007-11-03
Very Nicely done! What did you use to create the video?

---

### Post by Don9307 on 2007-11-03
I can only get a 3D Cube effect that appears like you are looking from inside a cube outward vs. looking at a cube from outside.  What settings do you use to get the latter effect?

---

### Post by P4man on 2007-11-03
> **bdamon said:**
> Very Nicely done! What did you use to create the video?

I used gtk-recordMyDesktop.
[http://packages.ubuntu.com/feisty/graphics/gtk-recordmydesktop](http://packages.ubuntu.com/feisty/graphics/gtk-recordmydesktop)
 No other editing, uploaded it straight to google.

I was also pretty amazed how well it works. I was running 1440x900, running both XP on a VM  and of course ubuntu, with all the bells and whistles,  playing back a DVD, recording everything, and it was still totally smooth as butter.Not anything like a hickup. Its not like I have a killer machine either, "just" a C2D 2.1 GHz, 2 GB Ram (half of which was never used) and 7900GS (256Mb).

---

### Post by P4man on 2007-11-03
> **Don9307 said:**
> I can only get a 3D Cube effect that appears like you are looking from inside a cube outward vs. looking at a cube from outside.  What settings do you use to get the latter effect?

Desktop Cube>Behaviour>uncheck "inside"

---

### Post by P4man on 2007-11-04
I am posting the howto here:
[http://p4mansubuntublog.blogspot.com/](http://p4mansubuntublog.blogspot.com/)

A brand new blog :) allows me more flexibility. 

Part 1 is almost online  (installing VirtualBox). You can start with that it should keep you busy for a while :) Next parts will focus on tweaking virtualbox and compiz and will be online soon!

---

### Post by P4man on 2007-11-05
[Parts 1 and 2 of the how-to  are online now. ]("http://p4mansubuntublog.blogspot.com/")

It would be nice if someone wanted to "test" this howto, because I don't have a fresh install here, so I might have made errors or forgotten stuff.

---

### Post by tomot on 2007-11-05
I tested your How to, and it works flawlessly so far. (Nice work!)

I'm looking forward to:  How to access other HDD's that are on my machine, which Ubuntu sees
but which don't show up in the XP virtual window.

I'm also wondering if a virtual machine might be better implemented using 
XP as the host and Ubuntu as the Guest. The reason being I can make better
use of my Dual Monitor setup under XP. I cant seem to get an expanded Desktop
working across 2 monitors running different resolutions using Ubuntu-fiesty

cheers!

---

### Post by tomot on 2007-11-05
that last part should read......Ubuntu-gutsy

---

### Post by P4man on 2007-11-05
Nice to hear it works so far. I thought I did explain how to make drives available, but maybe I should expand a bit more on it.

For now, in virtualbox, go to the settings of your VM (VM should be OFF), shared folders, add a shared folder for each of your drives that you want to be available in the VM. For instance, one would be:

folder path: /media/movieharddisk
folder name: movieharddisk

then, boot your windows VM, start/run/cmd  and type:

```
net use M: \\vboxsrv\movieharddisk
```

That will give you a "M:" drive that accesses the "movieharddisk" seen by ubtuntu.

---

### Post by P4man on 2007-11-05
> **tomot said:**
> I 
I'm also wondering if a virtual machine might be better implemented using 
XP as the host and Ubuntu as the Guest. The reason being I can make better
use of my Dual Monitor setup under XP. I cant seem to get an expanded Desktop
working across 2 monitors running different resolutions using Ubuntu-fiesty
!

This might be better asked in a separate thread; last time I tried dual monitor was with feisty, using nVidia's drivers, and it worked perfectly. Had the same options as with windows,  independant resolution, maximizing to one winows,  and everything.  It looked pretty amazing with Compiz too I might add.

Now I use the restricted driver that come with Ubuntu, and I wouldn't know where to set it up either TBH. Not that I tried, as I got only 1 LCD now. You might try downloading the nVidia drivers from their site, but I found it doesnt play nice with Gutsy's "bulletproof X", but then I was using gutsy beta (tribe 4).

---

### Post by tomot on 2007-11-06
> **P4man said:**
> Nice to hear it works so far. I thought I did explain how to make drives available, but maybe I should expand a bit more on it.


I did my install Sunday night, I didnt check to see you had added more so soon...!

Look like from all I have read, that an nVidia's card is more capable than an Ati card that I have.
I should probably pick a cheap  nVidia's card and give those drivers a try.
cheers!

---

### Post by hyper_ch on 2007-11-06
:(

> 
We're sorry, but this video may not be available. 

Try refreshing the page to see this video. 

To see more videos visit our home page


---

### Post by P4man on 2007-11-06
Oops, sorry about that., forgot to update first post Just click the link im my sig to get to the how-to page, which includes that video

---

### Post by civic_si on 2007-11-06
Thanks I needed this.

---

### Post by hyper_ch on 2007-11-06
nicely done (but I still prefer vmware ;)

---

