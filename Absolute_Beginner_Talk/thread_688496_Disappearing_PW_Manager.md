---
title: "Disappearing PW Manager"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by Over the hill on 2008-02-05
Hello, I am using Ubuntu 7.10 and after a bit of a struggle all my installed programmes are running fine apart from PW Manager. I installed it using Synaptic Package Manager and the programme icon appeared under Applications- Accessories. When I clicked onto it, the GUI 
appeared, although rather slowly.  
I put a few passwords into it and saved the file under a master password. Since then I have been unable to find the programme again, although the icon is still there under applications- accessories. 
If I type in SUDO PWMANAGER as a command line, I get the following reply :-

geoff@geoff-desktop:~$ sudo pwmanager
[sudo] password for geoff:
PwManager INFO: already running.
geoff@geoff-desktop:~$ 

Has anyone got any suggestions?

---

### Post by %hMa@?b&lt;C on 2008-02-05
try killing it with "killall pwmanager" then restarting it

---

### Post by Over the hill on 2008-02-05
Thank you very much jeffc313, I tried killall pwmanager and I could then get the programme to start straight away. When I close the programme , I need to use the command line again, but that is a good step forward.

---

