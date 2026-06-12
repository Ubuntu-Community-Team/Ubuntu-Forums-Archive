---
title: "wifi-radar woes in Edgy"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by happy-and-lost on 2006-10-27
I move around quite a bit, so I need wifi-radar to manage all my various wireless passwords etc., and it worked just fine in Dapper, but under Edgy I can't edit the connections that it's picked up, nor is there a connect button :(

[CENTER][IMG]http://i86.photobucket.com/albums/k98/happy-and-lost/Ubuntu/Screenshot.png[/IMG]

](*,)[/CENTER]

---

### Post by Metacarpal on 2006-10-27
This is, I think, a legacy of a [flaw in the current gnome-system-tools package]("https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/59159").

I am currently using another network switching applet.  I'm at work on a &@#% Windows machine right now, though, and I won't be home 'til late-late tonight.  Will post package name when I get a chance.

---

### Post by sebaxtian on 2006-11-10
I have had the same problem. I solved it editing 'interface' line in /etc/wifi-radar.conf (interface = eth1).

Hope it works.

---

