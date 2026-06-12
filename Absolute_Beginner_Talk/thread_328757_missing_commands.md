---
title: "missing commands"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by rcschroeder on 2006-12-31
Hi,

I hae been using other versions of linux / unix and have become used to shell commands like 'll' and 'whodo'. Are these and other shell commands available to be installed on ubuntu?

If so how would one install them?

Thanks,

RCS

---

### Post by bruenig on 2006-12-31
I am thinking that perhaps these are aliases that were default on your distro but maybe I am wrong, could you explain what those do.

---

### Post by IYY on 2006-12-31
ll is just an alias to 'ls -l'. To set it up, edit the file ~/.bashrc and uncomment the line

```
alias ll='ls -l'
```

(if it's not there at all, just add it)

---

### Post by port on 2007-01-21
Hi, 

I just got Ubuntu 6.06 LTS installed and while I am trying to configure my wireless card while following guides, i am missing commands like: iface and pre-up.

for example one guide says to do:

auto wlan0
iface wlan0 inet dhcp
wireless-essid   MYNETWOTK
wireless-key     FEFEFEFEFE
wireless-channel 11
wireless-mode    managed

But when i do iface wlan0 inet dhcp i get the following:
bash:iface: command not found

Am i missing a package or something ?

---

### Post by taurus on 2007-01-21
I think /sbin is not in your path!  Edit ~/.bashrc with

```
gedit ~/.bashrc
```
and add these two lines to it.

```
PATH=$PATH:/sbin
export PATH
```
Save it and then source it with

```
source ~/.bashrc
```
Now, try that command again and see what happens.

```
ifup wlan0 inet dhcp
```

---

### Post by Bachstelze on 2007-01-21
These are not commands but text you need to put in the network interfaces config file. Press Alt+F2 for the "Run command" dialog ant type this :

```
gksudo gedit /etc/network/interfaces
```

then copy/paste here what opens in your text editor.

---

### Post by port on 2007-01-21
Got it. Thans!

---

