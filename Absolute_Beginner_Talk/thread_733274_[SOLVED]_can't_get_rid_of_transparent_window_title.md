---
title: "[SOLVED] can't get rid of transparent window titles"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by elchico04 on 2008-03-23
I recently installed the compiz display settings and emerald (which I can't get to work). It is annoying because all of my windows have a clear title bar. Can anyone help me with this?

[IMG]http://alan.homeofthepioneers.com/post/transparent.jpg[/IMG]

---

### Post by drubin on 2008-03-23
Do you have the compiz setting manager installed?

If not install it.
```
sudo apt-get compizconfig-settings-manager
```

After that it will create  a submenu in your System->preferences->"Advanced Desktop Affects settings"

There should be an option in there to change the transparency. (Since it looks like the title bars are there just transparent)

---

### Post by drubin on 2008-03-23
Sorry i forgot the "install" param of the command, this is the correct one

```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by elchico04 on 2008-03-23
i fixed it by uninstalling emerald.

thanks for the tips anyways though.

---

