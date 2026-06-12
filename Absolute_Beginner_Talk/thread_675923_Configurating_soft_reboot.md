---
title: "Configurating soft reboot"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by Kirunux on 2008-01-23
Hello all,

i have an empty ***/proc/sys/kernel/ctrl-alt-del***, so that a reboot by CTRL-ALT-DEL doesn't work. I do now want to configure the machine to go into a soft reboot by CTRL-ALT-DEL, but I did not succeed so far. 

When I type in the terminal

**sudo echo "0" > /proc/sys/kernel/ctrl-alt-del**

I get the message

**bash: /proc/sys/kernel/ctrl-alt-del: Permission denied**

What am I doing wrong?

Thanks in advance!:)

---

### Post by caravel on 2008-01-23
I believe that the action that Ctrl-Alt-Del perfroms is defined in /etc/inittab

---

### Post by Kirunux on 2008-01-23
> **caravel said:**
> I believe that the action that Ctrl-Alt-Del perfroms is defined in /etc/inittab

in /etc/inittab I found:

# What to do when CTRL-ALT-DEL is pressed.
ca:12345:ctrlaltdel:/sbin/shutdown -t1 -a -r now

When holding down CTRL-ALT-DEL I am asked what I want to do (log-off, shutdown completely or reboot). For an automatic soft reboot i have to change the file to:

[B]# What to do when CTRL-ALT-DEL is pressed.
ca:12345:ctrlaltdel:/sbin/shutdown -r now[/B]

??

---

### Post by capink on 2008-01-23
> **Kirunux said:**
> Hello all,

i have an empty ***/proc/sys/kernel/ctrl-alt-del***, so that a reboot by CTRL-ALT-DEL doesn't work. I do now want to configure the machine to go into a soft reboot by CTRL-ALT-DEL, but I did not succeed so far. 

When I type in the terminal

**sudo echo "0" > /proc/sys/kernel/ctrl-alt-del**

I get the message

**bash: /proc/sys/kernel/ctrl-alt-del: Permission denied**

What am I doing wrong?

Thanks in advance!:)

Try modifying this to:

```
echo "0" | sudo tee -a /proc/sys/kernel/ctrl-alt-del
```

Also Ubuntu is using upstart now instead of init. The file inittab is there only for backward compatibility. It is replaced with a direcotry /etc/event.d where you will find a file called control-alt-delete.

---

