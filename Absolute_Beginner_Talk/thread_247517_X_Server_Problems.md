---
title: "X Server Problems"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by moricgaut on 2006-08-30
I just took out my Nvidea card out of my computer to send it for repairs. So for right now all i have is my onboard card which is an Nvidea. Now when i turn on my computer it loads and the gives me a x server problem with this jiberish and then it goes to like a black screen which i guess a command promt. ](*,)  It then says login so i login and then gave my password. But now i not sure what to do. I guess i need a command so that i can reconfigure the x windows system. So any ideas. :confused:  Thanks

---

### Post by Omnios on 2006-08-30
from command line
```

sudo dpkg-reconfigure xserver-xorg

```

 Counting on what kind of onboard vid you have you might want to try the nv driver or even versa

---

### Post by Toxicity999 on 2006-08-30
Correction, they mean vesa. As just a temporary solution first test nv, if the problem persists. Try vesa as instructed. What's happening is simply the proprietary nVidia drivers don't support your onboard setup. to put it simply. Just have to tough it out with nv or vesa till you get a new card I suppose.

---

