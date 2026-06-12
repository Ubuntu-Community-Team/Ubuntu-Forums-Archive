---
title: "Need help connecting to internet"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by Shauntp on 2006-11-18
Hi,
    I am a completely new to Ubuntu, so please make things detailed. I use a Motorola SURFboard SB5100 Cable Modem to connect to the internet. It will work using windows xp however not with Ubuntu (Edgy Eft). 

People are saying to download BPALogin through Synaptic Package Manager. The problem is it isin't in my Synaptic Package Manager!
Plz Help!

Shaun

---

### Post by loclei on 2006-11-18
try to search for it
```

apt-cache search BPALogin

```

if you find it that way then you can just 
```

sudo apt-get install BPALogin

```

---

### Post by Shauntp on 2006-11-18
It did nothing for the first code, so I tried the second and it said package not found!

---

### Post by robinl on 2006-11-18
On Edgy it's simply bpalogin (no capitals), try substitute BPAlogin with bpalogin and run the second command.

---

### Post by Shauntp on 2006-11-18
It says and does the exaxt same thing:

Reading package lists... Done
Reading dependancy tree
Reading state information... Done
E: Couldn't find package information!

---

### Post by Shauntp on 2006-11-18
> **Shauntp said:**
> It says and does the exaxt same thing:

Reading package lists... Done
Reading dependancy tree
Reading state information... Done
E: Couldn't find package information!
sorry, where it says package information it's meant to be package bpalogin.

---

### Post by Shauntp on 2006-11-18
Don't worry about it anymore. I decided to install a different operating system more suited to my needs. Thanks for the help though.

---

