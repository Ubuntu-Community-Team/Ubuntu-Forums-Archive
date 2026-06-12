---
title: "Third Party Software / Closed Source added to Linux Dist's ?? ..."
date: 2011-05-15
forum: Any Other OS
---

### Post by Tone303 on 2011-05-15
As i understand it, there is a distribution called Super OS and other dist's that comes with such things as Flash and restricted third party software pre-installed.

Tell me if i understand this right: It is ok to do this, except it will never be endorsed by Canonical. Also it can only be third party applications & plugins, never third party drivers under any circumstance.

In Other Words:

1) Third Party Software such as VLC, skype and flash = ok to pre-install as an unofficial amateur distribution, but dont count on it ever being officially endorsed. 

2) Third Party Drivers = Never do this under any circumstance. This is forbidden by the Copy-Left License 

Is the above about correct? Or am i misunderstanding? Thank You.

---

### Post by Sef on 2011-05-15
Click [here]("http://hacktolive.org/wiki/Super_OS") for info and a download link.

---

### Post by Tibuda on 2011-05-15
It makes no sense at all.

---

### Post by Tone303 on 2011-05-15
> **Sef said:**
> Click [here]("http://hacktolive.org/wiki/Super_OS") for info and a download link.

Im asking basically this:

 I cited Super OS as an example, im not asking where you can get Super OS, rather Im asking if it is it ok to make distributions of linux that have third party software pre-installed, as long as its not drivers? Or did Super OS get special permission from adobe and other companies?? I cant tell just from the fact that Super OS exists. Special permission or no?

Im asking because im making one for USB, and the more stuff you have pre-installed, the less stuff that later takes up persistence file space. If the stuff is installed after flashing a USB, then it takes up persistence space.

Example: if you preinstall skype, flash, java, microsoft core fonts and updates, you start off with a persistence file only 5% full. If you install that stuff when already on the emergency USB, then you end up like 45% full and only 55% room left. This is because whats in the .iso VS whats in the 4 GB Persistence. Preinstalled stuff within the .iso doesnt not take up the 4 GB of additional space. Plus its slow (but very possible) for people to install additional stuff when on USB.

Im working on a project called USB-untu that is preset to use only RAM memory in firefox/media caching and other sort of stuff specific to USB. Its calibrated in a few different ways to drastically cut down on USB writes and has been an interesting project. I was inspired to do this after my 4th hard drive failure (ive owned 4 hard drives that physically broke since the late 90s, lot of bad luck.)

know what i mean now? this (preinstalled third party) would be useful for Broken-Hard Drive Emergency Live Mode Dist.

---

### Post by Tone303 on 2011-05-15
maybe im misunderstanding Super OS, is it that it uses free open source flash plugins rather than adobe? maybe it doesnt make sense for me to cite it as an example. anyway the point is, im simply asking if its against licenses to have software like skype and adobe flash preinstalled on dists?

---

### Post by jeffathehutt on 2011-05-16
> **Tone303 said:**
> maybe im misunderstanding Super OS, is it that it uses free open source flash plugins rather than adobe? maybe it doesnt make sense for me to cite it as an example. anyway the point is, im simply asking if its against licenses to have software like skype and adobe flash preinstalled on dists?

That depends on a number of things, including where you live and the particular license used in the software.  Any GPL software can be included legally, but I know Adobe and Skype use other licenses, so you would have to read those licenses to find out if you can redistribute the programs.

Some distributions get away with including non-free software because they are made in a country where the laws are different than the US, and the US laws are not enforceable.

If in doubt, contact a lawyer.

---

### Post by Tone303 on 2011-05-16
> **jeffathehutt said:**
> That depends on a number of things, including where you live and the particular license used in the software.  Any GPL software can be included legally, but I know Adobe and Skype use other licenses, so you would have to read those licenses to find out if you can redistribute the programs.

Some distributions get away with including non-free software because they are made in a country where the laws are different than the US, and the US laws are not enforceable.

If in doubt, contact a lawyer.

Thanks, i appreciate this answer.

its a shame that empathy or pidgin havent built a voice & cam support for yahoo and skype, and that the freeware Iced Tea JAVA plugin doesnt work as good as Sun-Java6-Plugin.deb, and that the other flash plug ins dont work as good as adobe (full screen video is choppy with them).  Some day everything might function with all freeware.

One thing people can do for the computer illiterate is put .deb installers on the desktop for them, then they can learn synaptic package manager and ubuntu software center later.

---

