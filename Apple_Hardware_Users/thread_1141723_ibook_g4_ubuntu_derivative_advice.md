---
title: "ibook g4 ubuntu derivative advice"
date: 2009-04-28
forum: Apple Hardware Users
---

### Post by sha.goyjo on 2009-04-28
I've been tooling around with installing linux on my gf's computer for about a month now. I started out with debian+gnome, and then tried debian+xfce. Both worked fine, for me, but my girlfriend doesn't have the knowledge of the command line that I do, and she doesn't like fix-its as much as I do either. Seems she wants it to "just work". For that reason, I decided to try PPC ubuntu. My question to you lot is this.

for an ibook g4 1.3 ghz ppc processor 512mb ram 40 gb hd, for a person of relative linux inexperience who is also looking to have a computer that is not to terribly slow, but still does all she wants:

1. Would you recommend Ubuntu or Xubuntu
2. What version would you recommend (ie 7.10, 8.04, 8.10, 9.04)

Thanks for all of your time.

---

### Post by stream303 on 2009-04-28
I think the problem you'd face is that there aren't really any flash or 3D drivers that she would find acceptable because nobody makes proprietary ppc drivers.

FOSS equivalents are ok and coming along, but not nearly as suitable as the proprietary ones.  Not that I'm advocating proprietary solutions - far from it.  It is sad that we can't really establish FOSS standards rather than rely on corporate lock-ins.  Oh well.

In other words, that machine might be nice for you and me, but probably not for someone expecting an OSX work-alike.  You can get close, but she might be expecting more of a normal consumer experience from it.

And unfortunately with PPC, you'll often find yourself getting your hands dirty with config files and other rough spots once in awhile.

---

### Post by mkvnmtr on 2009-04-28
I have the same machine and Ubuntu suits my just fine. With an extra 1 Gb of ram it seems plenty fast. But like stream said it might not suit someone that wanted good flash.

---

### Post by sha.goyjo on 2009-04-29
I am aware of the downsides of using ppc linux (IE the 3d drivers and the flash issues). There are solutions to both of those problems, both with documented fixes. What I desire to know are the relative pluses and minuses with regards to ubuntu or xubuntu, and different distro versions. Thats all I desire to know.

Thanks for your time,

Jason Ritzke

---

### Post by stream303 on 2009-04-29
In that case, I'd recommend the standard Ubuntu 9.04 ppc.  You have enough memory and horsepower to try and install the live-cd version - although if that doesn't work you can easily try the text-based "alternate" installer (full gui afterwards).

Kubuntu (KDE) and Xubuntu (XFCE4) would also be fine choices, but it would be hard to tell if she would prefer one over the other.  Install Ubuntu, and if she like it, but wants more options (install Kubuntu), and if she wants it even easier, install Xubuntu.

Kubuntu has many more options than gnome-Ubuntu, and is thus considered somewhat of a heavyweight desktop.  Xubuntu is lighter than gnome (Ubuntu).

No matter which one you originally install, you can download the other without burning a new disk by downloading

xubuntu-desktop
or
kubuntu-desktop

and then switch to it at the GDM login screen by going into Sessions, and making the change either temporarily or permanently as the default from there - although you'll have somewhat of a mixed environment.

Aside from ram requirements: Kubuntu > Ubuntu > Xubuntu, it is really a matter of personal decision.  So I'd take the middle-of-the-road option and install Ubuntu and see if she likes it and move from there.

I don't think you'd go wrong with any of the three major options.  And that's the real problem. :)

---

