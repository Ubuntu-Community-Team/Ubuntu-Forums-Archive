---
title: "Permission Denied"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by btaylor101 on 2007-06-16
I am just trying to send the output of my iptables-save file to a txt file that can be used during startup.

This is what I did:
[B]
touch /etc/iptables_up_rules

sudo iptables-save > /etc/iptables_up_rules[/B]

I receive the error:
**-bash: /etc/iptables_up_rules: Permission denied**

I know this is something small that I am missing, but need some help.

---

### Post by trak87 on 2007-06-16
One thing is you need "sudo" before the touch command:

```
sudo touch /etc/iptables_up_rules
```

But I'm not sure that will solve the problem.

---

### Post by btaylor101 on 2007-06-16
Sorry left that off. I did have sudo before the touch command. It shows the file as being owned by root, so I'm not sure why the sudo command will not work. I am able to use sudo on other commands just not this one.

---

### Post by meborc on 2007-06-16
you can try ```
sudo -i
```then enter your password... now you are root... be sure to type exit after entering the command that needs root...

---

### Post by btaylor101 on 2007-06-16
That worked. I appreciate the assistance. Does anyone know what that commands requires me to be signed on directly as root?

---

