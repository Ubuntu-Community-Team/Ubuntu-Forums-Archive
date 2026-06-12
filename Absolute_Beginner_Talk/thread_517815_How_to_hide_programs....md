---
title: "How to hide programs..."
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by Hopeless on 2007-08-05
hi,

i have amule and want to hide it from the applications panel and while running from view...

how can i do this? so no one can see it lookin over my shoulder?

thanks..

---

### Post by superstylin on 2007-08-05
Hmm... interesting :P

Let me know how you do it with a GUI app!

:)

---

### Post by tbroderick on 2007-08-05
devilspie. Take a look at this guide,

[http://foosel.org/linux/devilspie](http://foosel.org/linux/devilspie)

There is a skip_tasklist and skip_pager action. Something like,
```

(if 
  (is (application_name) "amule") 
    (begin
        (skip_pager)
        (skip_tasklist)
    )
)

```

---

### Post by Hopeless on 2007-08-05
hi,

can i move the icon in /usr/share/application/amule to my home folder to execute it? will this remove it from the applications start menu?
thanks

---

### Post by panther_sn on 2007-08-05
You can remove it from the start menu by right clicking menu select edit menu, and then remove it from the menu, then to start just press <alt> f2 and type the startup command, in this case amule, and press enter

---

### Post by Hopeless on 2007-08-05
panther_sn thanks !!!! works great...

now just have to figure out a way of hiding amule when its running...?

---

### Post by atomkarinca on 2007-08-05
> **Hopeless said:**
> panther_sn thanks !!!! works great...

now just have to figure out a way of hiding amule when its running...?

is hiding amule to the notification area enough for you? then open amule, in preferences > general tab there are two options "enable tray icon" and "minimize to tray icon", check both of them. now when you minimize the window or double-click the amule icon on notification area, you will see only amule icon.

---

### Post by Hopeless on 2007-08-05
hi,
my other half can still see it and will probably click on it... so no... 

what about locking workspace 2 with a password? is it possible?

---

### Post by panther_sn on 2007-08-05
if ur missus is that worried about u downloading porn time to get a new missus, mine lets me, infact encourages lol

---

### Post by Hopeless on 2007-08-05
tell me about it.... your one got a sister? me look soon me thinks... in the mean time....less shouting if she don't find nothing...

---

### Post by Hopeless on 2007-08-05
i noticed when i right click the menu and take amule out i can't alt + f2 to amule i have to add it then run it and remove it again...

any ideas on how to remove and hide a program?

---

### Post by panther_sn on 2007-08-06
it should be just a matter of alt f2  then type amule and press enter, but give me a few and I'll test it for you

---

### Post by panther_sn on 2007-08-06
yep that works beautifully just press <alt>+F2 then type amule in the box, as I have done in the screen shot,  and press enter or click on run

---

### Post by Hopeless on 2007-08-06
i apologize... i only have 256 mb memory and had other progs working.... works great.... sorry about that...and thanks again for helping me..!!!

now just have to hide program running... in windows i used taskbar hide 1.28

p.s. i grew up in Ipswich....

---

### Post by ashmew2 on 2008-02-05
Well I need to hide Ktorrent when its running . Isnt there some sort of HotKey which , when once pressed , Hides Ktorrent and then restores it when pressed again ?
Or is there any other way >?
Thanks

---

