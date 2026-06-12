---
title: "No fullsreen Mplayer"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by rado2402 on 2006-12-02
I have a problem with my MPlayer I cant get a fullscreen I select a fullscreen and the video stays at normal size and around it creates a black screen Whats the problem? :-k

---

### Post by Bachstelze on 2006-12-02
Change your video output driver :)

---

### Post by rado2402 on 2006-12-02
Only x11 driver works fine... gl is very slow and -zoom doesnt work either...dont know what to do

---

### Post by taurus on 2006-12-02
In ~/.mplayer/config, add this line in there...

```
zoom=yes
```

---

### Post by MGStreak on 2007-04-29
> **HymnToLife said:**
> Change your video output driver :)
> **rado2402 said:**
> Only x11 driver works fine... gl is very slow and -zoom doesnt work either...dont know what to do
> **taurus said:**
> In ~/.mplayer/config, add this line in there...
```
zoom=yes
```

Just to bump what I consider to be a useful post... the discussion above replicated the problem I was having exactly (couldn't change from x11...) and the solution ALSO worked.  Hooray!

---

