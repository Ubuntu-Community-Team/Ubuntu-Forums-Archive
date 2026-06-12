---
title: "Cabextract problems"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by rbradshaw on 2007-02-20
I am trying to extract a driver for my linksys wpc54g PCMCIA card, but I keep getting errors.

Here is what I get...

rbradshaw@rbradshaw-laptop:~$ cabextract WMP54Gv4_20040415.exe
WMP54Gv4_20040415.exe: no valid cabinets found

All done, errors in processing 1 file(s)
rbradshaw@rbradshaw-laptop:~$ 

Any suggestions?

I want to get the .INF drivers for my Linksys WPC54g, but all I can find is zip files or exe files... can't seem to find only the INF driver I need. There are so many versions - it is difficult to know which one I need. 

Your help is appreciate!

---

### Post by ashmew2 on 2007-02-20
DO you have wine installed ? if you do , u can type this in the terminal , 

```
cd /directory/of/exe
wine <name_of_file>.exe

```
It SHOULD start a self extractor wizard (as in WIndows) and u can pick the INF from where it extracts.
If you dont have wine installed , simply type in terminal
```

sudo apt-get install wine
```

---

### Post by ashmew2 on 2007-02-20
Also  , if you are using ndiswrapper for installing the driver , may i suggest ndisgtk , It is a graphical frontend for ndiswrapper.
To get it , simply do in terminal , 
```

sudo apt-get install ndisgtk
```

---

