---
title: "Music codecs."
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by ry.syn05 on 2008-04-16
hello may anyone help me.... i cant paly any music in my ubuntu.... no plugin is installed... but i am unable to download it also.... hey plz rply...:confused:

---

### Post by bapoumba on 2008-04-16
Moved to its own thread.
You need to enable the multiverse repositories from Synaptic > Settings > Repositories, reload, and install ubuntu-restricted-extras.
While you are at it, you can enable all the ubuntu repos if you hve not already done so.

---

### Post by Sef on 2008-04-16
System > Administration > Software Sources

then check universe and multiverse.  

Next

System > Administration > Synaptic Package Manager

then search "Restricted Extras" (without the quotes), and check the system that you have (Kubuntu, Ubuntu, or Xubuntu.)   Click on the one you want, then click mark for upgrade, then click apply.

---

### Post by ry.syn05 on 2008-04-17
as you guys asked i have done all.... but still when i am going to play a mp3 file..its reporting that codec is not install.... i'm searchhing it through net as the player prompt.... but no plugins/codec is installed..... 

**plzzzzzz help.....me...**:(

---

### Post by oedha on 2008-04-17
really ??
1. activate software source just like Sef said
2. open terminal :==> applications - accessories - terminal
type
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ubuntu-restricted-extras
```

you should play the media files now......

---

### Post by ry.syn05 on 2008-04-17
as you guys asked i have done all.... but still when i am going to play a mp3 file..its reporting that codec is not install.... i'm searchhing it through net as the player prompt.... but no plugins/codec is installed..... 

**plzzzzzz help.....me...**:(

---

### Post by vanadium on 2008-04-17
Reread the above posts, repeat the procedure, and check on every step that you do. If error messages appear, report them here. The procedure mentioned above is the correct one to pull in mp3 support. You will find the same instructions here in the community documentation, which is a great place to read and look up if you have issues. [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

[edit]The procedure in the help uses Applications - Add remove" rather than the full blown Synaptic, so might be a tiny bit easier

---

### Post by gandaran on 2008-04-17
> **ry.syn05 said:**
> as you guys asked i have done all.... but still when i am going to play a mp3 file..its reporting that codec is not install.... i'm searchhing it through net as the player prompt.... but no plugins/codec is installed..... 

**plzzzzzz help.....me...**:(


which application you using to play MP3 files?

---

