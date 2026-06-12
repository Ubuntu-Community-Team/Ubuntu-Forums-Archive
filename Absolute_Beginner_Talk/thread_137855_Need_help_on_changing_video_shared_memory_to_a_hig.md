---
title: "Need help on changing video shared memory to a higher value"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by kenweill on 2006-02-28
I was once using Windows XP before, then migrate to Ubuntu completely.

Now heres what I've found out.

Under Windows XP, it detected that I have 96MB of Video Memory(built-in).
But under Ubuntu, its default is set to 8MB(detected under Cedega).

Is there a way to adjust the shared Video Memory in Ubuntu?
I have experience the same problem before in Red Hat 9. Under RH9, I can adjust the shared video memory, and I change it to 64mb. But here in Ubuntu, don't know where to find the utility to adjust the shared Video Memory.

My Windows games(psychic-doom) runs very slow on Ubuntu. I guess this is due to the video ram installed by Ubuntu which is only 8MB.

Need help about this problem. Changing the 8mb video shared to a greater value.

---

### Post by bluevoodoo1 on 2006-02-28
I think you can do it with 
```
sudo dpkg-reconfigure xserver-xorg
```

There's a screen that asks if you'd like to add memory to your video card. Then add it in in kb.

---

### Post by kenweill on 2006-03-01
[QUOTE=bluevoodoo1]I think you can do it with 
```
sudo dpkg-reconfigure xserver-xorg
```

There's a screen that asks if you'd like to add memory to your video card. Then add it in in kb.[/QUOTE]

Thanks alot.
I tried it. Changed the value of the memory of my video card to 96000(kb)

But Cedega still detects 8MB.
I'm not sure if its just on Cedega.
Is there a way to display my Video Card Specs on Ubuntu?
A command, or something to display how much memory(video) i have.

---

