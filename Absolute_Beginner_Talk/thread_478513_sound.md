---
title: "sound"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by dodzi on 2007-06-19
i just started using ubuntu i love it but for some funny reason my sound just doesnt work anymore.anytime i try playing music what ever software i use crashes.can anyone help

---

### Post by p_quarles on 2007-06-19
We're gonna need more details before anyone can help you. Is ALL sound not working (i.e., does it beep at you when you get new e-mail?) or is just the music playing software? Which music player are you using? What kind of sound card do you have?

---

### Post by Alex&amp;Linux on 2007-06-19
Heyo

Same thing happened to me intermittently, usually restarting X fixed it, however, sometimes the problem was that my sound was "muted"

In terminal run:

  alsamixer

This will show different speaker outputs, and weather theyre muted or not!
Theres a good chance that this isnt the problem, but make sure you see green boxes at the bottom of each bar...and that the levels are up a few notches. use the arrow keys to navigate and change.

---

