---
title: "Create Session Without DE??"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by brennydoogles on 2008-01-31
Hello, I have recently gotten in to remote administration with ssh, and have been having problems with forwarding X across the network. I am fairly certain that the problems I am having are a result of having the GUI from the remote computer running over my own. My question then, is how can I create a CLI only session on my local computer?? This would allow me to log in graphically to the other computer, without worrying about my GUI. Any help would be appreciated!!

---

### Post by Origin415 on 2008-01-31
Which computer do you want to be CLI only? Or do you want the remote access to be only command line?

---

### Post by brennydoogles on 2008-01-31
I would like the ability to run my local computer ( the one I am sitting in front of) without a GUI, but only temporarily when I need to Does that make sense?

---

### Post by robjoski on 2008-01-31
Have you tried Control-Alt-F2? Or do I misunderstand you?

EDIT: Sorry, I forgot to say what Control-Alt-F2 *does*. It switches to a virtual terminal. (AKA, a command line.)

---

### Post by brennydoogles on 2008-01-31
> **robjoski said:**
> Have you tried Control-Alt-F2? Or do I misunderstand you?

EDIT: Sorry, I forgot to say what Control-Alt-F2 *does*. It switches to a virtual terminal. (AKA, a command line.)

So would this actually kill my current X session and allow me to be in terminal only mode, or would this open something similar to a fullscreen terminal? Just curious, but this looks like what I was looking for. Thanks!

---

### Post by robjoski on 2008-01-31
Yes, it will switch to, as you put it, "a fullscreen terminal", and you can switch back to X with Control-Alt-F7. Oh, and you're welcome. :-)

---

### Post by picpak on 2008-01-31
You'd have to go to System > Administration > Services and uncheck "Graphical login manager (gdm)" if you want to log in to CLI only.

---

