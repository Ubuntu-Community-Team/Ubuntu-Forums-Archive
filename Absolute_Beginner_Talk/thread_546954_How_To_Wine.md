---
title: "How To Wine?"
date: 2007-09-09
forum: Absolute Beginner Talk
---

### Post by snakeminidez on 2007-09-09
I  recently downloaded Wine on the latest version of Kubuntu, however I have no idea how to make programs work and download them onto wine so that I can run them. It would be a great help if someone could give me some play-by-play instructions on how to do whatever it is I need to do to make the Windows programs work.

---

### Post by lespaul_rentals on 2007-09-09
You've installed wine, correct?

Download your .exe file and save it to the folder of your chosing.

Go into command line interface, whether you use Terminal or Konsole (I prefer Konsole but it makes no difference).  Type the following command:

wine *path of file*

wine will then run the file.  :KS

---

### Post by Dr Small on 2007-09-09
If the filename "setup.exe" was located on the desktop, you would run this command:
```
wine ~/Desktop/setup.exe
```

---

### Post by snakeminidez on 2007-09-09
I tried the above and got this:
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
dezaun@dezaun-laptop:~$

I went to the terminal and typed in: *wine desktop/ZuneSetup.exe *
is that correct?

---

### Post by FuturePilot on 2007-09-09
Did you run
```
winecfg
```first?

---

### Post by init1 on 2007-09-09
Many applications do not run in Wine. It may be that this app is one of them.

---

### Post by snakeminidez on 2007-09-09
Well if Zune won't work can anyone give me an example of a program that definitely will just so I can make sure I'm doing it right.

---

### Post by runemaste644 on 2007-09-09
I have some apps that work. If i can attach an executable file later on, which i know works out of the box, then we will know. Its a stress reducer that you get to beat up your desktop (though i dont know why you would do that in Linux...) Anyway, you can copy it on a flash drive (Its a stand alone executable)

---

### Post by snakeminidez on 2007-09-09
I installed Internet Explorer through wine and it told me to restart my computer and I did, but I don't know how to run it

---

