---
title: "CD / DVD creator Preferences"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by OriginalGrumpyOldMan on 2007-04-07
As I'm settling into the everyday usage of Ubuntu, I have burned today my first (data) DVD using the pre-installed CD/DVD Creator (Nautilus?), no particular problem.

However, I could not find any preferences dialog for it, and the built-in help and a search here and in Google didn't help much either. I'm aware of the options regarding the handling of a newly inserted CD / DVD (blank or otherwise).

However, I could not find any burn settings, specifically:

- How to choose between a multi-session burn or a Disc-At-Once (non-multi-session)
- How to choose whether to enable Verify after write

Can these be configured somewhere for the built-in burning app, or do I need to look for an alternative dedicated disc-burning app?

Cheers for any help!

---

### Post by RomeReactor on 2007-04-07
Hi. I don't think the Nautilus burning application has those features (though i may be wrong); you could try with GnomeBaker or K3B instead.

---

### Post by OriginalGrumpyOldMan on 2007-04-07
I'll give it a try. Seems to be on low maintenance though, not many updates for a while.

Usually I prefer a minimum of additional installs, so if anyone has any suggestions regarding the built-in burner, I'm still interested.

---

### Post by rklk on 2007-08-29
Well, I encountered the same issue here with multi session CDs in Nautilus burner.

And as of today there are a few options which you can customize trough gconf-editor. These include:
[LIST]
[*]burnproof
[*]debug
[*]default speed
[*]overburn
[*]temp_iso_dir
[/LIST]

You can find it (and descriptions) in gconf-editor under /apps/nautilus-cd-burner.

So unfortunately, Nautilus seems to lack multi session support which would be quite awesome. :) Maybe I will just file a request for it if nobody have done already.

Actually it's kind of weird that it is not implemented yet or even discussed as people noticed this over two years ago: [http://ubuntuforums.org/showthread.php?p=541750](http://ubuntuforums.org/showthread.php?p=541750)

There is [Gnome's bugzilla]("http://bugzilla.gnome.org/browse.cgi?product=nautilus-cd-burner") and [launchpad]("https://launchpad.net/nautilus-cd-burner/") dedicated to nautilus-cd-burner.

---

