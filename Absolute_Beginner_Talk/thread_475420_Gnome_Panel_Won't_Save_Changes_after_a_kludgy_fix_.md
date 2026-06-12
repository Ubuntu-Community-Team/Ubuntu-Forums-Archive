---
title: "Gnome Panel Won't Save Changes after a kludgy fix ..."
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by dpneal on 2007-06-16
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/5227](https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/5227) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I ran into an issue when GAIM wouldn't show up in the notification area in a Gnome panel, despite recreating the panel and the notification area a couple of times.

This issue was described at this url:

[https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/5227](https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/5227)

I "fixed" the problem, by, as that threat suggested, creating a new user and overwriting my

$HOME/.gconf/apps/panel

With the contents of the new user's panel.

Gaim works well now, and everything is great -- except when I restart Gnome or Ubuntu, I'm back with default panel settings.

A-ha, thought I, it's a matter of permissions.  

I tried:

```
sudo chown mylogin:mylogin /home/mylogin/.gconf/apps/panel/
```

No luck, unfortunately, as my panel changes are still discarded when the window manager restarts.

Ideas?

Thanks in advance,

Dan

---

