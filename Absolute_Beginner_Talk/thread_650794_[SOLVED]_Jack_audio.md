---
title: "[SOLVED] Jack audio"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by allsys3 on 2007-12-26
I get this message when tring to open Ubuntu studio    "The JACK server does not appear to be running. Double-check your settings".,,,,,,how do i check my settings

---

### Post by wormser on 2007-12-26
I found a post on [launchpad]("https://answers.launchpad.net/ubuntustudio/+question/14550") with the same error.  There was not much information.

> Jack is the sound server that connects all your jack enabled applications, like ardour, hydrogen, etc. I suggest you use qjackctl to start and configure JACK.

It looks like qjackctl is the command to bring up the [console]("http://qjackctl.sourceforge.net/").  Try the following command.  If not found then try installing it.

```
qjackctl
```

---

### Post by allsys3 on 2007-12-26
Thanks I've got that working....I just need to figure it out now:)

---

