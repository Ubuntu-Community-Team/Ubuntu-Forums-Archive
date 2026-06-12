---
title: "how do i find out what sound card i have..."
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by yui chan 18 on 2007-06-27
when i've already fully installed ubuntu an the entire hard drive? quick and simple question, google has offered no answers about sound cards in my kind of laptop. it's a gateway w340ui, if that helps any. thanks in advance for any help.

---

### Post by Anarchy965 on 2007-06-28
You can go into terminal and type ```
alsamixer
```

The alsa mixer will show you what sound card you have or if you have onboard sound it will show you what onboard sound and chipset you have.

---

### Post by yui chan 18 on 2007-06-29
helped...but now i need to figure out how to make it work. any ideas?

---

### Post by kevdog on 2007-06-29
How about just typing at the command line:

lshw -C multimedia

---

### Post by alienexplorers on 2007-06-29
Why not try in terminal :> lspci

---

