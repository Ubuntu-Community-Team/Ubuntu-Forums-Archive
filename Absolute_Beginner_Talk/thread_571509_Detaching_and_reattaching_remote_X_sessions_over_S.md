---
title: "Detaching and reattaching remote X sessions over SSH"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by stimpack on 2007-10-09
I have been happily running KTorrent on my linux server from my Macbook using ssh with X tunneling. I was wondering if it was possible to detach and reatttach to the process when required. (like screen but for X apps). ?

---

### Post by jfinkels on 2007-10-09
> **stimpack said:**
> I have been happily running KTorrent on my linux server from my Macbook using ssh with X tunneling. I was wondering if it was possible to detach and reatttach to the process when required. (like screen but for X apps). ?

If I understand correctly, you want access to the command prompt while a process is running. One way to do this is to specify that a process run in the background, by appending an ampersand ('&') to the command, like so:```
firefox &
```This allows you to continue to issue commands at the prompt while still having firefox run in the background. If you start a process, and then want to 'stop' it (i.e. send it to the background) simply start the process and then press <Ctrl>+<Z>. You can view stopped processes (they are actually 'jobs' in this case) by typing in the terminal:```
jobs
``` or by using```
bg
```To bring a job back to the foreground, type either:```
jobs %1
```to bring the job numbered '1' back to the foreground, or using the shorthand:```
%1
```

I also would suggest using rtorrent, see here for more info on rtorrent: [http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

---

### Post by stimpack on 2007-10-10
Thanks for the reply mate, but that's not what I'm after, I realise i'm not explaining very well :).

The reason I am doing this is so I can stop using rTorrent hehe. I basically pipe X through SSH so that while KTorrent is running on my server, the GUI appears on my Macbook. However I don't like the GUI onscreen except for when starting/stopping torrents, so would like to detach the GUI from the macbook, whilst still leaving KTorrent running on the server. Later I want to reattach to the process so the GUI again appears on my laptop, so I can close the torrent.

This is the X equivalent of using 'screen', for terminal applications. And just to make it harder, it may not even be possible. :).

---

### Post by jfinkels on 2007-10-10
> **stimpack said:**
> [I] would like to detach the GUI from the macbook, whilst still leaving KTorrent running on the server. Later I want to reattach to the process so the GUI again appears on my laptop, so I can close the torrent.

This is the X equivalent of using 'screen', for terminal applications. And just to make it harder, it may not even be possible. :).

Hmm, that's tricky, I'm not really sure how that would be done.

---

### Post by nocturn on 2007-10-10
I guess you want something like FreeNX or VNC over SSH.

---

