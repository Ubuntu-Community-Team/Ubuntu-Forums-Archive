---
title: "Source?"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by JasonBourneLinux on 2007-10-19
hey,

how do you add the following source?

Add the following line in /etc/apt/sources.list

deb [http://elisa.fluendo.com/packages](http://elisa.fluendo.com/packages) gutsy main

thanks

sorry im nOOb

---

### Post by Maestro23 on 2007-10-19
In a terminal type:

> gksudo gedit /etc/apt/sources.list

Once the file is open, add your line and save.

Then 

> sudo apt-get update

---

### Post by Hobo Joe on 2007-10-19
Run the command:
```

sudo gedit /etc/apt/sources.list

```

Then just paste the source to the end of the file and save it.

---

### Post by crimesaucer on 2007-10-19
for xubuntu:

```
sudo mousepad /etc/apt/sources.list
```

---

### Post by Dr Small on 2007-10-19
Also, another simpler method:
```
sudo su
echo -e "\n#Fluendo Repository\ndeb http://elisa.fluendo.com/packages gutsy main\n" >> /etc/apt/sources.list
```

That adds the output of echo to the bottom of sources.list


Dr Small

---

