---
title: "skype is running before GNOME desktop."
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by Daniel Song on 2007-07-08
Hello there,

I just installed Skype 1.4. It works fine so far except only one problem.

The problem is the Skype is come up lonely before GNOME desktop shows up. So, whenever I log in to GNOME desktop, I have to quit the skype by typing CTRL-Q, then I can enter GNOME desktop.

Is there anybody having similar experience above? And, how do I fix it?

---

### Post by felicity on 2007-07-08
You may want to start skype 15 seconds or so after your start up to give gnome time to start first. First you have to make a new file in your home directory with the name of:

.skype_startup.sh

And enter this code in the file:
```

#!/bin/bash
sleep 15 && skype;

```

Then give it permissions by typing this in terminal:
```

sudo chmod a+x .skype_startup.sh

```

Then go to System > Preferences > Sessions and find the skype entry. Edit it and where it asks for a command browse or type the location of the script (/home/$USER/.skype_startup.sh)

---

### Post by Daniel Song on 2007-07-08
felicity,

Thank you for your concern, felicity, but the problem is the Skype is come up before the Session starts. So, no matter how I set up in Session, Skype is running before the Session start.

---

### Post by felicity on 2007-07-08
Oh, sorry. I don't use skype so perhaps someone else can help you with this problem!

---

