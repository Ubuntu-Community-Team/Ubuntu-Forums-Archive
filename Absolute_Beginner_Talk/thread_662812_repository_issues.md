---
title: "repository issues"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by Crylos on 2008-01-09
Hey! I'm a Linux noob and I think I might have screwed up. While updating Wine to the latest version, I followed some advice and changed the repository address (I think...). Now, every time I try to install new system updates or try to install some packages from Synaptic, I'm not able to install them all. After doing "sudo apt-get update", an error message appears: 
[PHP]W: GPG error: http://wine.budgetdedicated.com gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263 [/PHP]
I've read similar threads but they didn't help much since I really didn't fully understand them. What can I do to revert back to how it was before? Thanks in advance!

---

### Post by FuturePilot on 2008-01-09
It's really  just a harmless warning. All it means is that you don't have a gpg key for that repo. By adding a key you are saying that you trust this repo. Here's the key for that Wine repo.
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```
Then run
```
sudo apt-get update
```

---

### Post by luisito on 2008-01-09
Open a console and run this command:
wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

This should solve it.

---

### Post by Crylos on 2008-01-09
Thank you both. It's working now.

---

