---
title: "HELP! I've gotten up and can't fall down!"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by Flatwinder on 2007-01-28
Hello to all.

I guess I'm just a "nosey" newbie for opening the program . . . just wanted to see what it was and what it looked like.

Anyway, I have opened a program called KSysV and I can't close the window, the "Quit" button does nothing, and I can't even restart the computer. When I try to do a restart I get a popup telling me my settings have been saved. I even went through removing the program in Synaptic and still can't close the KSysV program or do a restart. I'm afraid to power down manually for fear of "breaking something. I'm running Ubuntu 6.06LTS.

Can anyone tell me how to escape this program without breaking something?

Your help will be greatly appreciated.

Thanks,
Jim

---

### Post by bward1 on 2007-01-28
You could try a few different things.  First I would try and just kill the process by going to System->Administration->System Monitor and finding and ending the process.  You could also try running from a terminal```
killall KSysV
``` but I would suspect that would have the same effect.  If that doesn't work than you could kill all the processes of the user who ran it manually ```
pkill -u username
``` but you wouldn't want to do that if you ran the program as root (you ran it through sudo or you had to enter an administrative password).  If all else fails you should just be able to do a clean reboot by typing ```
sudo reboot
``` and that should kill all of the processes, including the one you want to kill, and restart your system.

---

### Post by Flatwinder on 2007-01-28
I really appreciate the super fast help.

The "pkill -u username" command did the trick . . . successful reboot and all is well again. That'll teach me not to be so curious, huh?

At any rate, I'm COMPLETELY Ubuntu now and loving it. NO MORE WINDOWS! And Ubuntu blows Windows away for speed. NEVER going back . . . I'm hooked!

Thanks again for the super-fast rescue. I appreciate it more than I can express.

Thanks a million,
Jim

---

