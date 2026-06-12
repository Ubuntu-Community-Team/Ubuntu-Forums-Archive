---
title: "Root access"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by rj7402 on 2006-07-31
I just installed Ubuntu for the first time and would like root access to set up the machine without usind sudo.  Can I do that?

---

### Post by NewbieNik on 2006-07-31
Yes, but you leave your system in an unsecure state. Programs running as you will need root access to install so it stops viruses and scripts corrupting the PC. Logging in as root opens that up for attack. sudo-ing is safer, but if you type

sudo passwd root

you can set hte root password

then run

su

to use root in the terminal.

On your own head though!!!

---

### Post by T700 on 2006-07-31
Please take a look at the "Where's Root?" link in my sig before you do this.  There are good reasons for the way Ubuntu does root.

Paul

---

### Post by gagne on 2006-07-31
You could also do sudo bash, which let only that term will be root and when you close the term or exit out you no longer root. I use this when I know I am going to do alot of commands lines in a term.

---

### Post by gagne on 2006-07-31
You could also do sudo bash, which let only that term will be root and when you close the term or exit out you no longer root. I use this when I know I am going to do alot of commands lines in a term.

---

### Post by aysiu on 2006-07-31
```
sudo -s
```

---

