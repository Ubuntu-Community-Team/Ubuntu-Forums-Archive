---
title: "How to Upgrading Feisty -NOOB"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by Radu43 on 2007-07-15
Hi,
i have not used ubuntu in a while and now i want to upgrade it to 7.04.
I'm currently on 6.10.
Update manger is telling me the system is up to date, with no upgrade option. What am i missing.
Thank you.

---

### Post by Arwen on 2007-07-15
[Take a look]("http://www.google.gr/search?hl=el&q=how-to+upgrade+ubuntu+6.10+to+7.04&btnG=%CE%91%CE%BD%CE%B1%CE%B6%CE%AE%CF%84%CE%B7%CF%83%CE%B7+Google&meta=") :-)

---

### Post by schorsch on 2007-07-15
Have you already tried:
```
sudo update-manager -c
```

---

### Post by Jimmyfj on 2007-07-15
My advice will be to got to Ubuntu.com and download the 7.04 iso-file - Make a Live Cd and install from scratch. This usually gives the best result.

Else open a terminal and run

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

This will require that you have a high speed Internet connection.

---

