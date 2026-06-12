---
title: "compiz problem"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by Sasa_Ivanovic on 2007-01-03
So i followed this tutorial [http://ubuntuguide.org/wiki/Ubuntu_Edgy#Eye_Candy]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Eye_Candy")
at the end when i ran compiz, all the windows are missing title bar, i can't move them, switch them or anything. All that i can do is move the mouse.
here's my terminal output :
```

(gedit:5811): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
sasa@sasa-desktop:~$ sudo chmod 755 /usr/bin/thefuture
sasa@sasa-desktop:~$ thefuture
/usr/bin/thefuture: line 2: gnome-window-decorator: command not found
sasa@sasa-desktop:~$ compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No manageable screens found on display :0.0

```
any suggestions ?

---

### Post by sardion on 2007-01-03
My first suggestion would be to use beryl not compiz.  [www.beryl-project.org](www.beryl-project.org)

That said, your problem is that you also need to run a window decorator.  Compiz is just the window manager.  (Sorry if these terms mean nothing).  Personally, I use beryl (which is a fork of compiz) and emerald (which comes with beryl).

I don't know what compiz uses for a decorator, but googling for compiz and "window decorator" should help you out.

Or, search the forums here for advice about beryl, which seems to be much more popular with the ubuntu crowd.

---

### Post by Sasa_Ivanovic on 2007-01-03
ok i managed to install beryl. But i had some problems with it. and bugs.

it's best if i use pure gnome... so forget it.

---

