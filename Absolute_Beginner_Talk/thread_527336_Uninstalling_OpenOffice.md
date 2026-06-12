---
title: "Uninstalling OpenOffice"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by vitalstatistix on 2007-08-16
I wanted to remove OpenOffice.org (ver. 2.0.4) from my ubuntu edgy installation to make way for sun's StarOffice. But synaptic says ubuntu-desktop will be removed as well. What does this meta-package have, what all dependencies will it leave unresolved and will it affect future distro upgrades? Are there any other effects as well....? I want to know if there is any way to remove OOo without touching other packages or just the best way to install SO. Thanx for helping!!:)

---

### Post by vitalstatistix on 2007-08-16
Guys pls reply!!!

---

### Post by Hobo Joe on 2007-08-16
I believe you can just uninstall, and then once it's done:
```

sudo aptitude install ubuntu-desktop

```
Better get another opinion though, cause I may be wrong.

---

### Post by Arthur Archnix on 2007-08-16
I think reinstalling ubuntu-desktop will put openoffice back on. Removing it has no effect, other than preventing you from upgrading directly from feisty to gutsy. In order to do that you'll have to install ubuntu-desktop, and only then will you be allowed to upgrade.

---

### Post by vitalstatistix on 2007-08-16
So there is no way(correct me if I'm wrong) to install SO without removing ubuntu-desktop. Obviously I don't want both SO & OOo together.

---

### Post by stchman on 2007-08-16
> **vitalstatistix said:**
> I wanted to remove OpenOffice.org (ver. 2.0.4) from my ubuntu edgy installation to make way for sun's StarOffice. But synaptic says ubuntu-desktop will be removed as well. What does this meta-package have, what all dependencies will it leave unresolved and will it affect future distro upgrades? Are there any other effects as well....? I want to know if there is any way to remove OOo without touching other packages or just the best way to install SO. Thanx for helping!!:)

I have a script to update your OO 2.0 to OO 2.2 on Edgy.  Don't worry about removing the ubuntu-desktop package as it means nothing.

[http://www.stchman.com/tools/OO_install.sh](http://www.stchman.com/tools/OO_install.sh)

If you want to see the steps go here:

[http://www.stchman.com/install_oo.html](http://www.stchman.com/install_oo.html)

If you install Feisty it has OO 2.2.

If you have a JRE installed you can comment out the line that installs the 1.5 JRE.

---

### Post by Arthur Archnix on 2007-08-16
You can install SO without removing ubuntu-desktop.

You cannot remove OO without also removing ubuntu-desktop.

---

### Post by Hobo Joe on 2007-08-16
> **vitalstatistix said:**
> So there is no way(correct me if I'm wrong) to install SO without removing ubuntu-desktop. Obviously I don't want both SO & OOo together.

Look around google some more.

[http://ubuntuforums.org/showthread.php?t=342490](http://ubuntuforums.org/showthread.php?t=342490)

That's the best I could find.

---

### Post by kevinlyfellow on 2007-08-16
I don't think you really **need** ubuntu-desktop, it is just a metapackage (a package with dependencies and nothing more) after all.

Reinstalling ubuntu-desktop would just bring back openoffice.org

---

### Post by vitalstatistix on 2007-08-16
Thanks a lot for your help everyone. I'll probably do a bit more research before uninstalling OOo and let you know tomorrow.

---

### Post by stchman on 2007-08-16
> **vitalstatistix said:**
> Thanks a lot for your help everyone. I'll probably do a bit more research before uninstalling OOo and let you know tomorrow.

My script does uninstall OO 2.0.

---

### Post by tashmooclam on 2007-08-16
Pardon me for my confusion, but I thought Staroffice and Openoffice were essentially identical.

---

### Post by stchman on 2007-08-16
> **tashmooclam said:**
> Pardon me for my confusion, but I thought Staroffice and Openoffice were essentially identical.

I believe that to be correct as well.

---

### Post by Irihapeti on 2007-08-16
If it's any help, I've uninstalled the Ubuntu version of OpenOffice (to make way for the "official" version - 'scuse the pun) and it doesn't seem to have done my system any harm at all.

There's a script for removing it as part of the Reconstructor liveCD modification program. It's easy enough to adapt to ordinary use.

Irihapeti

---

### Post by TheWizzard on 2007-08-16
> **stchman said:**
> I believe that to be correct as well.

staroffice is java based.

@OP:  stchman's script shows you how to uninstall OOo. just check it.

---

### Post by vitalstatistix on 2007-08-18
Thanks for helping out everyone. I have finally decided to wait it out for Gutsy before removing OOo. Dont wanna bother removing ubuntu-desktop just yet. As for removing OOo stchman's scripts ought to work but I think ```
sudo apt-get remove --purge openoffice*
``` should do equally well.
OOo is actually derived from SO's src code after it was released and is quite similar to it in basic framework as well as GUI. But SO is more advanced, has better compatibility with MS-Office files and a host of other features. Here I quote another user: >                  StarOffice = OpenOffice +

* more sample documents and templates
* more clipart graphics
* more fonts
* commercial spell-checker, thesaurus
* more file filters (e.g.: WordPerfect)
* support for Adabas D database
* central configuration tools

Most of the "new" features are useful for businesses or for a better compatibility with MS Office.Also google recently added SO to its Google Pack for windows and not OOo.:lolflag: Sun also actively develops, supports and sells SO.

---

