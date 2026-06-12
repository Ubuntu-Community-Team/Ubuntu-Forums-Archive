---
title: "Firefox using 50% of my CPU"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by Sparkster185 on 2007-09-14
I've tried searching the forums, but none of the results were relevant to my issue.

Firefox has been my browser of choice for some time.  However, in the last week or so, Firefox has been a CPU hog (~50% whenever it's open, regardless of opening a new page or just viewing).

I thought it might be some of my extensions, but I did an apt-get remove firefox and re-installed it and it's still happening.

This was never a problem before, I'm thinking one of the recent updates caused the problem?  I'm stuck using Konqueror and it's no where near as nice as Firefox.

BTW, I am running Kubuntu, but using Gnome desktop.

---

### Post by por100pre1 on 2007-09-14
Try renaming your /.mozilla/firefox folder to check if it is somehow damaged. You can also try [Opera]("http://www.opera.com/download/") if you haven't done so previously.

---

### Post by Sparkster185 on 2007-09-14
Renaming ~/.mozilla worked perfectly.

Thanks!

P.S.  Any idea why/how that would have gotten corrupted?

---

### Post by por100pre1 on 2007-09-14
That happened to me a lot when using Firefox in Windows. No idea why. Glad to help! 8)

---

### Post by Sparkster185 on 2007-09-14
It happens in Windows too?  So it's not a platform issue, weird.  

I never had this happen to me before.  I used Firefox on XP for two years and never had to do this.

Do you know what extensions you were using?  I had installed:

Mouse Gestures, Session Manager, Ad-Block Plus and Web Developer.

Do you think this is something I should report to the Firefox devs?

---

### Post by por100pre1 on 2007-09-14
Only Web Developer here, but it happened to me without that extension installed. Don't forget to move your bookmarks to your new profile folder.

---

### Post by alienexplorers on 2007-09-14
Here's a list of other extensions with problems;
> [http://kb.mozillazine.org/Problematic_extensions](http://kb.mozillazine.org/Problematic_extensions)

---

### Post by Wiebelhaus on 2007-09-14
> **por100pre1 said:**
> Try renaming your /.mozilla/firefox folder to check if it is somehow damaged. You can also try [Opera]("http://www.opera.com/download/") if you haven't done so previously.

just to reiterate this users sound advice.

---

### Post by cprise on 2007-09-24
I have the same problem with Kubuntu 7.10. Firefox has started chewing up 30-70% of my CPU, just within the last couple weeks.

I think it may have something to do with GTK theming, because at about the same time the "rough edges" disappeared from the firefox GUI... scrollbars, menus and such now have a 'candy' look where they used to be flat.

I haven't tried changing my profile, and probably won't. I have far more in there than just bookmarks.

---

### Post by p_quarles on 2007-09-24
Firefox has gotten pretty clunky and buggy since its first release. Anyway, for those of you having these types of problems, you might want to look at [Swiftfox]("http://getswiftfox.com/"). It's a Firefox build that's optimized for Linux, with different packages for each major architecture.

---

### Post by cprise on 2007-09-25
OK, I have a workaround:

For me, the CPU wastage problem only occurs if I am using the **default Firefox theme.** This is 100% reproducible.

When I switch to another theme, like Aquamarine, the GTK-KDE-integrated menus go away and they become flat and plain... and FF idle CPU usage remains consistently below 1%. As soon as I switch back to FF default theme, CPU usage starts at 4% and after 15 min of browsing goes above 15% and stays there even if I close all web pages.

Before changing the theme, I tried turning off Java with no effect.

One thing I did do at around the time the problem started was install Miro. Up to that point I had a Kubuntu 7.10 KDE desktop with only a couple isolated GTK programs including a clunky-looking Firefox 2.0.0.6. But Miro pulled in a handful of the common **Gnome** packages along with it, and I think this caused GTK (and FF which uses GTK) to change its behavior. Incidentally, the other GUI enhancements like buttons and scrollbars are still there with the other themes... the only difference I can detect is that the drop-down and context menus now look just like KDE menus if the default FF theme is used, while the menus remain flat when using the other themes.

So I think we have a bug here that relates to how Firefox reacts to GTK-KDE theme integration.

---

### Post by cprise on 2007-10-05
UPDATE:

The problem only exists if BOTH the default Firefox theme and the NoScript extension are being used. It seems I overlooked the presence of NoScript earlier, however it causes no problems if I use any other theme.

I reproduced the problem on a bare Kubuntu 7.10 install, so Miro/Gnome aren't the culprit. It is a problem with Firefox on Linux (or K/ubuntu), and I can verify that I haven't seen a CPU problem like this on Firefox Mac in a very long time.

Soon I will be doing an install of CentOS 5 and will try to reproduce the problem on that system.

---

### Post by abhilash82 on 2007-10-05
I have the same problem with Firefox. Tweaked some cache memory settings in it and the consumption reduced. But still it was quite large.. I have switched to Opera now and have no problem with it.

---

### Post by sachutney on 2007-10-08
I have been having major problems with firefox of late. 

1) just when it is idle - with a few pages open - it eats over 50% of cpu
2) when I use google docs it crashes (or more correctly freezes).

Both of these problems where solved in Camino.


I am not a super duper computer guy -

I work on OS X

I am not sure how to rename /mozilla (what do I rename it too?)

Also, how do I uninstall the greasemonkey script.

---

### Post by esc1 on 2007-10-08
I have had the same problem with a different theme.  I use the cyclence them and have seen high cpu usage.  I just try and keep the number of tabs down.

---

