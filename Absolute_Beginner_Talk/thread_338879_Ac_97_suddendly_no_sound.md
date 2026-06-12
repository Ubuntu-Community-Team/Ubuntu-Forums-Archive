---
title: "Ac 97 suddendly no sound"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by RamZie on 2007-01-15
I own a HP nx6125 laptop and everything was working normaly... But two days ago i suddendly lost sound. Didn't change any sistem sound preferences or anything... It just died, but it is working in XP.. Sound card is integrated Ac97..
P.S. I always do the automatic updates... Could be some conflict with new packages?
thx

---

### Post by jordanmthomas on 2007-01-15
gotta check the dumb stuff first:
run
```
alsamixer
```
in a terminal and make sure everything is unmuted (mainly PCM and master)
You can toggle them with the 'M' key

If everything is unmuted (and turned up, too) we can look further into the issue

*we being somebody else because I wouldn't know where to begin   ;)

---

### Post by RamZie on 2007-01-15
Found it, thx. :-D  But I still don't understand how it got muted.. :-k

---

