---
title: "Some of my screen is missing?"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by blasteryui on 2008-03-21
[http://img187.imageshack.us/my.php?image=screenshotjx3.png](http://img187.imageshack.us/my.php?image=screenshotjx3.png)
I must of done something wrong with the resolution and stuff but where the white is, is where the dock use to be and the rest of my background, and also now every thing I have opened so lets say Firefox, there is no minimize expand or close button I have to right click the window and click close.
What do I do to fix this?

PS: 
Okay so I went to my desktop effects and chose none and the white goes away and I have in the right corner of my windows the close, maximize, and minimize signs. But when I click normal, extra or custom the white space comes back and the same problem is there? Where the white space is, also where the dock would be and ugh what do I do to fix this? IT DIDN'T start doing this tell I went to.
system>administration>screen and graphics> and enabled screen two, so I disabled it but what should I do?

---

### Post by bumanie on 2008-03-21
I'm at work and am blocked from seeing your screenshot. Are you using an nvidia graphics card?

---

### Post by blasteryui on 2008-03-21
> **bumanie said:**
> I'm at work and am blocked from seeing your screenshot. Are you using an nvidia graphics card?

Yeah I tried to do some second screen thing then it made like some white space rise from the buttom up a bit, and my dock is completely gone, and it's just a white line going across my screen thats about 2-3 inches from bottom up. So I put the second screen to disabled, now what do I do?

---

### Post by bumanie on 2008-03-21
If you are using an nvidia card ctrl-alt-F1, log in and give password
then type this > sudo nvidia-xconfig --add-argb-glx-visuals -d 24  crtl-alt-F7
If it doesn't work log out and back in.

---

### Post by blasteryui on 2008-03-21
> **bumanie said:**
> If you are using an nvidia card ctrl-alt-F1, log in and give password
then type this  crtl-alt-F7
If it doesn't work log out and back in.

It didn't work it said command line not found or something.

---

### Post by bumanie on 2008-03-21
It worked on my nvidia card when I had similar trouble. Sorry, I don't have any other suggestions.

---

### Post by bumanie on 2008-03-21
Another thought, are you using desktop effects? If so may be you should try disabling them and see if everything comes back to normal. If so, re-enable one by one t see which one is interfering and don't use that. What is your system configuration?

---

### Post by blasteryui on 2008-03-21
Okay so I went to my desktop effects and chose none and the white goes away and I have in the right corner of my windows the close, maximize, and minimize signs. But when I click normal, extra or custom the white space comes back and the same problem is there? Where the white space is, also where the dock would be and ugh what do I do to fix this? IT DIDN'T start doing this tell I went to.
system>administration>screen and graphics> and enabled screen two, so I disabled it but what should I do?

---

