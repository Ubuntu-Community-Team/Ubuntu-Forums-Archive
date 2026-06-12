---
title: "using command: sudo apt-get install build-essential"
date: 2005-11-06
forum: Absolute Beginner Talk
---

### Post by racermike1967 on 2005-11-06
when I typed sudo apt-get install build-essential  into the terminal window, it tells me to install my hoary CD which I don't have with me.  Usually when I type in "sudo apt-get xxxxx I never got this request.  Why is it doing this now?  How can I fix this?

---

### Post by Copter on 2005-11-06
hi!

it happens like this because apt database thinks that the newest version of build-eddential package is on the cd. try```
sudo apt-get update
```to update this database from the internet. than run sudo apt-get install build-essential again. if it doesnt work again open this file```
sudo nano /etc/apt/sources.list
```and comment the line that says something about 'cdrom'. than update database again and run again sudo apt-get install build-essential

hope it helps :)

copter :]

---

