---
title: "Irc problem"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by brisingr_dagger on 2007-01-08
Im curently at uni and cant ge on to IRC because it is being blocked by my uni anyone know how i can get aroud the firewall

---

### Post by xopher on 2007-01-08
> **brisingr_dagger said:**
> Im curently at uni and cant ge on to IRC because it is being blocked by my uni anyone know how i can get aroud the firewall

How have they blocked it? They might just have blocked the most used ports [6667-6669], so try connecting with another port. Or, you could set up a shell, and ssh into it, run irssi or any other text based IRC client from there.

---

### Post by kj1h234lkj1234 on 2007-01-08
> **xopher said:**
> How have they blocked it? They might just have blocked the most used ports [6667-6669], so try connecting with another port. Or, you could set up a shell, and ssh into it, run irssi or any other text based IRC client from there.

That's exactly what I do.

Our admins use SSH to administer their servers remotely, so it's one of the only ports that is not blocked (others being 25, 80, and 443 naturally). SSH + screen + irssi = winner! :D

You could also set up an IRC proxy (a "BNC") on a computer of yours outside your university on a port that is not blocked, then just bounce your connection off of that.

---

