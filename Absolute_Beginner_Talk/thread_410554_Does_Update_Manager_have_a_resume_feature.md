---
title: "Does Update Manager have a resume feature"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by jacatone on 2007-04-15
I recently installed Ubuntu 6.06 and the Update Manager says I need to download and install about 260 megs worth of files. Since I'm on dialup would I be able to download these files and resume in the event my dialup connections failed? Or is there a download manager like GetRight that'll work better? Thanks.

---

### Post by shae on 2007-04-15
Yes, if your connection is disconnected, the package it is currently downloaded will have to be redownloaded, but any previously completed packages will be in aptcache.  Thus they should not have to be re-downloaded.

---

### Post by ksbalaji on 2008-01-02
It seems that the problem still persits! Can you try installing DAP or FDM thru Wine?
(I confess that I have not tried) Pl reply if it succeeds.

---

### Post by ksbalaji on 2008-06-25
> **jacatone said:**
> I recently installed Ubuntu 6.06 and the Update Manager says I need to download and install about 260 megs worth of files. Since I'm on dial up would I be able to download these files and resume in the event my dial up connections failed? Or is there a download manager like GetRight that'll work better? Thanks.

I´ve found out that the resume feature is built in. For example, If you have to download 100 packages or 150 files and you lose connection or close the synaptic package manager during a download, your next session of update will start from where you left. I use the latest hardy heron of Ubuntu.

---

