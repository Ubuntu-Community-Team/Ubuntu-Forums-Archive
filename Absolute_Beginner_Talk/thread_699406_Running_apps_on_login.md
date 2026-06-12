---
title: "Running apps on login"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by dgbearcat on 2008-02-17
Searched around and couldn't find anything about this. If you know of a good guide, please just point me to it.

I'm looking to be able to start up certain apps on login, hopefully on specific workspaces. 

For example, I'd like Evolution to start on workspace1, firefox to start on 2, and GnomeMud to start on three. 

I assume this is something I can edit in a config file in the terminal/editor, but I'm still pretty noobish when it comes to editing things like that. 

Any suggestions?

Thanks!

---

### Post by sb12 on 2008-02-17
> **dgbearcat said:**
> Searched around and couldn't find anything about this. If you know of a good guide, please just point me to it.

I'm looking to be able to start up certain apps on login, hopefully on specific workspaces. 

For example, I'd like Evolution to start on workspace1, firefox to start on 2, and GnomeMud to start on three. 

I assume this is something I can edit in a config file in the terminal/editor, but I'm still pretty noobish when it comes to editing things like that. 

Any suggestions?

Thanks!

depending on what DE/WM you run the autostart options will vary, and devilspie may be able to start the apps on seperate workspaces for you.  Alternatively, xfce allows you to save sessions which would load your config from your last login

---

### Post by stmiller on 2008-02-17
Yeah just setup everything as you want it, then log out. There should be a check box option to 'save session' or something like that. It depends if you are using KDE, Gnome, or others.

---

### Post by Crooksey on 2008-02-17
Gnome, go to ...

```

system >> prefrences >> sessions
```

Then add what applications.

KDE,...

```


$ kate ~/.kde/Autostart
firefox &
#save
chmod +x ~/.kde/Autostart
```

---

### Post by dgbearcat on 2008-02-17
Awesome, thanks! I hadn't found that sessions option yet.

---

