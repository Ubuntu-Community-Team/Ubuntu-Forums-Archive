---
title: "using ssh in terminal"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by greenw40 on 2007-03-28
Im using the terminal to connect to an ssh server but I cant display images, it says "display: unable to open X server".  In windows I would have to open the X session program, but I figured it would be easier using Ubuntu.  Anyone know how to do this?

---

### Post by nixclusive on 2007-03-28
are you using ssh on the text terminal? like the one you find on pressing Ctrl+Alt+F1?

---

### Post by tonyr1988 on 2007-03-28
Are you using X11 forwarding? Like:

> ssh -X [email]user@domain.com[/email]

---

### Post by greenw40 on 2007-03-28
thanks, i inserted -X and now it works

---

