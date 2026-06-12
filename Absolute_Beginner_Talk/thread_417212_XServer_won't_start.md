---
title: "XServer won't start"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by swey on 2007-04-21
I just ran the updater to 7.04 and followed all the steps but now it won't fully boot up- says XServer is configured wrong and then I get stuck at this DOS prompt like thingy. How can I fix it please?

GeForce 2 ultra graphics card so it was using Legacy NVidia drivers - is this the problem?

---

### Post by overdrank on 2007-04-21
> **swey said:**
> I just ran the updater to 7.04 and followed all the steps but now it won't fully boot up- says XServer is configured wrong and then I get stuck at this DOS prompt like thingy. How can I fix it please?

GeForce 2 ultra graphics card so it was using Legacy NVidia drivers - is this the problem?

Hi if you use the command *sudo dpkg-reconfigure xserver-xorg* then follow the instructions that should get you going. hope this helps good luck!

---

### Post by swey on 2007-04-21
Thanks - good idea but unfortunately when I do this a press enter I just get another command prompt blinking at me - it doesn't even say wrong command

---

### Post by marko_4454 on 2007-04-21
> **swey said:**
> Thanks - good idea but unfortunately when I do this a press enter I just get another command prompt blinking at me - it doesn't even say wrong command

What about doing 
```
sudo startx
```
??
What does that give you?

---

### Post by swey on 2007-04-21
Working now. I had to disable frame buffering to get it to start and then download the legacy drivers using Synaptic - the new restricted driver manager couldn't seem to to this automatically like its supposed to.

Now I have no networking though.

---

