---
title: "My keybord isnt working roperly"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by haxer on 2006-09-23
Hello my key bord isnt working is lag and ill have to press hard as hell 

Please help [-o<

---

### Post by bulldog on 2006-09-23
Buy a new one :D 

Did it get wrong after something you did?
Is your processor running at 100% by any chance?

---

### Post by haxer on 2006-09-23
Hmm.. i think it has something with wine to do becouse it was after wine i had this problem "steam" trough wine ... And this is rather funny ive got an windows keybord as well and my friend borrowed it and F8 wasnt working when he sut up an xp installation :)

---

### Post by GoneWithTheWind on 2006-09-23
My keyboard stopped copying and pasting, but these work fine with the trackball.  They had stopped working on windows, and still don't work with Linux.  I took some of the keys off and cleaned them out but they still don't work, and continue to work fine with the trackball.

Any more ideas?  

Or time for a new keyboard for me too.

---

### Post by bulldog on 2006-09-23
> **haxer said:**
> Hmm.. i think it has something with wine to do becouse it was after wine i had this problem "steam" trough wine ... And this is rather funny ive got an windows keybord as well and my friend borrowed it and F8 wasnt working when he sut up an xp installation :)

When you logged out and back in again the problem persist?
It sounds to me that something keeps your proc at his max,so there's a delay in typing and appearing on your screen.

---

### Post by haxer on 2006-09-23
Hmm dont know but it sounds just like the things you said but now after i wrote the first post it worked  so i dont know just want to know what im going to do next time

---

### Post by bulldog on 2006-09-23
Logout and back in,it kill the running proces and it should work flawlesly.

If I get stuck and know nothing better to do,I hit CTRL-ALT-BACKSPACE and the problems are over most of the times.

{not recommended when you're installing something ofcourse}

---

### Post by haxer on 2006-09-23
Ok thank you really much ill try that next time hope it will work its a pain in the a** when i cant write :)

---

### Post by xpod on 2006-09-23
> If I get stuck and know nothing better to do,I hit CTRL-ALT_BACKSPACE 

If it does not compute......try reboot:D

---

### Post by ubuntuuser on 2006-09-23
To see if a process uses a lot of CPU percentage you could open a terminal, type ```
top
``` and have alook at the %CPU column. If the process at the top row shouldn't be running anymore, hit k and enter the PID, then hit enter twice. If the process still runs after some time, do the same, but instead of hitting enter twice, tell top to use the signal 9.

Be carefull not to kill any important processes. If in doubt, don't do it.

[EDIT]
I should really improve my typing speed :)

---

### Post by bulldog on 2006-09-23
> **xpod said:**
> If it does not compute......try reboot:D

Only ex-window users ** reboot ** linux users hit ctrl alt backspace............much quicker:D

---

### Post by haxer on 2006-09-23
I looked at "top" and the onl thing that did a lot was xorg or something that used 3.0 % memory :) couldnt find any thing else that i would be bother about :) And ive got 1024mb ram so ill be fine :)

---

### Post by bulldog on 2006-09-23
> **ubuntuuser said:**
> To see if a process uses a lot of CPU percentage you could open a terminal, type ```
top
``` and have alook at the %CPU column. If the process at the top row shouldn't be running anymore, hit k and enter the PID, then hit enter twice. If the process still runs after some time, do the same, but instead of hitting enter twice, tell top to use the signal 9.

Be carefull not to kill any important processes. If in doubt, don't do it.

[EDIT]
I should really improve my typing speed :)

Keep posting and it will:D 

Thank you for that info,it's usefull.

---

### Post by ubuntuuser on 2006-09-23
> **haxer said:**
> I looked at "top" and the onl thing that did a lot was xorg or something that used 3.0 % memory :) couldnt find any thing else that i would be bother about :) And ive got 1024mb ram so ill be fine :)
I was talking about the %CPU column, not MEM. And this is only useful if the problem persists, but you said it's ok right now.

On a side note, CPU usage is not necessarily related to the ammount of RAM you have. In fact, it mostly isn't.

[EDIT]
Oh, and xorg is the server for your GUI, better not kill it :)

---

### Post by haxer on 2006-09-23
I know it was the cpu you was talking about and it was only at maximum 3%

---

