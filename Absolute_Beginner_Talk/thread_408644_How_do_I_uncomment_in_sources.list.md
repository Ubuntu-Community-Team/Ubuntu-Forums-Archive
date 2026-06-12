---
title: "How do I uncomment in sources.list?"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by supazio on 2007-04-13
Quick question, a guide told me to uncomment some lines, but I have no idea what that means or how to do it. Sorry for being such a noob, but I figured this was better than doing what I would have done otherwise(delete the lines).
```
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe
```and
```
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
```

---

### Post by Perfect Storm on 2007-04-13
Open the terminal;
Applications tab --> Accessories ---> terminal

type;
```
sudo nano /etc/apt/sources.list
```

Remove the # infront of the source lines.

save (ctrl+o) and exit (ctrl+x)

Then;
```
sudo aptitude update
```

---

### Post by D10 on 2007-04-13
Comments usually are lines that start with a # or ;. Just delete it from the line, and then whatever program needs to can read that line.

D10

---

### Post by aysiu on 2007-04-13
Commented (i.e., ignored... practically non-existent, as far as the system's concerned): ```
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe
``` Uncommented (active, as far as the system's concerned): ```
deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe
```

---

