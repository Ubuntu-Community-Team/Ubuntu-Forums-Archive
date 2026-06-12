---
title: "gdm fail"
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by wwbdd on 2005-11-16
While I was out today my brother and father stole my cd drive from my system and upon reboot gdm doesn't work.  I can't get the drive back to make things right again so it looks as if i'm gonna have to solve this problem from the terminal since that is the only thing i can get to now.  I tried /etc/init.d/gdm restart and it stopped it then tried to start again before saying [failed].  I tried stopping and starting with seperate commands and the same thing happend (no surprise).  When i press ctrl alt f7 the moniter says our of range.  Any help would be great

---

### Post by unixnorks on 2005-11-21
try this in terminal (ctrl+alt+F1)...

$apt-get install gdm

make sure you also vi the /apt/sources.list please uncomment some url..
then execute 
$apt-get update
$apt-get upgrade

afterwards just type gdm in terminal

---

