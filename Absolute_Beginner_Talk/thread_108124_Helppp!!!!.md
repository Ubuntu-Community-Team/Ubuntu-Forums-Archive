---
title: "Helppp!!!!"
date: 2005-12-25
forum: Absolute Beginner Talk
---

### Post by tane_stelzer on 2005-12-25
Okay since no one has really answered my other threads, I have sat down and tried to figure out what Xmacro is all about, now i know what this -s option is and how to use it. Just one last question. at the end of the command in my case xmacro -d 3000 -s 1.0 -k 54 remote_display. Well i know remote_display is not right and i know i have to substitute it for sth like bar:0.0 where bar is the computer name or? in my case ubuntu. Well now the only thing i dont understand is the 0.0 what no is that supposed to be, it is not my ip adderess cos i tried it and got error. am i right up until now? Please someone reply me this time, i am sure someones know sth in this forum, i am already frustrated enough with this!!!!
Tane

---

### Post by gruepig on 2005-12-25
I'm not sure what you're trying to do or what errors you are getting, but 0.0 is probably correct (default display) and shoudn't be substituted.  If 'ubuntu:0.0' doesn't work for your display, maybe try 'localhost:0.0'.  Good luck.

---

### Post by steve.horsley on 2005-12-26
Or try **:0.0** or just leave a blank string.

---

