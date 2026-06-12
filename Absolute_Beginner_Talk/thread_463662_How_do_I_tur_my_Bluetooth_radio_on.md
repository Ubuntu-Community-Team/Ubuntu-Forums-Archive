---
title: "How do I tur my Bluetooth radio on?"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by gohanssjn on 2007-06-03
Ok, here's the deal.  Usually I leave my BT on in Vista and it also stays on in Ubuntu.

But today I turned it off in Vista, is there a way to turn it on in Ubuntu now...because it's off!

I thought a setting like that wouldn't carry between OS's...

---

### Post by Inxsible on 2007-06-03
Have you installed bluetooth packages in Ubuntu ?
If not then do this:
```
sudo aptitude install gnome-bluetooth bluez-utils python-bluez
```
then to start up bluetooth you can either 

go to Applications -- > Accessories --. Bluetooth File Sharing

or enter the following command at the terminal
```
sudo gnome-bluetooth
```

---

### Post by gohanssjn on 2007-06-03
Installed all of that, ran the file.  Nothing :(

---

### Post by Inxsible on 2007-06-03
Do you get a blue triangle with concentric circles around it near the clock on the top panel ?

---

### Post by gohanssjn on 2007-06-03
Yes, but my paired mouse does nothing, and it worked before I turned the radio off in Vista...

---

### Post by Inxsible on 2007-06-03
When you pair a device in an OS, its only a software change. so when you boot into a totally different OS your settings will not remain. you will have to pair the device again in Ubuntu. this will be a one time thing

---

### Post by Inxsible on 2007-06-03
are you saying that it worked before in Ubuntu too ?

---

### Post by gohanssjn on 2007-06-03
Yup.  Worked in Ubuntu.

---

