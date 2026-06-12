---
title: "firefox won't start up????!!!!??!!"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by beanco on 2007-08-09
I get this when I try to launch from terminal


```
(firefox-bin:8325): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Segmentation fault

```

any ideas what to do?

Thanks

Robi

aka the terminal noobie

---

### Post by aysiu on 2007-08-09
Try pasting this command into the terminal: ```
sudo dpkg-reconfigure locales
```

---

### Post by beanco on 2007-08-09
thanks I will try it in a bit.

I had to turn the computer off do to a temp power loss here, when I rebooted it up I could open firefox with not problem... strange.

robi

---

