---
title: "Firestarter and multiple network cards."
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by wormser on 2007-12-24
I connect with my wired connection (eth0) and some times with my wireless card (eth1) on my laptop.  When it boots up and uses a different connection Firestarter says firewall stopped.  I am able to manually start it with the wizard by selecting the other connection.  Basically the problem is the firewall does not appear to be running when I switch connections.

---

### Post by mbmonk on 2007-12-24
When you make changes to your network configuration in Firestarter I THINK you have to restart your network  service to have those changes take affect. 

you can either reboot or do: ```
sudo /etc/init.d/network restart
```

I only use Firestarter for internet connection sharing, but I figured I would take a shot at helping you.

Good Luck

---

### Post by wormser on 2007-12-24
> **mbmonk said:**
> When you make changes to your network configuration in Firestarter I THINK you have to restart your network  service to have those changes take affect. 

you can either reboot or do: ```
sudo /etc/init.d/network restart
```

I only use Firestarter for internet connection sharing, but I figured I would take a shot at helping you.

Good Luck

I am not using connection sharing.  I connect to the internet wired and sometimes wireless.  Firestarter says the firewall is off when I boot and connect with the different connection.  Firestart or iptables should recognize which connection is in use and protect that one.

---

### Post by jerremy-tamlin on 2008-04-02
I have the same problem on my laptop. I don't run the wizard again, I just have to change the settings under preference -> Network Settings.

Did you ever find the solution?

---

### Post by wormser on 2008-04-03
Not yet.

---

