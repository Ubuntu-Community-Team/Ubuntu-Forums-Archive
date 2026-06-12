---
title: "Claws Mail"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by oldjock on 2007-03-20
I wish to upgrade my Mail program but  it requires the pgp key colin.publickey . I got the key and saved it in Abiword so how do I use it. I have tried seahorse :confused:  which cannot see it nor can sudo apt-key colin.publickey.
I can see the upgrade in synaptic repos but no key what now.

---

### Post by Kobalt on 2007-03-20
The command to add a key is ```
sudo apt-key add *your-key*
```
But you can also do it in GUI going in System > Admin. > Update Sources

---

### Post by oldjock on 2007-03-20
Thank you, I am not sure what I did but after reading how to get the Automatix key I tried that in a console and it seemed successful so I followed your instructions and when I tried synaptic it offered a system upgrade which seemed to work. Trial and error looks the way to go.

Much obliged.
Oldjock

---

### Post by Kobalt on 2007-03-20
> **oldjock said:**
> Trial and error looks the way to go.

Surely.
You're welcome :)

---

