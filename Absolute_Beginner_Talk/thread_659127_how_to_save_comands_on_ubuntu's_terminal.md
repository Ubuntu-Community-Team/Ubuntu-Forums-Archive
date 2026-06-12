---
title: "how to save comands on ubuntu's terminal"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by danijela on 2008-01-05
i have created virtual machine that is using ubuntu.
i want to save commands that i wrote in console after shutting down my virtual machine (entering ip addresses and stuff) but i dont know how to do this :(
any help would b welcome
thanx

---

### Post by adityakavoor on 2008-01-05
you can press " ctrl + r " .

It reverse searches your terminal history.

---

### Post by aktiwers on 2008-01-05
It does that for you already.

If you click the "up arrow" key (&#8592;&#8595;&#8594;) it will show the last typed commands.

Or type:
```
history
```

To see all the commands.

---

### Post by danijela on 2008-01-05
yes i know that, but after i power off my virtual machine its all gone.
i ve heard that mount floopy or snapshot can help.

---

### Post by danijela on 2008-01-05
i have to create a boot floppy image and tell VMWare to always boot from that..u know..its not only one command,there r lot of them 
i want to put my commands in that floppy img
hope u understood me :)

---

### Post by aktiwers on 2008-01-05
Do you want specific commands to run on startup?

---

### Post by danijela on 2008-01-05
yes..like i want to give ip addr to my virtual machine and create dns server ...
there r lot of commands for that to type it every time when i start my virt pcs...

---

### Post by Sayers on 2008-01-05
Add the commands to /etc/rc.local before the exit 0

---

### Post by aktiwers on 2008-01-05
```
gksudo /etc/rc.local
```

Just in case ;)

---

### Post by danijela on 2008-01-05
i think i should create script and mount it from floppy..ha?

---

### Post by aktiwers on 2008-01-05
Why?
Adding them to /etc/rc.local will run them automatically without floppy? :)

---

