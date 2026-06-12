---
title: "Gnome Schedular"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by eldredm75 on 2007-08-21
Hi there 

I have created a bashrc file that simply reboots the computer. I want to schedule to execute that file once a day. What is the line of code that will exec the file as a superuser using GNome Schedular. 

Many thanks 
Eldred:)

---

### Post by Skrynesaver on 2007-08-21
I'm slightly confused by your post, but if you wish to run a script on a daily basis at a specific time you can either
1. run crontab -e as root (sudo su -) and add the following line substituting the full path to your script for <scriptname>
```

0 3 * * * <scriptname>

```
2. use gnome-schedule to add this line, this is easily done in the advanced tab, however if the default user can't shutdown the computer this will not work.

---

