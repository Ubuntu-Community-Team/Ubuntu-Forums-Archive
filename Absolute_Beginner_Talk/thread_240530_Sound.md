---
title: "Sound"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by pitviper on 2006-08-21
Hello i have a problem in ubuntu my sound works but it just makes a sound over and over.I have tried everything i could think of HELP.
:D

---

### Post by seshomaru samma on 2006-08-21
Can you describe your problem in more details?
What do you mean by it makes a sound over and over?
For example can you get sound when playing the Ubuntu video in your home file?

---

### Post by pitviper on 2006-08-21
No i get just one sound and it's hell to listen i tried to change the driver but makes no diff it just does not see my sound card at all.
my sound card is on board and it reads it wrong it say's it is a via 82 but it's a via 686 driver.

---

### Post by seshomaru samma on 2006-08-22
can you post the output to :
> lspci
and
```
cat /etc/asound.conf
```

---

### Post by deadgobby on 2006-08-22
If you want to stop the loop open up the terminal and type

killall esd

Gobby

---

