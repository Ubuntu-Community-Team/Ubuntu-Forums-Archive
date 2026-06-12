---
title: "Valuble CPU Cycles"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by DrunkinRoxtar on 2007-11-12
Does anyone know if screen savers turn off when the monitor shuts off?  I currently am set up with random screen savers, and the monitor to shut off after 20 mins.  Obviously, my CPU/GPU will consume more power running the screen saver whilst the monitor is off, and since my computer is on 24/7, I'd like to conserver power as much as possible.  Does anyone know whether a monitor shut off signals the screen saver off as well?

thanks
Luke

Oh BTW, I'm running 7.10

---

### Post by jordanmthomas on 2007-11-12
I believe it keeps running.
If you're concerned about power, why not disable screensavers altogether?

---

### Post by steve.horsley on 2007-11-12
I _think_ they do. But it's a good question. When my PC gets hot, the fans inside speed up until the windows rattle (sounds like that anyway). And I've never heard them like that when the screen is blanked. But what you could do is run up the system monitor and leave the CPU graph on the screen, chose a saver that hammers the CPU and leave it to cook for a while. Then wake it up with a keystroke and look at the graph - see how busy its been in the last minute or so.

---

### Post by FuturePilot on 2007-11-12
Yes the screensaver stops running when the screen shuts off. If the screen turns off and a couple minutes later you wake it back up again, you can check your CPU usage and you'll see that when the screen shut off, the CPU usage dropped.
I've also noticed that my fan on my laptop doesn't run as much when the screen is off.

---

### Post by jordanmthomas on 2007-11-12
> **FuturePilot said:**
> Yes the screensaver stops running when the screen shuts off. If the screen turns off and a couple minutes later you wake it back up again, you can check your CPU usage and you'll see that when the screen shut off, the CPU usage dropped.
I've also noticed that my fan on my laptop doesn't run as much when the screen is off.

On mine (granted, I am not using Ubuntu and haven't used a screensaver since god knows when) the screen would shut off and if I just *barely* tapped the mouse the screen would come back on and the screensaver would still be running.  This could have changed since I've last used a screensaver, and I hope it has.  If it hasn't happened, it should.

---

### Post by dasunst3r on 2007-11-12
Another good way of checking this is to SSH into your machine while the display is turned off and running the *top* command.  Don't forget to install *openssh-server* first.

---

### Post by FuturePilot on 2007-11-12
> **jordanmthomas said:**
> On mine (granted, I am not using Ubuntu and haven't used a screensaver since god knows when) the screen would shut off and if I just *barely* tapped the mouse the screen would come back on and the screensaver would still be running.  This could have changed since I've last used a screensaver, and I hope it has.  If it hasn't happened, it should.

If you slightly tap the mouse the screensaver starts again, however it was not running while the screen was off. You can check this by looking at your CPU usage chart with the Gnome System Monitor. (you might want to wait about 30 seconds after the screen shut off before you wake it up again.)

---

### Post by jordanmthomas on 2007-11-12
> **FuturePilot said:**
> If you slightly tap the mouse the screensaver starts again, however it was not running while the screen was off. You can check this by looking at your CPU usage chart with the Gnome System Monitor. (you might want to wait about 30 seconds after the screen shut off before you wake it up again.)

Ok, well that's good to know.  It's just that it looked like it had been running for a while.  I forget what it was even called now...it draws lines that look like a city.

Like I said, you're probably right and I'm not going to confirm or deny it as I don't even want screensavers installed on my box any more.

---

### Post by DrunkinRoxtar on 2007-11-12
I leave it on 'cause I really like the Ubuntu savers.  I thought about using Gnome System Monitor, but, I don't think it redraws itself when the screen saver is on.  And yes, when I tap the mouse, the screen will turn on, and the screen saver will be in full swing, which leads me to believe it doesn't turn off.  I think a variable fan, or external temp gauge would be a good indicator.  Don't have either of these though :(

---

