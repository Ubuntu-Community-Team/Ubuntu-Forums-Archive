---
title: "[HELP] X Server Failure"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by styfer on 2006-12-01
ok i am absolutely new to linux
i can boot my ubuntu 6.06 from the CD-ROM but when it get to X Server, i got a failure message similar to the one in this thread
[http://ubuntuforums.org/showthread.php?t=310863](http://ubuntuforums.org/showthread.php?t=310863)

my computer spec is included in my signiture
I tried the command
[PHP]sudo dpkg-reconfigure xserver-org[/PHP]
pressing enter thruout all prompts since i dun really understand whats going on.. it come back to a black screen afterwards (similar to command prompt in windows) what do i do next?

THanks!

---

### Post by agustin.g on 2006-12-01
type your username, password, and then 
```
sudo shutdown -r now
```
which is basically rebooting the system...

If it doesn't work, please write what error messages the X server gave you

---

### Post by styfer on 2006-12-02
what do u mean type username/password?
i am at this prompt
> ubuntu@ubuntu$
how do i imput my username and password?

---

### Post by agustin.g on 2006-12-02
oh, sorry... 

there you're logged in as root, if i may use the expression. All you have to do now is type the reboot command, without the "sudo" (or you could try "reboot", i'm not too sure)

---

### Post by styfer on 2006-12-02
actually if i reboot, everything will be the same again
i am trying to install ubuntu now, how do i get back to installation in this 'command prompt' after i reconfigure this xserver thing?

---

### Post by agustin.g on 2006-12-02
sorry, i had failed to notice you were talking about the live-cd. (Final tip, if your motherboard has an integrated graphics chip (even though i don't think so), make sure your monitor is connected to the integrated graphics)

Well actually i don't think it's possible to do a text-based install from a Live-CD, if your time and bandwidth permit it, i would suggest to download the "Alternate Install CD", which allows you to install the operating system without having to start the X server.

---

### Post by styfer on 2006-12-02
thanks **agustin.g** for your help and suggestion!
lol i dun even know i am using the live CD in the first place! so i guess its my fault for not telling actually..
i juz ordered this CD thru shipit so din know what is it all about..
Thanks and i will try the Alternative Install CD instead



btw, the reason y i cant use this live-cd is becos of my graphics card?

---

