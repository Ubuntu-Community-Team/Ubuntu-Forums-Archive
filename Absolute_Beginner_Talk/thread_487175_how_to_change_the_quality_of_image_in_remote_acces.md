---
title: "how to change the quality of image in remote access?"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by Mazen on 2007-06-28
i'm connected to my ubuntu from work right now but it's slow cuz i think the quality of the image being sent is high and the connection isn't fast enough, so :
1- the colors are not good for some reason!
2- it's SLOW!
i changed it once but forgot how to!!
thanks

---

### Post by Rocket2DMn on 2007-06-28
Are you using vnc?
If so you can decrease the resolution on the vncserver by using the parameter "-geometry widthxheight" when you boot the server.  "-depth 8" [or 16 or 24] may also be relevant.
Here is the man page:
[http://www.realvnc.com/products/free/4.1/man/vncserver.html](http://www.realvnc.com/products/free/4.1/man/vncserver.html)

---

### Post by Mazen on 2007-06-28
I'm sure there was a graphical way to do it, liek precising is the quality, (HIGH, VERY HIGH , or LOW) something like that.
Thanks anyways:)

---

