---
title: "Firefox Profile Gone"
date: 2005-11-17
forum: Absolute Beginner Talk
---

### Post by justjuice on 2005-11-17
Yesterday when I tried to fire up another Firefox instance, it wouldn't let me do so with my default profile. So I just created another one, called Extra.  Today, when I started up Firefox, all my bookmarks, home page setting, links, history etc were all gone.  

I tried launching firefox through a terminal : firefox -p default, but that just opened a little profile dialog box asking me to select a profile, but there were none to select from.  

In my .mozilla/firefox directory there are two directories that seem to correspond to the two profiles: t2kszhkt.default and xupwmeog.Extra

I also tried to edit the profiles.ini, but it doesn't seem to make any difference. I changed StartWithLastProfile from 1 to 0, and moved the Default=1 from [Profile1] to [Profile0]:

[General]
StartWithLastProfile=0

[Profile0]
Name=default
IsRelative=1
Path=t2kszhkt.default
Default=1

[Profile1]
Name=Extra
IsRelative=1
Path=xupwmeog.Extra


So, how can I make it so that Firefox launches with my original profile?  And is my original profile still there, or am I mistaken?  Thanks.

---

### Post by manicka on 2005-11-17
Try renaming the folder called xupwmeog.Extra to bak.xupwmeog.Extra

---

