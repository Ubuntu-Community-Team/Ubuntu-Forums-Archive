---
title: "Pidgin Sound"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by SaiyanEye on 2007-07-27
Okay I added "bplay %s" into the preferences/sound tab and I still have no sound.  I decided to launch Pidgin from the terminal and it says
> 
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


Is that saying that I don't have my Sound Blaster Audigy 2 configured correctly?  I have sound with everything else though...
[I]
Edit-- Running Kubuntu, but I also had the same problem in Ubuntu..
I made sure I installed bplay too[/I]

---

### Post by SaiyanEye on 2007-07-27
*bump*:confused:

---

### Post by atomkarinca on 2007-07-27
have you tried

aplay %s

---

### Post by SaiyanEye on 2007-07-27
aplay %s isn't working either:confused::(

---

### Post by atomkarinca on 2007-07-27
do you have alsa installled? when you type alsamixer in a terminal window, can you see the mixer?

---

### Post by SaiyanEye on 2007-07-27
Ugh, Alsa Mixer master volume was all the way down:redface:


edit--
Should I uninstall Kmix since i have Alsa now?

---

### Post by atomkarinca on 2007-07-27
i don't think so. is it any harm to keep it? :)

---

