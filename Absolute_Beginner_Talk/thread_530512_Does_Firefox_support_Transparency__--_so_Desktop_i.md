---
title: "Does Firefox support Transparency ?? -- so Desktop is visible below??"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by kevdog on 2007-08-20
Is there anyway to make Firefox Transparent???  Or does it support pseudo-transparency to make it seem like the background is showing through??

Thanks!

---

### Post by Hobo Joe on 2007-08-20
If you have Compiz or Beryl you can do this.

---

### Post by kevdog on 2007-08-20
I dont have Compiz (wish I did) -- but my graphics card is so old (7 years) that is not compatible.

Seems like you should be able to do this without the "eye candy" programs.

---

### Post by Hobo Joe on 2007-08-20
Not really, older cards, particullarly ones as old as yours, have very bad support of things like trasparency.

---

### Post by bodhi.zazen on 2007-08-20
You should look at xcompmanager :

[http://kmandla.wordpress.com/2007/02/14/transparencies-in-openbox-with-xcompmgr/](http://kmandla.wordpress.com/2007/02/14/transparencies-in-openbox-with-xcompmgr/)

Not as fancy, but it works with older hardware (heck, it works with VMWare as well)

---

### Post by kevdog on 2007-08-20
xcompmanager Looks promising -- cant seem to find a home page or documentation page.  Do I need openbox to run this??

I basically need more info on how to run this program

---

### Post by crimesaucer on 2007-08-20
Xfce4.4 works on old computers and has compositing: [http://www.xfce.org/](http://www.xfce.org/)

Screen shots showing transparency without the use of Beryl/Compiz: [http://www.xfce.org/about/screenshots](http://www.xfce.org/about/screenshots)


...I like this one the best: [http://www.xfce.org/images/about/screenshots/4.4-2.png](http://www.xfce.org/images/about/screenshots/4.4-2.png)

---

### Post by kevdog on 2007-08-20
So what Im basically getting from you guys is that I need a different desktop environment other than gnome/kde -- something like xcfe, open/flux box etc??

Ive never ventured into the area of "alternative" desktops??  Any good tutorial on this??

---

### Post by bodhi.zazen on 2007-08-20
No, all you need to do is install and configure xcompmanager

Follow the links on the first page I gave you :

[http://gentoo-wiki.com/TIP_Xorg_X11_and_Transparency#xcompmgr_and_transset](http://gentoo-wiki.com/TIP_Xorg_X11_and_Transparency#xcompmgr_and_transset)

[http://wiki.archlinux.org/index.php/Xcompmgr](http://wiki.archlinux.org/index.php/Xcompmgr)

---

### Post by crimesaucer on 2007-08-20
> **kevdog said:**
> So what Im basically getting from you guys is that I need a different desktop environment other than gnome/kde -- something like xcfe, open/flux box etc??

Ive never ventured into the area of "alternative" desktops??  Any good tutorial on this??

You can do as bodhi.zazen suggested.....or.....you could install xubuntu:

```
sudo apt-get install xubuntu-desktop
```

then log out/log back in...and select XFCE as your desktop environment.

Then adjust your opacity in your: Settings Manager-->--Window Manager Tweaks

That's it for Xfce4.4....if you don't like it, then remove it with:

```
sudo apt-get remove xubuntu-desktop
```

---

### Post by kevdog on 2007-08-21
Thanks for your advice

I do have xcfe desktop already installed and I didnt know that it supported transparency.  I tried just the general desktop (not the transparency), and really didnt like it compared to gnome/kde.  Its lighter but I need (for me at least) something more "full" featured

As far as xcompmgr -- installed it -- Looks very Good!! ---- however big performance hit.   For example scrolling the Firefox window was extremely slow when activated.  Loved the appearance, but not functionally usuable.  Also seemed kind of strange that you had to activate the transparency on a per window basis, and that it couldnt be automatic.

Wish there were better alternatives, maybe Im just out of luck on this one!!

---

### Post by K.Mandla on 2007-08-21
There are ways to apply transparency automatically, but to be honest, if it's a drag on your system then it's probably not worth chasing. 

If you decide you want to try it sometime, you'll need to look into [transset-df]("http://www.forchheimer.se/transset-df/").

---

### Post by kevdog on 2007-08-21
I saw that link for transset-df in the gentoo wiki - however I think your right,  Transset works (like advertised) but it does tax the system.  Its weird since I dont see cpu usage jump or the program jump up to the top output (conky), but its definitely not usuable

---

### Post by K.Mandla on 2007-08-21
Just out of curiosity, what kind of system specs are you running? I can tolerate transset-df and xcompmgr on a 1Ghz machine, but I have a very good graphics card for a machine of that era.

---

### Post by kevdog on 2007-08-21
Laptop Dell 5000e (1999) 850 MHz processor - 512 Mb RAM, integrated ATI 128 Rage Mobility GFx card.

---

### Post by K.Mandla on 2007-08-21
Hmm. :-k I think you might be right. It's a solid machine, but that Rage Mobility is a little weak for translucent effects. Is it upgradeable? My Inspiron 8000 originally had a 16Mb Geforce2 in it, but I crammed a 64Mb Geforce4 440 Go in it.

---

### Post by kevdog on 2007-08-21
I never thought about changing the gfx card -- I thought it was integrated, but I could be wrong.  Your 8000 was the same era as mine.  Have any idea where I could pick up a gfx card?  I think your right, b/c I noticed that CPU utilization didnt really increase during the experiment -- so likely the gfx card.

---

### Post by K.Mandla on 2007-08-22
Ebay is the best source for outdated laptop parts. You'll have to do a little homework and research your machine. Find a service manual on support. dell.com and see if the video card is removable, and if so, what you can replace it with.

I got lucky with this 8000, since the same footprint, sockets and connectors were used through the 8100s and 8200s. Since the 8200s crossed the 2Ghz mark, they had 64Mb (then-powerful) graphics cards ... some Nvidia, some ATI. Both were cut to the same dimensions and could be replaced without a hitch.

The only downside is that the 8000s only reached 1Ghz, so if I want a faster CPU, I have to invest in a new motherboard (and chassis too, probably) with the proper socket for the faster chips. Of course, the good side of that is, I have all the components, parts and accessories I need for a righteous 8200. I just have to decide when I want it. 

Best of all, it'll probably run me less than $120, if I can find one that's working, with a chip and the rest is busted. :twisted:

---

### Post by kevdog on 2007-08-22
I love building computers (only done 2 desktops), however based on my piece of junk laptop, probably better off going with just a new unit!!  (Love the screen on the old one however, it was great).  On the Inspiron, the case is cracked in multiple locations, I would want to update cpu, which would mean new motherboard, RAM, GPU, and Harddrive, and battery (battery life stinks).  Dont really need port replicator in back anymore either.  

Any recommendations on new laptop or just a link to look at -- Im looking for fairly good performance, however dont want a ton of weight.  That 8000 you have -- now that's heavy (oops no I think I was confusing it with the 7500).

---

### Post by stchman on 2007-08-22
> **kevdog said:**
> I dont have Compiz (wish I did) -- but my graphics card is so old (7 years) that is not compatible.

Seems like you should be able to do this without the "eye candy" programs.

Transparent windows and such require far more processing power than regular desktops.

---

