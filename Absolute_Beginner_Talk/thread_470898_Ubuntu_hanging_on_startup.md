---
title: "Ubuntu hanging on startup"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by Huskiefan38 on 2007-06-11
I think I made a few changes in the login screen and now all I get is a blank screen with "busy" cursor, without seeing the login interface. Anyone know how to fix this?

---

### Post by p_quarles on 2007-06-11
[COLOR=Black]Give us some more details:
1) What changes did you make?
2) Does the hangup happen before you get to login? Or when loading the GUI?
[/COLOR]

---

### Post by Huskiefan38 on 2007-06-11
I think that I changed the welcome message, thats it. Very little change. If its not that, I don't remember. I was just kind of fooling around with it, since it was new and all, but I think that was what I changed, 80% sure that was it.

The problem happens before the login screen, its just a black screen with a "loading" ubuntu mouse. The little spinning thing.. It happens right after the ubuntu splash screen, and then does nothing (I let it sit over lunch and it didnt do anything)

Thank you so much for your help.

One more thing.. I dont know if it helps but the last thing that loads when I push ctrl+alt+f1 is "Running local boot scripts (/etc/rc.local)" and it says [OK]

I typed "dmesg | grep -i failed" and it said: "[ 6.356000] PM: Resume from disk failed... does that have anything to do with it? I dont know.. sorry, im kind of a n00b.

Thanks again!!

-HF38

---

### Post by limelightos on 2007-06-11
did you make it hibernate or sleep?

---

### Post by napster86 on 2007-06-11
try loggin in by pressing ctrl-alt-f1 and then login to your account ..

---

### Post by Huskiefan38 on 2007-06-11
> **limelightos said:**
> did you make it hibernate or sleep?

previously, yes. But when this started it was restarted thruogh ubuntu (correctly)

Oh, also, before I reset it I was playing with the theme as well.. I changed it once and then changed it back, but not all the settings were correct when I changed it back so I had to change some of them manually (simple things like icon size).. The way it acted was kind of funny. I just remembered that, sorry.

---

### Post by Huskiefan38 on 2007-06-11
> **napster86 said:**
> try loggin in by pressing ctrl-alt-f1 and then login to your account ..


what should I do next? I can do that, but I want to get into the GUI. I logged in and then pushed alt+f7, but its the same screen.

---

### Post by Huskiefan38 on 2007-06-11
any other suggestions? Thinking about starting from scratch, but really dont want to..... Took me 3 days to get my wireless working.....

---

### Post by p_quarles on 2007-06-11
I don't really know how to fix it, but for reinstalling, here's an idea:

Make a backup copy of your settings (basically, your entire user/home folder). I'm not sure that will save the wireless driver, but I'm guessing it would at least save whatever NDISwrapper settings you have. It'll make the reinstallation a lot easier.

---

