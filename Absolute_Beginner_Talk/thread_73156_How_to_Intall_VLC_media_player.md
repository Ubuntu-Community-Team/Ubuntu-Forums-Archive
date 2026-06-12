---
title: "How to Intall VLC media player"
date: 2005-10-08
forum: Absolute Beginner Talk
---

### Post by edurm on 2005-10-08
Vlc is a greate Media Player, I'm trying to install it according to debian dist.


[http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)




but an error comes along:


```

root@ubuntu:~# apt-get install vlc libdvdcss2
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package vlc

```


What is going on :confused:

---

### Post by heimo on 2005-10-08
vlc is in universe section of repositories, which is not enabled by default.  Here's instructions how to enable universe:
[https://wiki.ubuntu.com/UniversePackages](https://wiki.ubuntu.com/UniversePackages)

---

### Post by edurm on 2005-10-08
[QUOTE=heimo]vlc is in universe section of repositories, which is not enabled by default. Here's instructions how to enable universe: [https://wiki.ubuntu.com/UniversePackages](https://wiki.ubuntu.com/UniversePackages)[/QUOTE] There's no two lines with universe at the end ????????????????? :confused: http://files.upl.silentwhisper.net/upload1/scrren_shot.png[/IMG] ding universe to Ubuntu will give you access to more packages. To do this: 1. Select Computer menu at top of screen, select System Configuration then Synaptic Package Manager. 2. When the program starts select the Settings menu then Repositories. 3. Resize the window so you can read everything in it (left click on the bottom left-hand corner and drag). 4. On the right hand size of the center panel, _you will see two lines with universe at the end. _Follow the first line and make sure the checkbox at the left is checked. 5. Click on the OK button at the bottom on the popup; universe will then be selected.

---

### Post by heimo on 2005-10-08
Select Ubuntu 5.04 "Hoary Hedgehog" (Binary) and then Edit. To the field 'Sections' add *universe *(separated with a space). On main screen, press "Reload". If this doesn't work either, you can always edit list of sources using text editor (eg. gedit) - here's instructions on Ubuntuguide:
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

---

### Post by edurm on 2005-10-08
[QUOTE=heimo]Select Ubuntu 5.04 "Hoary Hedgehog" (Binary) and then Edit. To the field 'Sections' add *universe *(separated with a space). On main screen, press "Reload". If this doesn't work either, you can always edit list of sources using text editor (eg. gedit) - here's instructions on Ubuntuguide:
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)[/QUOTE]


Thank you very much


Working great now

---

