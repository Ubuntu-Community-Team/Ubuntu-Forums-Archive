---
title: "If I'm not root, THEN WHO IS!??!"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by knottshawk on 2008-04-18
I installed ubuntu yesterday. I made the account name my personal name. Well now I'm trying to install synCE and it's telling me to modify /etc/apt/sources.list

Problem is that when I do that it says I don't have permission because I'm not root. So.... since I installed this. WHO IS ROOT???? 

I need help please....

---

### Post by Vadi on 2008-04-18
It's the admin account.

To be able to modify stuff as root, put either "gksudo" or "sudo" in front of it and you'll be ok.

Edit: You shouldn't need to tinker with sources.list manually. Just go to System - Administration - Software Sources, click on the Third-party tab, click 'add', and add the lines (usually they start with "deb") they need. Much nicer!

---

### Post by MasterSushi on 2008-04-18
root is a username actually called 'root'. The username you are using is the first non-root user created. You can always use the sudo command in the terminal to run something as root. It will prompt you for the password you choose when you installed Ubuntu. I hope this helps.

---

### Post by jeffus_il on 2008-04-18
"root" is the administrator account in Linux. In Ubuntu, you generally don't log in as root, but use the "sudo" command before the command you want to run in the privileged mode. e.g.:
```
sudo gedit myfile
```

---

### Post by knottshawk on 2008-04-18
So can I not actually log in as root?

---

### Post by Jammy4041 on 2008-04-18
Not at the login screen. T o do so, type sudo (super user (aka administartor) do)

---

### Post by ACMarina on 2008-04-18
You technically can log in as root, and there are plenty of resources out there to tell you how to do so, but it's not generally a wise idea..

If you log in as root, you stand to mess up a whole lot more.  If you're only issuing commands as a super user (sudo), you can only mess up one thing at a time.  If you log in as root, you can do a lot more damage without realizing it..

To "act" as root in order to edit your sources file, you just type "sudo" before your edit line..

It would look something like this, for most users (IIRC)

sudo gedit /etc/apt/sources.list

---

### Post by Vadi on 2008-04-18
Here are the re-written instructions for that section:

"Go to System - Administration - Software Sources, click on the Third-Party Software tab, then 'Add...', and paste this line in:

deb [http://ppa.launchpad.net/synce/ubuntu](http://ppa.launchpad.net/synce/ubuntu) gutsy main


Click 'Add...' once more and add this line:

deb-src [http://ppa.launchpad.net/synce/ubuntu](http://ppa.launchpad.net/synce/ubuntu) gutsy main


Then click 'Close' and 'Reload'".

---

### Post by knottshawk on 2008-04-18
Thanks guys.... great info. I'll give it a whirl.... hopefully I can get my wifes phone to sync up

---

### Post by bodhi.zazen on 2008-04-18
For information on root / sudo :

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by jeffus_il on 2008-04-19
By the way...
sudo is a great solution to the Windows administrator user problem. Most Windows users run as an administrator category of user. I believe that this is the main problem for the rapid spread of viruses on Windows, as the virus also runs with administrative privileges and can "administrate" away to it's hearts desire. Not a pleasant situation. 

sudo runs only programs you explicitly run with root privileges, making Ubuntu alot safer. 
So don't be easily tempted to login as root, type those extra four letters "sudo" and be safe!

---

### Post by bodhi.zazen on 2008-04-19
Yes, that is part of the problem and certainly part of "hardening" Windows.

There are may other problems though including the number of servers listening on various ports.

In a nut shell, IMO, security and ease of use are a balance -- and perhaps Windows went too far. That is a matter of opinion as there are plenty of people who seem very happy with windows and find linux security or permissions "too hard".

---

