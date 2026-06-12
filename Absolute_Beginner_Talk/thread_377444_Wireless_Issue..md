---
title: "Wireless Issue."
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by Zerocf on 2007-03-06
Hey there! I'm a total newbie in the Ubuntu world, i've just installed the 6.10 version of Ubuntu on my Dell LapTop, evertything is OK except for my Wireless Card [Intel/Pro Wireless 2200BG] it's dead. I was reading the "begginer posts" and read something about "Mepis" but i have no idea, does anyone know if I can get drivers or something? LAN is very important on a PC! Thanks a lot! I'd appreciate information about drivers, "Mepis ¿Distro?" or something to fix this problem! Thanks in advance.

---

### Post by youthforlinux on 2007-03-06
try this link that I googled:
[http://www.student.dtu.dk/~s971652/ipw2200.shtml]("http://www.student.dtu.dk/~s971652/ipw2200.shtml")

---

### Post by Zerocf on 2007-03-07
First of all, thanks for answering, i was reading the page and noticed that you have to install "linux headers" i was "googling" searching for those things but i didn't find anything! So has anyone idea where can i get them? Also with de "Acer HotKey Driver" because the page that everyone is pointing at is offline, so i wasn't able to get those drivers!

Thanks in advance.

---

### Post by maniacmusician on 2007-03-07
the linux headers that you want depend on what architecture you're running. use this command to find out:
> uname -r

if it ends in "-386", you install those headers like "sudo apt-get install linux-headers-386"

if it ends in "-generic", you install "sudo apt-get install linux-headers-generic"

And so on, for whatever variant it is.

---

