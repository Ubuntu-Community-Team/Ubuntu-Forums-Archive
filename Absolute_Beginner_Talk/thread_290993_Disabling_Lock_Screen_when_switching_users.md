---
title: "Disabling Lock Screen when switching users"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by Juan_VCS on 2006-11-01
Whenever I leave my session open and then try to resume it from the login screen, I get prompted for my password twice - once on the login screen, and then again in the lock screen.

Is there any way to prevent that? Actually I would like to just get rid the lock screen and just use the login instance.

---

### Post by Ecthelion on 2006-11-03
Do you mean the lock screen when your screensaver gets activated?

You can turn that one of in System > Preferences > ScreenSaver

Just uncheck the right box.

Otherwise I don't see where you should put your password the second time when you switch user...

---

### Post by CatKiller on 2006-11-03
You need to enter your password if you've locked the session, it's true. I'm not sure why you're at the login screen to login again, though.

---

### Post by Ecthelion on 2006-11-03
He would be at the login screen if he was switching user like the title seems to say...

And if the screen saver is set on lock screen when activated... then he would have to take the lock screen away and then log in with his user...

If that's not it I don't know it either.

---

### Post by CatKiller on 2006-11-03
When I do it, I lock the screen and switch user. Then the other user has their session and logs out. Then it's at the unlock screen dialogue. I only have to enter my password once.

---

### Post by Tamil on 2006-11-03
> **CatKiller said:**
> When I do it, I lock the screen and switch user. Then the other user has their session and logs out. Then it's at the unlock screen dialogue. I only have to enter my password once.Thanks.

---

### Post by Juan_VCS on 2006-11-03
> **CatKiller said:**
> When I do it, I lock the screen and switch user. Then the other user has their session and logs out. Then it's at the unlock screen dialogue. I only have to enter my password once.
Yeah, but when the other user switches without closing its session, it goes to the login screen.

I'd like it to me more XPish, doing everything at the login screen. Is it possible under Gnome?

---

### Post by Arisna on 2006-11-03
Possible solution to the problem in the original post:

Launch a new session using the command `gdmflexiserver -l' from a Terminal or Run dialog.  If it works, create a shortcut/menu entry for it.

---

### Post by Juan_VCS on 2006-11-04
I found the solution [here]("http://www.dcemulation.com/phpBB/viewtopic.php?t=87672").

[quote="[Jan](http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2006-06/msg00904.html)"]Run the Configuration editor (it's gconf-editor if you run it from a
shell). Go to apps -> gnome-power-manager. There are four related
options there that control this: lock_on_blank_screen,
lock_on_hibernate, lock_on_suspend and lock_use_screensaver_settings.

And for some reason only the developers know, the
lock_use_screensaver_settings is unset by default. What I did was just
unset the other three, but I guess that setting
lock_use_screensaver_settings to true would work for you too. Unless
there was a good reason this was left unset of course.[/quote]
Thanks to everyone.

---

