---
title: "Broke cpufreq scaling lol"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by dbxuau on 2007-02-15
Being nosy and of course noob, i seem to have broken the cpu scaling. I get this message at start up. [http://img242.imageshack.us/img242/2821/screenshotjc1.png](http://img242.imageshack.us/img242/2821/screenshotjc1.png)

it was working all perfectly before i started screwing with it. plz help!

---

### Post by dbxuau on 2007-02-16
update: uninstalled and reinstalled cpudyn to no avail

---

### Post by sardion on 2007-02-16
What did you do to it?
What kind of processor do you have?

---

### Post by dbxuau on 2007-02-16
honestly i didnt do much at all other than try to change it from conservative to powersave via terminal, thats it. CoreDuo (not 2) 2.0ghz

---

### Post by sardion on 2007-02-16
How did you go about trying to change it?

Try

sudo /etc/init.d/powernowd restart

or even just rebooting...

---

### Post by dbxuau on 2007-02-16
fixed, thanks a ton man, my issue was i WAS NOT using cpudyn to begin with as soon realized

---

