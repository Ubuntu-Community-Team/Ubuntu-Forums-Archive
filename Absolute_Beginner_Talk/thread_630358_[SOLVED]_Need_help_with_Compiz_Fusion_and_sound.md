---
title: "[SOLVED] Need help with Compiz Fusion and sound"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by A09Z on 2007-12-03
Hi, I just installed 7.10 and I'm playing around with different things.

1. But once I installed the ccsm for Compiz Fusion and tried some effects my title bar (title, min/max button and exit button) disappears. The only way I could get it back is if I turn off my visual effects (to none). I'm wondering if this means my computer can't handle Compiz Fusion? I have a pretty old computer: P4 1.7 GHz, GeForce2 MX 400 and 512 RAM.

2. I'm also having problems with sound, I can only hear static on the speakers when I turn them on. I have a Creative Soundblaster Live soundcard that supports 5.1 surround sound (I'm not sure on the exact model).

Also, I'm wondering what exactly is a shell?  Is it the same thing as the terminal?
Any help would be appreciated thanks!

---

### Post by fineas on 2007-12-03
About compiz fusion, just try to enable less efects.Remember that not all of them are stable enough.
About shell and terminal, check this: [http://ubuntuforums.org/showthread.php?t=492379](http://ubuntuforums.org/showthread.php?t=492379)

---

### Post by PGill34 on 2007-12-03
i am having pretty much the same problems except the sound part.. you can try and add windows decorations its in customs that may help... i cant help with the sound problems.. sorry

---

### Post by LowSky on 2007-12-03
are you trying to use emerald with compiz?

try switching between sound drivers (OSS and ALSA)

---

### Post by A09Z on 2007-12-03
Thanks for all of your replies.  But now even when I turn the visual effects to normal the title bar is gone, I'm not using the ccsm.  Are there recommended hardware requirements, I know there is the required ones in order to run Linux.  As for the sound, how can I install the drivers?  I don't have a CD for it and I'm not sure if it even detects my soundcard.

---

### Post by DutyDuty on 2007-12-03
If you are using emerald, run ```
emerald --replace
then
compiz --replace &
```

best of luck. I've got nothing on your sound problem.

---

### Post by A09Z on 2007-12-03
Ummm, how do I know if I'm running emerald or compiz or compiz fusion?

---

### Post by DutyDuty on 2007-12-03
You are running Emerald and Compiz Fusion. Take my word, it's simpler.

---

### Post by karthikophobia on 2007-12-03
Some of the features in my compiz fusion are a bit problematic:
!. Once i use the annotate feature.........the system hangs.
2: Im not able to assign shortcuts to the new freewins plugin

thanq

---

### Post by DutyDuty on 2007-12-03
Freewins? Could you point me to that?

---

### Post by A09Z on 2007-12-03
> **DutyDuty said:**
> If you are using emerald, run ```
emerald --replace
then
compiz --replace &
```

best of luck. I've got nothing on your sound problem.

I copied that into the terminal but then it says emerald isn't even installed...

---

### Post by DutyDuty on 2007-12-03
```
sudo apt-get install emerald
```

Remember to post the two commands one at a time!

---

### Post by A09Z on 2007-12-03
So what exactly does emerald do?  Just having compiz fusion isn't enough?

---

### Post by DutyDuty on 2007-12-03
Emerald controls window boarders.

---

### Post by A09Z on 2007-12-03
Nothing happens after I enter those lines into the terminal (emerald --replace etc.).  How do I control emerald anyways?  Can ccsm control the emerald features or do I need a separate program?

---

### Post by karthikophobia on 2007-12-07
i found it in this site:
[http://forum.compiz-fusion.org/showthread.php?t=5303](http://forum.compiz-fusion.org/showthread.php?t=5303)

---

### Post by DutyDuty on 2007-12-07
You open emerald and click a theme. Use the replace command to change to that theme.

---

### Post by A09Z on 2007-12-09
Thanks for all your help.

---

### Post by nikoPSK on 2007-12-09
Please mark this thread as "SOLVED" :D.

---

### Post by karthikophobia on 2007-12-11
I found it here
[http://forum.compiz-fusion.org/showthread.php?t=5303](http://forum.compiz-fusion.org/showthread.php?t=5303)

---

