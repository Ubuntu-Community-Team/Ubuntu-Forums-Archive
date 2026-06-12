---
title: "Microphone troubles"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by benclinch on 2006-07-20
Hello,

I have got a mic connected to my computer running Ubuntu 6.06. But when I go into Audacity or Sound Recorder it does not work, I have tryed cycling through all the input devices, but none work. I know that my microphone works in Windows. It is a standard 3.5mm jack in the back of my pc. Could anybody please tell me what I am doing wrong/Not doing/what I need to do?

Thanks
Ben

---

### Post by Klemik on 2006-07-20
Run alsamixer (from terminal) and make sure that microphone is enabled and not muted.

---

### Post by benclinch on 2006-07-20
I have fiddled with everything there and it made no difference. Any other ideas?

---

### Post by benclinch on 2006-07-20
Right ok,
When i go into alsamixer and then into capture I get:
3D control centre - full volume
same with 3D control depth
capture is also on 100
every thing else including mic has 6 dashes where the volume control should be, they are locked.

Help?!?

---

### Post by Klemik on 2006-07-20
Maybe this screenshot will help you:

[[IMG]http://img204.imageshack.us/img204/3346/alsamixeryn3.th.jpg[/IMG]](http://img204.imageshack.us/my.php?image=alsamixeryn3.jpg)

Make shure that master mono and mic is **enabled** (M key to enable/disable device as shown on ss).

---

