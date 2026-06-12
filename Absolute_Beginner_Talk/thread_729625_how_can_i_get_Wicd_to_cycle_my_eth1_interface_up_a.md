---
title: "how can i get Wicd to cycle my eth1 interface up and down before connecting?"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by Sonic Reducer on 2008-03-20
i have a laptop that is just about dead. the battery holds literally no charge and i need to keep it plugged in to the wall to use it. when i leave it plugged in (like leaving it on the coffee table overnight) it will start up without any networking problems. but when i unplug it and move it i need to cycle the wireless on and off a few times to get it to work (i guess this is common in linux)

i decided to write a script to cycle it off then on a few times before connecting because i noticed that it is an option in Wicd.

so far i have this:
```
#!/bin/bash

sudo ifconfig eth1 down

sudo ifconfig eth1 up

sudo ifconfig eth1 down

sudo ifconfig eth1 up

sudo ifconfig eth1 down

sudo ifconfig eth1 up
```

is this right?

---

### Post by imdano on 2008-03-20
It won't work right in 1.4.2 because it tries to run the scripts in usermode.  So any commands that need root access won't run.  In 1.5.0 (the next version), scripts can only be edited as root, so they'll run as root too.  If you're comfortable with SVN you can download it now from the experimental branch of our SVN repository.

---

### Post by Sonic Reducer on 2008-03-20
then should i add the script to the list of startup programs in preferences/sessions?

---

