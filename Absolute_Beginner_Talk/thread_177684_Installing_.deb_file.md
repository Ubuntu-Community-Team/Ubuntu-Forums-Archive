---
title: "Installing .deb file"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by sumone on 2006-05-16
Hi

I'm new to Ubuntu and like the distro very much. I have downloaded gnucash, which |I have used before with Mepis. It is a .deb file. I opened a terminal and used su, the password I tried is my login password but I am getting an authorisation failure. i don't remember settng another password during install.

Thanks in advance

DJ

---

### Post by aysiu on 2006-05-16
You don't need to download GnuCash separately.

[Make sure you have extra repositories enabled](http://www.psychocats.net/ubuntu/sources), then paste these two commands into a terminal: ```
sudo apt-get update
sudo apt-get install gnucash
```

[http://www.monkeyblog.org/ubuntu/installing.html](http://www.monkeyblog.org/ubuntu/installing.html)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by NoUse on 2006-05-16
First of all, root is disabled in Ubuntu:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Second, Gnucash is installable via Synaptic. You just need to enable to universe repository:
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

Synaptic documentation:
[https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)

---

