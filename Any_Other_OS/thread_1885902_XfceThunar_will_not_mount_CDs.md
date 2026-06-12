---
title: "Xfce/Thunar will not mount CDs"
date: 2011-11-21
forum: Any Other OS
---

### Post by daniel227 on 2011-11-21
oh yes, this is thread necromancy :p - 
but, it seems i have the same "problem".

as hhh said, it's not much of an issue but i'd love to settle on ONE music player - right now i have my eyes on gmusicbrowser or rhythmbox - and they just don't "see" the cd.

thunar sees it but says it's not mountable. in thunar-volman i can add an application to open the cd. but, at least for vlc, if i use %d it won't work, i have to hard-code the command to vlc cdda:///dev/sr0

-- so is that just how it is, was and still is?

(i am using linux mint fluxbox based on ubuntu lucid LTS. this version uses elements of lxde and xfce)

my thread on this: [http://ubuntuforums.org/showthread.php?p=11475823#post11475823](http://ubuntuforums.org/showthread.php?p=11475823#post11475823)

---

### Post by bobcollard on 2011-11-21
> **daniel227 said:**
> oh yes, this is thread necromancy :p - 
but, it seems i have the same "problem".

as hhh said, it's not much of an issue but i'd love to settle on ONE music player - right now i have my eyes on gmusicbrowser or rhythmbox - and they just don't "see" the cd.

thunar sees it but says it's not mountable. in thunar-volman i can add an application to open the cd. but, at least for vlc, if i use %d it won't work, i have to hard-code the command to vlc cdda:///dev/sr0

-- so is that just how it is, was and still is?

(i am using linux mint fluxbox based on ubuntu lucid LTS. this version uses elements of lxde and xfce)

my thread on this: [http://ubuntuforums.org/showthread.php?p=11475823#post11475823](http://ubuntuforums.org/showthread.php?p=11475823#post11475823)
Open VLC>Tools>Preferences>Input & Codecs  Change the line reading /dev/dvd to read /dev/sr0 save and exit

---

### Post by daniel227 on 2011-11-23
> **bobcollard said:**
> Open VLC>Tools>Preferences>Input & Codecs  Change the line reading /dev/dvd to read /dev/sr0 save and exit
yes, i have to do that everytime, and still it is filled with gibberish after a restart....
i wonder what it means.
thanks anyway.

however vlc was one of the music players i was NOT going to settle on.

apart from that, gmusicbrowser is great!

---

### Post by Perfect Storm on 2011-11-24
Post splited and moved to Other OS/Distro Talk.

---

