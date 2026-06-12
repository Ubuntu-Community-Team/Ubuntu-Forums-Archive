---
title: "Serious bug:  G3 PPC+Rage 128 Ultra+Ubuntu 12.04+E17(from Ubuntu repo)"
date: 2013-06-12
forum: Apple Hardware Users
---

### Post by rkmugen on 2013-06-12
_**What I Did:**_[INDENT]I installed E17 via Synaptic (just to see what else would be installed along with it).  I also made certain that I have GPU acceleration by downgrading MESA to 7.11.x (needed for the Rage 128).
[/INDENT]

[U][B]The Problem...
[/B][/U][INDENT]If I click the left mouse button on the E17 desktop, I get the "Main" dropdown menu.  But if I hover the mouse on "Applications", and then select "Accessories", I get a pop-up error in a white window saying:
[/INDENT]
[INDENT=2]```
Enlightenment Error

This is very bad, Enlightenment SEGV'd.

This is not meant to happen and is likely a sign of 
a bug in Enlightenment or the libraries it relies 
on.  You can gdb attach to this process now to try 
debug it or you could exit, or just hit restart to 
try and getyour desktop back the way it was.

Please compile everything with -g in your CFLAGS

(F1) Recover      (F2) Exit
```
[/INDENT]
[INDENT]
Can else here verify if you also get this bug?  If you're a PPC user, simply install E17 and follow my procedure above to attempt to replicate it.
[/INDENT]

_**My Opinion...**_[INDENT]Well. this isn't the first time I've used/tried E17, as I've tried it on MintPPC.  One thing that has remained consistent, even to this day was how SMOOTH everything animates... it actually feels every bit as smooth as when I had OSX Tiger installed.  And even when I have a large Firefox window and I'm on a particularly "heavy" page, like Google News, complete with Javascript garbage, I can drag the ENTIRE window around the screen as fast as I can, and the screen redraws/renders it much faster than when I was on Unity, Unity 2d, XFCE... and even LXDE!

