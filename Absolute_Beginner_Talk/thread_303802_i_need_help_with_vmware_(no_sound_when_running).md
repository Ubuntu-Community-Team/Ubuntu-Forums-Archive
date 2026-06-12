---
title: "i need help with vmware (no sound when running)"
date: 2006-11-20
forum: Absolute Beginner Talk
---

### Post by jmanaz84 on 2006-11-20
i just installed windows xp proffesional, and everytime i start it up i get this....

Failed to open sound device /dev/dsp: Device or resource busy
Virtual device sound will start disconnected.

if someone could give me a step by step solution that would be great, im new to linux so i really need in depth steps, im not good with terminals and what not.

---

### Post by Bretls on 2006-11-20
I can't really give you a step by step. VMware will not be able to connect to your sound device if any other program it using it when you start it up. So if you playing music in the background or listening to a broadcast you should stop them first.

---

### Post by Atomic Dog on 2006-11-21
I posted a solution yesterday on another thread.  Search for it or click on my name and view my posts.  It'll be there.

---

### Post by davea402 on 2007-02-01
it worked for me through this site as atomic dog said soo...

[http://www.vmware.com/community/thread.jspa?threadID=47101&tstart=60](http://www.vmware.com/community/thread.jspa?threadID=47101&tstart=60)

after running the scrip i just chose vmwareesd to run vmware...sweet huh..

---

