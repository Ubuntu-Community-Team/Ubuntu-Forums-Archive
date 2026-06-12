---
title: "VLC bug or virus?"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by Blue_Sky on 2007-02-07
Hi,
VLC has been acting strange lately. I can't use the right click menu anymore, and when I try to exit using the x in the top corner, it doesn't quit. On the System Monitor is show two wxvlc (I think it is wx) processes and the second one uses about four times the memory of the first. It also does not seem to be connected in any way to the music or videos I play. Also firefox now opens a new tab every time I use it to %u .com. (I don't know if this is connected).
Is this just my Windows paranoia kicking in or is this a virus?

Thanks,
Blue

Ok, so I uninstalled VLC, and when I right click on a video I still have the option to open it with vlc. (I previously had two "Open with VLC..."). So, I have a virus. What should I do now?

---

### Post by Blue_Sky on 2007-02-07
So is no one going to help me with this?

---

### Post by etank on 2007-02-07
I am assuming here that you are using Gnome. I don't think that this is a virus at all. Try this: 

1) Right on a video file.
2) Click on Properties.
3) Click on the Open With tab
4) Select VLC media player and then click remove.

Then do ```
sudo aptitude purge vlc
``` and then I would try reinstalling vlc.

---

### Post by Blue_Sky on 2007-02-07
Thanks!
I guess I got a bit too paranoid after my computer started acting weird after I clicked on the second "Open with VLC" option for the first time.

Blue

---

