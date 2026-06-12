---
title: "Permissions"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by xtang on 2007-09-30
I created a text file in sudo mode, as such I can't make any changes unless I am administrator. I applied chmod +x and chmod 755 and yet I still can't make changes as a normal user, or am I missing something?

---

### Post by bobplano on 2007-09-30
hmm i thought some versions of that chmod command had an 'a' (the first one). you could also chown the file so you own it, but otherwise i'm out of ideas.

---

### Post by HermanAB on 2007-09-30
Chmod is half the story.  The other half is chown.

$ sudo chown username:usergroup filename

Cheers,

H.

---

