---
title: "Need help with Nvidia tv out"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by Melhisedek on 2008-02-08
Can anyone be so kind and explain to me how can I enable TV-Out on my 8800GT card using latest drivers and "Nvidia Settings" software?

I get part of the picture on my TV but my monitor turns off, or I get some error saying "The current Layout has some inconsistencies" if I ignore I just get part of my desktop on TV but monitor still turns off. It can't Auto-fix it either.

I choose the same resolution for both TV and monitor and chose Twin-view and clones on both. I've tried some other combinations but without success :( Any ideas?

---

### Post by talsemgeest on 2008-02-08
Ive tried doing something like this before, but couldnt get it to work.

You might want to try editing your xorg.conf file: ```
gksudo gedit /etc/X11/xorg.conf
``` 

Hope this helps :)

---

### Post by Melhisedek on 2008-02-08
Dam it is so close :) I mean I can get a part of my desktop to show on TV but not whole desktop and not without monitor turning off :/

---

### Post by talsemgeest on 2008-02-09
Does nvidia have anything like the "catalyst control center"?

---

### Post by overdrank on 2008-02-09
> **talsemgeest said:**
> Does nvidia have anything like the "catalyst control center"?

Hi and yes that would be the nvidia settings. You stated you have tried the nvidia settings but it will not give you the correct resolution?

---

### Post by Melhisedek on 2008-02-09
Yeah... I'm not sure what I'm doing there to be honest. I can chose between TV and monitor and than they have all the same settings to play with. Like twin view, position and resolution. I tried bringing down monitor res to 800x600 but no luck. So if anyone can explain to me what setting they are using I guess it would work :)

---

### Post by Melhisedek on 2008-02-11
small update... I've managed to change resolution on TV (I guess I was able to do it before as well but bottom bar wasn't all that visible so I didn't notice) so only problem left is that my monitor turns off, or rather goes into standby mode whenever I enable twin view. 

Any ideas?

---

### Post by talsemgeest on 2008-02-11
There are options with graphics card drivers that you can enable through the xorg.conf. But what they are with nvidia I have no idea...

---

