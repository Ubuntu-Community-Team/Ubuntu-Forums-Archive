---
title: "[SOLVED] Open Office Massively Unstable"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by E.T.Smith on 2007-11-19
I just upgraded to 7.1 Ubuntu last night. However, the new 2.3 version of Open Office is ridiculously unstable; I just got it to crash five times in as many minutes. This happens if I try to open any option on the toolbar, not just through any particular action. A quick scan of these forums shows this seems to be a common problem in the new version. How do I fix this? Or, failing that, rip out OO 2.3 and go back to the previous stable version?

---

### Post by MegaJim on 2007-11-19
The problem is with the open office gtk extensions, you can uninstall openoffice.org-gtk through the synaptic package manager.

---

### Post by E.T.Smith on 2007-11-19
> **MegaJim said:**
> The problem is with the open office gtk extensions, you can uninstall openoffice.org-gtk through the synaptic package manager.
Fast answer! Not that I have a choice about it, but what functionality will I lose by uninstalling that package? Basically, what is it there to do, and why is it causing problems?

---

### Post by MegaJim on 2007-11-19
Basically, it adds an open office quicklauncher to the notification area and draws the open office menus/toolbars/options dialogs etc. using the currently selected gnome theme.

It will work with the basic theme "human" but most of the others will cause it to crash.

So you won't lose functionality, just looks.

There is a thread about it here: [http://ubuntuforums.org/showthread.php?t=584088](http://ubuntuforums.org/showthread.php?t=584088)

---

### Post by E.T.Smith on 2007-11-19
Thank You! That seems to have fixed the problem.

---

