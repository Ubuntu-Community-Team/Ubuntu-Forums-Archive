---
title: "I'm stuck!"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by benner on 2006-11-09
i upgraded dapper to edgy and ran into what looks like a common problem with people that have ATI video cards.  i can't get beyond the login screen.  i get a blank screen that flickers and then it goes back to the login screen.  i haven't been able to sort it out so far...  i can only log in to recovery mode and use command lines.  i'm not very good a using command lines.
     today, after 5 days, i assumed that there was a fix available by now.  i logged in to the recovery mode and tried 'apt-get upgrade' and then more specifically, 'apt-get upgrade xserver-xorg- in both cases, i got "you don't have enough free space in /var/cache/apt/archives/'"  and I have no idea what to do.  i can't log in with a graphical interface and i need to come on this forum every time to get someone to tell me the command lines to do even the simplest tasks.  i gotta learn this stuff.  in the meantime, i need to get back onto my machine.
please help me out...

thanks in advance,

-benner

---

### Post by taurus on 2006-11-09
Looks like you are running low on space in your /var!  Therefore, you need to remove those files in /var/cache/apt/archives/ since they are just taking up space on your harddrive.  And don't worry, if you ever need them again, synaptic/apt-get/aptitude will download them from the net again.  Then, you need to reconfigure your X again.  From the recovery mode, do

```
rm -rf /var/cache/apt/archives/*
dpkg-reconfigure xserver-xorg
```

---

### Post by benner on 2006-11-09
i used your commands (what does the little asterisk mean, by the way?) and went through the reconfiguring process with the xserver-xorg.  i didn't knw the answers to most of the questions so i just kind of clicked my way through it.  i got back to where i started and rebooted...

it worked!  thanks a bundle

---

### Post by benner on 2006-11-09
new problem.  i can't download any updates through apt-get adept or synaptic.  i get a message that /var/cache/apt/archives/partial is missing.  how do i get that back?

---

### Post by darrenm on 2006-11-09
```
sudo mkdir /var/cache/apt/archives/partial
```
I always accidentally do that too,

---

### Post by benner on 2006-11-09
problem solved.  cheers!

---

