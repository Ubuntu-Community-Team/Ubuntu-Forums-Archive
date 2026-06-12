---
title: "Switching between desktops"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by Donnut on 2006-08-17
As it says in the title, how do I change desktops if startx is used from command line?  I accidently enabled something like "network logon" from the logon screen in gnome, it boots up in recovery mode in root in XFCE mode only, so I can't reconfigure the logon screen for gnome.

I really want my linux back :(

---

### Post by zxee on 2006-08-17
Ubuntu is set up slightly different than debian? I think
But the command to change your default DE is
> echo "exec startgdm" > ~/.xinitrc

I apologize if that's not quite right. I can't seem to find a ~/.xinitrc  file on my dapper install but that's how it's suppose to work.
Also check out the guide here: [http://ubuntuguide.org/wiki/Dapper#Make_it_start_when_you_login_thru_GDM](http://ubuntuguide.org/wiki/Dapper#Make_it_start_when_you_login_thru_GDM)

---

