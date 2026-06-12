---
title: "how to install games using wine?"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by damansandhu on 2007-08-23
hi , i am new in linux and i want install some games like flatout 2 , nfs most wanted on ubuntu 7.04 . so i dont know what to do , i have wine installed .

---

### Post by Dr Small on 2007-08-23
```
wine /media/cdrom0/installer.exe
```

^^ Something similar to that ^^

---

### Post by chrome307 on 2007-08-23
For me I just right click on the EXE file and then get a menu which says 'Open with WINE' .......... that is if you have it on your HDD already

---

### Post by bodhi.zazen on 2007-08-23
1. Winehq is the best source of information.

See the application database here : [http://appdb.winehq.org/](http://appdb.winehq.org/)

This may also help : [http://gaming.gwos.org/doku.php](http://gaming.gwos.org/doku.php)

---

### Post by Happy_Man on 2007-08-23
Not sure if those games will work.... but if you want to try, just stick the CD in the drive, and enter this command: ```
cd /media/cdrom0 <or whatever your CD drive is called>
wine ./setup.exe <or whatever the setup utility is called>
```

If all goes well, it should start up and install.

---

### Post by Daveth on 2007-08-23
I'd also look at cogadh's excellent sticky on the subject:

[http://ubuntuforums.org/showthread.php?t=497332](http://ubuntuforums.org/showthread.php?t=497332)

---

### Post by damansandhu on 2007-08-24
ok , during installation of flatout 2 , it asks me where should i install the game default is c:\program files\flatout 2 , but there are no c: , d: such drives in ubuntu , so what should i do?

---

### Post by WebSiteGuru on 2007-08-24
> **damansandhu said:**
> ok , during installation of flatout 2 , it asks me where should i install the game default is c:\program files\flatout 2 , but there are no c: , d: such drives in ubuntu , so what should i do?

Just leave it as default. let it run.


FYI: default virtual C: Drive for wine is /home/username/.wine/c_drive/

---

### Post by damansandhu on 2007-08-24
ok i have installed flatout2 but when i click on wine icon of flatout2 , it does not start.

---

### Post by WebSiteGuru on 2007-08-24
> **damansandhu said:**
> ok i have installed flatout2 but when i click on wine icon of flatout2 , it does not start.

What did it said or do?

---

### Post by damansandhu on 2007-08-24
nothing hapened

---

### Post by Daveth on 2007-08-24
so what happens if you type 

```
wine flatout2
```

 in a terminal?  

I assume it is called flatout2 not Flatout2 or flatout_2 or any other variant!

---

### Post by G3XOI on 2007-08-24
I usualy have to right click on the icon and press 'open'.

---

### Post by damansandhu on 2007-08-25
ok i am getting this error

daman@Ultimate:~$ wine flatout2
wine: could not load L"c:\\windows\\system32\\flatout2.exe": Module not found
daman@Ultimate:~$

---

### Post by damansandhu on 2007-08-25
someone plz reply

---

### Post by Happy_Man on 2007-08-25
Try this code in front of that:
```
cd ~/.wine/drive_c/flatout2
```

---

