---
title: "startup output"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by n3tg33k on 2007-11-26
hello all,

I seem to be having a problem with startup and shutdown issues.  I think that I have the shutdown issues fixed as I think that I had a flaky nic.  After removing the nic shutdown performs correctly. I have usplash disabled so I see the grub/ terminal on boot.  I see some errors but I can't read them as it moves too fast is the anywhere that I can find a log file output of grub?  I belive that this issue is being caused by psmouse cause it seems thats where it halts and then I get a kernel sync error stating fatal exception interrupt.  Any help would be appreciated!!!

n3t

---

### Post by mikewhatever on 2007-11-26
You may need to browse through your logs in System>Admin and get those error messages.

---

### Post by NathanB on 2007-11-26
```

$ dmesg | less

```

...to read, or...

```

$ dmesg > todayatfive.log

```

...to keep track.

---

### Post by n3tg33k on 2007-11-27
Ok guys that has helped now at least I have something to show ppl when asking.  Here it is though as stated I am having starup and shutdown probs and I have searched the forms tried all suggestions to no avail.  here is the output of grub on a failed restart posted as an image.  I need to mention that when I get this problem I have to shut the system down via the power supply switch and let sit for about ten minutes or the problem just keeps happening.  Maybe somebody has a better clue to this than I do.  I am wondering if it has to do with a ram problem based on the fact that I have to power the system down and let it sit for a few mins.  Any advice please!!!

N3t

---

