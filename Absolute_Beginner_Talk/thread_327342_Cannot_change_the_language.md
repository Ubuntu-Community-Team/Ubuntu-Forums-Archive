---
title: "Cannot change the language"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by kill_u on 2006-12-29
Hi all
I have the following error from my gnome
```

Error activating XKB configuration. 
It can happen under various circumstances: 
- a bug in libxklavier library 
- a bug in X server (xkbcomp, xmodmap utilities) 
- X server with incompatible libxkbfile implementation 

X server version data: 
The X.Org Foundation 
70000000 

If you report this situation as a bug, please include: 
- The result of xprop -root | grep XKB 
The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

```
Now i cannot switch between Cyrillic  and English language. When i change the language to cyrilick i just continue to type in English.

---

### Post by Apple 101 on 2006-12-29
Check your keyboard configuration in the System menu.

---

### Post by kill_u on 2006-12-29
I checked this, And i have a two languages Bulgarian and English, But i cannot write on bulgarian.

---

### Post by Apple 101 on 2006-12-29
Have you had any recent updates to do with libxklavier, xkbcomp, xmodmap or libxkbfile?

---

### Post by kill_u on 2006-12-29
yes ia was install a some specific software yesterday.
but now i have a two different layouts with one language. in Bulgarian I again type on english 
Here the [screen]("http://killu.hit.bg/temp/%D1%ED%E8%EC%EA%E0.png")

---

### Post by kill_u on 2006-12-29
I remove the problem. I install the same software again but now when I type on Bulgarian the keyboard indicator shows this symbol ?, and  when I type on English shows <BGR>

---

### Post by Apple 101 on 2006-12-29
Hmmm.  This is a strange problem.  Try downgrading the keyboard software, if possible, via Synaptic.

---

