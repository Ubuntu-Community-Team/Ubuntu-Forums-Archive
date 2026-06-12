---
title: "How do I update a program (e.g. Firefox)"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by David Floyd on 2007-01-25
Yesterday I installed 6.06 and today (with guidance) I've got the nVida driver to work.

Now I thought I would update Firefox.  I'm used to used to 2.0.0.1 on Windows, but Firefox on Ubuntu is 1.5.0.9 and the update item on the menu is greyed out.

I downloaded version 2 from the Mozilla site, but being only a newbie of 2 days I don't now know where the file is AND I also don't know who to load it from the compressed file.

I've looked it Synaptic but it didn't seem to be there.

Could some kind sole quide me in simple terms please.

Thanks,
David

---

### Post by benuski on 2007-01-25
The 2.0.0.1 version is in the Edgy(6.10) repositories, not in the Dapper (6.06) repositories.  If you want to manually install the new version of firefox, use the info found in [this]("https://help.ubuntu.com/community/FirefoxNewVersion") wiki page.  
To get this version on 6.06 through the repositories, try enabling backports, direction to be found [here]("https://help.ubuntu.com/community/UbuntuBackports").  However, there is no guarentee that Firefox has been backported, but it probably has.  Or, if you really want to, you could upgrade to Edgy.

---

### Post by r4ik on 2007-01-25
Try,

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

Good luck !

---

### Post by Frank Golden on 2007-01-25
> **r4ik said:**
> Try,

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

Good luck !
The script from Aysiu at psychocat works for me.
It downloads the latest FF and installs it, links your plugins,extensions and maintains your
bookmarks. Follow the directions on the link. If after installing the new FF you want
to update manually just open FF by typing in terminal ```
gksudo firefox
```.
This opens Firefox in root mode (no bookmarks etc.) where the update button is not greyed out. Use root mode for this purpose only.

---

