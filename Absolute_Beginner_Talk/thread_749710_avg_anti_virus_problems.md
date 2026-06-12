---
title: "avg anti virus problems"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by Falc7 on 2008-04-08
1. I have installed avg for linux, but when i try to update it says i don't have permission. What can i do?

2. Also, i scanned anyway, it found a virus, and it didn't give me an option to delete, how can i do this? I still have the log of the scan avaliable, so i could navigate to the folder, which is actually the IE for linux folder (small lol), but there must be a quicker way?

3. Is there a way to scan my windows area of the hard drive through a virus scanner in linux, I heard F-Prot could do it, could anyone confirm or deny? 

4. ClamAV says i must be root to update signatures, how can i be root temporarily to do this?


New update: I was reading around and it said do this:
Now when you try & update you will probably get 'cannot download avgupdate.ctf'

Go into System/administration/users & groups
Click on 'manage groups' button
Scroll right down the list to find the 'avg' group & click on it then properties button
Put a tick next to your user name.
OK/Close your way out
now LOG OUT AND BACK IN AGAIN

5. However, after doing that avg disappeared from my applications list, i tried unticking the box but it did not reappear. I tried clicking on the installer again, it says i still have avg installed though. How can i bring avg icon back?

---

### Post by pseudo-random on 2008-04-08
Out of interest was this 'virus' on your windows partition or was it linux?
If so what was it?

---

### Post by Falc7 on 2008-04-09
It was in the temporary files of IE for Linux, harmless i'm sure

---

### Post by Tomatz on 2008-04-09
AVG creates a seperate user account. You need to logout then login as (username) **avg** then type **avg** into a terminal and press **return** . Then update and log back into your account.

Cak i know ;)

---

### Post by Falc7 on 2008-04-09
What password should i use? It didn't accept my normal one

How can i bring avg back to my applications menu?

---

### Post by snkiz on 2008-04-09
If your sure you need to log in as avg them you need to give avg a password (Doesn't sound right to me bug I don't know to argue.) Then i I don't recomend using the gdm log in, as that would create an entire desktop enviroment. instead use the command su -l avg Then do your update command

---

### Post by SOULRiDER on 2008-04-09
Why dont you just delete your temporary IE for Linux files? Besides, even if the virus is there, it CANNOT affect you since it cant even be executed.

---

### Post by Tomatz on 2008-04-09
> **Falc7 said:**
> What password should i use? It didn't accept my normal one

How can i bring avg back to my applications menu?

No password if i remember correctly. You just leave it blank ;)

To add a menu entry just r-click on the applications button then click edit menus. The rest is easy just add a new item then add avg to the command field fill the rest out as you like.

---

### Post by Falc7 on 2008-04-15
Unfortunately it said the username password combination was incorrect, still can't update avg

---

### Post by Tomatz on 2008-04-15
> **Falc7 said:**
> Unfortunately it said the username password combination was incorrect, still can't update avg

Even with a blank password???

Strange! Try sending avg an email thats all i can suggest ;)

---

