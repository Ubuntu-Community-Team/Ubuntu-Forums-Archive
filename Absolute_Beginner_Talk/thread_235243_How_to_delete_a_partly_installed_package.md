---
title: "How to delete a partly installed package?"
date: 2006-08-12
forum: Absolute Beginner Talk
---

### Post by brandits on 2006-08-12
I was trying to install Java-3d, a package by the name "lg3d-java3d". The installation stalled for a moment and then the computer restarted. Now I am getting an error message that reads: 

'Unknown error: 'exceptions.SystemError' (E:The package lg3d-java3d needs to be reinstalled, but I can't find an archive for it.)'

I have already tried reinstalling twice, but still I seem to get this message when I restart. How do I get rid of this error? and/or Just delete the partly installed package? 

If someone would help me with this it would be great, I don't seem to be able to install anything else unless the package manager is free. 

Thank you.

---

### Post by John.Michael.Kane on 2006-08-12
If you can open synaptic it should notify you of broken packages,and allow you to remove them. if not then this should remove all problematic packages automaticaly

```
sudo apt-get -f remove
```

---

### Post by brandits on 2006-08-12
> **SD-Plissken said:**
> If you can open synaptic it should notify you of broken packages,and allow you to remove them. if not then this should remove all problematic packages automaticaly

```
sudo apt-get -f remove
```
Thanks for the code. It's asking me to run 'dpkg --configure -a' command with super use previledges. What does super user mean? I don't remember setting up a super user or anything during installation?

---

### Post by brandits on 2006-08-12
Another thing I am getting another error when I open synaptic package-

E: The package lg3d-java3d needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

and the list is all blank so, how do I remove broken packages?

---

### Post by John.Michael.Kane on 2006-08-13
lg3d-java3d should have been removed when you ran the code. 

**This should remove all problematic packages automaticaly :**
```
sudo aptitude -f remove
```

**This should configure all packages that are unconfigured :**
```
sudo dpkg --configure -a
```

**Also can you post your sources.list **
```
sudo gedit /etc/apt/sources.list
```

---

### Post by brandits on 2006-08-17
Thanks for the help. I am still stuck with the same error. I don't know what I say when it asks me...are you root?

---

### Post by Pawka on 2006-08-21
If someone still interested, I've got the same problem with jedit. To slove this, you need open /var/lib/dpkg/status file:

**sudo gedit /var/lib/dpkg/status**

then search your broken package name (for me was jedit, for you - Java-3d), and delete that section (few lines). Thats all!

---

### Post by Brownedwg89 on 2006-08-21
for your questions about superuser/root read this :[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by brandits on 2006-08-22
Hi Pawka,

I just finished editing the satus file. The package manager is still giving me the error. Do I have to restart the computer?

---

### Post by Pawka on 2006-08-23
Hmm you don't need restart :-/ Maybe try update apt list:

**sudo apt-get update**

How is it now?

---

