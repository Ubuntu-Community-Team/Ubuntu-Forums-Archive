---
title: "Who Has the Best Font Rendering??"
date: 2013-06-05
forum: Any Other OS
---

### Post by buzzingrobot on 2013-06-05
Which Linux distribution has the best out-of-the-box font rendering?


Discounting Ubuntu.


The quality of onscreen font rendering is very important to me.  If it's not good enough, that distro gets ignored.

I know this is terribly subjective, so here are a few of the things I look for:

1,  I don't want to see the pixels.
2.  I want clean and distinct edges on characters.  No fuzziness and no detritus hanging around inside of loops in letters like A's and O's.
3.  I want no bleeding on headline fonts.  See number two.

From what I see of it, Windows' font rendering is not all all to my liking.

---

### Post by vadimkolchev on 2013-06-05
I thik it is a matter of personal preference, but I can share mine. If we speak about out of the box font experience, i can think about CentOS, but it is enterprise and will suit you only if you are ok with good old rock solid packages and the lack of some desktop features. Also I've been impressed recently with all distros using gnome 3, debian 7 for instance or Archlinux with same gnome on top of it. Mind that liinux offers great flexibility and everything can be adjusted to your likings on any distro. I really think you should not dismiss any distro because of fonts for this reason, just find the one that is more convenient for you and build anything you want on top of it.

---

### Post by DisappearingOak on 2013-06-06
I hate Windows' blurry fonts. Such an eyesore. The only distros with font render that I liked were Ubuntu and Rosa Linux..

---

### Post by Rebelli0us on 2013-06-06
Linux MInt MATE has plenty of font rendering options. I prefer it over Windows which has fonts too thin IMO.

---

### Post by VanillaMozilla on 2013-06-07
> **buzzingrobot said:**
> Discounting Ubuntu.
The fonts are highly configurable on Ubuntu, and very likely on any POSIX release.  I would expect that any Gnome-based distro would offer the same capabilities, and very likely the others as well.  Nothing that you wrote suggests to me that you have tried this.  You just have to look.

And you may be asking the wrong question.  "Out-of-the-box" seems like an odd stipulation, since it takes far less effort to adjust font rendering than it does to switch distros.

If you're having trouble because you can see pixels, I suspect that your monitor dot pitch is too large.  That is to say, your monitor size is too large for the resolution.  Font rendering adjustments may help with disguising pixels on diagonals, but basically, if you can see pixels at all, that's a fundamental problem with your monitor or the way you are using it.  Computer stores like to sell big monitors, but sometimes they are so big that you can see the pixels.

Also, do note the difference between system fonts used in menus, etc. and fonts used for content.  Also note the different font types, which have different properties.

---

### Post by Derek10 on 2013-06-08
LInux mint 15 MATE with default font rendering and using Ubuntu typeface for everything is fine for me.

---

### Post by 3rdalbum on 2013-06-08
No operating system currently has "the best" font rendering. It's all subjective these days.

---

### Post by Mikeb85 on 2013-06-09
I personally like the font renderings on all Gnome 3 based distros, not a huge fan of the way KDE distros seem to render fonts (at least not by default).

---

### Post by buzzingrobot on 2013-06-09
> **VanillaMozilla said:**
> The fonts are highly configurable on Ubuntu, and very likely on any POSIX release.  I would expect that any Gnome-based distro would offer the same capabilities, and very likely the others as well.  Nothing that you wrote suggests to me that you have tried this. 

I asked out of curiosity.  I wasn't looking for a how-to.

I've adjusted font rendering to my tastes for years on a variety of platforms. I store fonts and various configuration files on Dropbox.  Those are applied soon after I've installed a new distribution. I've applied the Ubuntu font patches to freetype, etc., and used them on Debian and other Debian derivatives.  I've done the same with the Infinality patches.

While it is true that rendering quality can be a matter of personal preference, I sometimes think that can be used as an excuse to avoid working the issue. 

