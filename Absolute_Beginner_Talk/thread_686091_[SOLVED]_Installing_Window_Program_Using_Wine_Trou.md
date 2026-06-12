---
title: "[SOLVED] Installing Window Program Using Wine Trouble."
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2008-02-02
Ok, so I have Wine and I'm trying to run a windows program but when i click the .exe file to install it it doesn't do anything. and wine should easily be able to handle this program.

help needed please?:(

---

### Post by Rocket2DMn on 2008-02-02
What program are you trying to run?
Also, you should navigate to the directory and run
```
wine *yourprogram.exe*
```

---

### Post by Cypher on 2008-02-02
Which program is it and is there a Linux alternative? If no, perhaps you can try it within VirtualBox?

---

### Post by RadiationHazard on 2008-02-02
i would use virtual box...but the installation disc that they gave me when i did it geek squad made the disk for me and it's like a 1 disk recovery disk and i have to install it to the whole disk and i get errors when i try to install it to virtual box. and it's not a program you'd of heard of i promise. haha. but i'll try the navigating to it. so i go some thing like this?

```
wine /home/jordan/Desktop/programname.exe
```

it's on my desktop.

---

### Post by Rocket2DMn on 2008-02-02
Yes, that should work, or at least show error output which you can post back here.  Sometimes it helps to put the file in the wine directory which is hidden in your home folder and is called ".wine".  You can hit CTRL+H to see hidden files in nautilus.
So maybe move it to /home/jordan/.wine/drive_c/programname.exe

Try it your way first.  But really, what program is this, because not everything works under wine.

---

### Post by RadiationHazard on 2008-02-02
it tells me "Permission denied" :confused:

---

### Post by Rocket2DMn on 2008-02-02
Hehe, thats not good, you should own that directory.  We'll fix that
```
sudo chown jordan:jordan -R ~/.wine
```

---

### Post by RadiationHazard on 2008-02-02
Ok, so i used to always wish that a program like this would have been around back when i used to play runescape but no one had created it back then if they did i didn't know about it. but i just happened to stumble across this program and was wanting to try it out to see if it works. it's called auto miner and basically it mines for you and you don't have to sit there and mine. haha so i really don't have to get this app working cuz i don't even do runescape anymore but i taught it'd be cool so i wanted to give it a try.

---

