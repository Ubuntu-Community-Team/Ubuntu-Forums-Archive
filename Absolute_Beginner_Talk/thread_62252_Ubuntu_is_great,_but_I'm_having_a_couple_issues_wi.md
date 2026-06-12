---
title: "Ubuntu is great, but I'm having a couple issues with Firefox and XMMS"
date: 2005-09-03
forum: Absolute Beginner Talk
---

### Post by Gadren on 2005-09-03
I've been running an Ubuntu installation for a few days on VMWare, and I must say, I'm impressed -- it's easy to use, intuitive, and I love the package system (it's a great way of doing things, epecially in comparison with the Windows method...)

However, I've had a couple problems.  Occasionally, Firefox and XMMS will freeze up.  XMMS, for example, will load my MP3 files, but it just freezes when I press Play.  Both of these programs I have to force quit semi-regularly.  I can listen to music on the regular Music Player, but I'd like to get XMMS working.

Oh, and is there a keyboard shortcut to force-quit something?


(And one more thing: I truly am an "absolute beginner."  I know very little about the workings of Linux...so go easy on me. ;))

---

### Post by bjweeks on 2005-09-03
It could be VMWare causeing them to lock up?

---

### Post by Wolki on 2005-09-04
[QUOTE=Gadren]However, I've had a couple problems.  Occasionally, Firefox and XMMS will freeze up.  XMMS, for example, will load my MP3 files, but it just freezes when I press Play.  Both of these programs I have to force quit semi-regularly.  I can listen to music on the regular Music Player, but I'd like to get XMMS working. [/quote]

Enable esd output in the xmms preferences.

Don't know about your firefox problem, try to see if you can find out when it happens exactly.


> Oh, and is there a keyboard shortcut to force-quit something?

You can set one. Don't remember how right now, i'm not at my box.

or just Alt-F2, enter xkill. Your mouse cursor will become a crosshais-like thing. Point at the window and pull the trigger :)

---

### Post by Kapre on 2005-09-04
[QUOTE=Gadren]I've been running an Ubuntu installation for a few days on VMWare, and I must say, I'm impressed -- it's easy to use, intuitive, and I love the package system (it's a great way of doing things, epecially in comparison with the Windows method...)

However, I've had a couple problems.  Occasionally, Firefox and XMMS will freeze up.  XMMS, for example, will load my MP3 files, but it just freezes when I press Play.  Both of these programs I have to force quit semi-regularly.  I can listen to music on the regular Music Player, but I'd like to get XMMS working.

Oh, and is there a keyboard shortcut to force-quit something?


(And one more thing: I truly am an "absolute beginner."  I know very little about the workings of Linux...so go easy on me. ;))[/QUOTE]

Regarding the XMMS freeze when you press play, all the threads that I've read and also experiencing this type of crash, I would suggest to change the settings on your XMMS (change the sound setting --->change it from OSS to ESD...or from ALSA to ESD). On the Firefox crash, I think this is a bug that up until now hasn't been addressed (always popping up every now and then on the forum). I guess this will be addressed on the Breezy (hoping)...

K

---

### Post by Lux Perpetua on 2005-09-04
> Oh, and is there a keyboard shortcut to force-quit something?I usually do it from a terminal. Just type "killall xmms" or "killall firefox". 
> or just Alt-F2, enter xkill. Your mouse cursor will become a crosshais-like thing. Point at the window and pull the trigger :)I didn't even know about that. Thanks :) Reading the man page, though, it looks like it doesn't actually kill the process; it only closes the connection to that X client, so it is up to the process to kill itself when that happens. Which most probably do, but isn't guaranteed, correct?

---

### Post by Knyven on 2005-09-04
My XMMS freezes also, they also say to change it to OSS, but it is in OSS so i change it back to ALSA and the other, it does not freezes but there is a message box appear saying "cannot play audio".

The best solution i tried is go to System>Preference>Sound and disable/uncheck the sound server at startup and close the window. and it works it XMMS does not freeze then open it again then check it then close the windows then it freezes again... so it is the one causing my sound error... even in cedega no sound if i check the sound server at startup.

---

### Post by Gadren on 2005-09-04
Thank you all greatly!  My XMMS works now...

I have another question: how can I use XMMS (or another Linux program) to connect to an Internet radio station?

---

### Post by rafakl on 2005-09-04
its good to change the sound server too, from ESD to ALSA because ESD will give you more problems.

---

### Post by Kapre on 2005-09-04
[QUOTE=Gadren]Thank you all greatly!  My XMMS works now...

I have another question: how can I use XMMS (or another Linux program) to connect to an Internet radio station?[/QUOTE]

Garden - you need to install streamtuner. Make sure your repo is updated and go to synaptic and install streamtuner. Enjoy!!

K

---

### Post by Kapre on 2005-09-04
[QUOTE=Knyven]My XMMS freezes also, they also say to change it to OSS, but it is in OSS so i change it back to ALSA and the other, it does not freezes but there is a message box appear saying "cannot play audio".

The best solution i tried is go to System>Preference>Sound and disable/uncheck the sound server at startup and close the window. and it works it XMMS does not freeze then open it again then check it then close the windows then it freezes again... so it is the one causing my sound error... even in cedega no sound if i check the sound server at startup.[/QUOTE]
 Knyven - change it to ESD not OSS or ALSA. Try it again.

K

---

### Post by Gadren on 2005-09-05
Oh, and I discovered that Firefox only freezes when there's Flash on the webpage.  I installed (and reinstalled!) the libflash-mozplugin, but now the pages freeze (instead of just saying the some plugins aren't installed).

What do I do?

---

### Post by Steve1961 on 2005-09-05
My XMMS used to freeze as well untill I changed it to esd by following the instructions in this thread and then rebooting:

[http://ubuntuforums.org/showthread.php?t=19089&highlight=change+sound+daemon](http://ubuntuforums.org/showthread.php?t=19089&highlight=change+sound+daemon)

Although lots of people seem to recommend alsa I've never found the sound quality to be as good as esd.  Sorry I can't help with the firefox problem.

---

