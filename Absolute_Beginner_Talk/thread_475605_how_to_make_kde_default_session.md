---
title: "how to make kde default session"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by drshrikant on 2007-06-16
just installd the kubuntu desktop...

and am in love with it.. absolutely..

plz help me with this...

how do i make the kde as my default session...

---

### Post by Happy_Man on 2007-06-16
ANOTHER CONVERT!!!!! START THE CELEBRATION!!!!!!! *throws confetti*

Assuming you have the default login manager (eg brown all over):

Choose KDE from the options, then enter username and password, and when it pops up a window asking if you want to make default, make it default. Easy! NOW WHERE'S THE PARTY??????

---

### Post by drshrikant on 2007-06-16
login manager is kde.. im in a kde session now.. how do i make this my default

---

### Post by Austin_KW on 2007-06-16
If you installed ontop of ubuntu then your login manager is probably still gdm even if your window manager is kde. I think gdm will still remember your last session (kde) so it should be the default.

If you want to use the additional features of the kde display manager (auto login, passwordless login, blue login screen,etc)  then you need to switch to kdm.
sudo dpkg-reconfigure kdm
and select kdm from the list.

---

### Post by HotShotDJ on 2007-06-16
> **drshrikant said:**
> just installd the kubuntu desktop...
and am in love with it.. absolutely

\\:D/  -- Keep one thing in mind... KDE doesn't get as much love from Ubuntu developers as Gnome.  BUT, that may change after KDE 4.  MANY changes going on upstream, so it would be kind of a waste of resources for Ubuntu developers to put in a lot of work into the 3.5.* series.

---

