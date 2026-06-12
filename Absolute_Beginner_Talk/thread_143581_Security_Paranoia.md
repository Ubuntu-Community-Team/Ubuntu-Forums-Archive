---
title: "Security Paranoia"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by yoshtodd on 2006-03-12
Hello,

       I'm completely new to Linux and made the switch to turn this machine into a file backup server for my Dad who's on Windows. I got it all set up with Samba and all that is working fine but I'm just worried about security. Right now the only programs I've learned how to use for security are Firestarter and running chkrootkit. Earlier today while I was using Bittorrent, Firestarter caught a service called Gatecrasher on port 6969 which is supposedly a virus. It stopped when I closed Bittorrent but it makes me kinda worried.

      I plan to leave the computer running to serve as a backup for him but I really don't want someone coming in and getting access to all his data. Any advice for a total newbie? On windows I felt secure by loading up on anti virus/spyware programs but from what I read Linux is supposedly even better than that. Just need some proactive things to put my mind at ease that his data won't be compromised.

Thanks in advance,
Todd

---

### Post by eqisow on 2006-03-12
I assume you also have a hardware firewall (if you use a router, you do). To be honest, that's really all you need. I gues you can also keep Firestarter if it makes you feel safer. If you're really really paranoid you can get Aegis virus scanner. Just type 'sudo apt-get install aegis-virus-scanner' in the terminal.

But, like I said, I personally woulnd't worry about anything more than a hardware firewall... and keep ssh disabled if you don't use it, but I believe Ubuntu comes this way by default.

Edit: To further aid your comforte you I thought you would like to know that there have been like a dozen Linux viruses in the wild. These are all pretty much obsoleted now unless you're running an ancient Linux system.

---

### Post by Robgould on 2006-03-12
This is a post from another forum, but it should hlp you:

[http://forums.fedoraforum.org/showthread.php?t=52270](http://forums.fedoraforum.org/showthread.php?t=52270)

---

### Post by yoshtodd on 2006-03-12
I appreciate the responses thank you. I am behind a router so that's good to know.

---

