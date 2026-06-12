---
title: "Root User...what is it?"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by kelinu on 2008-02-27
Hi,
I've been hearing a lot of people mentioning a root user...What is this?
Thanks (I'm curious LOL)

---

### Post by Crooksey on 2008-02-27
The super user on a *NIX system, with full permisions todo anything they want.

---

### Post by philinux on 2008-02-27
Have a read here.

[http://www.psychocats.net/ubuntu/security#limiteduser](http://www.psychocats.net/ubuntu/security#limiteduser)

---

### Post by pedro_orange on 2008-02-27
Wikipedia is your friend.

[http://en.wikipedia.org/wiki/Superuser](http://en.wikipedia.org/wiki/Superuser)

---

### Post by Junglizer on 2008-02-27
The best way to look at root is to compare it to the Administrator account on a windows based system. However, it is a bit more far reaching. What I'm trying to say is that its more of a "no-holds-barred" account. You can tell the system to delete itself, and if you are logged in as root it will. This is why most will tell new linux users to not log in as root, but simply make a seperate user account. Logging in as root is not a bad thing, its just not recommended, especially for users that may not know what commands are doing when they enter them. So, long story short, if you create a seperate user account for yourself, you're less likely to mess something up.

---

### Post by kelinu on 2008-02-27
so then how would u log in to root?

---

### Post by meindian523 on 2008-02-27
It's not required in the Debian and RedHat families because of sudo and su methods of executing programs with superuser privileges respectively.Small differences are still present in that su makes you a super-user till you logout while sudo only runs that particular executable with super-user privileges.But sudo can give you complete control via an argument -i.

---

### Post by Junglizer on 2008-02-27
either
```
 su - 
```
or 
```
 su 
```

In the terminal/command line, the first will launch a seperate session for you as root, the second, gives root permissions to your current user.

---

### Post by pedro_orange on 2008-02-27
Or if you just want to run one command as root you do

```
sudo <command> <arguments>
```

---

### Post by kelinu on 2008-02-27
ok guys thanks but u think its best for me not to go into this stuff? is it risky?

---

### Post by pedro_orange on 2008-02-27
You need to be in root user when you do anything effecting the system.

ie. Installing programs and updating ubuntu etc.

It's not risky, just run commands you are sure will not screw your machine up. Or use the tools built into Ubuntu like Synaptic / Update manager when you can, you should be fine

---

