---
title: "How to peek under Gnome for a while?"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by Tom Chaudoir on 2007-06-07
Hi,

If I hit Ctrl + Alt + Backspace Gnome restarts. That's fine. After it shuts down there's a screen of text. Some of that text tells me that there are problems and gives me suggestions on how to fix them. The thing is that Gnome restarts after a few seconds so there's no time to write it down.  It's a black screen with white text.

So how do I get some time to read the text? Thanks!

Tom

---

### Post by pbw on 2007-06-07
look in your logs, or shut down X for a few minutes.

---

### Post by Tom Chaudoir on 2007-06-07
Sorry if this is a repost.

Thanks! How do I do those things? I'm an absolute beginner. What's X and how do I turn it off? Where are my logs?

Tom

---

### Post by pbw on 2007-06-07
sudo /etc/init.d/gdm stop

ctrl + alt + backspace


and your logs are stored in /var/log, xorg is the one you want.

---

