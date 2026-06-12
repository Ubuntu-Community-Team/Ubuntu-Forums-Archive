---
title: "Opera font troubles..."
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by mahy on 2007-05-15
Hi y'all,

no matter what i do, i can't get Opera to display the fonts i want it to display. I encoutered no probs while setting it's interface fonts to match my Xfce font (DeJaVu Sans 9). But the webpage font is giving me a headache. Opera is set to display pages in Times New Roman, which i neither like nor have. When i set it to ANYTHING else, it begins to display pages in a very small Arial clone and further changes make no effect until i remove the entire profile. My question: WTF?! It used to work great in Edgy! Idead, anyone? Any help will be much appreciated. TIA.

---

### Post by zvacet on 2007-05-15
**tools>preferences>advanced>fonts**

I expirienced same and it is not what I used to but it is better then it was.If you set it as you want it to be feel free to let me know.

---

### Post by mahy on 2007-05-15
I've done it!

I edited the /etc/fonts/fonts.conf to include the fonts directory on my windows partition and also added the same location to my xorg.conf. Now it's all rosy! :guitar:

BTW, the above mentioned solution won't work coz i'm on Xubuntu. Besides, Opera doesn't care about UI fonts.

---

