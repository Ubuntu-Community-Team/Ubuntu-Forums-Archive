---
title: "Firefox and RealPlayer"
date: 2006-03-31
forum: Absolute Beginner Talk
---

### Post by janki on 2006-03-31
I installed Firefox according to the description on [https://wiki.ubuntu.com/FirefoxPlugins]("https://wiki.ubuntu.com/FirefoxPlugins"). RealPlayer works fine when I start it from the terminal, and also as a plugin in Mozilla. But when I try to run it as a plug-in in Firefox it doesn't work. I tried uninstalling and re-installing Firefox, but still it doesn't work.

I've looked at other threads in this forum, but I haven't found anything that makes Firefox acknowledge my installation of RealPlay.

There must be a lot of other people that have had the same problem. Anybody have a solution

---

### Post by Stereotypical Rage on 2006-03-31
Have you tried Helix?

---

### Post by teataster on 2006-03-31
I had the same problem having installed FF 1.5.0.1 because the Real installs the needed files to the Mozilla folder.  Per the help on the [www.bbc.co.uk](www.bbc.co.uk) site, copy nphelix.so and nphelix.xpt from the mozilla install plugins folder /usr/lib/mozilla/plugins to the 1.5.0.1 folder /opt/firefox/plugins, close and restart FF and all should be well.

Why it doesn't install to the mozilla-firefox install folder, I don't know!  Bear in mind that you might have to do this again if you upgrade Realplayer/FF in the future.

HTH!

---

### Post by janki on 2006-03-31
[QUOTE=teataster]I had the same problem having installed FF 1.5.0.1 because the Real installs the needed files to the Mozilla folder.  Per the help on the [www.bbc.co.uk](www.bbc.co.uk) site, copy nphelix.so and nphelix.xpt from the mozilla install plugins folder /usr/lib/mozilla/plugins to the 1.5.0.1 folder /opt/firefox/plugins, close and restart FF and all should be well.

Why it doesn't install to the mozilla-firefox install folder, I don't know!  Bear in mind that you might have to do this again if you upgrade Realplayer/FF in the future.

HTH![/QUOTE]

This worked perfectly! Though, don't understand why the installation can't do this automatically. Anyway, thanks!

---

### Post by trent dillman on 2006-03-31
Installing FF to /opt doesn't install it the way that most programs are installed, which is why it didn't pick it up. This also goes for Flash, Java, etc.

---

