---
title: "probably running binary file"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by puterboy on 2007-06-09
So I'm trying to use official NVIDIA drivers. however, to install them, i can't have the X server running, so i use

sudo /etc/init.d/gdm [start|stop]

to shut down/start up the X server. The problem is, when I'm in the terminal or running from just the prompt, i get "Can't execute binary file". so it seems like the thing will only start with X server running, but it needs X server to be shut down before it'll run. any help?

---

### Post by Rocket2DMn on 2007-06-09
I think the command to start up the X session again is 
```
startx
```
but I've never had to use it myself

---

### Post by taurus on 2007-06-09
Are you in the right directory when you tried to run/execute it?  Did you change the permissions to executable?

---

### Post by puterboy on 2007-06-09
Thanks for the help, but i don't need the help anymore. Thanks anyway!

---

