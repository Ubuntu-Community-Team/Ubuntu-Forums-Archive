---
title: "Another Zsnes sound issue, please help"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by zazen666 on 2007-08-05
I was having a Zsnes sound issues, crackling and such that most people have. (I am using xubuntu by the way) I tried downloading:

libsdl1.2debian-oss

No I get NO sound at all. I have gone into configuration=>sound, and tried different samples rates.

I get this output with the terminal:

Starting Mouse detection.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event8. Make sure you have read permissions to it.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.


Anyone have any suggestions?

---

### Post by zazen666 on 2007-08-05
I use :

AlsaMixer v1.0.13 

perhapse I downloaded the wrong thing?

---

### Post by zazen666 on 2007-08-05
I treid this:

and I got the sound back, with crackel

sudo apt-get install libsdl1.2debian-alsa

still would like to elimante the crackel

---

