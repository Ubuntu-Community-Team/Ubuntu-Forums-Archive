---
title: "getting wine emulator to work"
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by alwiap on 2007-02-03
Ok, I went to applications ---> add/remove ---> and installed Wine Emulator etc.etc.

Then I go to look for it on my computer, or try to open a Windows game cd and look for the option (open with...) etc.. and it doesnt appear to be installed at all.

So i went back, unchecked it, applied, and rechecked it, and I still can't either find Wine on my system or it doesn't install.

Is there another way I can download it ? (probably), and if I can download it another way, how would i get it on my pc?

Thanks for your help, I am using ubuntu 6.10.

---

### Post by lamego on 2007-02-03
To run a program with wine you should use the terminal.
Open the terminal and run the windows program under wine with:
```
wine program.exe
```

---

### Post by alwiap on 2007-02-03
ok, thanks, i just did that.  this message came up:

could not load L"c:\\windows\\system32\\program.exe": Module not found

so i assume that it is not installed on my computer? it is checked in the add/remove programs list though.

---

### Post by kregg on 2007-02-03
try

```

wine iexplore.exe

```

---

### Post by alwiap on 2007-02-03
> **kregg said:**
> try

```

wine iexplore.exe

```

ok, that brought up iexplore.exe, thanks.

so i guess it is working now, just to clear up my confusion, is wine a program that is not to be 'found' anywhere on the system anyway? like it's not a program that has a gui you can open up, its only really to be used in the terminal as wine?

thanks for the help :]

---

### Post by kregg on 2007-02-03
It's not so much in the terminal, it's just that you have to pass parameters to wine (the file name - in my case, it was internet explorer) then it will load any windows program

Hope it helps

---

### Post by jvc26 on 2007-02-03
> **kregg said:**
>  then it will load any windows program
Not strictly true, you can't run ANY windows app in wine, just some of them. Often there is an alternative you could use instead which doesnt require wine.
Il

---

### Post by alwiap on 2007-02-03
> **kregg said:**
> It's not so much in the terminal, it's just that you have to pass parameters to wine (the file name - in my case, it was internet explorer) then it will load any windows program

Hope it helps

ok, thanks.

after putting 'wine iexplore.exe' in the terminal, internet explorer comes up but its completely blank and doesnt appear to load correctly. here's some ss's:

[[IMG]http://img470.imageshack.us/img470/7190/screenshotws8.png[/IMG]](http://imageshack.us)

[[IMG]http://img470.imageshack.us/img470/2919/screenshot1gc9.png[/IMG]](http://imageshack.us)

---

### Post by phansiizwe on 2007-02-03
You might also want to try (type in the console),

```
winecfg
```

this will start the wine configuration program. For instance if you want to access your CD drive from wine, you will have to go to the 'Drives' tab, click Add... and type in the mount path to your CD drive, e.g. /media/cdrom

When trying to run applications using wine, e.g. Setup.exe on your CD, which you mounted as D: in winecfg, type (from a terminal):

```
wine "D:\\Setup.exe"
```

The "'s are needed for if you have spaces in the pathname.

---

### Post by kregg on 2007-02-03
> **Illuvator said:**
> Not strictly true, you can't run ANY windows app in wine, just some of them. Often there is an alternative you could use instead which doesnt require wine.
Il

I stand corrected :)

---

