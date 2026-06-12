---
title: "Set proxy in evolution..?"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by kramer65 on 2007-01-30
Hello,

I want to setup a proxy for my evolution. I read in the manual that when you go to Edit >> Preferences >> Edit account and then click on the Proxy tab you can set it. However, With me I only see these tabs: Identity, Receiving Email, Receiving Options, Sending Email, Defaults, and Security. But there it ends and there is no proxy tab...

Does anybody know why not? And how I can get the tab back or set proxy settings otherwise?

---

### Post by kramer65 on 2007-01-30
Nobody has a clue? Does anybody then maybe know where else I can ask this question or get more information? Any link? Something?
[edit]
Ok, I just found out that I need an echange or groupwise account to use a proxy. But does anybody know how I can get that? I cannot find anything about it?

---

### Post by aliennet on 2007-03-27
Hi, 
   same problem. It appears as evolution doesn't have this feature...it's crazy I know.
The solution is in using tsocks (sudo apt-get install tsocks) and launch tsocks evolution.
The configuration of tsocks is "quite" easy...just edit the file /etc/tsocks.conf
Hope it could help

---

### Post by c_cammann on 2007-12-18
Feisty has global proxy settings.
Try
system --> Preferences --> Network Proxy --> (your configuration) go to Details to enter username or password.

Evolution should get the settings automatically.

---

