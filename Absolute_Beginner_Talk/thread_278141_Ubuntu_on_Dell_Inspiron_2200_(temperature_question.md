---
title: "Ubuntu on Dell Inspiron 2200 (temperature question)"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2006-10-15
I have read that a Dell Inspiron running Ubuntu will get hot and could damage hardware (due to Ubuntu not being able to controll the fan right or something)
[http://ubuntuforums.org/showthread.php?t=257684](http://ubuntuforums.org/showthread.php?t=257684)
> IMPORTANT: FAN CONTROL (do this to avoid overheating!)
1. sudo apt-get install i8kutils gkrellm gkrellm-i8k
2. sudo modprobe i8k force=1
3. sudo gedit /etc/modules
4. add the following line to the end of the file: i8k force=1
5. go to System > Preferences > Sessions > Startup Programs
6. Click ADD and put the command: gkrellm
Now you will see the GKrellm utility load at startup and you can then configure your fan thresholds, etc.
 Is it safe to run an Inspiron with Ubuntu or will I need to run that program all the time? When I used Ubuntu, I never experienced overheating, but as soon as I ran GKrellm it cranked my fan up. So is it needed or not?

---

### Post by John.Michael.Kane on 2006-10-15
I would say that if your fans are turning on as they are supposed to. As in the case of running cpu intenceive programs you should be fine. 

Does your machine seem abnormally hot when doing only minor work ie: email web ?

How does the machine act on a day to day use?

Have you had any random shut downs corrupt data?


Also looking at that howto you linked to. it's writen for a completely diffrent machine then you own.

---

### Post by tdrusk on 2006-10-15
I started running XP again, just so I could protect my hardware. I remember the fan blowing lightly when I wasn't using Gkrellm, so I suppose it was working properly. That tutorial just scared me a bit. I just didn't want my computer to burst into flames or anything. Nothing went wrong with it while it was running Ubuntu, so I guess it was fine. I would just rather learn from others mistakes than my own. 


Thanks for your help. I am considering switching back to Ubuntu now.

---

### Post by psycosmyth on 2006-10-15
I have the 1200, one below yours and my fan works fine, just not as much as it did with xp, less load, less heat I suppose.

---

