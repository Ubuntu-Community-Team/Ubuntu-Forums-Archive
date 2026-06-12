---
title: "XGL/Compiz disappearing windows"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by DSn0wMan on 2006-08-13
My application windows seem to fly away somewhere on specific types of mouse movements. I can sometimes get them to come back by wiggleing the mouse up and down.

There must be a parameter somewhere to off this behavior. I just cant find it.

Any ideas?

---

### Post by c_x on 2006-08-13
In terminal enter:
```
gconf-editor
```
And in it navigate to apps>compiz>plugins>showdesktop>allscreens>options.
Empty out initiate_edge, Done!
If you want to remove the other "mouse to corner effects" (which i think is really annoying) check apps>compiz>plugins>scale>allscreens>options and empty out the effects that you don't want

---

### Post by DSn0wMan on 2006-08-13
Thanks for the tip. This works perfectly. One last annoyance. My gdesklets come up at weird places after system startup. Any idea what causes this?

---

