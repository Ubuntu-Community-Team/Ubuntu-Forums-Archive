---
title: "How to take a screenshot with Totem showing the vid being played?"
date: 2006-07-05
forum: Absolute Beginner Talk
---

### Post by Cherry Popper on 2006-07-05
While reading about Totem in [Wikipedia](http://en.wikipedia.org/wiki/Totem_%28media_player%29), I noticed this - 

[ATTACH]12243[/ATTACH]

but when I try to take a screenshot (Print Screen Sys Rq), like the pic above, it comes up blank. How can I take a pic like the one in the Wikipedia article? This is what my pic looks like - 

[ATTACH]12245[/ATTACH]

---

### Post by aysiu on 2006-07-05
Well, Totem itself has a screenshot utility built in.

You could also try ```
gnome-screenshot --delay 5
``` It may also depend on the kind of video you're playing.

---

### Post by Cherry Popper on 2006-07-05
"gnome-screenshot --delay 5" -- Didn't work. The screenshot still came up blank. 

The built in screenshot in Totem only takes a pic of the video, but I'd like to take a pic of my whole desktop with Totem showing the vid being played so I can show it off in those 'Post you desktop' threads. :p ;) 

The vid is a .mpg file :)

---

### Post by Hi_Im_Fubar on 2006-07-05
"Looks like it's hardware acceleration / hardware video overlay that causes it. In Windows Media Player, under the performance tab, slide the video acceleration to something less than full. In Winamp, under Video Options, uncheck 'Allow hardware video overlay'. This should allow you to take screenshots with any program." - Yes, I copied that from somewhere else. Maybe someone can tell me how to do something of that effect with totem.

---

### Post by aysiu on 2006-07-05
Maybe **View** > **Deinterlace** might work.

---

### Post by Cherry Popper on 2006-07-05
Nah, "View > Deinterlace" didn't work. Something about 'Overlay', I remember being able to this in Windows Media Player by disabling some overlay feature.

Totem doesn't seem to have the option though. :(

---

### Post by user1397 on 2006-07-05
what if u just pause it first, and then take the pic?

---

### Post by Jagot on 2006-07-05
What format video are you playing when you try and cap - I've just messed around with ogg and mpg and they both work for me when taking screenshots?

---

