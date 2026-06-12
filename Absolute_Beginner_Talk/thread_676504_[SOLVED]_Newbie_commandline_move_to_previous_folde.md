---
title: "[SOLVED] Newbie commandline move to previous folder"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by ckennow on 2008-01-23
Ok this is really annoying... if i am in /var/www/website/web in commandline how would i easily move to the /var/www/website folder without having to type cd /var/www/website?

---

### Post by drs305 on 2008-01-23
```
cd ..
```

---

### Post by ckennow on 2008-01-23
THANK YOU!!! they should really post that somewhere for people to see cuz that could really get one going

---

### Post by drs305 on 2008-01-23
Here's a bonus tip for going the other way:

You are in /var/www/website/thirtysomethingormore
You "cd .."  to get back to /var/www/website
Now you realize you need to go back to thirtysomethingormore
Type "cd " and then the first letter of the subdirectory. Then press the tab key to autocomplete the entry. If there is more than one subdirectory beginning with 't' you would hit TAB until the correct subdir appears.

---

### Post by ckennow on 2008-01-23
kewl

---

### Post by jaytek13 on 2008-01-23
There are actually quite a few places on the web that discuss 'cd' and it's uses... but just to add some more tips:

typing just 'cd' at the prompt will return you to your home folder

If you are trying to change to a directory that has 2 names (eg. "My Programs") you would use \ to define a literal space. So, cd My\ Programs will change you to that directory, whereas cd My Programs will result in an error

cd .. always returns you to the next top directory of the directory your in. Using cd .. move you up one, so if your in /etc/users using cd .. will take you to /etc... it does not take you to the previous directory. so if you're in /home/user, then you cd to /etc/users, cd .. will still take you to /etc, it will not return you to /home/user

---

