---
title: "Minimizing applications on boot?"
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by hackle577 on 2007-08-07
I just installed Liferea and added it to my Sessions list so it starts up when I login. However, it always starts maximized, when what I would like to do is have it minimized to the system tray thing. Is there a way to do this?

---

### Post by BobCFC on 2007-08-07
There is an application called **alltray** that will do this for you either search in System->Admin->Synaptic Package Manager or open a terminal and paste
```

sudo apt-get install alltray
```

Now you just have to prefix any application command with alltray to start it minimised to the system tray.  So to get liferea to boot on startup add

```
alltray liferea
```

To your sessions list in System->Prefs->Sessions

---

