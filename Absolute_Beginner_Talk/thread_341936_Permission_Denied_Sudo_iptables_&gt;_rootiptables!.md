---
title: "Permission Denied: Sudo iptables &gt; /root/iptables!!!"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by MindRiot on 2007-01-19
I entered a series of valid arguments using the iptables command in **Fluxbuntu**. 

For example:

```
sudo iptables -A FORWARD -i ppp0 -m state --state NEW,INVALID -j DROP

```

Anyways, when I enter "sudo iptables-save > /root/iptables" I get "Bash: Permission Denied."

Anyone know what I need to do to save the iptable so I don't have to type a series of rules for my firewall everytime I start Fluxbuntu.  I haven't tried this in Xubuntu or Ubuntu, but I don't see how that would make any difference.

---

### Post by x64Jimbo on 2007-01-19
Have you thought about using an iptables program like firestarter to manage your firewall?

---

### Post by taurus on 2007-01-19
```
sudo iptables-save > sudo /root/iptables
-or-
sudo cp iptables-save /root/iptables
```

---

### Post by mysticmarks on 2007-01-19
im a bit riskier than most, but i like power! make sure you set your root password to something you can use. Then ctrl+alt+f1 to terminal and login as root. cd / ,then do a   chown * *   this eliminated most of these ridiculous problems with ubuntu configuration. Yea, it not secure(whatever), but if its just you, so what! and if you manage users and set yourself as a member of root, you should be able to do almost anything with out the time consuming feedback because of permissions. Simple, quick, done.:-D

---

### Post by x64Jimbo on 2007-01-20
> **mysticmarks said:**
> im a bit riskier than most, but i like power! make sure you set your root password to something you can use. Then ctrl+alt+f1 to terminal and login as root. cd / ,then do a   chown * *   this eliminated most of these ridiculous problems with ubuntu configuration. Yea, it not secure(whatever), but if its just you, so what! and if you manage users and set yourself as a member of root, you should be able to do almost anything with out the time consuming feedback because of permissions. Simple, quick, done.:-D
Don't do this. Linux is only more secure than windows because of its  implementation of super user and limited user accounts. Take that away, and you're right back in Win95. As Spiderman's uncle said, "With great power comes great responsibility." Only use root under the extremely rare circumstance that what you're trying to do cannot be done without root credentials.

---

