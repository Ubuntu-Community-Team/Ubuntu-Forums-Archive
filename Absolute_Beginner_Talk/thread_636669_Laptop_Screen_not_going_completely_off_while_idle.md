---
title: "Laptop Screen not going completely off while idle"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by hockeyfighter09 on 2007-12-10
I have a dell inspiron 8200 and I dont know the specific screen I have on it but I know its the ultrasharp kind that came with the laptop back in the day.  My problem is that when my laptop is idle for 15 minutes it is supposed to set the screen to go to sleep mode and when that time does my screen goes blank but it doesnt turn off.  It looks like i just have the blank screensaver enabled.  How do I make the screen turn all the way off when it the screen is supposed to go to sleep?

---

### Post by Harpoon on 2007-12-10
I am assuming that you are using gnome, and that you mean the backlight stays on when you think it should go dark.  The answer may be rather simple.  In gnome you go to System, Preferences and then to Screensaver.  You set a time when the screensaver should start (even a blank screen).  Also at the bottom is a button for power management.  On that screen there is an entry for "put the screen to sleep when idle for . . . " (or something like that).  

The way it works is, the timer first starts counting for the screensaver.  When that gets hit, THEN the power managment timer kicks in.  So, if you have both set to 15 minutes, you get the blank screen after 16 minutes, and 15 minutes after that the display goes to sleep.

Drove me nuts for a while, too.

---

### Post by hockeyfighter09 on 2007-12-10
Nope my screens backlight says on anyways.  I have my screen saver to come on at 10 mins idle and it does the pipe screensaver.  Then at 15 mins its supposed to go to sleep, but instead of going off it is just a black screen with the backlights staying on.  Anyone have a solution to this?

---

### Post by kefurd06 on 2007-12-10
how old is this computer? sounds like ubuntu may be sending it a power off signal but the monitor doesn't recognize it

---

### Post by hockeyfighter09 on 2007-12-10
I think the computer is about 5 years old, Im gonna say it was made in 2002.  Its a dell inspiron 8200, is there a solution that would make the screen go off completely?

---

### Post by cypha on 2008-05-26
OK, so I apparently can't create my own threads yet, but I am essentially having the same issue. I cannot get the LCD on my HP TX1000 laptop to turn off in my Hardy install. The blank screen I have set as the screen saver starts, but the backlight stays on throughout the night!

In screen saver options, I have "Regard the computer as idle after 10 mintues", and "Activate screen saver when computer is idle" is checked.

In power management, I have (On AC Power) Put computer to sleep when Inactive for NEVER. I never want the computer to turn off, just the screen please. I was able to do this in Windows, and I'd hope I can do this in Linux. I still have processes running through the night, and would simply like the screen to be off. Continuing, "When laptop lid is closed: Blank Screen". "Put display to sleep when inactive for 40 minutes". "Dim display when idle".

I can give you the Battery Power tab options, but I might as well fix one thing at a time. This issue I'm having is on AC Power, as that's how I leave my computer overnight.

BTW, I am a complete newb, so please no big words =)

---

