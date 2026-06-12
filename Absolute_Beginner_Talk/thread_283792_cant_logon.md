---
title: "cant logon"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by bam17au on 2006-10-24
Hi i am new to these i just got a computer with ubuntu on it and i started it up and a logon screen comes up but i dont know the logon name or password can anyone help to get aroound this problem Thanks bam17au

---

### Post by taurus on 2006-10-24
Did you install it yourself or somebody installed Ubuntu and then gave you the machine?

---

### Post by grim918 on 2006-10-24
who did you get the computer from. That person should know the password that they set on the computer.
You could use a live cd and just change some files to give you access. Here is a link that could get you started.[http://www.computing.net/linux/wwwboard/forum/28131.html](http://www.computing.net/linux/wwwboard/forum/28131.html)

you can always reinstall Ubuntu.

---

### Post by taurus on 2006-10-24
You can boot into recovery mode from GRUB and either create a new user or change the password to something you can remember so you can log in.  No need to reinstall unless you want to reinstall!!!

---

### Post by bam17au on 2006-10-25
someone else installed it and i got the machine off them but i dont know the person who installed ubuntu

---

### Post by bam17au on 2006-10-25
> **taurus said:**
> You can boot into recovery mode from GRUB and either create a new user or change the password to something you can remember so you can log in.  No need to reinstall unless you want to reinstall!!!

i don't know how to use grub and i don't have grub

---

### Post by Bachstelze on 2006-10-25
Yes, you do have GRUB even if you don't know it ;) At the first screen when you boot your computer, you should see "Press ESC to show menu", press ESC and tadaaaa, here's GRUB :D Select the "recovery mode" option and after Ubuntu loads, you'll have a command prompt, type *passwd username*, set the new password, voilà :)

P.S. : if you don't know the username, this command will tell you :

```
cat /etc/passwd | grep 1000
```

---

