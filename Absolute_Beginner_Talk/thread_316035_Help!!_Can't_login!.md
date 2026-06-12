---
title: "Help!! Can't login!"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by aridus on 2006-12-10
Help! Please! I have been using Ubuntu 6.1 happily for several months on a Dell laptop dual boot windows/ubuntu. Today I can't log in to Ubuntu. I enter my username and pwd but it goes into a loop, so it seems, and asks me for it again. Tried to login with different session types, but the same happens. If I use in an invalid username it recognizes it as such, but won't let me login with my real username and pwd. All my work is on the ubuntu partitiion of course... Is there a way I can still login by editing the grub menu somehow? I would be *extremely* grateful for help with this! Thanks, Martin Fisher

---

### Post by slimer on 2006-12-10
Try to login in to text mode (Ctr+F1)

---

### Post by aridus on 2006-12-10
Thanks - but at which point do I use Ctr-F1?

---

### Post by r4ik on 2006-12-10
Try,

Ctrl Alt F1  at the startup screen

passwd mustangsallydd
(assuming mustandsallydd is your username...)
<new password>
<retype the new password>
shutdown -r now

and try agian.

Good luck !

---

### Post by aridus on 2006-12-10
ok - thanks - using this I can now login and i have a text screen saying:
martin@ubuntu:~$
waiting for me to type something. 
I am not familar with the commands. How can I now start a gnome session (i.e. try to get back to normal)? 
(I know I'm going to value this experience once I have it all sorted!)

---

### Post by r4ik on 2006-12-10
Try,

Ctrl Alt F7 or F8

to get back to the GUI and try to log in.

---

### Post by aridus on 2006-12-10
ok many thanks - i can get back in now... i think the problem may be that i am v short on disk space

---

### Post by r4ik on 2006-12-10
Glad it worked.
Free diskspace is another ballgame.
I suggest you open a new thread on that one.
I got to go for now have a nice day !

---

