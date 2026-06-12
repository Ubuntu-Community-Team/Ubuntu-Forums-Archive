---
title: "avi not working"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by swp6499 on 2006-09-20
i need a avi codec for kubuntu...i cant get any avi to play...says format not supported in all video players?? any suggestions?

---

### Post by enopepsoo on 2006-09-20
if you install vlc ir mplayer in synaptic it should install the proper codecs.  I think they mostly come with synaptic.

For things like wmv9 on amd64 or dvd playback, see a different thread.:)

---

### Post by swp6499 on 2006-09-20
i have vlc installed it says the same thing??

---

### Post by qyot27 on 2006-09-20
mplayer comes with everything built-in (since libavcodec handles a bajillion different types of compression formats).  It's in the repositories - universe or multiverse if I recall correctly.

---

### Post by swp6499 on 2006-09-20
vlc,mplayer,etc all say plugin or codec not found??

---

### Post by gils0040 on 2006-09-21
make sure that universe and multiverse repos are enabled and try
sudo apt-get install w32codecs

---

### Post by swp6499 on 2006-09-21
it says its already the newest version when i try apt-get install?

---

### Post by Barts_706 on 2006-09-21
Quite frankly, I am surprised that VLC would ask for codecs, since they are integrated with the player.

Didn't you run Totem Media Player after installing VLC?

Please, do not feel offended, but since you are asking beginner's questions, it might just be that you didn't actually run VLC to watch your avi?

---

### Post by swp6499 on 2006-09-21
what exactly do u mean run vlc?? i opened vlc and opened the file and it doesnt work??

---

