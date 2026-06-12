---
title: "GNU Screen question"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by djhworld on 2007-07-07
I've just discovered the wonders of screen and was wondering if there was some option or command that lets you 

1. Open a screen session
2. Run a command
3. Detach it. 

Now, obviously, this is pretty simple by pressing Ctrl-a and d, but I was wondering if you could automate this process entirely? 

The reason why I'm asking is I want to create a bash alias that opens "rtorrent" and leaves it running in a screen session which I can reattach to whenever I want to.

Any ideas? Or is it keyboard commands only?

---

### Post by djhworld on 2007-07-07
Never mind, I found out how to do it

```
alias torrents="screen -dmS torrentit rtorrent"
```

Cheers!

---

