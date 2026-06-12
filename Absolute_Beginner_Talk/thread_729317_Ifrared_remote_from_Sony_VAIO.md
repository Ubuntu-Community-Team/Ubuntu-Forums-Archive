---
title: "Ifrared remote from Sony VAIO"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by Jeezus on 2008-03-19
I just found an IR remote, and receiver from an old sony vaio, and was wondering if there were a way to set it up on my toshiba Satellite A105.
I'm still pretty new to ubuntu, so I would need some reasonably detailed instructions.
I'm running Gutsy Gibbon

---

### Post by sayakb on 2008-03-19
You might need a package called lirc

```
sudo apt-get install lirc
```

Thats all I know. I installed lirc and my integrated IR Receiver started sensing my laptop's remote.

---

### Post by Jeezus on 2008-03-19
Thanks, I'll give it a shot.

---

### Post by Jeezus on 2008-03-19
I think I need a driver set, or an lirc.conf for the remote.
on the bottom of the remote, it has :
VAIO
PC
RM-MC1

and the receiver is:
PCVA-IR6U

anyone know where I could get drivers, or an lirc.conf for that model remote and receiver?

---

