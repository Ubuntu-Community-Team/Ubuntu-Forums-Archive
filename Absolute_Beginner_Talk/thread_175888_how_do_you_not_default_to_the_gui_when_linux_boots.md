---
title: "how do you not default to the gui when linux boots"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by Silver-revo on 2006-05-14
I am trying to do some stuff that requires me to not be utilizing the gnome desktop, how do I boot into a straight console.

---

### Post by aysiu on 2006-05-14
I don't know how you *boot* straight to the console, but you can press Control-Alt-F1, log in,  and type ```
sudo /etc/init.d/gdm stop
```

---

### Post by banadushi on 2006-05-14
If you remove the links to the GDM startup script from the runlevel directories it will not start on boot.  The easist way to do this is

```

$ sudo update-rc.d -f gdm remove

```

and then to put it back

```

$ sudo update-rc.d  gdm defaults

```

Have a good one!

Jason

---

### Post by Silver-revo on 2006-05-14
ok, is there an easy way to do that for suse linux?

---

### Post by banadushi on 2006-05-14
Its been a while, but I think that SuSE still uses runlevels the way they were supposed to be used.  If i recall correctly you can edit /etc/inittab and change the line that says

```

id:5:initdefault:

```

to

```

id:3:initdefault:

```

to have init boot into runlevel 3 which is 'multiuser with networking'.  You can also just disable the *dm that is running through YAST by going to system services and disabling xdm.

Have a good one!

Jason

---

