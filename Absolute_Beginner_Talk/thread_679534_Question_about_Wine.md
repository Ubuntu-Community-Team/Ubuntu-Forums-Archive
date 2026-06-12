---
title: "Question about Wine"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by Fanatico on 2008-01-27
I've installed Wine via Synaptic Manager. As far as I understood in order to run Windows application  under Linux, I have to add that application to Application page in Wine configuration utility. The problem is that when I open browse dialog in Wine configuration utility I see only very limited number of my Windows directories. For example I see only following:

C:\Program Files\ Common
C:\Program Files\Internet Explorer
C:\WINNT\System32

Could you explain what is wrong and how can I configure ANY Windows application in Wine?

Thanks

---

### Post by swoll1980 on 2008-01-27
you have to install the program via its exe file then cross your fingers

---

### Post by Fanatico on 2008-01-27
Could you be more descriptive? Are you talking about Wine installation?

---

### Post by rhc on 2008-01-27
For ex. download a program that works via Wine.
Then run setup.exe.
Wine comes with nothing.
You should download programs and install them via Wine.

---

### Post by energiya on 2008-01-27
Lets say you want to install Winamp, and you have the setup in your home path. You just
```

wine ~/winamp_setup.exe

```
in terminal and it will execute.

---

### Post by swoll1980 on 2008-01-27
say you want to install morrowind you would right click the morrowind exe and click open with wine it will install the program as if you were using windows. then you simply click apps>wine>programs>morrowind to run it

---

### Post by Fanatico on 2008-01-27
Thanks to all. Now it is much more clear.
Still I have a question: What to do if certain Windows application doesn't require installation setup and distributed by exe's which is ready to ru.

---

### Post by jesrani on 2008-01-27
I have a windows program called "Aida32". It doesnt need installation but it is also not a single file. I copied the folder from my XP to Ubuntu computer. Then I double-clicked the file aida32.exe and got an error message. But when I right clicked the same file and used the option "Open with Wine....", the program ran as it would in windows.
In short, use "Open with wine..." option from right context menu on any non-installable exe file.

---

### Post by Incense on 2008-01-27
> **Fanatico said:**
> Thanks to all. Now it is much more clear.
Still I have a question: What to do if certain Windows application doesn't require installation setup and distributed by exe's which is ready to ru.

You would run it the same as the setup files. Just right click the .EXE, Open With, and select WINE, and it may or may not run. You just need to keep in mind that not every windows program will run under WINE. You can just the AppDB on [http://www.winehq.org/]("http://www.winehq.org/") to see how others fared with the application you are trying to run. 

If you NEED an application that will not run with WINE, you could utilize vitalization and run windows in Ubuntu using a program like [VirtualBox ]("http://www.virtualbox.org/wiki/Downloads").

---

