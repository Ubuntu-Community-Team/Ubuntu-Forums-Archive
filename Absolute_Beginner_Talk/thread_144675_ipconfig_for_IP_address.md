---
title: "ipconfig for IP address"
date: 2006-03-14
forum: Absolute Beginner Talk
---

### Post by raghus on 2006-03-14
I set up Ubuntu server and gave my server a name called raghu01. It can connect to the internet as well as the intranet. However to get other machines to connect to this Ubuntu box I need it's IP address at the minimum? I am unable to get it - ipconfig is not recognized, even when I log in as root and go to the directory where ipconfig is present.

Please help

---

### Post by mlind on 2006-03-14
try ifconfig

---

### Post by jjf on 2006-03-14
ifconfig

go figure ;)

---

### Post by raghus on 2006-03-14
Ok! That worked. Thanks guys. So what is ifconfig as different from ipconfig?

---

### Post by mlind on 2006-03-14
ipconfig is a windows command. linux has ifconfig.

---

### Post by raghus on 2006-03-14
Ok, thanks for the explanation

---

### Post by mlind on 2006-03-15
no problem. "apropos" command is very useful when you want to find commands
or other resources related to some functionality. for example, typing [I]apropos
network[/I] on a  terminal will show you bunch if different networking utilities and
their explanations.

when you find a command / script that could suit your needs, this case ifconfig,
you can get all sorts of useful information using

*man ifconfig* or *ifconfig --help*
these are usually applicable to all unix/linux commands.

---

### Post by MiniJames on 2006-03-16
So can you release and renew IP addresses with Ifconfig? I really need this :) Just fixed my network to a new subnet and I need to change lappy to the new subnet to get it back on the internet.

Thanks in advance

---

### Post by Brunellus on 2006-03-16
[QUOTE=MiniJames]So can you release and renew IP addresses with Ifconfig? I really need this :) Just fixed my network to a new subnet and I need to change lappy to the new subnet to get it back on the internet.

Thanks in advance[/QUOTE]
sudo dhclient eth0

will do that for the first ethernet device on your machine.

---

### Post by mlind on 2006-03-16
you can do

```

sudo /etc/init.d/networking restart

```

---

