---
title: "Update broke Frostwire"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by MarvinZurcher on 2007-04-15
Frostwire loads and closes before you can do anything after the last update.

---

### Post by digital_sabotage on 2007-04-15
if you go to synaptic package manager ...sun-java6-jre and sun-java6-bin should be available in the repositories ...if not then go to "settings ...repositories ...internet updates" and enable backports ...reload and do a search for java6 and you should then be able to install it ...if it's still not showing there go to terminal and do > sudo gedit /etc/apt/sources.list at the end of that text file add...
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
...go back to synaptic package manager and then java 6 should be available. I personally uninstalled java 5 first ...don't know if it matters.

after you have java 6 installed go back to terminal and type...> 
 sudo update-alternatives --config java
...this will list all java virtual machines installed and allow you to choose the default ...java 6 of course

worked for me when xgl/beryl wouldn't allow frostwire to open  ...hope this helps

---

### Post by mad chey on 2007-04-15
> **digital_sabotage said:**
> if you go to synaptic package manager ...sun-java6-jre and sun-java6-bin should be available in the repositories ...if not then go to "settings ...repositories ...internet updates" and enable backports ...reload and do a search for java6 and you should then be able to install it ...if it's still not showing there go to terminal and do  at the end of that text file add...

...go back to synaptic package manager and then java 6 should be available. I personally uninstalled java 5 first ...don't know if it matters.

after you have java 6 installed go back to terminal and type...
...this will list all java virtual machines installed and allow you to choose the default ...java 6 of course

worked for me when xgl/beryl wouldn't allow frostwire to open  ...hope this helps

you are wonderful, we now have frostwire working lurvely thanks

---

### Post by microsoft92sucks on 2007-04-15
Thank u very much thats been making mad 4 awhile but it works now

---

### Post by kingrattus on 2007-04-15
> **digital_sabotage said:**
> if you go to synaptic package manager ...sun-java6-jre and sun-java6-bin should be available in the repositories ...if not then go to "settings ...repositories ...internet updates" and enable backports ...reload and do a search for java6 and you should then be able to install it ...if it's still not showing there go to terminal and do  at the end of that text file add...

...go back to synaptic package manager and then java 6 should be available. I personally uninstalled java 5 first ...don't know if it matters.

after you have java 6 installed go back to terminal and type...
...this will list all java virtual machines installed and allow you to choose the default ...java 6 of course

worked for me when xgl/beryl wouldn't allow frostwire to open  ...hope this helps

*does a happy dance*
I've been having nothing but issues with frostwire for months, so I updated it today & it was even worse... Followed your steps & it works perfectly!!   

Thanks :D

---

### Post by Gyrotwister on 2007-04-22
Thankyou digital_sabotage,  

Selecting Java 6 as default fixed it!

---

### Post by jso2897 on 2007-04-22
Same here. When first installed in a fresh 6.10 inst., wouldn't even start. Installed java 6, no more problem.:)

---

### Post by digital_sabotage on 2007-04-24
cool:-)  ...glad i could help

---

### Post by ricardovich on 2007-05-18
```
sudo update-alternatives --config java
```
This fixed Frostwire for me after I installed Eclipse, which appears to have caused java-gcj to become default.
:)

---

### Post by PMatt on 2007-05-20
> **digital_sabotage said:**
> if you go to synaptic package manager ...sun-java6-jre and sun-java6-bin should be available in the repositories ...if not then go to "settings ...repositories ...internet updates" and enable backports ...reload and do a search for java6 and you should then be able to install it ...if it's still not showing there go to terminal and do  at the end of that text file add...

...go back to synaptic package manager and then java 6 should be available. I personally uninstalled java 5 first ...don't know if it matters.

after you have java 6 installed go back to terminal and type...
...this will list all java virtual machines installed and allow you to choose the default ...java 6 of course

worked for me when xgl/beryl wouldn't allow frostwire to open  ...hope this helps

I know this was posted awhile ago, but I got to say this. You da man!

---

