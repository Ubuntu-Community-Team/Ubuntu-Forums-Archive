---
title: "Cant get Beep media player to start"
date: 2005-08-23
forum: Absolute Beginner Talk
---

### Post by rama on 2005-08-23
I am having trouble starting bmp. I ve searched for it in the repositories using synaptic. I installed it but when I try to start it from the menu nothing happens. Is there a log or something I could check to find out what is wrong?

---

### Post by KingBahamut on 2005-08-23
open up a terminal window 

type beep-media-player 

hit enter

what happens?

---

### Post by rama on 2005-08-23
:confused:  :shock:  :confused: 

jsar@orion1800L:~$ beep-media-player
jsar@orion1800L:~$


Do I need any additional packages allong with the one named "beep-media-player"?

---

### Post by KingBahamut on 2005-08-23
Thats odd....

no, not that im aware of.

---

### Post by Stormy Eyes on 2005-08-23
Try running bmp from the terminal instead.

---

### Post by rama on 2005-08-23
[QUOTE=KingBahamut]Thats odd....

no, not that im aware of.[/QUOTE]
 I also tried to find the directory where the bmp files are stored and I got this: 

jsar@orion1800L:~$ find bmp
find: bmp: No such file or directory
jsar@orion1800L:~$ find beep-media-player
find: beep-media-player: No such file or directory
jsar@orion1800L:~$

Could you give me step by step instructions to uninstall and install bmp once again in case I 'm not doing something trivial right.

---

### Post by KingBahamut on 2005-08-23
apt-get remove beep-media-player
apt-get install beep-media-player

---

### Post by rama on 2005-08-23
[QUOTE=KingBahamut]apt-get remove beep-media-player
apt-get install beep-media-player[/QUOTE]
 I reinstalled it using the commands you wrote.No errors during the process. But  I still get nothing. 
Anyway I can always use xmms. 
Thanks for the replies.

---

### Post by KingBahamut on 2005-08-23
Ok, if that works for you.

---

### Post by rama on 2005-09-03
[QUOTE=KingBahamut]Ok, if that works for you.[/QUOTE]
 I tried again today to install and run beep-media-player ... I wanted to see if it would show track titles when listening via shoutcast cause xmms doesn't.

I finally realized that the problem was xmms. YES!!! I guess it has to do with the fact that bmp is a fork of xmms. I realised this after typing 
```
beep-media-player --help
```
at the console ...
There is an option that says :
```
-n, --session          Select BMP/XMMS session (Default: 0)
```
... So I simply shut down xmms, typed beep-media-player at the console and there it was!!!!
And it does display the track titles!

PS: It is really amazing that **every time** I tried to start bmp in the past, xmms was running so it failed to start!
PS: Now I need a "edge-like" skin to match my desktop!

---

