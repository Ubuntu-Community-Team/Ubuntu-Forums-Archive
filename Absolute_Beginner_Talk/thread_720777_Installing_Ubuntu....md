---
title: "Installing Ubuntu..."
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by crimsonandred88 on 2008-03-10
I just installed ubuntu on a new PC, and it keeps saying it cannot load the greeter app. anybody else had this problem or know how to fix it?

---

### Post by Therion on 2008-03-10
What version of Ubuntu did you install? 

I know this was a (common?) problem under Feisty Fawn, but not so much under Gutsy... or at least I didn't think it was.  Either way, though, when you installed did you install Feisty Fawn (Ubuntu version 6.06) or Gutsy Gibbon (Ubuntu version 7.10)?

---

### Post by billgoldberg on 2008-03-10
> **Therion said:**
> What version of Ubuntu did you install? 

I know this was a (common?) problem under Feisty Fawn, but not so much under Gutsy... or at least I didn't think it was.  Either way, though, when you installed did you install Feisty Fawn (Ubuntu version 6.06) or Gutsy Gibbon (Ubuntu version 7.10)?

Feisty fawn was version 7.04

---

### Post by billgoldberg on 2008-03-10
I don't know what the greeter app is.

Never heard of it.

Please mention the version you run (7.10 -7.04- 6.06 ...)

---

### Post by Therion on 2008-03-10
> **billgoldberg said:**
> 

Feisty fawn was version 7.04
Correct.  Thank you.  

I'm going to assume (!) the poster installed Feisty and redirect them to [this thread](http://ubuntuforums.org/showthread.php?t=190310) for a possible solution.  

It's quittin' time for me and I can't get outta here fast enough today...

---

### Post by linux1time on 2008-03-10
i´ve googled and i found this...hope it helps frriend :)

If the GUI fails to load and you are unable to access the system menu then you should try the instructions below.

1. first reboot your computer into maintenance mode/recovery mode.

2. open /etc/gdm/gdm.conf-custom by entering the following command

sudo vim /etc/gdm/gdm.conf-custom

3. press i to enter into insert mode. Locate the following line and comment it by inserting a # in front of the line.

GtkModulesList=gail:atk-bridge:/usr/lib/gtk-2.0/modules/libdwellmouselistener:/usr/lib/gtk-2.0/modules/libkeymouselistener

4. press the Esc key and then type in :wq to save and quit the editor.

5. type sudo init 6 to reboot that should fix the problem.I am using gutsy tribe 5 and looks like this problem has been present in Ubuntu ever since dapper hope they fix it before gutsy gets released.

---

### Post by crimsonandred88 on 2008-03-10
I installed Gutsy...I suppose I should also mention that its an older HD with a corrupted version of Windows that I can't get off. I know that could be the problem right there, but I was just wondering if there were any other known causes/fixes for it. thanks for responding, i really appreciate it.

---

