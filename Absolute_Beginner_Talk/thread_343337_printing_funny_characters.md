---
title: "printing funny characters"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2007-01-21
Hi, when printing from open office writer, Sometimes I get letters printed over each other making the document unreadable. This seems to only happen with this application. Why do you think this is and how can it be solved? 

My current/non-permanent solution is converting all documents to PDF's and then printing and it works fine.

---

### Post by mikewhatever on 2007-01-22
I had a similar problem before installing GLX support. Lets see what this gives ```
glxinfo | grep rendering
``` if this is the outcome ```
 $ glxinfo | grep rendering
direct rendering: Yes

```
then you have GLX installed, otherwise, try searching for GLX support for your video card.

---

