---
title: "Installing amarok"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by sailingboarder on 2006-11-03
i am trying to install amarok, and i followed the directions on their website for how to install on kubuntu(i'm running ubuntu dapper), but got the following error:
The following packages have unmet dependencies:
  amarok: Depends: libvisual-0.4-0 (>= 0.4.0) but it is not installable
E: Broken packages

any ideas?

---

### Post by Marsolin on 2006-11-03
You need to enable the dapper-backports repository. Make a copy of the dapper line in your /etc/apt/sources.list file and replace dapper with dapper-backports. Don't forget to run "sudo apt-get update" next.

---

### Post by sailingboarder on 2006-11-03
*  wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)
    * sudo -s
    * apt-key add kubuntu-packages-jriddell-key.gpg
    * echo "deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main" >> /etc/apt/sources.list
    * apt-get update
    * apt-get install amarok amarok-engines 

that is wut i did
on the final command, i got the error
wut else do i have 2 do 2 enable dapper-backports?

---

### Post by Bachstelze on 2006-11-03
What if you just run *apt-get install amarok* ? Same error ? If so, do this :

```
sudo nano /etc/apt/sources.list
```

Search for any line with "backports" in it and uncomment it (remove the #). Than save your file (Ctrl+O, Return), exit nano (Ctrl+X) and run

```
sudo apt-get update && sudo apt-get install amarok
```

---

