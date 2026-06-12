---
title: "What config file handles my sound drivers?"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-11-10
What config file handles my sound drivers?
I booted between Windows XP and Ubuntu Feisty so many times because I had to use my scanner in Windows that something got messed up in Ubuntu regarding the sound.  It's like its dead :confused: it still works like normal in Windows so there's no cable or circuit frying problems.

I'm thinking that if I --purge reomove whatever config file or program that handles the sound drivers in Ubuntu I can re-install fresh so that the sound will work again like it did some hours ago.

---

### Post by TheLions on 2007-11-10
to reinstall your sound card you need reinstall alsa. You can dwn it from  [www.alsa-project.org](www.alsa-project.org)

But to answer you q:
all hardware confg is saved in /etc/x11/xorg.conf (to edit it you must be root)

---

### Post by jingo811 on 2007-11-11
I already did a new re-installation by following this tutorial on the forums.  The hardware seems to get detected without problems.  It was detected without problem even when the sound suddenly died. :confused:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

```
$ sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```
```
$ sudo apt-get install linux-sound-base alsa-base alsa-utils
```
```
$ sudo apt-get install gdm ubuntu-desktop
```
```
$  aplay -l
```


> /etc/x11/xorg.conf 
What section in that conf file should I look for regarding my sound device?
How should that section look like maybe I can copy off somebody elses configurations?

---

### Post by rorestuff on 2007-11-11
have you checked alsamixer to make sure you didn't mute your sound somehow? happens some times...type 'alsamixer' at the console

---

### Post by jingo811 on 2007-11-11
Yeah I ran that earlier trying to to activate every possible column and raising the equalizers no difference.  But by fiddling around in the usual speaker GUI icon I found out about this by chance.
[IMG]http://i8.tinypic.com/7xt0qia.png[/IMG]

I unticked that box which I never touched or seen before and I could hear again :lolflag: It's not fun being death as a bat even for 24 hours.

---

