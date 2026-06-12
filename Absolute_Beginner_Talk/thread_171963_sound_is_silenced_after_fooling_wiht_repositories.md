---
title: "sound is silenced after fooling wiht repositories"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by ggankhuy on 2006-05-07
Hello, I wanted the Rhythm Box to play MP3 player, the I found that the WIKI says run
apt-get install  gstreamer0.8-mad...
after installing gstreamer0.8-mad through repositories.. as far as I understood.
I didn't find hte gstreamer0.8-mad package but marked several packages with similar names, now there is no sound at all. How could be possible the there is no sound after running some repositories? 
The sound card nad speakers are ok, since I was able to log into Windows and play song. Is there a way to fix it? THanks!

---

### Post by ProjectGod on 2006-05-15
try xmms? i think its xmms.

"sudo apt-get install xmms"
"sudo killall gnome-panel" assuming its ubuntu / gnome.

after the installation. don't double click on the *.mp3 file. open xxms player up and then browse to the file to play... otherwise it may very well use your default / previously installed / pre installed media player... which as you've said does not work.

---

