---
title: "System temperature/fan speed monitor"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Hellcom on 2007-08-02
Is there a utility for monitoring system temperatures and fans, and is not overly complex to install as lm-sensors?

---

### Post by ramjet_1953 on 2007-08-02
Yep!

There are a few steps:

1. [COLOR="Red"]apt-get install hddtemp[/COLOR]
When it installs, it will ask you a couple of questions, just accept the defaults.
This will allow you to monitor your HDD temperature.

2. [COLOR="Red"]apt-get install sensors-apple[/COLOR]t
After this is done, just right-click on either the top, or bottom panel and choose [COLOR="Blue"]Add to Pane[/COLOR]l.

3. Choose [COLOR="Blue"]Hardware Sensors Monitor[/COLOR].
It will add an icon to the panel and you just right-click on the icon to configure whatever sensors you system has.

4. Make sure that you put a tick in the box of each sensor that you want to monitor.

Regards,
Roger :cool:

---

### Post by Hellcom on 2007-08-03
Thanks, this is perfect!

---

### Post by Inxsible on 2007-08-03
Another app:
Right click top or bottom panel. Select Add To Panel. Look for CPU Monitor.

Yet another app:
Install screenlets. It has pre-defined screenlets to monitor CPU temp and also network speeds and such along with weather...etc

---

