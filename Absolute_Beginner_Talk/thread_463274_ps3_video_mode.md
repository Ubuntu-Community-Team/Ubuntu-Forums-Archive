---
title: "ps3 video mode"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by doggydogg232 on 2007-06-03
how do you change the screen to 480i standard.

---

### Post by LCC on 2007-06-04
Don`t know what you mean by standard but basically you check what hertz your TV uses (60hz or 50hz, usually shown at the back of the TV) then you type on the terminal:

[COLOR="Red"]
ps3videomode -v  1 -f[/COLOR]      # for a YUV 60Hz  TV

[COLOR="Red"]ps3videomode -v  33  -f[/COLOR]  # for  a RGB 60Hz TV

note that the full display  [COLOR="Red"]**-f**[/COLOR] might not be supported by your TV so you need to change**[COLOR="Red"] -[/COLOR]**f to [COLOR="Red"]**-d**[/COLOR]
I also couldn`t figured out why did I have to type [COLOR="Red"]ps3videomode -v 1 -d[/COLOR] every login so I just went to sessions (system>preferences>sessions) and added to the start up programs to execute ps3videomode -v  1 -f every time I logged in. If the screen goes black it means the video mode you chosen is not supported but don`t worry it will be back when you reset your ps3 but[COLOR="Red"]** DO NOT**[/COLOR] use a ps3videomode command on the start up that is not supported by your TV and if you are sure if you should use the start up option simply don`t use it. Hope it helps.

---

### Post by davidme on 2007-07-08
Here is how I finally solved my problem after spending 5 hours with this whole setup. I hate this thing, Because of one space I wasted so much time.

Anyhow I have a Samsung 40 inch LCD TV with 1080i HDMi

I tried many options including:

video=ps3fb:mode:4
video=ps3fb:mode:5
video=ps3fb:mode:131
video=ps3fb:mode:132
video=ps3fb:mode:133

All head something wrong with it. Either out of borders or black borders. The thing that finally worked for me is this

I looked closer at the setup here [http://www.edepot.com/playstation3.html](http://www.edepot.com/playstation3.html)
and found that there were spaces after the word mode. I though it probably does not matter, but after almost giving up I added a space and rebooted and all looks good now.

"video=ps3fb:mode: 4"

Notice the space after ":" for some reason this gave me the right resolution.

Take a look here: [http://psubuntu.com/forum/viewtopic.php?t=13&postdays=0&postorder=asc&start=15](http://psubuntu.com/forum/viewtopic.php?t=13&postdays=0&postorder=asc&start=15)

[B]Edit: Nah, I just rebooted and again I get black borders. I give up. Setting this mode to 4 makes it full screen, next time I reboot, I get black borders. 

???[/B]

---

