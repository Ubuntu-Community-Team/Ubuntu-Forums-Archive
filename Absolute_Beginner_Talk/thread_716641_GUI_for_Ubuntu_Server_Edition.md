---
title: "GUI for Ubuntu Server Edition"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by ben22 on 2008-03-06
Hello,

I have just installed the Ubuntu server. When starting with the install it showed a graphical interface, the installation however was "old styled". 

When I boot now it only shows command line, so the question: Is there a graphical interface as in the desktop version gutsy gibbon.

And if yes, how can I access it?

Thx,
Ben

---

### Post by kesman on 2008-03-06
I think you need to install gdm and gnome desktop, but you really don't need these for a server.

---

### Post by ben22 on 2008-03-06
> **kesman said:**
> I think you need to install gdm and gnome desktop, but you really don't need these for a server.

that would be the following command: 

```
sudo apt-get install gdm-desktop
```


i read somehwere to install xubuntu desktop

```
sudo apt-get install xubuntu-desktop
```

any experience with these?

---

### Post by K.Mandla on 2008-03-06
Most people who run the server edition don't want a GUI. The graphical interface can sometimes slow a server's performance.

If you want a full desktop, consider installing ubuntu-desktop, kubuntu-desktop or xubuntu-desktop. Any one (or even all three) of those will give you a graphical environment like you've mentioned.

---

### Post by ben22 on 2008-03-06
> **K.Mandla said:**
> Most people who run the server edition don't want a GUI. The graphical interface can sometimes slow a server's performance.

If you want a full desktop, consider installing ubuntu-desktop, kubuntu-desktop or xubuntu-desktop. Any one (or even all three) of those will give you a graphical environment like you've mentioned.

I hade probelms with installing Lamp on the dekstop, so I go with the server edition.

can u please tell me whether this is the right command to get the gnome desktop:

> sudo apt-get install gnome-desktop

---

### Post by ben22 on 2008-03-06
interestingly the user created during the setup of Ubuntu server did not have administration rights.

so I rebooted in recovery mode and added it with visudo

---

### Post by Cadmus on 2008-03-06
On a related note, is it possible to have a server boot gui-less and then start/stop the gui as necessary? Presumably this would help reduce the impact on resources.

---

### Post by AndyCooll on 2008-03-06
> **Cadmus said:**
> On a related note, is it possible to have a server boot gui-less and then start/stop the gui as necessary? Presumably this would help reduce the impact on resources.

Assuming you've installed the"gui" environement (e.g. GNOME, KDE or even just X) this thread should answer you query: [Runlevels in Ubuntu 7.10 Desktop]("http://ubuntuforums.org/showthread.php?t=692821").

:cool:

---

### Post by louieb on 2008-03-06
Fast machine, lots of ram. Just my two cent worth Nothing wrong with running a gui even Gnome. Learning is easier. Don't get thrown into command line cold turkey. 
[HOWTO: Leightweight Gnome - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=298818&highlight=xorg+gdm+gnome-core")

---

