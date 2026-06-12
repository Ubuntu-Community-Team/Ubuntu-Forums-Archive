---
title: "How to edit"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by Netspeed on 2007-04-04
I'm trying to edit a line in Asterisk. Here's what the terminal displayed:

cat /etc/default/asterisk
# This file allows you to alter the configuration of the Asterisk
# init.d script
#
# RUNASTERISK: run asterisk upon boot. Should be set to "yes" once you have
#              setup your configuration.
RUNASTERISK=no

So how or what command do I use to change the RUNASTERISK to "yes"?<br /><br />
----------------------------------------<br />

----------------------------------------<br />

---

### Post by taurus on 2007-04-04
```
gksudo gedit /etc/default/asterisk
```

---

### Post by edgecoug71 on 2007-05-04
you can also use vi /etc/default/asterisk through the terminal editor.....you can edit it either way, hope everything works out for ya.....

if you want a tutorial on the vi editor, type in terminal:  man vi

---