I only wish that there was a way to get either the Greybird and Ambiance window decorations to work with E17.  And pair that with Linux Mint icons... that'd be my dream setup!  I also wish there was a PPA that contained compiled binaries that work with PowerPC.
[/INDENT]
[U][B]
Other things i noticed...[/B][/U]
[INDENT]The version in the Ubuntu repo is older than what I see on [http://www.enlightenment.org/?p=download](http://www.enlightenment.org/?p=download).  Naturally.  But I wonder if the newest version of E17 fixes this bug...
[/INDENT]

---

### Post by este.el.paz on 2013-06-15
> **rkmugen said:**
> _**What I Did:**_[INDENT]I installed E17 via Synaptic (just to see what else would be installed along with it).  I also made certain that I have GPU acceleration by downgrading MESA to 7.11.x (needed for the Rage 128).
[/INDENT]
[U][B]The Problem...
[/B][/U][INDENT]If I click the left mouse button on the E17 desktop, I get the "Main" dropdown menu.  But if I hover the mouse on "Applications", and then select "Accessories", I get a pop-up error in a white window saying:
[/INDENT]
[INDENT]
[/INDENT]
_**Other things i noticed...**_[INDENT]The version in the Ubuntu repo is older than what I see on [http://www.enlightenment.org/?p=download](http://www.enlightenment.org/?p=download).  Naturally.  But I wonder if the newest version of E17 fixes this bug...
[/INDENT]


@rkmugen:

Saw your post a couple days ago, but I was busy, so I subscribed to see if there was any followup . . . not surprisingly, there wasn't.  So, I was going to try to follow what you are doing and try it out, but I don't have G3 anything . . . .  I did send a PM to "str8bs" to see if he could drop by and offer some comment, but it seems he must be "dormant" . . . for the time being.

Anyway, I could look into this "Enlightenment" thingie . . . I am searching for the mystic union with Oneness, AKA "enlightenment" so if this app or DE could help with that it might be worth checking out.  But, I don't know if it will help you since I don't think I have Rage 128 or whatever it is . . . .  Maybe Svetlana could try it out, I know she's been complaining about "no acceleration" for quite awhile, maybe if she tries Enlightenment it might move her to a higher state of mind??  : - )))

e.e.p.

[Edit: a couple hours later in the same day: @rkmugen . . . you should move to the G4 processor, I installed e-17 thru Synaptic and tested out your issue, click on desktop and contextual menu dropdowns are OK . . . but all is not well in Enlightenment-land; having arrived in the Enlightenment state . . . a few things are not working, I got an error window saying that "some themes and backgrounds have not transferred over to E-land" . . . and as usual I ignore these kinds of suggestions, I'll have to read it in a bit.  But, and this is a major deal breaker, Suspend button doesn't work . . . have to log out of the E session to get to Suspend.  And, some of the items that I checked off for the "cairo-dock-like" dock do open from there, but then for example the "Application Finder" app could not launch Synaptic, and it didn't launch from the left end of the dock, or from the left click drop down menu.  "There was an error opening Synaptic" was the error message.  So far, just Firefox has launched, and I'm typing this now in FF from within the Enlightenment state . . . but, as some very advanced people have said, "Enlightenemnt isn't all its cracked up to be--just Be, AS you are . . . don't try to hold onto Enlightenment, even the 17th level of it."  : - ))

I'll see if any of this can be adjusted by reading about runnning the "edje_convert" command from something called "libxxxx" ????]

---

### Post by este.el.paz on 2013-06-15
> **este.el.paz said:**
> @rkmugen:

e.e.p.

[Edit: a couple hours later in the same day: @rkmugen . . . you should move to the G4 processor, I installed e-17 thru Synaptic and tested out your issue, click on desktop and contextual menu dropdowns are OK . . . but all is not well in Enlightenment-land; having arrived in the Enlightenment state . . . a few things are not working, I got an error window saying that "some themes and backgrounds have not transferred over to E-land" . . . and as usual I ignore these kinds of suggestions, I'll have to read it in a bit.

I'll see if any of this can be adjusted by reading about runnning the "edje_convert" command from something called "libxxxx" ????]

@rkmugen:  I checked out the "README.Debian" file, which is different than the "README" file . . . both are in /usr/share/doc/e17/README.Debian . . . and found this, have you read it?  I don't know if I want to run this "configure" command or not, if it would do nothing to my LXDE DE that would be OK, so far the LXDE in Xubuntu 12.04 is working the best on my iBook, the E17 deal has a little more eye flash, but so far not everything is working, so, it's "busted Enlightenment" . . . .  Any thoughts?

> e17 0.16.999.55225 upgrade notes
---------------------------------
This version of e17 uses a new format to store themes and backgrounds.
If your usual themes or background no longer work correctly, you need to update
them. To do this, please run the 'edje_convert' command (from the 'libedje-bin'
package) on all themes and backgrounds that need converting.

Usually, user-supplied themes and backgrounds are located in ~/.e/e/themes
and ~/.e/e/backgrounds, respectively. A simple 'find ~/.e -name \*.edj'
should be enough to find all themes and background.

  -- Albin Tonnerre <lutin@debian.org>  Sun, 03 Apr 2011 18:34:21 +0200


Enlightenment DR0.17
--------------------
About the menu files
  Enlightenment handles the menus according to the FDO menu specification.
  In order to have an 'Applications' menu, you need to use a .menu file.
  Please see [http://wiki.enlightenment.org/index.php/E17_and_Efreet](http://wiki.enlightenment.org/index.php/E17_and_Efreet) for further
  information.
  If no menu is found, then /etc/xdg/menus/enlightenment-applications.menu,
  provided by the 'e17-data', package, will be used as a fallback

  -- Albin Tonnerre <albin.tonnerre@gmail.com>  Thu, 01 May 2008 12:58:45 +0200



e.e.p.

---

### Post by este.el.paz on 2013-06-15
> **rkmugen said:**
> _**What I Did:**_[INDENT]I installed E17 via Synaptic (just to see what else would be installed along with it).  I also made certain that I have GPU acceleration by downgrading MESA to 7.11.x (needed for the Rage 128).
[/INDENT]


[INDENT] I only wish that there was a way to get either the Greybird and Ambiance window decorations to work with E17.  And pair that with Linux Mint icons... that'd be my dream setup!  I also wish there was a PPA that contained compiled binaries that work with PowerPC.
[/INDENT]


@rkmugen:

In terms of your request for "Linux Mint icons . . . rsavage posted a bunch of stuff backported or whatever to work with PPC on the "Testers wanted for 12.04" thread . . . did you see any of those posts or try any of the packages out?  I don't know if they are still available there, he took his Xubun 12.04 for PPC package down . . . he also posted a link to a thread in the LM forums about how somebody got an updated MATE DE that was "mint-like" but I don't think that was for PPC . . . .  But check out the rsavage packages and see if it will do anything for you.

e.e.p.

---

### Post by rkmugen on 2013-06-16
I appreciate your effort, e.e.p.  But I think I'll settle with XFCE after all.  Seeing as how I've gotten so familiar with Linux Mint 13 XFCE on my x86 PC.  It's such a shame though; I mean, despite E17's bugs and modestly steep learning curve (compared to Gnome, XFCE, and LXDE), the performance/responsiveness it yields on pure software rendering alone is relatively astounding and shows much promise.

Actually, no, I didn't see the Readme file(s).  In fact, i didn't even notice that I had any installed!  Oh well, it's too late anyway; I uninstalled it and I imagine that it'd be a long time before I try Enlightenment again.  Perhaps when they release E18, perhaps things might be better (one would hope).

---

### Post by este.el.paz on 2013-06-16
> **rkmugen said:**
> I appreciate your effort, e.e.p.  But I think I'll settle with XFCE after all.  Seeing as how I've gotten so familiar with Linux Mint 13 XFCE on my x86 PC.  It's such a shame though; I mean, despite E17's bugs and modestly steep learning curve (compared to Gnome, XFCE, and LXDE), the performance/responsiveness it yields on pure software rendering alone is relatively astounding and shows much promise.

Actually, no, I didn't see the Readme file(s).  In fact, i didn't even notice that I had any installed!  Oh well, it's too late anyway; I uninstalled it and I imagine that it'd be a long time before I try Enlightenment again.  Perhaps when they release E18, perhaps things might be better (one would hope).

@rkmugen:

Dude, I was trying to bring some attention to your thread from someone who might actually know something, but you've already wiped it out . . . OK, well the thought of erasing E-17 also occurred to me, since there are issues with it also in the G4 arena, and there was some bleed over to the LXDE realm.

Speaking of XFCE . . . it should be in rsavages packages if there isn't anything in Synaptic for PPC.  I had LM13 MATE 64 bit installed, but it developed a strange problem with the cursor when typing on the built-in keyboard on the MBPro, and couldn't get any insights on a fix for it, so I zero-ed it out . . . went to Xubun 64 bit 12.04 until a couple weeks ago, then tried LM15 Cinn 64 bit--it's nice, but the problem with the keyboard bug is still there.  One thing I miss about the LM 13 MATE is the Floating Feet screensaver, I might go back to LM 13 just to have those feet floating around on my screen . . . very funny, very close to attaining "Enlightenment."

e.e.p.

---

