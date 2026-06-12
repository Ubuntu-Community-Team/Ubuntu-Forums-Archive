---
title: "Synaptic Package error message and won't run"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by maxjensen on 2007-05-25
Hi. I'm very new to Ubuntu.

When I try to run Synaptic or if I try to update Ubuntu I get the following message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I've searched this forum and I see others have the same problem. Only thing is that I don't understand how they fixed it. 
It may be wrong but I think it happened after I installed Amarok.

Any help on how to solve this would be greatly appreciated!

Thanks,

Max :confused:

---

### Post by Pragmatist on 2007-05-25
You could try this suggestion:
[http://www.linuxquestions.org/questions/showthread.php?t=361965](http://www.linuxquestions.org/questions/showthread.php?t=361965)

My **/var/lib/dpkg/updates **is also empty, so if yours isn't, the suggestion in the above thread might work for you.

---

### Post by maxjensen on 2007-05-25
> **Pragmatist said:**
> You could try this suggestion:
[http://www.linuxquestions.org/questions/showthread.php?t=361965](http://www.linuxquestions.org/questions/showthread.php?t=361965)

My **/var/lib/dpkg/updates **is also empty, so if yours isn't, the suggestion in the above thread might work for you.

Thanks!! Well the folder isn't empty. BUT...I don't have privileges to delete the files. So I have to get to root in some way right? Can it be done from the terminal window?

Thanks again!!

Max

---

### Post by mikewhatever on 2007-05-25
If you are sure you want to delete the content of /var/lib/dpkg/updates, type this in the terminal
> sudo rm /var/lib/dpkg/updates/*

---

### Post by maxjensen on 2007-05-25
Thank you!!

Everything is working like a dream again :)

I appreciate it!

Kind regards,

Max

---

