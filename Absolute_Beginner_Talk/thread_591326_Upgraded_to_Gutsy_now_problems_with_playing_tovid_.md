---
title: "Upgraded to Gutsy now problems with playing tovid encoded video"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Statik on 2007-10-25
Hey all,

As the title says, I've just dist-upgrade d to Gutsy and I'm having trouble playing videos encoded in tovid now. Xine and MPlayer startup but freeze before the video plays. Movieplayer complains it cannot open the video device. kdenlive opens the video but doesn't play it. Same thing happens with wmv and avi files.

I cannot close the players from the corner X, but the right-click menu on the bottom menu bar brings up the 'force quit' menu.

Where do I start looking for solutions?

Statik

---

### Post by shamusl on 2007-10-25
Try using vlc, it does wonders for every file I use.

---

### Post by Statik on 2007-10-25
No joy there either. Video plays but no sound (atleast with the tovid encoded file). Clicking the corner X gives me the 'not responding, force quit' popup.

Statik

---

### Post by Statik on 2007-10-25
Well, this is weird. I think I fixed it, but I don't know how.

Usually, when one of these programs locks up, even after it visually closes using the right-click context menu, I need to go into the system monitor and kill the process. After testing the VLC playback I went looking for it and I noticed TWO mplayer processes. So, I killed one, a ZOMBIE, and a flood of different sounds came out, probably in a queue. Now Xine, and VLC play the files fine, and my FIrefox Flash works now too!

Thanks all

I hope this doesn't come back.

Statik

---

