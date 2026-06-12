---
title: "Wining About Wine"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by ShadowMKII on 2007-11-02
I had some Wine problems before - that being getting the program and making it run - but this is entirely new. After not using after the first time I got it running, Wine will no longer work. It is listed underneath the Applications->Other heading, but when I click on it, it fails to open up or work. I was going to try and see (obviously, you are going to discover very quickly that I am a fool) if Autodesk Inventor would install using Wine. This, obviously, did not work very well at all, seeing as how Wine would not even open! XD Anyhow, could some one help me with this? I have been getting a lot of problems like this recently, and I do not know why.

---

### Post by Hospadar on 2007-11-02
well, wine doesn't really open.  you just run applications with wine, for example (from a command line)```
wine your_program.exe
```
It's not the sort of thing you open up and browse around with.  the wine folder in your Applications menu will hold anything that you install with wine (stuff that in windows would add start menu options, will add its stuff here)

---

### Post by ShadowMKII on 2007-11-02
Yarg! I forgot about that! Also, why does the CD not run the setup program when I right click the .exe setup icon and choose for it to open with "Wine Windows Emulator?"

---

### Post by TeaSwigger on 2007-11-02
May I offer some suggestions.

After installing WINE, in a terminal run 

```
wineprefixcreate
```

and then

```
winecfg
```

to finish the setup. That may help avoid some odd problems.

Consider installing all WINE programs from the terminal, in the directory of the program's installer. It's easy to do - just open a terminal there and enter 

```
wine name_of_setup.exe
```

It's said to avoid a number of potential pitfalls in some cases. In the case of a CD, it can sometimes help to rip the whole CD to the hard disk as an ISO, mount it, then install from there

> **Hospadar said:**
> It's not the sort of thing you open up and browse around with.  the wine folder in your Applications menu will hold anything that you install with wine (stuff that in windows would add start menu options, will add its stuff here)

Well you can open up and browse around with WINE's file manager, winefile.

( I know what you mean I'm just being impish. :p )

---

### Post by ShadowMKII on 2008-03-26
Thank you, I will try that!

Just got to get experienced with Wine again now that I have all of my other little problems fixed.

---

