---
title: "Automatix and EasyUbuntu"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by timzak on 2007-05-02
I keep hearing how terrible it is to use these programs because they "break" things.  How bad is it to leave these on my system with the things they've already installed?  Am I hurting myself down the road?  Should I reinstall Feisty Fawn from scratch?  Or can I move forward from here and learn to install programs without having to reinstall the OS?

Second question, I installed EasyUbuntu on 7.04 before learning it wasn't compatible with 7.04 (yet).  As of now, there is a launch icon in my menu that does nothing when you click it.  I don't see that it's hurting anything, but it's completely useless and I don't know how to uninstall it.  Will it hurt to just leave it there?  Does anyone know how I can uninstall it manually?

Thanks.

---

### Post by Kobalt on 2007-05-02
These won't literally break off your system, but they can be messy and in my opinion pretty useless (since Feisty is now shipped with Universe & Multiverse enabled by default). 
You can leave the packages you installed through these and yet remove automatix or easyubuntu. And you can edit your menu entries with Alacarte (Alt+F2 > alacarte).
The next move would be to clean your sources.list file with what you want to install (I guess the Medibuntu repos will have to be added and that's it)...

---

### Post by shaft350x on 2007-05-02
If you aren't really using the programs to download things, then they should be able to just sit there.  The way that Automatix has been said to break things is because is uses certain scripts to make changes to the system, and download from different repositories.  It does not do this to be malicious, it is just how it worked.  (Don't know if this is still the case).  Easy Ubuntu does something similar, but it basically installs codecs and whatnot.

If you want to download programs and such, I would suggest learning to use Add/Remove and the Synaptic Package Manager, and then the terminal for anything extra you may need to do.

Automatix and EasyUbuntu are kind of made obsolete by Feisty, since it will download, most, codecs on its own.  You still may have to use the medibuntu ? files to be able to run encrypted dvd's, perhaps some others.

Also you may want to check out these threads
[http://ubuntuforums.org/announcement.php?f=13](http://ubuntuforums.org/announcement.php?f=13)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by K.Mandla on 2007-05-02
> **timzak said:**
> How bad is it to leave these on my system with the things they've already installed?  Am I hurting myself down the road?
Not necessarily bad, but it's hard to say. Ask the same question on the forum for the script you used, and if you have problems in the future with things, that's the first place to ask.

> **timzak said:**
> Should I reinstall Feisty Fawn from scratch?  Or can I move forward from here and learn to install programs without having to reinstall the OS?
I wouldn't reinstall unless you really aren't comfortable with it, but yes, it's worth learning how to install and uninstall things without scripts.

> **timzak said:**
> Second question, I installed EasyUbuntu on 7.04 before learning it wasn't compatible with 7.04 (yet).  As of now, there is a launch icon in my menu that does nothing when you click it.  I don't see that it's hurting anything, but it's completely useless and I don't know how to uninstall it.  Will it hurt to just leave it there?  Does anyone know how I can uninstall it manually?
It probably won't hurt to leave it there, but again, ask the same question in [the forum for EasyUbuntu]("http://ubuntuforums.org/forumdisplay.php?f=86"), and perhaps someone can give you some guidance on that.

---

