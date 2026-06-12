---
title: "Linux style terminal for windows"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by ninocass on 2006-05-10
Is it possible to get a terminal that operates in windows?

i still need to use windows for the odd thing and i find myself typing linux commands into the MS dos prompt

Thanks

Nino

---

### Post by kabus on 2006-05-10
[http://www.cygwin.com/](http://www.cygwin.com/)

---

### Post by NetMatrix on 2006-05-10
Are you asking for a program that will make linux commands work in windows?

---

### Post by ninocass on 2006-05-10
what im looking for is a fully functioning terminal that will run in windows ie i type ls and itll give me directory listings just like the DIR command in dos, only the basic commands suhc as moving files and navigation not running  linux programs etc

---

### Post by Rinzwind on 2006-05-10
I have not seen any programs like that but you can easily do it with a BAT script.

C:\>EDIT ls.bat
@ECHO OFF
DIR


Save it and **ls** will do:
> 
C:/>ls

 Het volume in station C heeft geen naam.
 Het volumenummer is A878-84DE

 Map van C:\

24-09-2004  14:46                 0 AUTOEXEC.BAT
24-09-2004  14:46                 0 CONFIG.SYS
17-02-2005  13:19    <DIR>          CubeJava
24-09-2004  14:46    <DIR>          DELL
05-05-2006  12:25    <DIR>          Documents and Settings
10-05-2006  09:44    <DIR>          Images
10-05-2006  15:49                16 ls.bat
04-03-2005  10:26    <DIR>          PHPDOCS
05-05-2006  08:28    <DIR>          Program Files
10-05-2006  08:36    <DIR>          WINDOWS
               6 bestand(en)       12.512.773 bytes
               8 map(pen)  15.835.099.136 bytes beschikbaar


---

### Post by gibson on 2006-05-10
[QUOTE=ninocass]what im looking for is a fully functioning terminal that will run in windows ie i type ls and itll give me directory listings just like the DIR command in dos, only the basic commands suhc as moving files and navigation not running  linux programs etc[/QUOTE]


Cygwin does just that -- you can either use a bash terminal that it gives you, but even better (for what you want i think) you can add the path to "c:\cygwin\bin" or whatever into your PATH variable ang use commands like grep and ls through the standard cmd.com command prompt.

hth
g

---

