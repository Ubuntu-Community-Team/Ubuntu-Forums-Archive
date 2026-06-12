---
title: "Mplayer error and move files to root"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by kramer65 on 2007-02-12
Hello,

I just have two questions:

1. Because Movie player gave me very bad sound (don't know why) I changed the default player to Mplayer. However, with mplayer I get a bug when I already have one window open and I click on another movie file. I hoped it would just open in the same player but it opens another mplayer and gives an error. Is this a known bug or can I do something about it?

2. When I want to move a file to somewher in the root (for example a skin to the shared xmms folder) I just want to drag and drop. But this gives an error because I dont have access (I understand that). So I need to do it with sudo etc. This works out. Right now I'm so far (but this is about the most technical thing I can do with linux. How can I move a file to a root folder dragging and dropping. Can't it automatically ask fopr the root password?

---

### Post by an.echte.trilingue on 2007-02-12
Depending on your version of Ubuntu, if you open nautilus an right click on a file, you should have an option scripts --> open as administrator, and then you will have a root session of nautilus that you can drag and drop in.  If not, you can simply "gksu nautilus" in a console and you will have administrator access that way.  You can also create a launcher so that you can do this with a double click.

For Mplayer, the best I can suggest is that you try another front end, such as kplayer.

Take care
-mat

---

### Post by kramer65 on 2007-02-12
ok. Thanks. And how do I access nautilus? Is it somwhere in a menu or something?

And about kplayer. I cannot find it in the add/remove function. Where would I be able to find that?

ps. I have ubuntu 6.06

---

### Post by an.echte.trilingue on 2007-02-14
Nautilus is the default file browser.  When you open your places menu, that is nautilus.

To install kplayer, you need to open the synaptic package manager (Desktop --> Administration --> Synaptic), enable the universe and multiverse repositories, hit the "reload"  button, and it should be there.

Take care,
-mat

---

