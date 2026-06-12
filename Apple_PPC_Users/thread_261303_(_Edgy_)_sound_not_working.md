---
title: "( Edgy ) sound not working"
date: 2006-09-20
forum: Apple PPC Users
---

### Post by Peter76 on 2006-09-20
Hi, I've just installed Edgy Knot3 on my iBook g3 900, but the sound is not working. If I run alsamixer from thecommand line, I get something like: device not found.
I haven't got a clue  where to start looking.... anybody has thye same problem or knows where I have to look to solve this?

Thanks,

Peter

---

### Post by frigaut on 2006-09-20
yeah. same for me under 6.06, after the last 47 kernel-image update (686). I have a macbook pro. Don't know where to start either. I have re-installed alsa (1.0.12), but to no avail: I get the "device not found" error too. I was hoping that edgy would solve this, but apparently not :-(

---

### Post by brenx on 2006-10-27
try typing ```
sudo modprobe snd-powermac
```

if it works, then put 
**snd-powermac** 
in /etc/modules

---

### Post by Peter76 on 2006-10-27
Yes, found that out, but never posted the solution:-( But don't know if that's the same for a macbook ( pro )

---

### Post by brenx on 2006-10-28
I don't know about the macbook ( pro ), I own the Ibook G3 900.

---

