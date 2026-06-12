---
title: "I do not find Device     Manager"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by bender182 on 2008-04-07
Hello, I am a expert in Windows any version, and my mind is set already in windowsw, but i want to learn Ubuntu, or linux, but in windows I have a section call device manager, and i need help in how to find a place or section where i can look all the hardaware at once, (excuse my english) like a device manager in windows, my name is Mario Escobar I lived in Honduras

---

### Post by Orcaporka on 2008-04-07
> **bender182 said:**
> Hello, I am a expert in Windows any version, and my mind is set already in windowsw, but i want to learn Ubuntu, or linux, but in windows I have a section call device manager, and i need help in how to find a place or section where i can look all the hardaware at once, (excuse my english) like a device manager in windows, my name is Mario Escobar I lived in Honduras

Systems>Preferences>Hardware Information.

---

### Post by bender182 on 2008-04-07
In System Preferences, I do not have Hardware information,  I have Sounds, bluetooh etc. but not  hardaware information, I am Using Ubuntu 8.04 beta, there is another way to find hardaware information

---

### Post by mikewhatever on 2008-04-07
> **bender182 said:**
> In System Preferences, I do not have Hardware information,  I have Sounds, bluetooh etc. but not  hardaware information, I am Using Ubuntu 8.04 beta, there is another way to find hardaware information

What hardware info are you looking for? Try <sudo lshw> from Terminal.

---

### Post by louieb on 2008-04-07
> **mikewhatever said:**
> What hardware info are you looking for? Try <sudo lshw> from Terminal.

Or you can make it a little easier to read by sending it to your browse.
```
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html
```Or you can have it come up line by line it in the terminal
```
sudo lshw | more 
```And because it Linux where more is actually less,  you can use your page up, page down, up arrow and down arrow keys.  
```
sudo lshw | less 
```

In either case press** q to quit**.

---

### Post by bender182 on 2008-04-07
Thanks the command  sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html      WORK but is not the same in windows a can change drivers easy,   but at least the information was very very usefull, thanks, i  Have a Tv   Tuner and i want to make it work with linux

---

### Post by mikewhatever on 2008-04-07
> **bender182 said:**
> Thanks the command  sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html      WORK but is not the same in windows a can change drivers easy,   but at least the information was very very usefull, thanks, i  Have a Tv   Tuner and i want to make it work with linux

You are quite right, it's not the same. Why should it be?

---

