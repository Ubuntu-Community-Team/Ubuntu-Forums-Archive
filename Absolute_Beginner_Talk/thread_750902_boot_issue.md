---
title: "boot issue?"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by Mutant Corn on 2008-04-10
So I've gotten Xubuntu(gutsy) onto my laptop, finally, and I just got through updating everything. When a restart was rquired, I got an error message upon reboot telling me that I wasn't allowed to access the system configuration. Currently, the CPU is hovering at around 75% with major fluctuations, the system is moving very slow in general, and  the desktop is not displayed. I have the taskbars, and can run programs, but the actual background and icons and all that are missing. There's just that tan color that you see during the boot process.

I've installed xubuntu on 2 other systems so far, using the very same disc, and have never encountered this problem....have I killed it?

The computer is a Dell XPS m1210 with a 2ghz centrino chipset and 2 gigs of ram

---

### Post by tamoneya on 2008-04-10
can you post the output of ```
top
```

---

### Post by Mutant Corn on 2008-04-10
what part of it? I can't type that whole readout...

---

### Post by tamoneya on 2008-04-10
list the five processes as well as there cpu percentage if you can.

---

### Post by Mutant Corn on 2008-04-10
...it keeps changing...do I just pick a number?

What five processes? I'm very new at this...:(

edit: It's midnight and my tiny laptop is overheating pretty bad...I'm going to have to pick this up tomorrow..

---

### Post by tamoneya on 2008-04-10
just hit ctrl-c to stop top and it will stay on one screen.  Then the top five processes would be the top five lines.  Better yet if you have a camera accessible just take a picture and post it to the forums.

---

### Post by Mutant Corn on 2008-04-10
Now that I've rebooted, the cpu seems to be doing fine, and I didn't get that error message again, but I still have no desktop...?

---

### Post by Mutant Corn on 2008-04-10
..anyone?

---

### Post by Mutant Corn on 2008-04-10
here's this, almost forgot

---

### Post by Mutant Corn on 2008-04-10
:confused:

Is this just uncommon or something?

---

### Post by Mick8882003 on 2008-04-10
if you take a look at the cpu usage you will realise that nothing is slowing the comp right down, having said that it i cannot tell you what the problem is.

---

### Post by Mutant Corn on 2008-04-10
^ that SS was taken after I rebooted...the cpu is fine now

Thanks for the reply though!

---

### Post by Mutant Corn on 2008-04-11
Is there a way for me to reinstall the GUI without losing my data?

---

### Post by smartboyathome on 2008-04-11
Have you tried right clicking and seeing if it was shaded?

---

### Post by Mutant Corn on 2008-04-11
Right clicking on the blank space does nothing...:(

---

### Post by angry_johnnie on 2008-04-11
Open your settings manager.
Go to **Sessions and Startup**.
Then, where it says Session Chooser, check the box for **Display chooser on login**.
Then, the next time you log in, it will ask you whether you want to start a new session, or continue where you left off last time.
Choose a new session, and see if XFCE starts working normally.
If it does, go back to Sessions and startup.
Uncheck "Display chooser on login".
And the next time you log out, check the box where it asks you whether you want to save the session.
I hope that helps. :-)

---

