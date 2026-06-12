---
title: "Running a shellscript?"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by Bagboy23 on 2007-07-26
Can someone tell me how to run a shellscript based on key combinations pressed. For instance pressing CTRL + ALT + W combination THREE TIMES will run my shellscript called "School Timetable.sh".

P.s. I have Compiz installed so the keys CTRL + ALT + W dims my background. (Just makes my time-table script easier to read).

Many thanks. 

The Bag. :guitar:

---

### Post by aysiu on 2007-07-26
I don't know about pressing it three times, but you can make your shell script part of the executable path. Let's say it's currently on your desktop: ```
cd ~/Desktop
sudo mv School\ Timetable.sh /usr/local/bin/SchoolTimetable
sudo chmod +x /usr/local/bin/SchoolTimetable
``` Then, create a keyboard shortcut for the command ```
SchoolTimetable
```

---

### Post by Bagboy23 on 2007-07-26
Thanks for the help, but can I record the keystrokes using that shellscript to detect the presses three times, then have an output response to this?

---

### Post by indytim on 2007-07-26
Aysiu,

Additional follow on question to your thread,  does the .sh have to be located in /usr/local/bin, or can it be located in a /bin created somewhere else?

Thanks,

IndyTim

---

### Post by Nekiruhs on 2007-07-26
> **indytim said:**
> Aysiu,

Additional follow on question to your thread,  does the .sh have to be located in /usr/local/bin, or can it be located in a /bin created somewhere else?

Thanks,

IndyTim
If you put a /bin folder in your home folder, log out and log in it will look there too.

---

