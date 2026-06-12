---
title: "How do I install this .run file?"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-03-29
How do I install this [COLOR=Blue].run[/COLOR] file inside terminal? What are the commands. I have the file on my desktop. Thank you for the help.
kh

ati-driver-installer-8.35.5-x86.x86_64.run

---

### Post by bodhi.zazen on 2007-03-29
> **kittyhawk63 said:**
> How do I install this [COLOR=Blue].run[/COLOR] file inside terminal? What are the commands. I have the file on my desktop. Thank you for the help.
kh

ati-driver-installer-8.35.5-x86.x86_64.run

```
cd ~/Desktop
mkdir -p ~/src/ati
mv ati* ~/src/ati
cd ~/src/ati
chmod a+x ati-driver-installer-8.35.5-x86.x86_64.run
sudo ./ati-driver-installer-8.35.5-x86.x86_64.run
```

Note: this will move the script off you desktop and save it for later (if needed) in ~/src/ati

(~ = /home/user_name)

Use tab completion to satve on typing

Type ati-<tab> :)

---

### Post by kittyhawk63 on 2007-03-29
> **bodhi.zazen said:**
> ```
cd ~/Desktop
mkdir -p ~/src/ati
mv ati* ~/src/ati
cd ~/src/ati
chmod a+x ati-driver-installer-8.35.5-x86.x86_64.run
sudo ./ati-driver-installer-8.35.5-x86.x86_64.run
```Note: this will move the script off you desktop and save it for later (if needed) in ~/src/ati

(~ = /home/user_name)

Use tab completion to satve on typing

Type ati-<tab> :)

Thanks alot.
kh

---

### Post by kittyhawk63 on 2007-03-29
After I installed the driver, the program asked me to save X window configuration and then run aticong. What does this mean?
kh

---

