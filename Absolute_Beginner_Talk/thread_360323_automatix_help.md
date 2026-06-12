---
title: "automatix help"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by The55Gon on 2007-02-13
ive been trying to get my wireless connection working for a while. I read somewhere that i should get ndiswrapper and network manager through automatix. however, when trying to install them, automatix gives the errors

fatal error: ndiswrapper
an apt-based error occured and installation was unsuccessful

fatal error: network manager
an apt-based error has occured and installation was unsuccessful

what should i dooooo

---

### Post by sunexplodes on 2007-02-13
> **The55Gon said:**
> ive been trying to get my wireless connection working for a while. I read somewhere that i should get ndiswrapper and network manager through automatix. however, when trying to install them, automatix gives the errors

fatal error: ndiswrapper
an apt-based error occured and installation was unsuccessful

fatal error: network manager
an apt-based error has occured and installation was unsuccessful

what should i dooooo

Well, i'm not too sure about how to fix automatix, but you can get both of those applications through apt-get or synaptic package manager.

---

### Post by jackrobinson on 2007-02-13
> **The55Gon said:**
> ive been trying to get my wireless connection working for a while. I read somewhere that i should get ndiswrapper and network manager through automatix. however, when trying to install them, automatix gives the errors

fatal error: ndiswrapper
an apt-based error occured and installation was unsuccessful

fatal error: network manager
an apt-based error has occured and installation was unsuccessful

what should i dooooo
apt is broken because of which automatix spits those errors:
paste the result of the following commands:
```
sudo apt-get update
sudo apt-get upgrade
```

You can also try the automatix forums for high quality support:
[http://www.getautomatix.com/forum](http://www.getautomatix.com/forum)

---

