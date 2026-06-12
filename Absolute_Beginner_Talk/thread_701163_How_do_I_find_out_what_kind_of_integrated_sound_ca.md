---
title: "How do I find out what kind of integrated sound card I have and how to use it?"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by psam3 on 2008-02-19
I have the speaker connection connected to the integrated sound card but their is no sound at all. Do I need to install a driver?

---

### Post by jan quark on 2008-02-19
run this in terminal to detect your sound card
```

sudo lshw -C multimedia
```

---

### Post by kpkeerthi on 2008-02-19
Ubuntu should have already installed drivers for your on-board card. Type **alsamixer** in a terminal and make sure the channels (esp. master & pcm) are not muted and sliders raised enough.

If it is marked as MM, it means Muted. Press 'm' key to unmute. Use arrow keys to navigate and 'Esc' to quit.

---

### Post by psam3 on 2008-02-19
Thanks guys. I did a search and I just needed to make it the default card.

---

