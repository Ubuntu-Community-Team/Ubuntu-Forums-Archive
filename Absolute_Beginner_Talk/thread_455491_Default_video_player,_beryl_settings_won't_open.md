---
title: "Default video player, beryl settings won't open"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by phoenix23 on 2007-05-26
I want VLC to be my default player for .mp4 videos. I right clicked on the thumbnail, clicked properties, and checked VLC. When I went to open the file again (regular double click) I got this error:

> The filename "Lost.S03E23.[iPodNova.tv].mp4" indicates that this file is of type "MPEG-4 video". The contents of the file indicate that the file is of type "MPEG-4 audio". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "MPEG-4 audio", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 

What's strange is I can still open the video with VLC (right click, open with other app), but why won't it work by default?

-------

One more thing. I've installed Beryl, and all the pretty effects work except beryl-settings. I get this error in terminal:

> Traceback (most recent call last):
  File "/usr/bin/beryl-settings", line 22, in <module>
    import berylsettings
ImportError: No module named berylsettings
 

I can't open the settings manager with the red diamond either.

Thanks!

---

### Post by starcraft.man on 2007-05-26
The answer to your Beryl question is that the command is "beryl-settings", I just ran it in tilda/terminal and it works fine.

I don't know why the m4a gives you trouble in vlc, did you try totem/audio player?

---

### Post by phoenix23 on 2007-05-26
Thanks starcraft man. I used the beryl-settings command in terminal, and got the error mentioned above.

I can open the video "manually" (right click open with), but I can't double click to open with VLC when I set it as the default.

---

