---
title: "Wine windows program link on desktop -what is happening?"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by Atomic Dog on 2007-07-03
Wine placed a launcher on my desktop for a program I installed.  The command is: env WINEPREFIX="/home/john/.wine" wine "C:\Program Files\NCH Swift Sound\WavePad\wavepad.exe"

I can drag a sound file and drop it on top of the link and the program will open and it will play the sound file.  However if I try to make this the default program to open certain types of sound files it won't work.  I tried pasting the command into the "use custom command" box -no work.  I tried drilling into the .wine directory and selecting the executable -no work.  

So why can't I get this wine/windows app to be the default program to open certain files?  Boy would it be nice to be able to associate it, and even better to be able to get firefox to open them.   Is there some sort of way I can make this happen?

---

### Post by Rocket2DMn on 2007-07-03
Try giving the custom command:
env WINEPREFIX="/home/john/.wine" && wine "C:\Program Files\NCH Swift Sound\WavePad\wavepad.exe"
note the "&&"
No guarantees, but it's worth a shot.

---

### Post by Atomic Dog on 2007-07-04
Didn't work.  Won't launch at all with the "&&" in there.  How is it that when a file is dropped onto the launcher on the desktop it opens up the program and opens the file (in this case a sound file)?  What is the command/argument actually passed when i drop a file onto the desktop launcher?

Man would I love to know the answer too this one.

---

