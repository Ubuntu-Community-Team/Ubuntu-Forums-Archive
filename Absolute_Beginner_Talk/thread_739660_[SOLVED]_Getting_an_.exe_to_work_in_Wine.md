---
title: "[SOLVED] Getting an .exe to work in Wine"
date: 2008-03-29
forum: Absolute Beginner Talk
---

### Post by linuxbeatswin on 2008-03-29
I've used Ubuntu for a while, and just installed Wine. I am trying to get my wife's windoze based cd-rom to work, and was able to install it, but when I right-clicked the exe file to run the program, I got this error message:

EAccessViolation in module CompRev4.exe at 00000000
AccessViolation at address 00000000 in module 'CompRev4.exe'.
Read of address 00000000

What does this mean, and how do I fix it? My wife really needs this to work, and I have been looking at forums for the past two hours trying to figure this thing out before I bothered you nice folks about it,. Any help you can give is greatly appreciated.

Thank you!

---

### Post by herbster on 2008-03-29
Can you provide any details on the program itself? Have you searched the WineHQ AppDB? [http://appdb.winehq.org](http://appdb.winehq.org)

And is that the output from terminal or a pop-up error when you opened it from a file browser? Run it in a terminal and paste the output, it won't necessarily be the same.

```
wine CompRev4.exe
```

---

### Post by linuxbeatswin on 2008-03-29
> **herbster said:**
> Can you provide any details on the program itself? Have you searched the WineHQ AppDB? [http://appdb.winehq.org](http://appdb.winehq.org)

And is that the output from terminal or a pop-up error when you opened it from a file browser? Run it in a terminal and paste the output, it won't necessarily be the same.

```
wine CompRev4.exe
```

The program I am running is an NCLEX study guide. (It helps nursing students study for the NCLEX certification exams.) The output I wrote about was from a popup window. I got this from term:

wine: could not load L"c:\\windows\\system32\\CompRev4.exe": Module not found

Thank you for your time, and your knowledge.

---

### Post by iSplicer on 2008-03-29
Hmmm... I dont think wine is a good solution for this, have a look at this:

[http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux](http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux)

---

### Post by linuxbeatswin on 2008-03-29
This looks great- similar to VMWare at the office. (They won't touch linux even though we use BSD and Fedora as servers.)
The only problem is, I don't have any windoze installation disks- I don't use it except at the office. Darn, I may have to break down and buy windoze. Just when I thought I could get away from Gates. 
Is there any other possible way for me to get this to work for my wife?

---

### Post by herbster on 2008-03-29
Yeah, VirtualBox is a good choice, but let's see if we can get this working in Wine as it already installed successfully before he undertakes the adventure of setting up VBox and installing XP, etc.

linuxbeatswin: I just checked some other links that had your issue. Try this in a terminal:

```
cd ~/.wine/drive_c/windows/system32 && wine CompRev4.exe
```

Paste the output.

---

### Post by linuxbeatswin on 2008-03-29
> **herbster said:**
> Yeah, VirtualBox is a good choice, but let's see if we can get this working in Wine as it already installed successfully before he undertakes the adventure of setting up VBox and installing XP, etc.

linuxbeatswin: I just checked some other links that had your issue. Try this in a terminal:

```
cd ~/.wine/drive_c/windows/system32 && wine CompRev4.exe
```

Paste the output.

This is what Term gives me:

wine: could not load L"c:\\windows\\system32\\CompRev4.exe": Module not found

---

