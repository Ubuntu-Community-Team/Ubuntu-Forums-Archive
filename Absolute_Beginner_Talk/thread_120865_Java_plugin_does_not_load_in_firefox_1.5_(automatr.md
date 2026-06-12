---
title: "Java plugin does not load in firefox 1.5 (automatrix)"
date: 2006-01-23
forum: Absolute Beginner Talk
---

### Post by Mortimer on 2006-01-23
Ok, so I ran Automatrix to get firefox 1.5, which worked, but none of the plugins that came along with that set are loaded. I even tried running animatrix again selecting firefox 1.5, and it goes through all the tasks, skipping all the stuff that's already there, and it says java 1.5+update5 is already installed, or something to that effect. Then I tried installing java 1.4 from the ubuntu Add Applications, and it installed, but it won't load it's plugin in firefox.

So I'm guessing I did something wrong and now the plugins are not linked to firefox. Could someone tell me the Dummies version of how to link the plugins?

Btw, before all this, I followed these instructions from another site in an attempt to install ff 1.5 by itself:

> First, you need to download the firefox archive file on Get Firefox
After downloading the needed file, it was very simple because it's just a matter of executing only 3 commands :

tar -xzvf firefox-1.5.tar.gz
sudo mv firefox /usr/local/
sudo ln -s ../firefox/firefox /usr/local/bin/

That's all folks !

...but it didn't work (and ff wouldn't even load from the menu after that). So I'm guessing this is what botched things up. Any help on reversing this?

---

