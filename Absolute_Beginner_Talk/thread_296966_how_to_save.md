---
title: "how to save"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by holsv1 on 2006-11-10
Hi I am new with ubuntu, and I have just editing something in /etc/network/interfaces on my ubuntu server, but how du I save it?

---

### Post by Bachstelze on 2006-11-10
You need to edit it with *sudo*, i.e.

```
sudo vim /etc/network/interfaces
```

But is there a reason why you don't want to use the network-admin GUI ?

---

### Post by taurus on 2006-11-10
What text editor did you use?  Since you are running a server, I assume you use nano and with nano, just hold down <Ctrl> while pressing x.  When it asks you if you want to exit, hit y and hit the return key to save it to the original name, unless you want to name it something else...

---

### Post by taurus on 2006-11-10
> **HymnToLife said:**
> 
But is there a reason why you don't want to use the network-admin GUI ?
Because he is running server version!!!

---

### Post by Bachstelze on 2006-11-10
You, sir, have a point here :D I guess I should read threads more carefully...

---

### Post by holsv1 on 2006-11-10
> **taurus said:**
> What text editor did you use?  Since you are running a server, I assume you use nano and with nano, just hold down <Ctrl> while pressing x.  When it asks you if you want to exit, hit y and hit the return key to save it to the original name, unless you want to name it something else...

[http://www.howtoforge.com/perfect_setup_ubuntu_6.10_p3](http://www.howtoforge.com/perfect_setup_ubuntu_6.10_p3)

here u can see what I did but when I have writen the comand: vi /etc/network/interfaces   ,and editing static ip, I cant save :confused:

---

### Post by taurus on 2006-11-10
```
sudo vi /etc/network/interfaces
```

---

### Post by holsv1 on 2006-11-10
thx for the replays, I think I figured it out now :-D

---

### Post by taurus on 2006-11-10
Remember, if you need to modify anything outside your $HOME, you need to run it with sudo command...

---

### Post by holsv1 on 2006-11-10
do u know wich buton I have to press to save?

---

### Post by Bachstelze on 2006-11-10
In vi(m), press Esc to exit the insertion mode and ZZ to save. I recomend using nano though, vi(m) can be a pain in the *** if you're not used to it.

---

