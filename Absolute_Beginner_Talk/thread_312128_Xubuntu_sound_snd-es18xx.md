---
title: "Xubuntu sound snd-es18xx"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by Bill L on 2006-12-03
I have Xubuntu edgy on an Armada 7400, love that it finds my Belkin wireless but I cant get sound to work. I found some things to try but when I open the files to edit with notepad I can not save my changes because the file is root protected.

My sound card needs es18xx driver so the path of least resistance for sound is great but the root password problem is one that haunts me in all my ubuntu experience so help there is important

---

### Post by drphilngood on 2006-12-04
> **Bill L said:**
> I have Xubuntu edgy on an Armada 7400, love that it finds my Belkin wireless but I cant get sound to work. I found some things to try but when I open the files to edit with notepad I can not save my changes because the file is root protected....

Exactly how are you opening the files to edit them?  Are you using something like:

```
gksudo gedit /file/to/edit
```

in a terminal?

---

### Post by Bill L on 2006-12-04
> **drphilngood said:**
> Exactly how are you opening the files to edit them?  Are you using something like:

```
gksudo gedit /file/to/edit
```

in a terminal?

I tried, the first time it prompted me for a password and went back to the prompt.  The second time it said gedit was not found

```
 bill@bill-laptop:~$ gksudo gedit /etc/modeprobe.d/alsa-base
bill@bill-laptop:~$ gksudo gedit /etc/modeprobe.d/alsa-base
sudo: gedit: command not found 
```

---

### Post by gabkdlly on 2006-12-27
gedit is not installed on a default Xubuntu Edgy install.

Try:

```
gksudo mousepad /etc/modeprobe.d/alsa-base
```

---