I excepted Ubuntu because this is the Ubuntu forum and because its rendering is widely accepted as being very good.  I find that I prefer the rendering on 13.04, using Liberations Sans for documents and Ubuntu for the rest. Gnome Shell's defaults don't work for me, so I alter them first thing. (How I alter them depends on whether or not I'm using Infinality.)

As you suggest, the monitor plays a big role here.  Adjusting the sharpness control on my monitor has more impact on the appearance of fonts on the screen that anything I can do in software. I'd guess, though, that few people ever play with that adjustment just to see what happens.

---

### Post by VanillaMozilla on 2013-06-09
> **buzzingrobot said:**
> I've done the same with the Infinality patches.
Never heard of it.  There is a utility that comes with Ubuntu (or used to), with several options.  It seems to be gone from my menus, so darned if I remember what it was.  It was obvious, in the system stuff.  I adjusted everything once, all was perfect, and I've never touched it since.

> **buzzingrobot said:**
> I find that I prefer the rendering on 13.04, using Liberations Sans for documents and Ubuntu for the rest.
Huh?  Those are fonts, not rendering settings.  And I thought all these versions were the same.  At least they're all perfect for me.

> **buzzingrobot said:**
> Adjusting the sharpness control on my monitor has more impact on the appearance of fonts on the screen that anything I can do in software.
Amazing.  The one I'm using at the moment has a setting.  It's perfect by default, but any adjustment makes it terrible.  I can't imagine why the setting even exists.  This has nothing to do with distros.

---

### Post by buzzingrobot on 2013-06-09
> **VanillaMozilla said:**
> Never heard of it.  There is a utility that comes with Ubuntu (or used to), with several options.  It seems to be gone from my menus, so darned if I remember what it was.  It was obvious, in the system stuff.  I adjusted everything once, all was perfect, and I've never touched it since. 

You are perhaps remembering the Font section of the "Appearance" panel in Gnome 2. That functionality is now included in Gnome Tweak Tool and the corresponding Unity Tweak Tool.

Here ([http://www.infinality.net/blog/](http://www.infinality.net/blog/)) is the link to the Infinality developer's site.  Some of his work has been recently been incorporated into Freetype, so everyone using Linux is, or soon will be, using that code.


> Huh?  Those are fonts, not rendering settings.  And I thought all these versions were the same.  At least they're all perfect for me.

Different fonts are rendered differently on different architectures.  The Liberation fonts were designed to mimic Arial.

>  Amazing.  The one I'm using at the moment has a setting.  It's perfect by default, but any adjustment makes it terrible.  I can't imagine why the setting even exists.  This has nothing to do with distros.

My monitor -- a Dell 2410 -- has no default, just a 0-100 scale. If you see no change when you adjust your monitor's sharpness control, perhaps it is not adjusting sharpness at all. I don't understand the point about distros.

---

### Post by silv3rm00n on 2013-06-12
All linuxes can now render fonts exactly the same beautiful way.
Just hack your .fonts.conf file

Here is my version that makes your fonts look gorgeous.

[https://gist.github.com/silv3rm00n/5599072](https://gist.github.com/silv3rm00n/5599072)

Also install Droid Sans, Noto sans from google free fonts.
You cannot get fonts any better than this.

Silver

---

### Post by VanillaMozilla on 2013-06-12
Warning:  sometimes called "fritterware".

---

### Post by BubuXP on 2013-06-12
> **Fritterware:** Software with excess capability that serves no productive end. The term describes anything that eats huge amounts of time for quite marginal gains in function but seduces people into using it anyway.

What you consider "fritterware"? The obsessive search for the best font rendering?

---

### Post by buzzingrobot on 2013-06-12
> **VanillaMozilla said:**
> Warning:  sometimes called "fritterware".


Almost all my computer time is spent reading and writing, then rinse and repeat. I want the text on my screen to look as good as it possibly can, ideally as good as the best hard copy text.

Does time spent trying to work up a better display boost productivity (speaking of obsessions) ? I dunno, but it's not really important to me.

---

### Post by BubuXP on 2013-06-13
As said before, the best way to improve font rendering on screen is having a good monitor. The more DPI (or better [PPI](http://en.wikipedia.org/wiki/Pixels_per_inch)) it has, the better it is. At some high DPI values there will be no need for font hinting.

---

