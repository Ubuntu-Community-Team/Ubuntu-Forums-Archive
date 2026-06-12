---
title: "Installing problems."
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by JJX90 on 2008-02-21
I was trying to install a Java bundle with the Netbeans IDE, I downloaded the .sh file and installed it as I was told, sh + path in terminal. Here's a screenshot:

[[IMG]http://img512.imageshack.us/img512/3640/screenshotjjunknownlaptup3.png[/IMG]](http://imageshack.us)

During the installation, two ignoring messages appeared aswell as an installer wizard window but this window remained blank and disappeared after a while, is my program already installed? if not how can I fix this?

---

### Post by JJX90 on 2008-02-22
Could someone help me? I really need to get this program installed to work on my code which is due for monday.

---

### Post by macogw on 2008-02-22
Turn off Compiz (Desktop Effects), then try it.  You can do that with ```
metacity --replace
```Sun Java has a bug that's been outstanding since Java 5 where Swing windows are blank on composited desktops.  There's a setting somewhere in Compiz's settings thing (install compizconfig-settings-manager to get all the configuration stuff if you haven't already), I think in the Workarounds plugin, to make Java work right.

And since I don't think Eclipse uses Swing, it should also work fine instead of NetBeans.  Or you could just use Gedit or Vim.  I write all my Java in Vim.

---

### Post by Biggy on 2008-04-05
i've the same problem ! i try metacity --replace but still same prob.

help plzz

---

### Post by Biggy on 2008-04-05
someone help me?

---

