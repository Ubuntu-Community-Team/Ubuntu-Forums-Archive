---
title: "[SOLVED] gnome-power-manager shows 0% even though battery is full"
date: 2008-03-26
forum: Apple Intel Users
---

### Post by fabbaz on 2008-03-26
hi!
i have a problem with my macbook core2duo 2ghz (early 2007) running ubuntu 7.10
recenty the gnome-power-manager shows wrong battery information, worst of which it shows that the battery is charged at 0%, whether the ac is plugged or not, and even though it claims to be charging when on ac, the symbol still shows 0% and stays there.
it seems to me it is a gnome specific problem, but since the apple hardware is so "special" i thought it would be better to post here.
```
cat /proc/acpi/battery/BAT0/state
``` shows
> present:                 yes
capacity state:          ok
charging state:          charging
present rate:            0 mW
remaining capacity:      0 mWh
present voltage:         0 mV
attached a screenshot showing that the applet gives the same output, but less... "acurately".[IMG]http://lh6.google.com/fabian.bazant/R-qjxfqy2aI/AAAAAAAAFcg/008afLCfssE/Screenshot.png[/IMG]
i can't remember the full exact phrase that is supposed to stand there, but it was definitley at least 5 times that long (not that i ever cared what was standing there, just the fact it WAS standing there kind of eased my mind. you know, like when flying a space ship and seeing no valves or lcd's or leds or blingblings showing you where the next kilrathi missile is coming from. WAAAAAH!!!!)
i am not aware of having changed any settings which could have inflicted this, nor am i aware of any recent updates which might have caused that.

ah, i almost forgot: the battery lifetime is not changed: the macbook battery has a status led showing the capacity and current state, and those are both acurate and seem correct to me. so it isn't a hardware problem with the battery itself, i believe...


thank you for all support!!

---

### Post by cyberdork33 on 2008-03-26
Well, before you went off on a Wind Commander tangent, I was thinking maybe you need to make sure the applesmc module is loading...

---

### Post by david_edmundson on 2008-03-26
It's a known hardware bug. Affects OS X too.
The fix is listed on Apples website somewhere.

Shutdown, take the battery out, and disconnect the mains. Then press and hold the power button for a while. Reassemble, and all will be good.

---

### Post by fabbaz on 2008-03-31
thanks a dozen!
took the battery out, put it back in, applet works again. yay!
now just for finding out how to mark a thread as "solved"... ;)

---

