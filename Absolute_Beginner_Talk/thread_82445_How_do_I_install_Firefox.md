---
title: "How do I install Firefox?"
date: 2005-10-26
forum: Absolute Beginner Talk
---

### Post by monomaniacpat on 2005-10-26
I've opened a file called firefox-1.0.7.installer.tar.gz and I don't know what I'm meant to do from here in? The release notes at firefox.com are of no help whatsoever. Little help?

Thanks in advance!

Mono.

---

### Post by Kyral on 2005-10-26
1) Suggest Movement to the Absolute Beginners Forum

2) It should be already there

---

### Post by jeffreyvergara.NET on 2005-10-26
do you use Breezy? 5.10? if so, firefox 1.0.7 is already installed

---

### Post by aysiu on 2005-10-26
[QUOTE=Kyral]1) Suggest Movement to the Absolute Beginners Forum[/quote] Suggestion taken.

[quote=monomaniacpat]I've opened a file called firefox-1.0.7.installer.tar.gz and I don't know what I'm meant to do from here in? The release notes at firefox.com are of no help whatsoever. Little help?[/quote] As people are already trying to indicate to you, Firefox is already installed in Ubuntu. It's a little blue globe icon. If you don't have the latest version (say, you have 1.0.6 or something), then just open a terminal and type ```
sudo apt-get update
sudo apt-get install firefox
``` and you'll get the latest version. This can be done graphically, too, using a program called Synaptic Package Managers--see the second link in my sig.

If you don't like the ugly blue globe icon, [there's a script to get the original Mozilla icons to replace the Ubuntu ones.](http://www.ubuntuforums.org/showthread.php?t=34354) There's really no need to install from the .tar.gz [unless you want Firefox beta 1.5.](http://www.ubuntuforums.org/showthread.php?t=79283&highlight=howto+firefox+beta)

---

