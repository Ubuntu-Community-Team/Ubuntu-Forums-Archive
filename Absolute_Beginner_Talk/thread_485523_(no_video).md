---
title: "(no video)"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by Roasted on 2007-06-27
What would explain this? On some sites with embedded videos, I get a black box with (no video) in the center. However, sometimes about 5-10 seconds later it'll start anyway.

But I was on apple.com/trailers trying to watch a movie trailer and I was unable to. There's buttons to click the size trailer screen you want, and each one says (no video) which is kind of weird for a button to do that.

Anyway, something's goofed. Everything else works. But what's up with the (no video)? How do I get rid of it?

---

### Post by BHelts on 2007-06-27
```
sudo aptitude install ubuntu-restricted-extras
```

```
sudo aptitude install gstreamer0.10-plugins-bad
```

```
sudo aptitude install gstreamer0.10-ffmpeg
```

on a fresh install this gets me up and running with any multimedia i can imagine!

---

### Post by Roasted on 2007-06-27
Didn't work.

Another thing, at least with apple.com/trailers, firefox just shuts off if I try to do anything else in the page.

---

