---
title: "GPG Decrypt"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by Frak on 2006-10-05
How do you decrypt a GPG file, I got something that for me is life or death, but I don't know how to use this freakin thing.
I have the key, I just can't decrypt.
(Stupid Prompt)
(GUI was made for a reason)

---

### Post by Jussi Kukkonen on 2006-10-06
*man gpg* helps.

Assuming the public key is in your keyring, try
```
gpg --decrypt <file>
```

If you are still interested in a GUI, run
> apt-cache search gpg
that'll list all gpg related packages, among them are several GUIs.

---

