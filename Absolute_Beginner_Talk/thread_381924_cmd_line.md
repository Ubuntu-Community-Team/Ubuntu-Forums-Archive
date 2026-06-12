---
title: "cmd line"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by rtpca65 on 2007-03-11
question, is there a cmd line to see if my graphics card 3d accelorated capable? i am using ubuntu btw, because i want to install beryl

---

### Post by wpshooter on 2007-03-11
Try "**glxgears**"

There is another command which gives a text readout but the command escapes me at the moment.

---

### Post by rtpca65 on 2007-03-11
thanks, is a dualboot best with two hard drives? only reason i am asking is because the cable i need for my new drive won't arrive til tommorow

---

### Post by sad_iq on 2007-03-11
**fglrxinfo** should print the name of the video card and other stuff and **glxinfo |grep direct** should say **direct rendering: Yes**
 if fglrxinfo says **Mesa** blah...blah.. then it's a no go:( 
 It works for Ati cards...don't know about other

---

### Post by anaconda on 2007-03-11
glxgears -printfps
and 
glxinfo

---

