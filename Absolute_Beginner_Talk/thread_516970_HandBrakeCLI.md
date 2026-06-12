---
title: "HandBrakeCLI?"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by Wolfraptor1 on 2007-08-03
I've always used the latest version of an encoder called HandBrake, but having used it in windows I had a GUI, can anyone help me with the CLI version in Linux?

---

### Post by Wolfraptor1 on 2007-08-03
This is the command that I put in:

 /home/*******/HandBrakeCLI -i /cdrom/video_ts -o /home/osbornj/tast.avi -t 1

and this is what I get back from the terminal/CLI:

HandBrake 0.8.5b1 (2007042001) - [http://handbrake.m0k.org/](http://handbrake.m0k.org/)
1 CPU detected
Opening /cdrom/video_ts...
No title found.
HandBrake has exited.

Anyone know what the heck is going on here, I'm new to this and I want to learn?

---

### Post by ThrobbingBrain66 on 2007-08-03
i think the correct path is /media/cdrom/video_ts

---

### Post by Metallinut on 2007-09-05
Has anyone tried using Handbrake's Windows GUI through wine?

---

### Post by destructaball on 2008-05-04
Doesnt work, needs NET framework 2.0 so no help there

---

### Post by tylerapayne on 2008-05-22
The reason it isn't finding anything in the video_ts folder is because it should be all caps. it should read /cdrom/VIDEO_TS.

---

