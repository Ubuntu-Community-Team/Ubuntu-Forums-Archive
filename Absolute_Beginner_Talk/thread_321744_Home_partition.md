---
title: "Home partition"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by drito on 2006-12-19
I was trying to make a separate Home partition following [http://psychocats.net/ubuntu/separatehome]("http://psychocats.net/ubuntu/separatehome")
I mean, I booted from a LiveCD and typed in Terminal: 

 ```
sudo aptitude update && sudo aptitude install gparted 
```

but I am getting error messages: 

```
Temporary failure resolving archive ubuntu.com.
```

---

### Post by Kobalt on 2006-12-19
How do you connect to the Internet usually ? You need to enable your internet connection in the LiveCD session or allow Synaptic to use the Ubuntu CDrom as a source : go into Synaptic package manager > Categories > Repos and add the CDrom.

---

### Post by ThrobbingBrain66 on 2006-12-19
> **drito said:**
> I was trying to make a separate Home partition following [http://psychocats.net/ubuntu/separatehome]("http://psychocats.net/ubuntu/separatehome")
I mean, I booted from a LiveCD and typed in Terminal: 

 ```
sudo aptitude update && sudo aptitude install gparted 
```

but I am getting error messages: 

```
Temporary failure resolving archive ubuntu.com.
```

I thought that gparted was already included on the live CD.  You may want to check System -> Administration to see if it's already there

---

### Post by drito on 2006-12-19
> **Kobalt said:**
> How do you connect to the Internet usually ? You need to enable your internet connection in the LiveCD session or allow Synaptic to use the Ubuntu CDrom as a source : go into Synaptic package manager > Categories > Repos and add the CDrom.

Of course! Mea culpa. I set the network connection and everything worked. Thanks a lot.

---

