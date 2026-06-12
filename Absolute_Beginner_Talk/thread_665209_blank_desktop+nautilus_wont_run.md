---
title: "blank desktop+nautilus wont run"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by swoll1980 on 2008-01-12
when I login desktop is non existent I try to run nautilus and it will not open, tried to run it in a terminal and it wont do anything no errors or anything. Re starting some times fixes it but it's 50/50 sometimes everything works fine sometimes it doesn't any idea what could be causing this?also nm icon in taskbar says i'm disconnected but network is working fine

---

### Post by Arthur Archnix on 2008-01-12
When I mess things up real bad I usually create a new user and log on with that user. If things work fine then I know my system is ok and I just messed up my profile.

At that point you have the option of trying to track down the problem or just copying your files to the new account and deleting the old account. It usually takes me an hour to setup my desktop the way I like it, and it often takes me longer to track down problems.

If you decide to track down the problem, I'd take a look at any changes you've made to the gdm lately, session changes you've made, services you've disabled, and especially any config files you've manually edited. Have you had your fingers in gconf-editor? I've messed up some things in there before.

---

