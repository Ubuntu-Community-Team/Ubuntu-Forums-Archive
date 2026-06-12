---
title: "[SOLVED] No workspaces nor panels in Nautilus"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by altonbr on 2007-05-07
I somehow managed to set workspaces to 0 (zero) using the GUI and now the panels have disappeared. Luckily I have a terminal window open so I can launch my applications, but how do I set Nautilus to have 1 (one) workspace?

This is the silliest bug I've ever seen. I don't see any mention of it in the bugzilla.gnome.org website either.

---

### Post by fakie_flip on 2007-05-07
The only fix I know for this is to create a new user by running gksu users-admin. The new user will have all the workspaces. Then copy your files over and delete the old user.

---

### Post by rai4shu2 on 2007-05-07
If you can, run "gconf-editor", then navigate to "/apps/metacity/general/num_workspaces". You might be able to fix it there.

---

### Post by altonbr on 2007-05-07
> **rai4shu2 said:**
> If you can, run "gconf-editor", then navigate to "/apps/metacity/general/num_workspaces". You might be able to fix it there.

It had 2 when I found it, so changing that won't fixit.

> **fakie_flip said:**
> The only fix I know for this is to create a new user by running gksu users-admin. The new user will have all the workspaces. Then copy your files over and delete the old user.

You're kidding me right?


Has anyone heard of this bug?


EDIT:: I mixed up the two quotes.

---

### Post by fakie_flip on 2007-05-07
> **altonbr said:**
> You're kidding me right?



It had 2 when I found it, so changing that won't fixit.

Has anyone heard of this bug?

How many were you expecting? The older releases of Ubuntu have 4 workspaces by default, but the newer ones have 2. You can change the default settings to have how many workspaces you want.

---

### Post by rai4shu2 on 2007-05-07
> **altonbr said:**
> You're kidding me right?

No. What's the big deal?

---

### Post by altonbr on 2007-05-07
Kidding me in regards to making a new user. That's a little drastic.

I have NO panels. NO workspaces. This is a bug of some sort, even though gconf-editor said I have 2. I do NOT have 2 workspaces. I have zero.

I'm lucky I had a terminal window up, else I wouldn't be able to launch programs. I can reboot via Ctrl + Alt + F1 so that's fine...



EDIT:: It looks like I mixed up my quotes. I meant to say "Are you kidding me" in regards to making a new user account.

---

### Post by fakie_flip on 2007-05-07
> **altonbr said:**
> Kidding me in regards to making a new user. That's a little drastic.

I have NO panels. NO workspaces. This is a bug of some sort, even though gconf-editor said I have 2. I do NOT have 2 workspaces. I have zero.

Unless you have a better solution, I suggest you use that one. It is almost guaranteed to fix everything you screwed up. It beats reinstalling the whole system.

---

### Post by bapoumba on 2007-05-07
To the OP:
do you see that with all your users ? Make a new one (**sudo adduser test**, assuming test will be the loggin). Do you have the same problem ?

If not, it may be a problem with a regular user conf file.
Try to rename, one by one:
.gconf
.gnome
.gnome2

Each time, logout and log back in.

---

### Post by altonbr on 2007-05-07
Well, it was simply fixed by a reboot, but a word to the developers: DO NOT ALLOW ZERO WORKSPACES, or have a fallback/failsafe of ONE by default.

They won't read this, so I'll make a bug at bugzilla.gnome.org.

---

### Post by bapoumba on 2007-05-07
> **altonbr said:**
>  so I'll make a bug at bugzilla.gnome.org.
check also on Launchpad for bugs (I have not done it, just an idea).

---

### Post by brennydoogles on 2007-05-07
> **fakie_flip said:**
> How many were you expecting? The older releases of Ubuntu have 4 workspaces by default, but the newer ones have 2. You can change the default settings to have how many workspaces you want.

I have been looking for a way to do that... How would one do that on edgy??

---

### Post by fakie_flip on 2007-05-07
> **brennydoogles said:**
> I have been looking for a way to do that... How would one do that on edgy??

Right click one of the squares for workspaces, and then click on preferences. Next change the number of workspaces to whatever you want. This is how I can do it in Feisty, but I'm sure Edgy isn't much different if any. 36 is the most workspaces you are allowed to have. I just tested it.

---

