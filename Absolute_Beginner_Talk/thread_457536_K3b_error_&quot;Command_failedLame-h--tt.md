---
title: "K3b error &quot;Command failed:Lame-h--tt"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by David4 on 2007-05-28
Just installed K3b with all recommended plugins and Libk3b2-mp3 as per prior posts.
K3b launches well, I select all files recorded on my HD, then select the filetype as MP3 Lame, then Start and get this error, Command Failed:lame-h--tt
I have Ubuntu 7.04, installed K3b using Synaptic.
PS: If select OGG-VORBIS as filetype it works just fine.
appreciate your help
David

---

### Post by yabbadabbadont on 2007-05-28
Make sure that you have the universe and multiverse repositories enabled, then install lame.

Edit: In synaptic, settings->repositories, enable universe and multiverse.  Save the changes.  Then hit the reload button.  Now search for and install lame.

---

### Post by David4 on 2007-05-28
Thank you very much.worked just fine.
My mistake was trying to install the file using terminal.
David

---

