---
title: "Problem with playing DVD"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2006-12-09
Hi,

To watch a DVD film I use gxine. It's good if I don't use full screen. But by the using of full screen the picture stops eche 4 a 5 sconds for a short time and then it begins to play.
Could you guide me to solve this problem?

Thanks,

---

### Post by linux-beginner on 2006-12-09
Is there anyone who helps me?

---

### Post by linux-beginner on 2006-12-09
I've just seen that I have that problem with all movies using the full screen:confused: :(

---

### Post by beefcurry on 2006-12-09
Does this problem also happen with VLC/mplayer or some other player?

Also check if you have DMA on

```
sudo hdparm -d1 /dev/hdc 
``` sub what ever your device is to hdc.

Also try ripping your disk to an ISO, then mount the ISO and play that. It should run more smoothly

---

### Post by houstonbofh on 2006-12-09
What video card do you have, and what driver are you using?

---

### Post by linux-beginner on 2006-12-09
To beefcurry: Thanks, it's solved.
Bye

---

### Post by ingo on 2006-12-13
how? it is always nice to spread hacks, solutions, knowledge - let people know :)

---

