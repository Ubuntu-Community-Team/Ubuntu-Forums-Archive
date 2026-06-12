---
title: "cpu running slow"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by graha on 2007-02-27
i just installed kubuntu but when i look at the power management thing the cpu running at 800mhz my processor is amd turion 64 x2 1.8ghz. is there anyway i could change to 1.8ghz ? everything seem to run slower than xp.

---

### Post by GameManK on 2007-02-27
Is the bar where it shows the CPU speed full or halfway?

Click on powermanager and see if "cpu frequency scaling policy" is set to powersave and if so change it.  (This feature might only be in Feisty, I don't remember right now.  Sorry if I'm wrong.)

---

### Post by graha on 2007-02-27
its halfway through and everytime i click the power manager it only showed me battery powered etc

---

### Post by mikewhatever on 2007-02-27
Hi graha,
your CPU is scaled down because it's full speed is not needed atm. It is done to save battery power (if any) and reduce heat output. When the full speed it needed, be sure the system will use it. You can check it by running some heavy programs and entering in the terminal:
cat /proc/cpuinfo
[http://ubuntuforums.org/showthread.php?t=346255&highlight=cpu+frequency](http://ubuntuforums.org/showthread.php?t=346255&highlight=cpu+frequency)

the link leads to another similar discussion.

---

### Post by graha on 2007-02-27
oh right i never knew that anyways thanks for the info and also i know how to change the clockspeed :popcorn:

---

