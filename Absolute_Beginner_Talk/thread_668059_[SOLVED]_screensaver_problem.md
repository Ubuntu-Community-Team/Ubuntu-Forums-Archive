---
title: "[SOLVED] screensaver problem"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by srikrishnan on 2008-01-15
Hi All,

In the system/Preferences/Screensaver menu I have choosed "Braid" screen saver, Immediately my system got hanged. So I have helplessly reboot my system.

after my reboot, I place my system ideally for 10 minutes, Screen saver appears, but it was not gone even when i shake my mouse. Again system got hanged.

So I feel something wrong with that screensaver, so I plan to disable that, when i try to open the "scrensaver" menu. Again my system got hanged. What can I do with that, 

How can I solve this problem, please help me?

Thanks in Advance,
Srikrishnan

---

### Post by mattismyname on 2008-01-15
Srikrishnan-

I've had similar issues.  When I posted to the forums, most people believed it was an issue with the 3d drivers.  Are you using the restricted NVidia driver?  That one seems to have the most problems.

Also, since the screensavers are CPU intensive, it is potentially an overheating issue on the CPU.

---

### Post by srikrishnan on 2008-01-15
Hi,
Thanks for your response.

Yes I am using Nvidia driver.

OK, Is it possible to disable my screen saver option?

please help me to solve this problem.

Regards,
Srikrishnan

---

### Post by mattismyname on 2008-01-15
Go to System->Preferences->Screensaver and either un-check the box marked "Activate screensaver when idle, OR select the "blank screen" option for the screensaver which will just make a black screen instead of a CPU/GPU intensive screensaver.

---

### Post by srikrishnan on 2008-01-15
Hi,

I think you are not read my first mail clearly.

When I try to open system -> preferences -> screensaver, immediately my system got hanged because of the screen saver selection.

Now I want to know, whether it is possible to uncheck the "Activate. . ." through Terminal (command line)?

Regards,
Srikrishnan

---

### Post by mattismyname on 2008-01-16
Good question, sorry I don't know the answer.  If it were me, I would look in the dotfiles in your home directory, especially .gconf, .config and see if you can find the config file for the screensaver anywhere so you can edit it directly.  

Hopefully somebody else here knows how to do it.

---

### Post by FuturePilot on 2008-01-16
Before opening the Screensaver Preferences enter this in a terminal
```
metacity --replace
```
This will turn off Compiz. Then open the Screensavers and change it.
Then you can turn Compiz back on
```
compiz
```

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/101943]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/101943")

---

### Post by srikrishnan on 2008-01-18
Hi,

Thanks for your reply.

It automatically got disabled. I don't know, may be by some OS updates.

Regards,
Srikrishnan

---

### Post by GOfree on 2008-04-29
Interesting...

I am still trying to figure this out, myself.

Thanks.

---

