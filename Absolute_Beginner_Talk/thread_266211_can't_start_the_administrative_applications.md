---
title: "can't start the administrative applications"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by jdrott1 on 2006-09-27
cant't start administrative applications. As soon as it starts it disappears.
i've tried these solutions with no luck. my computer doesn't allow me to sudo nano /etc/hosts in recovery mode. my hostname is (none).

this is what message i'm getting:

jonathan@(none):~$ gksudo synaptic
sudo: unable to lookup (none) via gethostbyname()

---

### Post by unisol on 2006-09-27
you cant sudo in recovery mode how about typing: addgroup username admin (in recovery mode) its worth a try

---

### Post by jmartini on 2006-09-27
You don't have a hostname so sudo is failing.  The difficulty is that ubuntu doesn't enable the root account by default so you'll probably need to boot into single user mode to get a root shell.  The following steps should get you a root shell on the box:

[LIST=1]
[*]reboot the machine
[*]Hit <esc> when you see the grub menu
[*]select the kernel you want to boot and press <e> to edit the entry
[*]select the kernel line and select <e> to edit it
[*]append the word "single" to the kernel line
[*]select <b> to boot the box, when it comes up you will have a root shell
[/LIST]

When you have a root shell you can use vi or nano to edit the /etc/hosts and /etc/hostname files to give your box a name. They should end up looking something like this:
```

jmartini@zen:~$ cat /etc/hostname
zen
jmartini@zen:~$ cat /etc/hosts
127.0.0.1 localhost.localdomain localhost zen
```

Reboot the box and you should be good to go.

---

