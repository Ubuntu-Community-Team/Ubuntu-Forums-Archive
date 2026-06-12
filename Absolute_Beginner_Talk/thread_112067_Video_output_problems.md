---
title: "Video output problems?"
date: 2006-01-03
forum: Absolute Beginner Talk
---

### Post by Janzuka on 2006-01-03
So at first I had this annoying problem with mplayer: allways when i tried to watch videos with it and i switched to the fullscreen mode, i got just a tiny window for the video and thick black frames around it. So in order to fix it i turned to the FAQ of mplayer and I found instructions for my problem. But typically, i thought i figured out a solution by typing -vo xv to the command line. And after i did that, it gives me an error that says "Error opening/initializing the selected video_out (-vo) device". So my question is how to cancel this -vo thing so that everything would be as it was earlier. For the original problem I have already found a much more reasonable solution. I would really appreciate it if someone would give me some advice.

---

### Post by gnu2tux on 2006-01-03
[QUOTE=Janzuka]So at first I had this annoying problem with mplayer: allways when i tried to watch videos with it and i switched to the fullscreen mode, i got just a tiny window for the video and thick black frames around it. So in order to fix it i turned to the FAQ of mplayer and I found instructions for my problem. But typically, i thought i figured out a solution by typing -vo xv to the command line. And after i did that, it gives me an error that says "Error opening/initializing the selected video_out (-vo) device". So my question is how to cancel this -vo thing so that everything would be as it was earlier. For the original problem I have already found a much more reasonable solution. I would really appreciate it if someone would give me some advice.[/QUOTE]

Hi, from 'man mplayer':
 
       Available video output drivers are:

       xv (X11 only)
       x11 (X11 only)
       xover
       xmvc
       dga
       sdl
       vidix
       xvidix

and many more...

so, give them a try and see if it goes away.
If not, its probably a preference stored in your ~/.mplayer/config file. Try deleting the file and restarting mplayer.

Regards,

Al.

---

### Post by Janzuka on 2006-01-03
Thanks for the advice,
 
So I tried to change those output drivers, but as far as i can understand, it does nothing by typing for instance: sudo -vo xv . When i first did that, it caused the problem, even though it gave me also then these instructions on how to use SUDO, but they were for me like Hebrev. So if it's possible could you give me the exact command which changes the drivers?

---

### Post by gnu2tux on 2006-01-13
[QUOTE=Janzuka]Thanks for the advice,
 
So I tried to change those output drivers, but as far as i can understand, it does nothing by typing for instance: sudo -vo xv . When i first did that, it caused the problem, even though it gave me also then these instructions on how to use SUDO, but they were for me like Hebrev. So if it's possible could you give me the exact command which changes the drivers?[/QUOTE]

try:

sudo mplayer -vo xv

cheers,

---

