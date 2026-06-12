---
title: "Screen Res probs on Dell Inspiron 630m"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by Riggers on 2007-03-12
Hello people.

Noob tearing my hair out. I have done a million things to fix the screen resolution. I get it happening but as soon as I reboot it's all disappeared despite commands to save it in start up. Anyone got any ideas!

---

### Post by freebird54 on 2007-03-12
I am not sure I have an answer - but you are more likely to get a good one with a bit more information if you can find it!  

What  kind of video card does it have?  
What is the resolution you are looking for?  
Is Ubuntu installed, or are you running from the live CD?  
How familiar are you with finding hardware things on computers?

With that information, I am sure someone will dive in to get you going in the manner you wish -- and with the clarity and detail you need.

---

### Post by kolinab on 2007-03-12
I have a Dell 630m. In order to enable the 1280 X 800 resolution, all I had to do was:

```

sudo aptitude install 915resolution

```

That worked for me, I think a reboot was required. There are all kinds of explanations and pages and howtos around showing many variations of complicated processes. They weren't necessary for me! Try typing the above command into a terminal window and let us know how it goes.

[edited a few minutes later]
I have installed Ubuntu twice on this machine and this resolution tweak is the first thing I have done both times. SO, if you've diddled with other video settings I guess it's possible that things could be a little messy. But it ought to work. In any case, post back with your results!

---

