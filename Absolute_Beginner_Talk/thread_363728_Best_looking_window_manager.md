---
title: "Best looking window manager"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by 67GTA on 2007-02-17
I have been running Ubuntu for about a month, and I am slowly getting M$ out of my system.   I am trying to test and customize my desktop. If I understand correctly, Gnome uses Metacity by default. I tried to install Beryl and was not supported by my ATI card. What other window managers should I consider for my desktop. I want a smooth look, and some eye candy. Any suggestions?

---

### Post by reacocard on 2007-02-17
I've heard Enlightenment is good. It's a pity Beryl doesn't work on your card though, it's awesome.

---

### Post by 67GTA on 2007-02-17
Yeah, I was all foamed up about Beryl :( . I will look at Enlightenment. Thanks.

---

### Post by mcduck on 2007-02-17
I'm pretty sure Beryl works with your graphics card. I'm using it on both Radeon 9600 XT and Mobility Radeon X1600, and I've also installed it on X1800..

You just need to install fglrx drivers, and then use XGL, not AIGLX.

edit: you could try this guide about Ati, fglrx, XGL & Beryl: [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html]("http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html")

---

### Post by 67GTA on 2007-02-17
First I tried to install Beryl using AutomatixBleeder, and it said card not supported. Then I was directed to the link you gave me and after finishing that method, I could not switch from Gnome manager to Beryl(several error messages). Maybe it was me. I might try it again before I look elsewhere. I really liked the Beryl look.

---

### Post by g3k0 on 2007-02-17
It works on my x1300 as well.  ATI works with linux.  You juist have to get your drivers working

---

### Post by K.Mandla on 2007-02-17
You can get tolerable eye candy with transparency and window shadows with xcompmgr; it'll run on the oldest of machines and looks really good.

[[img]http://xs312.xs.to/xs312/07076/screenshot.jpg.xs.jpg[/img]](http://xs.to/xs.php?h=xs312&d=07076&f=screenshot.jpg)

That's a 300Mhz machine running Openbox on a Neomagic MagicGraph 256AV (?!). You can tie the window transparency to the mousewheel and change window opacity on the fly. Menus fade in and out and all the effects are tweakable.

[[img]http://xs412.xs.to/xs412/07073/xcompmgr-2.jpg.xs.jpg[/img]](http://xs.to/xs.php?h=xs412&d=07073&f=xcompmgr-2.jpg)

That's a 1Ghz with a 64Mb Geforce4 440 Go, so it does a little better. ;) xcompmgr doesn't have all the flair that Beryl has, but I can almost guarantee it will work on your machine. :D

It's not limited to Openbox, either. I believe (but of course, I can't guarantee) you could accomplish the same thing on a machine using Fluxbox or IceWM or Xubuntu or. ... You get the picture.

---

### Post by kvonb on 2007-02-17
I don't mean to be rude, but.....

If it's not a laptop, beg/borrow/steal the money to get an Nvidia card :)

I have a 2nd machine that has a GeForce 2/MX 400 - 64 meg really quite old card, and Beryl works perfectly on it!

You can pick those up for next to nothing on ebay.  I had a spare one but I gave it to a chap in Africa who didn't have one!

Not really a help I know, but ATI have neglected Linux which is a shame because they are good cards and they could have been great!

I struggled for nearly a year with my old ATI 9200se, which did run Beryl (just!).  Fortunately my wife bought me an Nvidia 6600gt for Christmas, and the difference is just mind-blowing!

It is 10 times as fast, and the driver is much better quality.  Plus you get a settings tool.

Regards, Kev :)

---

### Post by karl_forshaw on 2007-02-17
A lot of ATI/fglrx users are struggling with beryl lately, and I cant seem to find out why. I read somewhere that there was a problem with the OpenGL libraries in Ubuntu, but I also read that its just a bug with Beryl-XGL that they are working on. Ive got the latest beta running at the moment but its just a useless white (cube) desktop that i can spin around. Its a pain the *** really, I have it working fine at work with an Nvidia card (Dual Screen Godliness).

I'm in the process of downloading Feisty Herd 4 at the minute to see whether it makes any difference.

---

### Post by kvonb on 2007-02-17
> **K.Mandla said:**
> You can get tolerable eye candy with transparency and window shadows with xcompmgr; it'll run on the oldest of machines and looks really good.

[[IMG]http://xs312.xs.to/xs312/07076/screenshot.jpg.xs.jpg[/IMG]]("http://xs.to/xs.php?h=xs312&d=07076&f=screenshot.jpg")

That's a 300Mhz machine running Openbox on a Neomagic MagicGraph 256AV (?!). You can tie the window transparency to the mousewheel and change window opacity on the fly. Menus fade in and out and all the effects are tweakable.

[[IMG]http://xs412.xs.to/xs412/07073/xcompmgr-2.jpg.xs.jpg[/IMG]]("http://xs.to/xs.php?h=xs412&d=07073&f=xcompmgr-2.jpg")

That's a 1Ghz with a 64Mb Geforce4 440 Go, so it does a little better. ;) xcompmgr doesn't have all the flair that Beryl has, but I can almost guarantee it will work on your machine. :D

It's not limited to Openbox, either. I believe (but of course, I can't guarantee) you could accomplish the same thing on a machine using Fluxbox or IceWM or Xubuntu or. ... You get the picture.


That's brilliant, is there a good guide for setting up xcompmgr?

---

### Post by CheeseEatingBulldog on 2007-02-17
I have beryl running on a geforce2 mx400 64 card and have recently had to switch from XGL to AIGLX as the former just stopped working after an update. I must say that AIGLX feels a lot slower than XGL, but then that was without the flame and beam effects....

---

### Post by 67GTA on 2007-02-17
Any thoughts on Compiz? I see a lot of votes for it instead of Beryl.

---

### Post by 67GTA on 2007-02-17
> If it's not a laptop, beg/borrow/steal the money to get an Nvidia card 

I was going to attempt to build my own desktop from scratch pretty soon. (first time)
I was looking at making the switch from Ati to Nvidia. I bought my daughter's Dell with Nvidia just out of curiosity, and am pleased so far.

---

### Post by karl_forshaw on 2007-02-17
From what I've seen (which is only what comes with suse 10.2) Compiz isnt anywhere near as nice as Beryl. From what I've seen it just makes the windows wobble and gives you a very basic version of the Desktop cube.

Feisty 4 is burning to disk now..

---

### Post by Cardmaster91 on 2007-02-17
AAAAHHHH, i shouldn't have with what i don't know. Beryl sounded cool, i wanted to try it. I KILLED IT. i don't know what i did, im a noob. help me. I start ubuntu up and it says ERROR ERROR EROOR ERROR ERROR ERROR ERROR ERROR. AAAAHHHH. WHY HOW DO I FIX THIS.

---

### Post by shareMenaPeace on 2007-02-17
Hej sometimes beryl soednt get uninstalled correctly see my signature for a small how to on uninstall beryl correct and than reinstall ...try it :)

---

### Post by Cardmaster91 on 2007-02-17
ok, i got to the startx command. but it sasy fatal error: no windows found. the same error returned when i start ubuntu normally

---

### Post by karl_forshaw on 2007-02-17
It worked guys, 

I upgraded to Feisty Herd 4, and now I have my ATI200m running the latest Beryl SVN using XGL. No more white cube.

---

### Post by 67GTA on 2007-02-17
Thats cool! maybe I will just wait until I upgrade. Did you have to do the config manually?

---

### Post by karl_forshaw on 2007-02-17
I installed fresh using the latest Feisty disk and then installed everything through the package manager, I didnt try beryl 1.999999 but I'm pretty sure it would have worked as I've had to downgrade the beryl-settings manager to 1.9999999.. Its running really nice. Feisty has some very cool improvements aswell, I'm feeling very much at home on this machine now.

---

### Post by testube_babies on 2007-02-17
> **kvonb said:**
> I don't mean to be rude, but.....

If it's not a laptop, beg/borrow/steal the money to get an Nvidia card :) 

...even if it is a laptop, you can probably find a nvidia card for it on eBay.  Dell refused to put a nVidia card in my new laptop because they don't support the Vista drivers for it.  So I got one on eBay and put it in myself.  Couldn't be happier!

---

### Post by K.Mandla on 2007-02-18
> **kvonb said:**
> That's brilliant, is there a good guide for setting up xcompmgr?
:-k Hmm. I just installed it through aptitude, then used the --help flag to get the available tweaks and picked the ones I wanted.

The best information is in the Gentoo and Arch wikis. You'll have to compile transset-df to get the keybindings to work right in Openbox ... otherwise just plain transset will work, but you have to manually set the transparency via terminal command. 

I [blogged]("http://kmandla.wordpress.com/2007/02/14/transparencies-in-openbox-with-xcompmgr/") a teeny bit about it a few days ago, so some links are there that can get you started. When you're done, if you have a machine that can handle GLX and is running around 1Ghz or more, you can add 3ddesktop to it and get all the effects in one neat package. :biggrin:

---

### Post by CheeseEatingBulldog on 2007-02-18
I only recently found [3d desktop]("http://desk3d.sourceforge.net/"), which is in the repos. I have a vaio with a 4mb graphics card on it, which can't handle beryl. But after instsalling 3ddesk and tweaking the config file I have a pretty neat desktop switching GL. :)

---

### Post by energiya on 2007-02-18
You could always use XFCE. You can enable display comositing and you have shadows under windows and menus and true transparency. And its lite.

---

### Post by old_geekster on 2007-02-18
> **67GTA said:**
> I was going to attempt to build my own desktop from scratch pretty soon. (first time)
I was looking at making the switch from Ati to Nvidia. I bought my daughter's Dell with Nvidia just out of curiosity, and am pleased so far.
Now you are talkin'.

I did my first build last May (see my sig).  It was a great experience.  The best part is when you have a problem, there are so many good forums, you can fix most anything yourself.  You built it, so you know where things are and how they went where they are.

Here is a link to a great enthusiast site: 

[http://www.diy-street.com/](http://www.diy-street.com/)

You can get all of the help you will ever need from them.  They are the best.  Just click on "Forums".

---

### Post by mexlinux on 2007-02-19
If you are looking for more eye candy and more customization, you must give KDE a try, install kubuntu-desktop

---

### Post by 67GTA on 2007-02-19
> mexlinux  	If you are looking for more eye candy and more customization, you must give KDE a try, install kubuntu-desktop

I tried Kubuntu, but it seemed buggy. It did not seem as stable as Gnome. 


> old_geekster  Now you are talkin'.

I did my first build last May (see my sig). It was a great experience. The best part is when you have a problem, there are so many good forums, you can fix most anything yourself. You built it, so you know where things are and how they went where they are.

Here is a link to a great enthusiast site:

[http://www.diy-street.com/](http://www.diy-street.com/)

You can get all of the help you will ever need from them. They are the best. Just click on "Forums".

Thanks for the link. Any good links for parts? I am just researching hardware right now. I have my pc being worked on at Best Buy for the 7th time in two years. (I bought a 3 year warranty)Two weeks every time. Hard drive, tuner card, graphics card, dvd-rom, motherboard, and right now cpu fans.  

I have been talking to several Feisty Fawn testers, and Beryl is used as default. I will just wait and see how that works before I start messing with other window managers.

---

### Post by flamarro on 2007-02-20
> **g3k0 said:**
> It works on my x1300 as well.  ATI works with linux.  You juist have to get your drivers working

Hi, could you tell me how did you manage to config beryl with your X1300? I also have X1300, and i've followed a bunch of how to's  to put ATI working with beryl, and no good. Some say that beryl needs composite to work but we must turn it off if we use 3d fglrx, and to use radeon driver, that driver is not supported with some X graphics card like X1300.... So how we do it? Like i said, i followed [[COLOR="YellowGreen"][COLOR="Sienna"]this[/COLOR][/COLOR]]("http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html") for exemple and when i select XGL, it start's but then the image stops, but i can understand that, under what i am seeing all is working, i can hear the sound of some programs starting even the mouse works, but i cant select anything.

PS: Sorry for my english

---

### Post by bodhi.zazen on 2007-02-20
It's a little off topic, but, take a look at Wolvix :

Wolvix hunter has the most polished "out of the box" configuration for Fluxbox I have seen yet.

[wolvix-hunter-1.0.5.iso](http://www.rubyringtech.com/click/phptrak.php?http://gamma.rubyringtech.com/wolvix/wolvix-hunter-1.0.5.iso)

MD5sum :> d14bd6ef2323be71c1297b2bf9bfeb23  wolvix-hunter-1.0.5.iso

Home page : [http://wolvix.org/](http://wolvix.org/)

---

### Post by jjf on 2007-02-20
> **karl_forshaw said:**
> It worked guys, 

I upgraded to Feisty Herd 4, and now I have my ATI200m running the latest Beryl SVN using XGL. No more white cube.

Does Feisty ship with Beryl?  I thought I read that the Ubuntu team was considering that, but Shuttleworth nixed it because Beryl still wasn't ready.  :confused:

---

### Post by bodhi.zazen on 2007-02-20
> **jjf said:**
> Does Feisty ship with Beryl?  I thought I read that the Ubuntu team was considering that, but Shuttleworth nixed it because Beryl still wasn't ready.  :confused:

Feisty will not ship with beryl because it is not felt beryl is yet stable enough ...

I am not sure who made the decision ...

But ... I have beryl up and running on Feisty with no problem. It was not too hard to set up.

I believe once beryl is deemed stable it will ship with Ubutnu.

If you would like to see what IMO is the best implementation of Beryl, try Sabayon.

Home page : [http://www.sabayonlinux.org/](http://www.sabayonlinux.org/)

---

### Post by karl_forshaw on 2007-02-21
It doesn't ship with beryl no. But it seems better equipped to handle it. Its still running very nicely.

// Edit
I ran some updates last night and it broke completely lol. Plus Feisty has been misbehaving this past couple of days.

---

### Post by MasterOfDisaster on 2007-04-09
I'd have to give my vote for Enlightenment.  For lower end machines, try XFCE 4.4, now  with built-in composite.

---

