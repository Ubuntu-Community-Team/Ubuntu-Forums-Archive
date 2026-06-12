---
title: "Just trying to set my rez to 1680x1050"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by osc1882 on 2007-10-06
Ok so I installed nvidia drivers thru envy.
I went into the vnivia control box and told it to set the rez to 1680x1050 and I had to use a sudo in order just to get it to save to keep it that way next time I boot.  And so I rebooted and look at the top right hand side. 
[IMG]http://img407.imageshack.us/img407/6308/screenshotnl0.png[/IMG]
..... I just need to set the screen to 1680x1050.... can anyone help?

---

### Post by Pumalite on 2007-10-06
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by osc1882 on 2007-10-07
Still no luck... grrr...
The only way I have been able to get it to go that rez is to use sudo for the nvidia control pannel and then it looks like the screen shot I Posted above. Someone help me, pretty pretty please.

---

### Post by osc1882 on 2007-10-07
Please help me... I'm losing my mind over here.

---

### Post by st33med on 2007-10-07
Hrm... you might want to modify the xorg.conf

Could you do:
```
cat /etc/X11/xorg.conf | grep Modes
```

And post it here?

---

### Post by alienexplorers on 2007-10-07
What is wrong with the right hand side other than your panel buttons moved.   Left click on the out of place icons and select to unlock from panel.  Select move and move them back to where they should be.  Relock the icon.

---

### Post by osc1882 on 2007-10-08
alienexplorers, you called it. I'm still a newbie.. I'm sorry. I didn't know you had to right click and tell them to unlock so I over reacted.
Thank you.

---

