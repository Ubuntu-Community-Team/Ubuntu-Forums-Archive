---
title: "Disable GUI"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by Ignite_nz on 2006-03-10
Is there a way I can stop the GUI from running in the background? As I'm only connecting via SSH (Putty), and I dont want the GUI to be running in the background as it just slows it down.

However should I do something wrong I'd like to be able to get it going again, in order to start it, I would use the command

```
startx
```

Yes?

Please fill me in on this. Thanks :KS

---

### Post by el3ktro on 2006-03-10
The easiest way:

apt-get install sysv-rv-conf

a little tool to control init scripts. Start sysv-rc-conf, and then disbale X in the init scripts - so X won't be loaded during bootup. If you still need it, then just type

/etc/init.d/gdm start

or

/etc/init.d/kdm start

if you use Kubuntu.


Tom

---

### Post by codejunkie on 2006-03-10
[QUOTE=Ignite_nz]Is there a way I can stop the GUI from running in the background? As I'm only connecting via SSH (Putty), and I dont want the GUI to be running in the background as it just slows it down.

However should I do something wrong I'd like to be able to get it going again, in order to start it, I would use the command

```
startx
```

Yes?

Please fill me in on this. Thanks :KS[/QUOTE]
you could use ```
sudo update-rc.d -f gdm remove
``` this will make ubuntu startup without a gui.
to enable the gui again run
```
sudo update-rc.d -f gdm defaults
```

---

