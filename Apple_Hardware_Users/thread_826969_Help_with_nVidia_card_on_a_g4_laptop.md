---
title: "Help with nVidia card on a g4 laptop"
date: 2008-06-12
forum: Apple Hardware Users
---

### Post by ruialexbarbosa on 2008-06-12
Hi, how can I adjust brightness with my nVidia Corporation NV34M (GeForce FX Go5200) (rev a1) card?

Thanks for any help.

I'm on 8.04 ubuntu

---

### Post by stream303 on 2008-06-13
I'm not sure nvidia-driven G4 ibooks have the capability of brightness controls - although I could be wrong.  Stay on the lookout for a new module, "nvbacklight" or some such that I saw being mentioned in the Debian lists.

In the meantime, you can fake it if your problem isn't *too* bad, and if you don't do any photo-editing with this funky workaround:

```
xgamma -gamma 0.8
```

Where the default value is 1, and typically you can run somewhere from 0.5 to 1.5 before it becomes unusable.  You can put this line into your xorg.conf to make it permanent, but don't forget about it when the real fix comes out.

I noticed that Xubuntu has a similar gui tool which may be more convenient for this fake brightness alternative, but keep your eyes out for a real solution.

---

