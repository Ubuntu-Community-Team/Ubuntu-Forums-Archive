---
title: "Knotes on Gnome"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by queque on 2008-01-27
Hello, I am using Ubuntu 6.06.1 (Dapper Drake) Gnome I think. I saw that Knotes is for KDE, but I found it in Add/Remove of Applications, and successfully installed it. It works well, so it's good. But, I was wondering how this is possible. That is, how is it that I can run this KDE program on Gnome? Thank you in advance for your help.

---

### Post by taurus on 2008-01-27
If you paid attention during the installing of knotes, you should have known that it didn't only install knotes.  It installed all the necessary KDE libraries before it installed knotes.  And if you look at your system processes before and after you start knotes, you would see there are a few other KDE processes are running when you run knotes.  That's how you are able to run KDE app in a Gnome environment.  And it's the same as when you run Gnome app in KDE environment.

Just open synaptic and in the Search field, type **kde** and you would see a few KDE already installed on your machine even though you only installed one, knotes.

---

### Post by seventhc on 2008-01-27
Well, KDE is more of a desktop environment, but the file system should be the same. You can even install the kde desktop next to gnome. I don't mean on separate partitions, I mean if you install kde-desktop you can then choose which desktop you want at the login screen. :)

---

