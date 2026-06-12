---
title: "problems with mpd"
date: 2008-11-13
forum: Arch and derivatives
---

### Post by zephyrus17 on 2008-11-13
Well, I've followed arch's wiki entry on mpd, and here's the problems I have:

1) The last state won't save. If it does save, it saves a particular song and ALWAYS loads off with that one song.

2) Some songs don't play. They, uh.. just stay there.

3) Running mpd just from the daemon doesn't get it to load. I have to add it to gnome-sessions as well. Is that correct procedure or merely a workaround to a bigger problem?

4)mpd --create-db outputs this: ```
cannot init supplementary groups of user "gary" at line 8: Operation not permitted
```

5) mpd --create-db will ALWAYS hang at a particular song (not the song that is loaded from the state file). Even trying sudo mpd --create-db, which I know is a bad idea, still hangs at that song.

Uh, help? :(

---

