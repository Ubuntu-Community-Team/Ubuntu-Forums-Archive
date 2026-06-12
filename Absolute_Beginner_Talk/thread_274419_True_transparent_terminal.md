---
title: "True transparent terminal"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by aktiwers on 2006-10-09
So how do I get this?
I have XGL + Beryl and would like my Terminal to be true transparent.

I mean, if there is a window behind the terminal, it should be show as well.. and not only the desktop.

Anyone knows how to do the trick?

---

### Post by po0f on 2006-10-09
aktiwers,

[rxvt-unicode](http://packages.ubuntu.com/dapper/x11/rxvt-unicode) has real transparency.  You will either have to [get the latest sources](http://dist.schmorp.de/rxvt-unicode/) and compile it yourself (you will need [libxft-dev](http://packages.ubuntu.com/dapper/libdevel/libxft-dev) and [libperl-dev](http://packages.ubuntu.com/dapper/libdevel/libperl-dev)) if you are using Dapper, or upgrade to Edgy, which has rxvt-unicode-7.7.

[EDIT]  Just to clarify, Dapper's rxvt-unicode-7.0 doens't include real transparency.

---

### Post by jordanmthomas on 2006-10-09
If you are on Edgy, then you have Gnome 2.16
gnome-terminal 2.16 has true transparency built in.  Best of all, the letters don't go transparent, so you can still read it.

Right click in the terminal, and edit your profile.  In the effects tab, there is the option for transparency.

Of course, if you still have Gnome 2.14 this will be fake transparency, so you might want to go with rxvt as suggested.

---

### Post by AndyCooll on 2006-10-09
You get it by opening up your GNOME terminal. 

Then select Edit-->Profiles.

Highlight the profile you want to be transparent and select edit. 

One of the tabs is "Effects" and in here you can choose "Transparent Background". You then use the slidebar to your desired level of transparency.

:cool:

---

### Post by dbott67 on 2006-10-09
> **aktiwers said:**
> So how do I get this?
I have XGL + Beryl and would like my Terminal to be true transparent.

I mean, if there is a window behind the terminal, it should be show as well.. and not only the desktop.

Anyone knows how to do the trick?

I'm running Ubuntu 6.06 with XGL & Beryl and have set my terminal to true transparency (80%).  Scroll down to "Set Window Attribs by various criteria".  Under "Window Opacity" create a new string with the following text:
```
c:Gnome-terminal:80
```

See the attached screen shots.

-Dave



Open up Beryl Settings Manager,

---

### Post by jordanmthomas on 2006-10-09
Is that Leo Laporte?  The ScreenSavers totally needs to come back on.  </offtopic>

Your solution is good, but it also makes the words transparent.
It's what I used for a good while before upgrading to Edgy though.

---

### Post by dbott67 on 2006-10-09
Yep... that's me, my wife & 2 daughters with Leo back in Dec. 2004.  Leo is still on the air here in Canada.  After TechTV died, Rogers in Canada approached him about reviving Call for Help in Toronto.  The new CFH is a cross between the old ScreenSavers & Call for Help.  Leo flies to Toronto once a month & tapes 15 new shows.  The shows air in Canada, Australia, and a few other places.  You can also watch on Google video ([http://www.callforhelptv.com/callforhelp/video/](http://www.callforhelptv.com/callforhelp/video/)) or via bit-torrent ([http://www.cfhtracker.info/)](http://www.cfhtracker.info/)).

Yes, the transparency/opacity also affects the text.  Apparently, there is something called "copacity" that can fix this.

-Dave

---

### Post by jordanmthomas on 2006-10-09
Sweet, thanks!

---

### Post by corefile on 2006-11-30
using the Gnome-terminal transparancy setting is NOT true transparency. If so you would see other applications behind it. With real transparency when you move the window you would see whatever is behind it, and that does not happen with the transparency setting in gnome-terminal

---

### Post by CatKiller on 2006-11-30
> **corefile said:**
> using the Gnome-terminal transparancy setting is NOT true transparency. If so you would see other applications behind it. With real transparency when you move the window you would see whatever is behind it, and that does not happen with the transparency setting in gnome-terminal

Yes you do, if you have a compositing window manager like Compiz or Beryl. If you're using Metacity then you get pretend transparency, since that's the best you're going to get.

---

### Post by corefile on 2006-11-30
> **CatKiller said:**
> Yes you do, if you have a compositing window manager like Compiz or Beryl. If you're using Metacity then you get pretend transparency, since that's the best you're going to get.

No that does the whole application, not just the transparency settings in gnome-terminal, with Compiz or Beryl you can set transparency for any app. But when you are talking about the preferences of gnome-terminal and setting the transparency, it does not use real transparency, you do not see the windows behind it. Now sure if you set your beryl to make that whole window transparent then yeah, but again that is not the same as just the text field pseudo transparency of gnome-term

---

### Post by jordanmthomas on 2006-11-30
I'm afraid you're wrong corefile.  Here's an example.  Notice the borders are still mostly opaque, while the inside of the terminal is totally transparent, except the text.  

Yes, this is unreadable, but I was just doing it to illustrate the transparency.

---

### Post by corefile on 2006-11-30
OH snap! I stand corrected. :-) Now that looks nice. Are you using beryl or compiz?

---

### Post by jordanmthomas on 2006-11-30
beryl svn on fedora core 6
It usually looks better, but I made it really transparent for the screenshot.

---

### Post by durand on 2006-12-02
cool, nice screenshots.

---

### Post by meldroc on 2006-12-11
Is there anything that's more KDE-friendly?  I remember hearing rumors about newer versions of Konsole having real transparency, as opposed to fake grab-the-wallpaper-and-hope-the-user-doesn't-notice transparency, but the version of Konsole that's in Kubuntu doesn't seem to do that.

---

### Post by jordanmthomas on 2006-12-11
You have to rebuild konsole from source, but a patch for it does exist:
[http://www.kde-apps.org/content/show.php?content=48303](http://www.kde-apps.org/content/show.php?content=48303)

**scratch that, on the same page I found a precompiled link
[http://3v1n0.tuxfamily.org/pool/edgy/beryl-svn/konsole_3.5.5-0ubuntu3-3v1ubuntu0_i386.deb](http://3v1n0.tuxfamily.org/pool/edgy/beryl-svn/konsole_3.5.5-0ubuntu3-3v1ubuntu0_i386.deb)

---

