---
title: "Help please, monitor goes black after xubuntu loading.."
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by darchmitt on 2008-01-03
Hello!!
im new to xubuntu/linux and to the forum

ive just installed xubuntu on and old computer but i have a problem...
During the installation i was asked to select the resolutions to be kept bu the "xserver", i accidentally didn´t mark any resolution and hit "enter" to go to the next step.
The installation process was completed with appearently no erro, i hit "restart", removed the instalattion cd and xubuntu began loading. However the monitor went black (like when it detects no signar or something because a little led on the monitor was blinking) just after the loading screen that has the Xubuntu logo and the progress bar.... 
Can anyone help me to fix this?
i´d apreciated so much..
i searched on the forrums a threat like mine´s but i could´t found one with the exact same problem, so if there is one, sorry..
it is also important for me to say that afther the Xubuntu finishes loading i can´t do a thing because i can´t se a damn thing, the monitor just seems to be missing singal or something...

thanks for listening (or reading)

---

### Post by kestrel1 on 2008-01-03
How about re-installing XUbuntu? Did it work with the live CD?

---

### Post by jken146 on 2008-01-03
Hello.

Boot into Recovery Mode and run this command:  ```
dpkg-reconfigure xserver-xorg
```

This will take you through a wizard for setting up your X server.

You shouldn't have to reinstall.

---

### Post by darchmitt on 2008-01-03
kestrel1, thanks for the advice.. i did actually reinstall the whole thing but tha problem persisted.
luckly jken146´s solution worked!!! i was prompted for alot of settings, most of wich i didn´t had an idea of what should i enter but i managed to set it right..

thanks you guys...
im very exited about trying xubuntu!!!
thanks for the help!!! is a very nice thing this forum!!

:)

---

### Post by kestrel1 on 2008-01-03
Glad someone knew how to fix it for you.

---

### Post by ~LoKe on 2008-01-03
That line of code is something you should write down somewhere.  It'll usually solve and graphic related problem you have.

Also, I think with your problem, if you had just waited a little while, the login screen would have came on.  That's how it is for me.

---

### Post by darchmitt on 2008-01-03
ohh, i see..
well i was kinda nervous cause im newbie on ubuntu...
i´ll keep that command line in an email to have it accessible..

"see" you around in the forum guys!
and thanks a lot one more time for your help!!

---

