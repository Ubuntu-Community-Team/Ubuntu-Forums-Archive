---
title: "In reference to 'root'...?"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by phantalon on 2007-12-01
........I'm a novice to linux, and not all that well versed in computer speak,  I'm running Gutsy and I have Discovered that I am NOT 'root'...Can I change this, and if so, How? I've just given up on microsoft and now that there is something else I wish To Move In This Direction...any help would be appreciated...thanks.

---

### Post by werewolfzx8 on 2007-12-01
> **phantalon said:**
> ........I'm a novice to linux, and not all that well versed in computer speak,  I'm running Gutsy and I have Discovered that I am NOT 'root'...Can I change this, and if so, How? I've just given up on microsoft and now that there is something else I wish To Move In This Direction...any help would be appreciated...thanks.

For the most part, you do SHOULDN'T be root. Any commands that requires you to be root, you should put sudo before them, which allows you to run commands as the "super user does".

---

### Post by davidc502 on 2007-12-01
Any particular reason why you want to run as root? As a user you may install/uninstall software, copy and delete most files. Unless you really need to be root or in Ubuntu's case Super-User, I don't recommend you get into the habit of switching users. Over time of running as root you will find the only way you can get things done is to run as root because of all the past changes you made as "root".  Hard to explain, but it's a snowball affect unless you are really Linux savvy and know exactly what you are doing. 

Example: I'm a 4 year Linux user who no longer runs as root unless needed. I've learned the pitfalls of root. lol

Davidc502

---

### Post by JillSwift on 2007-12-01
For abvout every instance you need to use root, you instead use an admin account (the first account the installer helps you create will be an admin account) and the command "[sudo]("https://help.ubuntu.com/community/RootSudo")". (**S**uper **U**ser **DO**) The command asks for your admin account password, and then executes the rest of the line as the super user, for instance:
```
sudo apt-get install esound
```
This lets you do rooty things without actually logging in to root.

---

### Post by Dr Small on 2007-12-01
Please read more about RootSudo from the WIki:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

