---
title: "default window size"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by elchico04 on 2008-04-06
is there a way to control my window's default size?
I use gnome.

---

### Post by SunnyRabbiera on 2008-04-07
I dont think so in gnome, kde has a way to do this but not gnome.
I know its annoying, trust me I get annoyed by it too.

---

### Post by elchico04 on 2008-04-07
its annoying because some programs open to their default size which is a little bit bigger than my desktop so it appears on the taskbar of other workspaces.

---

### Post by SunnyRabbiera on 2008-04-07
Hey I feel yah, you have my sympathy

---

### Post by noynac on 2008-04-07
There is no single setting that controls the size of all windows for all programs, but some applications allow you to set window size by way of a geometry command line option. The terminal and nautilus are two examples:

```
nautilus --geometry=1110x700
```

```
gnome-terminal --geometry=80x35
```

 Look at the man page for the specific application to check.

---

### Post by erginemr on 2008-04-07
There is a terminal program, or rather, daemon (background process): **devilspie** that allows you to have your windows opened with a certain size / at a certain location / at a certain vitual desktop / maximized or minimized. And it has a Gnome frontend called **gdevilspie**, which makes it really easy to use.

For **devilspie**, please refer to:
[https://help.ubuntu.com/community/Devilspie](https://help.ubuntu.com/community/Devilspie)
[http://burtonini.com/blog/computers/devilspie](http://burtonini.com/blog/computers/devilspie)

And for **gdevilspie**, refer to:
[http://code.google.com/p/gdevilspie/wiki/gDevilspie](http://code.google.com/p/gdevilspie/wiki/gDevilspie)
[http://gnomefiles.org/app.php/gDevilspie](http://gnomefiles.org/app.php/gDevilspie)

---

### Post by Shannon_Lowder on 2008-04-30
Is there a similar program that would extend the context menu to allow you to choose a certain size (say 800x600, or 10204x768) like you can with web developer in firefox?

---

