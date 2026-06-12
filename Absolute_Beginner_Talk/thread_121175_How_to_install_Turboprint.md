---
title: "How to install Turboprint?"
date: 2006-01-24
forum: Absolute Beginner Talk
---

### Post by johnkennethhughes on 2006-01-24
Having tried free drivers from Canon with no success, I have resorted to Turboprint to set my Canon i250 up on my Ubuntu computer. However, when I follow the instructions on the Turboprint website ([http://www.turboprint.de/english.html)](http://www.turboprint.de/english.html)), it won't let me run as root to install anything. As such, nothing happens.

I know there must be a simple solution, but I just can't quite see it! Thanks.

---

### Post by MartinG on 2006-01-24
I think you've fallen foul of the fact that there is no separate root user in Ubuntu.  Try replacing the sequence on the website```
xhost +
su root
export DISPLAY=:0
``` with the following:```
xhost +localhost
sudo -s
```This should add the root user to those allowed to run graphical programs, and then give you a "sticky" root prompt.

---

### Post by johnkennethhughes on 2006-01-27
Thank you very much! The printer is finally working perfectly. If I can just kick my MS Excel habit now, I'll be a complete Linux convert.

Thanks again!

---

