---
title: "Samba Doesnt Dance With Vista"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by thefreepatriot on 2008-03-31
I am able to get my vista machine to browse my shared folder on my Ubuntu machine.. however I have not been able to browse the vista machine from ubuntu... I have ubuntu 7.10..ntfs is installed and I created a user and pass in samba.. any suggestions?

Sorry, couldn't display all the contents of "Windows Network: olgasales-pc".

---

### Post by dark_harmonics on 2008-03-31
Can you connect to the vista machine from another vista or xp computer? You need to check for a file/printer sharing exception in you firewall, your local security policy, and of course username with access rights. I've only done some very rudimentary experimentation with vista file sharing and so i dont know if i can offer much more than that. It seems to be more difficult (the added security features) to connect to than XP or server 2003

---

### Post by thefreepatriot on 2008-03-31
Before ubuntu I had win2k3 enterprise.. and it worked fine until one of the startup files got corrupted...and i said f it.. im tired of windows and now i am happy I made the switch... I know this issue must be on the vista side of the machine.. I changed the securicty protocal to Ntlm not the Nltm v2 which helped allot (now i can browse ubuntu from vista) but I still cant browse vista from the Linux machine..i hope the next version of Ubuntu fixes these issues..

---

### Post by rkd on 2008-03-31
Have you looked in the event log on the Vista system and in the syslog and Samba log on the Ubuntu system to see whether there are any messages from around the time of the attempted access that would shed any light on the reason for the failure?

---

### Post by thefreepatriot on 2008-03-31
Nope good idea :)

---

