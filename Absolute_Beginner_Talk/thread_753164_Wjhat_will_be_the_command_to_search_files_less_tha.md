---
title: "Wjhat will be the command to search files less than 500 kb?"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by Linux Lover on 2008-04-12
I have downloaded a lot of mp3 songs but unfortunately some of the songs did not download properly and all such songs contain only 316 kb space. I want to find those files which are less than 500 kb. What command should I use?

---

### Post by Inxsible on 2008-04-12
you need to use the find command. Something like```
 find <*path to look in>* -size -500k
```The -ve 500 indicates less than 500k. if you want greater than 500 you need to use  +500. See the man pages for find, for additional info```
man find
```

---

### Post by Linux Lover on 2008-04-12
Thank you. It worked perfectly. My best regards to you.

---

