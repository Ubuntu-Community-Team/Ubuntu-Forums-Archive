---
title: "VLC playing AVI file problem"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by quinlo on 2008-04-01
When I open up an avi file with VLC... it displays a blue screen instead of the video.  The audio is fine.  I tried for a few hours to fix this but to no avail.  I am new at ubuntu, linux, and the whole thing so give me some slack.  

The same blue screen is displayed when I try to play it with Mplayer as well.  I did however find out that if I open the file with Mplayer (and get the blue screen error) and then, while it is still open, open the avi file with VLC then the video works perfectly.  

Is there anyway to avoid having to open multiple programs just to watch avi's?

---

### Post by adityakavoor on 2008-04-01
Did you try with other video avi files as well ? MIght be a problem with this video.

---

### Post by taavikko on 2008-04-01
Might help changing the video output module in mediaplayers preferences

---

### Post by quinlo on 2008-04-01
Yeah... I tried other AVI files... same thing.  It also does it with other file extensions .wmv etc....

---

### Post by taavikko on 2008-04-01
> **quinlo said:**
> Yeah... I tried other AVI files... same thing.  It also does it with other file extensions .wmv etc....

DId you try other video output modules!?

---

### Post by quinlo on 2008-04-01
I went into settings on VLC and clicked on each video output module, does this enable it? I am not quite sure... the screen remained blue and the sound continued to play.  Is there some sort of administratve setting to enable these modules for all programs or something?

thanks for helping a newbie out by the way, and damn that last response was fast.

---

### Post by taavikko on 2008-04-01
> **quinlo said:**
> I went into settings on VLC and clicked on each video output module, does this enable it? I am not quite sure... the screen remained blue and the sound continued to play.  Is there some sort of administratve setting to enable these modules for all programs or something?

Yes, in the preferences window, on the bottom right corner is a advanced options box
put a tick on it, it enables you to change the settings.

and in the left side is the menu, go to Video->Output modules
and change the video output module : Default to something else.

Save, I don't remember if it was mandatory to restart to changes to take effect.
Propably the opengl or x11 driver is good enough.

---

### Post by quinlo on 2008-04-01
AH! Beautiful, I switched to Open GL, restarted the program and it worked like a charm... with all video formats that I wish to play.  Thanks a lot!

---

