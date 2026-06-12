---
title: "Ugly background of boxes buttons in Firefox 3 under Aurora"
date: 2008-03-03
forum: Art &amp; Design
---

### Post by joemok on 2008-03-03
I have been using Aurora 1.4, and midnight theme. But recently I have changed to firefox 3.0 beta 3. It usually incorporates well with the theme, but not all the aurora themes.

How can I make the background outside the box, which is a bit grey, disappear? Even the buttons in the menu appear to suffer the same problem. 

PS: it seems to the problem of firefox only, as the buttons in gedit, etc. are totally fine.

Anyone facing the same problem?

---

### Post by DJ_Peng on 2008-03-03
What is Aurora 1.4? Also, keep in mind that Firefox 3 is a beta, which means that things are still changing for it. Just in the past week there have been some major changes to themes in Fx3beta that have sent themers scurrying to fix their themes.

While your problem seems to be strictly in Fx3beta, and they're making Firefox 3 more integrated with the OS, the issue could be resolved when Fx3b4 hits in the next week or so. In other words it may be a temporary issue due to something specifically in that beta.

---

### Post by smartboyathome on 2008-03-03
By the way, DJ_Peng, Aurora is a GTK engine.

---

### Post by DJ_Peng on 2008-03-03
Thanks. I knew it sounded familiar but I couldn't place it.

---

### Post by joemok on 2008-03-03
Thanks every one.

I might just wait for beta 4 of firefox.

---

### Post by genuchelu on 2008-07-29
firefox has been officialy out for a while and the problem still exists...I think the bug lies in the engine..and was never adreesed

---

### Post by spupy on 2008-07-30
[http://ubuntuforums.org/showthread.php?t=857468#5](http://ubuntuforums.org/showthread.php?t=857468#5)

---

### Post by genuchelu on 2008-07-30
That explains the problem a little more, but there is no solution...

---

### Post by DJ_Peng on 2008-08-02
It sounds like an Aurora/GDM theme has the "ugly icons". Have you tried picking another theme, then starting Firefox to see if it resolves the problem? It may also be a case of being a bug wherein Firefox 3 looks for Gtk widgets that Aurora doesn't provide properly so it takes the last supplied icons from a GDM theme. In that case I'd suggest filing a bug on Bugzilla against Firefox 3 as well as a Launchpad bug against Aurora (after looking to see if someone's already reported it, of course) so the devs can see about resolving the matter.

---

