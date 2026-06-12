---
title: "What happened to the fade effect?"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by Johnny K on 2007-06-23
I recently installed and then uninstalled KDE. To remove KDE, I used
```
sudo aptitude remove kubuntu-desktop
```
For some reason, that left some applications (konqueror, konsole, etc), so to make sure KDE was completely gone I typed "KDE" into synaptic and removed a couple packages that looked to be related to KDE.

Anyway, the point is that now there is no longer a fade effect when I click the "Quit" button on the panel, or am asked for the root password. Is there a certain package that deals with this effect that I might have accidentally deleted?

---

### Post by netyire on 2007-06-24
Kubuntu-desktop is a meta-package (whats that?), think of it like a package which doesn't really install anything on itself, but depends on all the packages that make up Kubuntu-desktop, hence checking it will prompt a messege asking you to install the other stuff. When you remove the package, the other packages may still remain. I'm not really sure if this will help, but try the following:

```
sudo apt-get autoremove --purge -y 
```
```
sudo apt-get install deborphan && deborphan | xargs sudo apt-get autoremove --purge
```

If it still does not work, try installing Kubuntu-desktop then typing"

```
sudo apt-get autoremove kubuntu-desktop --purge -y
```

Works? In any case, for the fade effect, try running gconf-editor then opening apps->compiz->general->allscreens->options and select active plugins. Check if there is a fade listed. If not click add and enter fade.

Does these fix the problems?

---

### Post by Johnny K on 2007-06-25
The KDE removal worked great! Thank you!

As for gconf-editor, fade *was* listed in apps>compiz>general>allscreens>options>active_plugins but the fade effect still does not work. I don't use Compiz/"Desktop Effects" or Beryl or anything like that.

---

