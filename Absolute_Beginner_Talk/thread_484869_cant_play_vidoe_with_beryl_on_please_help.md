---
title: "cant play vidoe with beryl on please help"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by jerrykun on 2007-06-26
hehe this is funny, my only problem comes when i have beryl on i found that i cant play videos on my labtop. But if i turn off beryl i can see them in all players.

when i have beryl on i get this messege when i run vlc from the terminal
[php]X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  82
  Current serial number in output stream:  83
[/php] 

But it so happens that when i switch my window manager to metacity it plays vidoes just find. btw when i have beryl on the only way for me to see play videos is with mplayer by putting this codec X11( XImage/shm )to make it able to go full screen i had to add this to my Mplayer-config: zoom=yes in the end i found wierd how my Mplayer-config looks all thought im a newby in the linux comminty. this is how it looks after adding the line in the bottom: 
[php]
# Write your default config options here!

zoom=yes
[/php]
 
Any help at with this problem i would gladly apreciate thanks

---

### Post by ggaaron on 2007-06-26
You have a radeon probably and you are using xgl. If you don't have radeon then install beryl using aiglx or nvidia drivers, I remember that there were many howtos to install beryl, using xgl and aiglx for sure. xv video output uses opengl to rescale video from what I know, and xgl can only support one opengl app at one time (so beryl uses this place). Alternatively you can change video output of player to some software output (xshm or something like that), it will use more cpu, but on modern cpu it is not a problem.

---

