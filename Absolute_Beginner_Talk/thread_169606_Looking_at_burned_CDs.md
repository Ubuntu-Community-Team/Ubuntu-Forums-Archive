---
title: "Looking at burned CDs"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by Cereus on 2006-05-02
I have a bunch of old burned CDs with music, pictures etc. I can access the contents of these CDs with winXP.

I cannot access all of the CD contents using Ubuntu. Sometimes I can access some of the files or some files come up with lots of ????????.

What is the cause and how can I fix it. Does it have to do with long filenames? The TOC of the burned CD? Wrong drivers for the reader (a LG combo DVD/CD burner).

I apologize for the n00b-ness of the question. I've done some googling but no solutions and thanks in advance to any replies.

Cereus

---

### Post by johnc4510 on 2006-05-03
We need to know what format the files are.

---

### Post by Cereus on 2006-05-03
Some are .mp3, others are .mpg, .exe, .jpg, .avi, just lots of general files.

---

### Post by Cereus on 2006-05-03
I've found another person with the problem.
[http://www.ubuntuforums.org/showthread.php?t=39970](http://www.ubuntuforums.org/showthread.php?t=39970)

The idea is that CDs burned at a high speed in windows aren't read by Ubuntu/Linux well and there's no solution.

---

### Post by catlett on 2006-05-03
It may be that Linux doesn't know the file it is made into. I'm thinking along the lines when you download something in windows and it has a question mark. When you go to open it windows prompts "windows does not know the program that made this file. Do you want windows to go online ti find out the file type or do you want to manually choose the program to open it". This may be what is happening but in a Linux way.
Exe files are windows specific. They won't run in Linux. I don't know how they are represented in tyhe file browser.
Try opening a Linux mp3 player and have it open the file and see what happens. If it is a compatable file it should play even though the file browser didn't recognise it.

---

### Post by Sandlst on 2006-05-03
Quick question: are you unmounting the cdrom from the computer (ie not just pressing the physical button) when taking cds out?  On my computer, when I installed the automatix auto-eject from normal button push, if I didn't unmount them, I would constantly get the same error-my cds would show up, with a bunch of ???????? for files/folders.  This cleared up however as soon as I did a ```
eject
```and put the cd back in....I wasnt aware that burning high-speed in windows could have this effect too, thanks for pointing it out, I'm sure you saved me some future headaches.

---

