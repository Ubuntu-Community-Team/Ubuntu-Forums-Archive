---
title: "Problem installing last.fm"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Rhumbline on 2007-10-25
I'm using edgy and trying to install last.fm from the auto download and install.
When the package installer runs I get a red error message dependency not satisfiable libasound2.
I checked and I do have libasound 2.
I did sudo apt-get install libasound2 and i have the up to date version
I tried the open lastfm_1.2.3.13_i386.deb again and got the same message
Am I missing something?

Paul

---

### Post by aidanr on 2007-10-25
Try one of the i386.debs from this page
[http://archive.ubuntu.com/ubuntu/pool/universe/l/lastfm/](http://archive.ubuntu.com/ubuntu/pool/universe/l/lastfm/)

---

### Post by Rhumbline on 2007-10-25
I just tried one and I got the same message...

---

### Post by mayonaise15 on 2007-10-25
Just FYI - The music player Amarok has a built in last.fm client. [Here is a screenshot.]("http://amarok.kde.org/d/en/index.php?q=gallery&g2_itemId=1060&g2_imageViewsIndex=1")

---

### Post by aktiwers on 2007-10-25
Rhythembox has it build in as well

---

### Post by Vadi on 2007-10-25
Try "sudo apt-get install lastfm". The client is also in the repositories.

---

### Post by Rhumbline on 2007-10-25
Thx a lot of similar posts about lastfm seem to recommeng amarok...maybe I should try it

---

### Post by Rhumbline on 2007-10-25
Is that the full scrobbling version or just the radio player???

---

### Post by mayonaise15 on 2007-10-25
It does full scrobbling, including stuff you play from the radio stream.

---

### Post by macogw on 2007-10-25
Banshee and Exaile (and Songbird too, I think) do last.fm scrobbling as well.

---

