---
title: "su command won't work"
date: 2007-04-18
forum: Absolute Beginner Talk
---

### Post by Wake Rider on 2007-04-18
I am trying this tutorial [http://linuxcommand.org/wss0050.php](http://linuxcommand.org/wss0050.php) and when I attempt to run the script in the terminal it says permission denied. I try entering sudo before the ./(script_name) but it says the command cannot be found. I then try the su command. It asks for my password, I enter CORRECT password but it keeps bringing up the error message, password couldn't be verified, sorry. After screwing up Ubuntu once by accidentally modifying bin/sh I have a separate folder in my home folder labeled scripts where I run my created scripts from. 

Also does anybody know of any other really good tutorials that I could use to gain further knowledge on the use of the Ubuntu Terminal and also the programming language Python?

---

### Post by Bachstelze on 2007-04-18
You don't use *su* in Ubuntu :

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by anaconda on 2007-04-18
try
sudo su

---

### Post by Perfect Storm on 2007-04-18
> **Wake Rider said:**
> I am trying this tutorial [http://linuxcommand.org/wss0050.php](http://linuxcommand.org/wss0050.php) and when I attempt to run the script in the terminal it says permission denied. I try entering sudo before the ./(script_name) but it says the command cannot be found. I then try the su command. It asks for my password, I enter CORRECT password but it keeps bringing up the error message, password couldn't be verified, sorry. After screwing up Ubuntu once by accidentally modifying bin/sh I have a separate folder in my home folder labeled scripts where I run my created scripts from. 

Also does anybody know of any other really good tutorials that I could use to gain further knowledge on the use of the Ubuntu Terminal and also the programming language Python?

Make sure you made the script executable first.

---

