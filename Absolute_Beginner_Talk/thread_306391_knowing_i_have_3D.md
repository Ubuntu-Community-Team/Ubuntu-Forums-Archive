---
title: "knowing i have 3D"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by Mazen on 2006-11-24
How can i know that i have 3D support, i have a ATI radeon X700
and i installed Beryl, which i still don't know the real concept behind it, i can pick it when i logon as a session and i still have gnome, anyway it looks awful, i looked at some ATI solutions posted but they meant nothin, can anyone re-explain to me the concept behind Beryl and what it really is? and how can i know that my card is in 3D mode or something?
thanks

---

### Post by SZorg on 2006-11-24
Open a Terminal/Konsole (Ubuntu and Kubuntu, respectively)

Copy and paste this command into the console:

```
"fglrxinfo"
```
(I'm nto sure if it's with or without the quotation marks, and I'm on nVidia so I can't check). The response should tell you.

Something like "Direct Rendering: Yes/No".



Also, did you install drivers and enable them using ATI's tool or yourself in xorg.conf?

---

### Post by rlozano on 2006-11-24
run interminal fgl_glxgears, to see if you have 3D working...

---

### Post by junglepeanut on 2006-11-24
If you have set it up, try fglrxinfo and glxinfo. The first should say all ATI info, the seconds most important bit is at the top where it should say off the top of my head "direct rendering: yes" if either of those is wrong you probably messed up the install. Note the X700 occasionally has lock up issues with beryl, but I haven't experienced it in a long time.

To find out more about compiz and beryl just google them there is more than you could ever want to know out there. I prefer beryl, here is a link to the forum.

[http://forum.beryl-project.org/](http://forum.beryl-project.org/)

---

