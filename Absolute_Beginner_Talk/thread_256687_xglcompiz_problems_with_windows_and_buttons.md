---
title: "xgl/compiz problems with windows and buttons"
date: 2006-09-13
forum: Absolute Beginner Talk
---

### Post by zekopeko on 2006-09-13
i use quinnstorms repository and a few days ago something strange happened.
after fetching updates i could no longer move windows and click on buttons.
right click works and i can rotate the cube, so the plugins are working.

anybody have a solution or a similar problem?

---

### Post by ciscosurfer on 2006-09-13
compiz.net forums will help you out...but I believe you need to switch over your startup scripts to reflect the change to csm, etc.

My startcompiz script looks like this now (replacing gnome-window-decorator with cgwd, replacing compiz with compiz-start, changing over to csm, etc...:
#!/bin/sh
killall gnome-window-decorator
wait

cgwd &
compiz-start --replace csm &

---

