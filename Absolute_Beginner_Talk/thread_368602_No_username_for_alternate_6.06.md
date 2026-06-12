---
title: "No username for alternate 6.06"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by tomco on 2007-02-23
I have just installed 6.06. At one stage I had to give a password but was not asked for a username. Now I cant log on as I need this! Help!

---

### Post by taurus on 2007-02-23
The username would be oem.  After log in, make sure you run

```
sudo oem-config-prepare
```
to create an actual account for you to use from then on.

---

### Post by Bachstelze on 2007-02-23
Did you do an "OEM" install ?

---

### Post by tomco on 2007-02-23
Thanks guys - worked! Not sure how I was supposed to guess that though!

Cheers

---

### Post by Bachstelze on 2007-02-23
You aren't supposed to do an OEM install in the first place. It's for computer sellers that want to sell systems with Ubuntu preinstalled so the user only needs to run that command to set hit/her username and other stuff.

---

