---
title: "Solution to adding a new screen resolution"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by mjpatey on 2007-02-06
Hello, Group-

I posted last night about my problem in the Feisty Live CD install, and can't find the post for the life of me, so here's what I did to fix the problem I was having.

For some reason, Feisty Beta (if that's what it's called?) simply listed my monitor as "Generic", and didn't allow its native resolution, which for an LCD, makes for big ugliness.  It looked awful at 1024x768, and desperately needed to be switched to 1280 x 1024.

I went to the Dell website, looked up its manual (the Dell 1801FP) and found the horizontal sync rate to work with 1280 x 1024 at 60Hz vertical sync (it turned out to be 64 for horizontal).

I changed the horizontal sync in xorg.conf under "Monitor" to 64, and the vertical sync to 60 (I didn't name a range, just those 2 numbers, because the LCD monitor looks awful at any other resolution anyway).

Then further down in xorg.conf, under "Display" I added "1280x1024" (no spaces, quotes included) in the "24" depth subsection (as 24 bit is selected as my default color depth).

I rebooted, and voila!  Pretty 1280 x 1024 resolution.

I think I forgot to subscribe to my original post, so finding it and adding this text to it was nearly impossible.

I hope this helps someone!

-Mark

---

### Post by jingo811 on 2007-02-06
yeah it sure is helpful so I'm gonna bookmark it for future use when I have more time.  But I'm too afraid of messing directly with forced hardware configurations, I always manage to do something wrong which results in [COLOR="Red"]Red Alert, Red Alert![/COLOR]

I hope the Ubuntu/Linux programmers can make a more permanent solution for this!  Clickable options that shows all your monitors specs yet doesn't exceed your monitors hardware specs.  This tech stuff is too hard for me to mess with.

---

### Post by mjpatey on 2007-02-06
Jingo,

Don't worry about making a mistake.

When you first open a file like xorg.conf, save a backup copy of it before making any changes.  One popular method is adding the date to the end of the filename, like "xorg.conf.2007-02-06".  Then make your changes, and re-save as "xorg.conf", overwriting the original.  But now you have your date-stamped backup file in case you need it.

With a file like xorg.conf, if you have to restore the backup, you're sometimes stuck doing so from the command line, because if you muck it up it breaks the GUI.  That's the only danger.  If you can get used to working from the command line in emergencies like that, life feels a lot safer, and you have more power and flexibility.

That said, amen to your comment!  I'd love to be able to make theses changes in an easy-to-understand dialog box!

-Mark

---

### Post by Jimmy_r on 2007-02-06
This may or may not work with every screen, but I discovered this on my LG Flatron L1950H(Native 1280x1024, auto-set to 1024x768 in xorg.conf):

If I completely removed the lines that specified sync and refresh, and also removed the sections specifying resolutions, 
the x server would auto detect the correct settings and boot up in native 1280x1024!(This was a small shock to me)

My guess is that the x server in edgy and later is advanced enough to recognize the correct settings, 
but the debian(ubuntu) installer is not adapted to this yet so it specifies a faulty setting in xorg.conf, which overrides the correct, auto-detected setting.

And it appears as the xorg.conf will even be unnecessary for the xserver after the two next releases(Xorg 7.3)

So, then the only needed tool to change resolutions will be the one that is currently in ubuntu (System->Settings->Resolution) or in the kde settings manager...

---

### Post by moshuptrail on 2007-02-06
If you are looking for your previous thread or posts, click on Search above, and near the bottom (you might have to scroll up) you can select "My Threads" or "My Posts".  Very handy if it's the next day and you want to get back where you left off.

---

### Post by mjpatey on 2007-02-06
Jimmy,

Wow, that's pretty interesting.  I hope your news about xorg.conf being replaced by GUI functionality comes to pass!  Pain in the butt, editing that thing.  (I guess that sounds anti-Linux, but it wasn't meant to.)

Thanks, moshuptrail... I knew it was somewhere, but it seemed more logical to look in the control panel.  It's been a while for me!  Good to be back.

-Mark

---

### Post by Jimmy_r on 2007-02-07
From [http://community.linux.com/article.pl?sid=06/11/13/2112259&from=rss]("http://community.linux.com/article.pl?sid=06/11/13/2112259&from=rss")
> According to Packard, X.org 7.3 shouldn't even require an xorg.conf -- everything should be autodetected at run time. X.org will receive information about new devices dynamically from D-Bus.

According to [http://wiki.x.org/wiki/ChangesForX11R73]("http://wiki.x.org/wiki/ChangesForX11R73")
Both XInputHotplug and Output hotplug have already been checked into git.

So yes, we live in exciting times :)

---

### Post by Limitless on 2007-02-08
> **Jimmy_r said:**
> 
If I completely removed the lines that specified sync and refresh, and also removed the sections specifying resolutions, 
the x server would auto detect the correct settings and boot up in native 1280x1024!(This was a small shock to me)


This solution oddly enough also worked for me. I have a sony flatpanel that's relatively old. It actually detected my monitor correctly but for whatever reason put in extremely low resolution defaults so I could not change the resolution through the system menu. Jimmy's fix (surprisingly) worked perfectly upon restart and I was immediately booted into a higher resolution. Thanks for the help!

---

