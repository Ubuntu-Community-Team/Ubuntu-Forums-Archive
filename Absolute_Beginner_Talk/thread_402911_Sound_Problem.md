---
title: "Sound Problem"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by nhandler on 2007-04-06
Ubuntu has been working fine for a while now. However, recently I have been having problems with the sound. I have checked all my sound levels with 'alsamixer' from a terminal, and from the sound applet on my panel. In both of them, I have raised the sound levels all the way up and unmuted all of them. I still have no sound. The only way I can get sound is if I plug an external speaker into my laptop. I know for a fact my sound card is compatible because it worked without any modifications on ubuntu. Any help would be appreciated.

---

### Post by theninthdimension on 2007-04-06
Cheater,

     Nothing like a bizarre and unexplained problem to start the day with. Have you installed, updated, or changed any other settings recently?

Jeff.

---

### Post by nhandler on 2007-04-06
I've done all of those things recently. So trying to track down a bad program is probably out of the question (since I can't remember everything I've done). I don't believe I've done anything with a sound program or setting.

---

### Post by theninthdimension on 2007-04-06
Cheater,

     I would recommend starting with two things. First, I guess make sure that it isn't some strange hardware problem where you laptop speakers just aren't connected anymore. Try booting from a live CD and see if you get sound then. If that works, or even before you try it, make sure everything is up-to-date. Open a terminal and type sudo apt-get update. There's an outside chance that during one of your previous actions not all of something was installed.

Jeff.

---

### Post by nhandler on 2007-04-06
Using a Feisty live cd, my sound worked perfectly. I also have just preformed an apt-get update and apt-get upgrade. No sound works. I've tried a movie, music file, and even a simple beep from the terminal. None of them work.

---

### Post by theninthdimension on 2007-04-06
Cheater,

     I hate to say this, but I'm stumped. I don't know if you have found this forum list, but it might help: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

     I have been trying to "break" my sound system to see if I can come up with anything but haven't had any luck yet.

     One thing has occurred to me as I'm typing, is there any chance that you have physically muted your sound from your keyboard? I know that on my system, even when I have muted things from the keyboard, it doesn't show up as muted in my sound display on the desktop.

Jeff.

---

### Post by nhandler on 2007-04-06
Thanks for your help. The I've tried hitting the unmute key on my keyboard, and using the volume keys there, they still don't make my volume work. I'm away from my computer right now, but I'll take a peak at that site when I get back. The thing that is stumping me is why the card is only partially working. The line out works, but the internal speakers don't. I guess I'll keep fooling around. Worst comes to worst, I'll do a full backup and reinstall.

---

### Post by theninthdimension on 2007-04-06
Cheater,

     I'm guessing that if the laptop speakers will work from a live CD, but not from your hard-drive install while external speakers do work that the problem is probably in the drivers for the sound card. You may be able to just patch or re-install the drivers without having to reinstall the entire OS.

Jeff.

---

### Post by nhandler on 2007-04-06
I feel like a complete idiot. I just went through the site posted earlier. It turned out "External" was muted. It didn't show up in the sound applet because you can't adjust the volume. I had no clue what this did, so I didn't pay much attention to it, but unmuting it gave me sound. The only problem is that my speakers are making a soft noise even when they are on a low volume. Any idea what sound bar would fix this?

Edit: Never mind. I just lowered the Master volume bar to about 50%. That fixed it. Thanks theninthdimension for your help.

---

### Post by theninthdimension on 2007-04-06
Glad it all worked out.

---

