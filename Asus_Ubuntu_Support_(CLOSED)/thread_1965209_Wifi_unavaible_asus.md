---
title: "Wifi unavaible asus"
date: 2012-04-25
forum: Asus Ubuntu Support (CLOSED)
---

### Post by stuya1 on 2012-04-25
First note i'm a complete newbie .
I recently installed ubuntu on my asus laptop and i cant connect to anuthing wireless. There are no additional drivers installed. I actually looked up this problem but they do not work. I dont know what to show you know so post the commands i need to do.
I BEGGG YOU FOR HELP!!!! Please

---

### Post by TBABill on 2012-04-25
Can you open a terminal, run a few commands and paste their output here so we can begin to understand what hardware you have and what drivers are running? ```
lsmod
lspci | grep Network
sudo lshw -C
```

---

### Post by stuya1 on 2012-05-03
Nvm i installed the drivers manually sorry for the inconvinience

---

### Post by linuxmatt7 on 2012-05-06
What version of Ubuntu, Kubuntu, Xubuntu, Lubuntu, or Ubuntu Studio are you running. If you are running anything before 11.04 you will have to configure your wireless manually. Ubuntu 11.04 and up comes pre-configured. This is what happened to a friend I have.

---

### Post by JoeRacette on 2012-05-06
> **linuxmatt7 said:**
> What version of Ubuntu, Kubuntu, Xubuntu, Lubuntu, or Ubuntu Studio are you running. If you are running anything before 11.04 you will have to configure your wireless manually. Ubuntu 11.04 and up comes pre-configured. This is what happened to a friend I have.
I have just upgraded to 12.04 from 11.04 on my eeePC 1000HA.  11.04 worked fine every time.  12.04 connects for a second (I get a successful connection message) then disconnects and asks for the key.  Connecting to a Netgear WNR3500 which I have rebooted since the problem occurred.  Any ideas?

---

