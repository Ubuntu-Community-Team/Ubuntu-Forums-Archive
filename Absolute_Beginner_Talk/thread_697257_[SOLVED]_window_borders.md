---
title: "[SOLVED] window borders"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by Sinkingships7 on 2008-02-14
so i was hangin' out at gnome-look.org, taking a look at all the pretty things i could do with my desktop. i decided (mostly for the learning experience of it) to go ahead and try to do a bunch of things. i went ahead and download the mac4lin project, because it included all the stuff i would need to do a complete makeover, and manually (again, for the learning experience). so i got everything set up properly, and was proud. yay me. i knew from the start i wouldn't want to keep it, so i began deleting and reverting. it seems that i've done everything right, save for one thing: i still have mac4lin window borders (thumbnail attached), i can't find out how to get rid of them. i've already tried going to system -> preferences -> appearance and just selecting the human theme, but that didn't work. so i went to customize and went to window borders and, of course, made sure that human was selected. it was. and the mac4lin borders aren't there anymore because i deleted them already.

so what i need to do is get back my old, human borders before i go insane. any ideas?

---

### Post by PeterJS on 2008-02-14
Are you using compiz? If so the borders are controlled by emerald, try looking in System > Preferences > Emerald Theme Manager.

---

### Post by Sinkingships7 on 2008-02-14
will uninstalling emerald solve this problem?

---

### Post by PeterJS on 2008-02-14
Why would you do that? Just pick another theme

---

### Post by Sinkingships7 on 2008-02-14
lol sounds good. there's no way to get the ubuntu default theme back?

---

### Post by spiderbatdad on 2008-02-14
The mac4lin metacity theme reports to be buggy. You might try these things.

```
metacity --replace
```
Then try to select human again.

You might look for a hidden gtk folder in your home directory containing mac4lin configuration files...delete them.

Reboot.

---

### Post by Sinkingships7 on 2008-02-14
> **spiderbatdad said:**
> The mac4lin metacity theme reports to be buggy. You might try these things.

```
metacity --replace
```
Then try to select human again.

You might look for a hidden gtk folder in your home directory containing mac4lin configuration files...delete them.

Reboot.

that code worked perfectly. thank you.

---

