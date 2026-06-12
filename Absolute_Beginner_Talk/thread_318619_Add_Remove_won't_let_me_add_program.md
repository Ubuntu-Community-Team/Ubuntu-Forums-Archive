---
title: "Add Remove won't let me add program"
date: 2006-12-14
forum: Absolute Beginner Talk
---

### Post by danieltowsey on 2006-12-14
Hi..I am new to all this. I just installed Ubuntu 6.06 LTS with duel boot XP..I don't know how to to do scripts. I went to the add remove and tried to install things..it sasy Sudo won't let me install..now after rebooting  I just went looking for Add Remove and I can't find it..Can you helps me? I also can not find users..

---

### Post by Sef on 2006-12-14
> I also can not find users.

Users should be under System > Administration > Users and Groups

---

### Post by Kobalt on 2006-12-14
The system is asking you for the 'root' password, you should have specified it during your installation...

---

### Post by danieltowsey on 2006-12-14
Its not there! Why is it not there?

---

### Post by taurus on 2006-12-14
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
groups
```

---

### Post by danieltowsey on 2006-12-14
Heres what is says    daniel fax tape

---

### Post by taurus on 2006-12-14
What about 

```
cat /etc/group
```

---

### Post by danieltowsey on 2006-12-14
It came back with a whole list of things..I tried to post it and it says I can't post more than 8 things

---

### Post by danieltowsey on 2006-12-14
> **Kobalt said:**
> The system is asking you for the 'root' password, you should have specified it during your installation...
You lost me..I am not shure what your answering to

---

### Post by taurus on 2006-12-14
Basically you need to add yourself, daniel, to both adm & admin in /etc/group!  So, boot into recovery mode from GRUB menu and at the prompt, add daniel (which is your username) to the end of both adm & admin in /etc/group...

```
nano -Bw /etc/group
```
Save it with <Ctrl>x and reboot.

```
shutdown -r now
```
Now, log in with your username and password and see what happens if you run these two commands from a terminal.

```
sudo aptitude update
sudo aptitude upgrade
(use the same password that you use to log in...)
```

---

