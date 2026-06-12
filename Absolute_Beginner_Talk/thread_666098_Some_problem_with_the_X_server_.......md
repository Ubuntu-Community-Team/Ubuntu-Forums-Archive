---
title: "Some problem with the X server ......"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by arjayes on 2008-01-13
I really have no clue what the problem is ..... 
there were some very strange symptoms though .....
While i was watching a movie-**doing nothing else** -, the system suddenly gets hung ...
I tried evrything :- killing the X server , switching to an alternate tty .....nothing worked 
so i did a hard restart .... during the boot process it gave some message regarding a **file system error** and tried to reboot .......  this time during the boot process i get a** blue screen with a message saying that " The X server couldn't start because of some unknown  internal error ....**. and that happens everytime i try to reboot now .... 


I'm Sorry for givin such a long rambling commentary but coz i don't have a clue what the problem is I thought it best to put everything  out there . thnks for readin this & pls. help .

---

### Post by PmDematagoda on 2008-01-13
Boot Ubuntu in Recovery Mode and execute:-
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
after reconfiguration is done, execute:-
```
startx
```

---

### Post by taurus on 2008-01-13
Maybe you just need to reconfigure your X server again.  Boot into recovery mode from GRUB menu and run

```
dpkg-reconfigure xserver-xorg
```
When you are done with it, reboot your machine with

```
shutdown -r now
```

---

