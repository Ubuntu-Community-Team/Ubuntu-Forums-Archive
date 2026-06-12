---
title: "Boot slowdown after trying live DVD"
date: 2009-04-26
forum: Apple Hardware Users
---

### Post by Aurora on 2009-04-26
Hello,

I'm running a first generation MacBook, dual booting Ubuntu Studio (Hardy) and OS 10.4.11.  It was running pretty well, aside from problems with using JACK for audio production.

I think I have done some damage with the AVLinux 1.0 Live DVD. It booted up fine, I played with it for awhile, then shut down and removed it. Now, it takes several minutes to get to the rEFIt screen.  If I boot into Ubuntu,
the penguin splash screen will sit there for another five minutes or so before the GRUB screen shows up, then it's normal from there. ("Normal" meaning no video unless I use recovery mode, but I can live with that). In OSX, it takes longer than usual to get to the login screen, and the keyboard, mouse, and trackpad are not enabled when it gets there. After another couple of minutes I can log in.

What could have happened?  I thought live cds/dvds didn't change anything on the hard drive.  Before installing Ubuntu, I had tried several live CDs with no problem.  Any ideas how to fix this?

--Paul in Seattle

---

### Post by cyberdork33 on 2009-04-27
I really don't know what could have caused what you are describing. There are something that could alter your files:

[LIST=1]
[*]the LiveCD you used automounted your HFS+ partition and altered something: bad, shouldn't happen.
[*]Some of what you are saying sorta describes rEFIt not being blessed correctly, you could try reblessing it (the enable-always.sh script in the refit folder).
[/LIST]

---

### Post by Aurora on 2009-05-02
For the record, it spontaneously normalized...I have no explanation.

I had a similar phenomenon with my AMD 64 desktop a few weeks ago after running some routine updates.  The slow booting also disappeared, although much quicker than the MacBuntu...that's why I asked for help; I didn't think it would come back by itself like the desktop.

Apparently much ado about nothing...although it is still puzzling.

---

