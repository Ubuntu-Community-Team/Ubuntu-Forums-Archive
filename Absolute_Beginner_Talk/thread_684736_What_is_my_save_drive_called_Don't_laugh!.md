---
title: "What is my save drive called? Don't laugh!"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Terminal Sobriety on 2008-02-01
I cannot find out what my slave drive is named for the life of me. I need to get to a 500gb Seagate that has all my movies and music on it for Myth, but i cannot find what the path would be called. Today is my second day with Linux so don't hate on the n00b.

---

### Post by emarkd on 2008-02-01
No hate.  We're all noobs at one time or another.  You can run

```
mount
```

to see where everything is mounted.

PS.  Try not to think "drives" like in Windows.  Linux doesn't really have the concept of drives. Everything is just one big file system where EVERYTHING is a file (even that keyboard you're typing on).

---

### Post by iansane on 2008-02-01
LOL nah just playin. I'm noob too. You can list your available drives in terminal.

```
 sudo fdisk -l 
```

That will tell you if it's hdd, hda, hda1, or whatever it is if you can recognise it by the size and file type.

---

### Post by Terminal Sobriety on 2008-02-01
Oh man you guys rule face! Thanks so much. I love this place.

---

### Post by emarkd on 2008-02-01
You're welcome.  And welcome to the community.

---

### Post by Terminal Sobriety on 2008-02-01
Oh man you guys rule face! Thanks so much. I love this place.

---

### Post by Terminal Sobriety on 2008-02-01
Sorry aboot the double (triple) post.

---

