---
title: "Video Card/Xserver(?) Help"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by b33rnutz on 2006-07-15
I installed Ubuntu (6.06) for the first time today. The install went fine and the boot manager works great (I'm currently posting this from Windows XP on the same partition.)

Now my problem: Whenever I try to start Ubuntu, it tells me that Xserver (or something, I don't remember exactly) has failed. I have no idea what to do with this. If it matters, I have an nVidia 6600, no onboard video to use instead :-| I'm a complete noobie here. Any help would be greatly appreciated.

Dustin

---

### Post by fluffington on 2006-07-15
Assuming that the only problem is that it didn't like your video driver, get to the terminal (Ctrl+Alt+F1 should do it if you're not already there), log in, and do the following:

```

sudo apt-get install nvidia-glx
sudo dpkg-reconfigure xserver-xorg

```

The second command will run through the X.Org setup. When asked, your video driver is "nvidia", and when you get to the part about modules, make sure "dri" is unchecked and "glx" is checked.

When you're done, reboot (*sudo reboot* in the terminal) and see what happens.

---

### Post by b33rnutz on 2006-07-16
Thanks a ton. I'll go try that.

---

### Post by b33rnutz on 2006-07-16
It worked! Thanks a ton.

---

### Post by fluffington on 2006-07-16
> **b33rnutz said:**
> It worked! Thanks a ton.

Cool. It's been long enough since I did that, I wasn't sure if I was missing anything or not.

---

