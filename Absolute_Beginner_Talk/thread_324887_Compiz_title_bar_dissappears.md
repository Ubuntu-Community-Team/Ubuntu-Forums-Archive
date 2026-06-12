---
title: "Compiz title bar dissappears"
date: 2006-12-24
forum: Absolute Beginner Talk
---

### Post by muguwmp67 on 2006-12-24
I've installed compiz via the instructions on:
[http://www.go-compiz.org/index.php?title=Ubuntu_Installation_Guide]("http://www.go-compiz.org/index.php?title=Ubuntu_Installation_Guide")

But when I boot into Xgl and enable the GL Desktop, the screen flickers 3 times.

1.) title bars on open windows disappear
2.) title bars reappear
3.) title bars dissappear again.

When this happens, all windows are frozen in place.  New windows open in the top left corner of the screen (on top of the app/places/system menu).

I can get the titlebars back by running
metacity --replace &

But this disables the open gl setting (and I assume compiz)

Any help getting this thing off the ground?  I want to amaze my friends and family with ubuntu eye-candy.

---

### Post by KuriKai on 2006-12-24
Does adding this into the "Device" section of /etc/X11/xorg.conf fix it?
```
    Option "DisableGLXRootClipping" "True"
    Option "AddARGBGLXVisuals" "True"
```

Backup your xorg.conf first

---

### Post by muguwmp67 on 2006-12-24
Nope, it did hang my xwindow session after I enabled compiz though.

The flicker thing is where I think the problem is.  It looks like maybe its starting 3 different window decorators?  (if the window-decorator is where the title bar comes from, it could be a theme manager, I'm not sure how all of this fits together yet)

What configuration files besides xorg.conf are used to start xgl -> gnome -> compiz.  If I knew where to start, I might be able to see what got messed up.

---

### Post by KuriKai on 2006-12-25
Use this site to install compiz
[http://gandalfn.wordpress.com/compiz-repository/](http://gandalfn.wordpress.com/compiz-repository/)

---

