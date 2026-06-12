---
title: "Another shiny sidebar.."
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by adileader on 2008-01-19
I would like to install this sidebar but I don't know how. thanks In advance.


Link:    [http://www.gnome-look.org/content/show.php/Sidebar+Screenlet+%28Vista%27ish+look%29?content=63172](http://www.gnome-look.org/content/show.php/Sidebar+Screenlet+%28Vista%27ish+look%29?content=63172)

---

### Post by lian1238 on 2008-01-19
You'll need to install screenlets first. [**Here**]("http://hendrik.kaju.pri.ee/screenlets/?q=node/5") is a good guide to doing so.
Then download [**sidebar**](http://www.gnome-look.org/content/show.php/Sidebar+Screenlet+(Vista'ish+look)?content=63172).

Open the screenlets manager. (Alt+F2 then, screenlets-manager)
Install the screenlet, sidebar. Then launch it.
*Note that the sidebar does NOT include ANY of the screenlets shown in the screenshot. It's just the "bar".

---

### Post by adileader on 2008-01-19
I want to install the 1.5 version...but after I extracted from the .tar.bz2 file what do I do?

---

### Post by adileader on 2008-01-19
PLease help...:mad:

---

### Post by lian1238 on 2008-01-19
Have you installed screenlets?
If not, do that first. You need screenlets to run the sidebar.

If so, you can copy the sidebar folder into '/usr/local/share/screenlets'.

---

### Post by adileader on 2008-01-19
> **lian1238 said:**
> Have you installed screenlets?
If not, do that first. You need screenlets to run the sidebar.

If so, you can copy the sidebar folder into '/usr/local/share/screenlets'.

Screenlets are installed the only thing is that I can't find the /screenlets folder

---

### Post by lian1238 on 2008-01-19
> **adileader said:**
> Screenlets are installed the only thing is that I can't find the /screenlets folder
Are you able to run screenlets-manager?
```
screenlets-manager
```
If you can't find the screenlets folder, try:
```
locate screenlets/Clock
```
See where it is.

---

### Post by adileader on 2008-01-19
Yeah i was able to open the screenlets manager....but when I navigate I can't find the screenlets folder...I am going to disk/usr/local/share/ but no screenlets

---

### Post by imon9 on 2008-01-19
hi,

simplest way: create a [user]/.screenlets folder, then put the extracted file into it

then run screenlet-manager, ur neew plugin will be visible

---

### Post by adileader on 2008-01-19
Well thank you...it works now but I don't like it :lolflag:

---

