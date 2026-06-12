---
title: "Can't find GNOME Partition Manager in Gutsy"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by RBird on 2008-04-21
Hello,

I am a relative newbie to Ubuntu. I am currently using Gutsy Gibbon.  I am trying to find gparted or GNOME Partition Manager on my system.  Synaptic shows it as installed, but I cannot find it anywhere.

In the Ubuntu version I was using before (6.06 I believe), this was listed under System > Administration > Gnome Partition Manager.  Now it is not there and I can't think of where else it might be.  I also am not sure what command I could use (if any) to run it from terminal.

This is very frustrating as I know it is installed, but cannot locate it.  Can someone tell me where it might be?  I have looked through the forums but could not find an answer to this question.  I did find a discussion, but I could not figure out how they fixed the issue. Any help at all would be greatly appreciated.

Thanks.

R Curtis

---

### Post by NightwishFan on 2008-04-21
Press alt+f2 and type:
```
gparted
```

---

### Post by bumanie on 2008-04-21
You can also type > sudo apt-get install gparted in terminal. The app. is available under System --> Administration --> Partition Editor

---

### Post by george9233 on 2008-04-21
It should be in /usr/bin. You could just run it by typing /usr/bin/gparted.

Or maybe just reinstall it in Synaptic.

---

### Post by skymera on 2008-04-21
If its installed it should be

```
 sudo gparted
gksudo gparted 
```

or if it's not installed

```
 sudo aptitude install gparted 
```

---

### Post by housam on 2008-04-21
You'll not find it in the installed version. if you want to use it , you've to insert the ubuntu live cd or Gparted live cd.
You can download and burn it from [[COLOR="Red"]_here._[/COLOR]]("http://gparted.sourceforge.net/livecd.php")

---

