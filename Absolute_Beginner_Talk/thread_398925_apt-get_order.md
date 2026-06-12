---
title: "apt-get order"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by nickburns on 2007-04-01
If I type in apt-get install x y z

what is the order that the packages are installed and configured?

is it in the order x, then y and z last?

or z, y then x?

---

### Post by neoaddict on 2007-04-01
I think it's in XYZ order.

---

### Post by nickburns on 2007-04-02
Anybody know for sure????

---

### Post by tonyr1988 on 2007-04-02
Hope I'm not too intrusive, but what all are you installing? If the order is extremely vital, you could always just use different apt-get commands (unless you're installing a ton of packages)

I also think it's XYZ, though.

---

### Post by nickburns on 2007-04-02
I want to make a script / package that will get a LAMP install, with other packages (phpmyadmin, etc...) on a ubuntu gnome install.  It is best if you install apache then php5 in order for it to configure correctly.  I guess it is better to set up everything as a separate line rather and the x y z scenario.

---

