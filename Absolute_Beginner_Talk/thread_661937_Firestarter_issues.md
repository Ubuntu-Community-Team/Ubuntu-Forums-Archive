---
title: "Firestarter issues"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by sparelaptop on 2008-01-08
Greetings,
I have a query regarding Firestarter. After a while (varies from 5 mins - 30 mins) Firestarter stops working with is error.

```

***MEMORY-ERROR***: firestarter[6360]: GSlice: assertion failed: sinfo->n_allocated > 0
Aborted (core dumped)

```

What can I do to stop fix this? And also is a firewall actually needed anyway?
I am previously a Windows user so i always had a firewall installed even though I don't ever recall an intrusion. I connect through a Linksys router that has security settings enable.

I did a quick search for explanation but did'nt find it yet.

Thanks.

---

### Post by vikram on 2008-01-08
firestarter is just the program that configures iptables. You dont need to have it running to enable a firewall. you can also configure iptables manually

[https://help.ubuntu.com/community/IptablesHowTo?highlight=%28iptables%29]("https://help.ubuntu.com/community/IptablesHowTo?highlight=%28iptables%29")

I would recommend a firewall. Personally I use a simple manual script.

---

### Post by vikram on 2008-01-08
FYI my script is based on 

[http://users.piuha.net/martti/comp/ubuntu/en/install.html#11](http://users.piuha.net/martti/comp/ubuntu/en/install.html#11)

---

### Post by sparelaptop on 2008-01-08
Thank you Vikram.
So I do not really need to worry about it then. I am very new to linux/ubuntu so I will not be using manual scripts I do not understand just yet. I am relieved nothing is wrong.

---

### Post by julian67 on 2008-01-08
I've noticed that sometimes the Firestarter GUI crashes, but it doesn't matter too much as the rules you set are still being applied. And anyway it's better to run Firestarter in the background and just start up the GUI when you want to check/change something. There's a very good howto on doing this [here]("http://ubuntuforums.org/showthread.php?t=542756").

But if your router is set up right you can live without a firewall on your PC without worrying.  For regular desktop use behind a router I wouldn't run Firestarter or enable any iptables rules unless I was using the desktop PC to be the gatewayu for another  LAN needing NAT, DHCP, DNS etc, it's just duplicating the firewall on the router.

---

