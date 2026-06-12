---
title: "after install no xwindow"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by kasnas01 on 2006-07-23
hello all,
it is urgent after I installed ubuntu 6 and rebooting I get to a prompt line, I would like to ask If I missed anything that cause to  be unable to launch the xserver although no errors at the installation time,
I appreciate your direct reply cause it is urgent,
thanks

---

### Post by rowanparker on 2006-07-23
Sounds like you did a server install?
If you did, you need to normal install or run ```
sudo apt-get install ubuntu-desktop
``` from the prompt.

---

### Post by adam.tropics on 2006-07-23
If you had no errors, it sounds like you may have installed the server edition. Assuming you have a connection, you might try 

```
sudo apt-get install ubuntu-desktop
```

---

### Post by kasnas01 on 2006-07-23
I did not configure the network while installing,
but I have the Kubunto CD, Can I install the xserver from it,
regards,

---

### Post by adam.tropics on 2006-07-23
I've never had to do this, but I believe you can put the cd in the drive, then type
```

sudo apt-cdrom add
sudo apt-get update
sudo apt=get install kubuntu-desktop
```


but before all that just check if 
```
startx
``` 
goes anything!

---

