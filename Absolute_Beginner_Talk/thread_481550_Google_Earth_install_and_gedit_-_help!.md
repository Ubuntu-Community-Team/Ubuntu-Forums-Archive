---
title: "Google Earth install and gedit - help!"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by overandunder on 2007-06-22
Hi

Just tried to install Google Earth via Firefox and when opening the downloaded file get gedit window opening with this error;

Could not open the file /home/rpc/GoogleEarthLinux

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

Character coding Current Locale UTF-8

Any ideas most appreciated.

---

### Post by christhemonkey on 2007-06-22
You need to run the program not view it.

The way that comes to mind is to go to a terminal and type:
```
cd home/rpc/
chmod +x ./GoogleEarthLinux
./GoogleEarthLinux
```

---

### Post by overandunder on 2007-06-22
Ooops!

Thanks for that. I changed the file permissions (chmod) and now sorted.

Thanks again

---

### Post by christhemonkey on 2007-06-22
No worries.
Post back if you have any problems.

---

