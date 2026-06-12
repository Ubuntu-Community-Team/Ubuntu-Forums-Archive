---
title: "Synaptic Package Manager Problems"
date: 2006-07-02
forum: Absolute Beginner Talk
---

### Post by EdThaSlayer on 2006-07-02
Iam using Ubuntu 6.06 LTS with GNOME...
So i can start Synaptic Package Manager and i can browse through it nicely...
but when i try to install a application, and click on apply, a menu pops up as usual. But the problem starts when i press Apply on that popup menu...Synaptic Package Manager just quits!!!

[IMG]http://img64.imageshack.us/img64/6996/bigscreenshot5oo.jpg[/IMG]
so i try doing it via the terminal...
i get this~i dont get it at all!!!!~  :confused: 

```


~$ sudo synaptic

(synaptic:9391): Gdk-WARNING **: locale not supported by Xlib

(synaptic:9391): Gdk-WARNING **: cannot set locale modifiers
Gtk-Message: Failed to load module "atk-bridge": libatk-bridge.so: cannot open shared object file: No such file or directory
GTK Accessibility Module initialized


```

and when it suddenly quits when i press the popupwindow apply button[to download the needed files for that program...]

i get this

```

** ERROR **: file gailtreeview.c: line 3604 (garbage_collect_cell_data): assertion failed: (GAIL_IS_TREE_VIEW (data))
aborting...
Aborted

```

i have tried everything i possibly can...  :| 
and i dont know the reason why this is happening...  :confused: 

Thanks to anyone that helps me...

---

### Post by cacharreo on 2006-07-02
Have you tried to find broken packages and repair them?

---

### Post by EdThaSlayer on 2006-07-03
[QUOTE=cacharreo]Have you tried to find broken packages and repair them?[/QUOTE]

i tried that...it doesnt work...
it has to do something with that error i got...

---

### Post by christhemonkey on 2006-07-03
That sounds a bit rough!

Try reinstalling it:
```
sudo apt-get --reinstall synaptic 
```

Let us know if that helps!

---

### Post by EdThaSlayer on 2006-07-03
[QUOTE=christhemonkey]That sounds a bit rough!

Try reinstalling it:
```
sudo apt-get --reinstall synaptic 
```

Let us know if that helps![/QUOTE]
i reinstalled it...

i still get this error when i start up[in the terminal...]

```

(synaptic:2222): Gdk-WARNING **: locale not supported by Xlib

(synaptic:2222): Gdk-WARNING **: cannot set locale modifiers
Gtk-Message: Failed to load module "atk-bridge": libatk-bridge.so: cannot open shared object file: No such file or directory
GTK Accessibility Module initialized


```

and this message when it quits after i press the apply button to download the software in synaptic package manager...


```

** ERROR **: file gailtreeview.c: line 3604 (garbage_collect_cell_data): assertion failed: (GAIL_IS_TREE_VIEW (data))
aborting...
Aborted

```

---

### Post by EdThaSlayer on 2006-07-03
I think i found a fix...
seems more people had my problem...


[https://launchpad.net/distros/ubuntu/+source/synaptic/+bug/30685](https://launchpad.net/distros/ubuntu/+source/synaptic/+bug/30685)

thanks anyway people! I was missing the GOK library!

---

