---
title: "Disable Screen Saver in Ubuntu?"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by jlp09550 on 2007-04-30
Hi there.

I'm pretty well-known when it comes to Ubuntu, but I have one question;
how do I disable to screen saver (screen going off automatically) in Ubuntu?

I saw a topic on disabling it in Xbuntu, but I need Ubuntu.

BTW, I'm running through a basic command line. (just the base system installed)

Thanks,
Jared

---

### Post by bashologist on 2007-04-30
I'm not sure if these are the right keys but you could try them:
```
#To disable the screensaver:
gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type=bool false

#To disable monitor sleeping:
gconftool-2 -s /apps/gnome-power-manager/ac_sleep_display --type=int 0
```Did you want to disable the screensaver or monitor sleeping? If this works make sure to tell us.

---

### Post by jlp09550 on 2007-05-01
> **bashologist said:**
> I'm not sure if these are the right keys but you could try them:
```
#To disable the screensaver:
gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type=bool false

#To disable monitor sleeping:
gconftool-2 -s /apps/gnome-power-manager/ac_sleep_display --type=int 0
```Did you want to disable the screensaver or monitor sleeping? If this works make sure to tell us.


OK, just set the command for monitor sleeping. I'll see if it works actually.

Status1: Waiting..
Status2: Nope, didn't work. Restarting and trying again.
Status3: Nope, didn't work either.

---

### Post by AnRkey on 2007-12-10
> **bashologist said:**
> I'm not sure if these are the right keys but you could try them:
```
#To disable the screensaver:
gconftool-2 -s /apps/gnome-screensaver/idle_activation_enabled --type=bool false

#To disable monitor sleeping:
gconftool-2 -s /apps/gnome-power-manager/ac_sleep_display --type=int 0
```Did you want to disable the screensaver or monitor sleeping? If this works make sure to tell us.

Thanks very much, it works perfectly for me on Gutsy.

AnRkey

UPDATE: I only used the screensaver bit

---

