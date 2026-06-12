---
title: "Help upgrading to Feisty please (update manager won't work)"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by Narcoleptic_Insomniac on 2007-04-25
Hi, I tried updating to 7.04 through the update manager and about 2 hours into the installation a window came up saying it had a bunch of errors and couldn't retrieve this and that with a long list of repositories, or they looked like repositories anyway.

Anyway, whats the terminal way of upgrading. I'm thinking I just open the sources.list and change all things that say edgy to feisty but I just want to check with you guys first, and how do I get my sources.list opened? Is it sudo apt-get gedit /etc/apt/sources.list? I forget. 

Thanks a million in advance.

---

### Post by Sef on 2007-04-25
> how do I get my sources.list opened? Is it sudo apt-get gedit /etc/apt/sources.list? 

Almost that.  The correct code is ```
gksudo gedit /etc/apt/sources.list
```.

---

### Post by kpkeerthi on 2007-04-25
gksudo gedit /etc/apt/sources.list. Good luck with your upgrade.

---

### Post by Narcoleptic_Insomniac on 2007-04-25
So I was right about chaning all things Edgy to Feisty?

---

### Post by Narcoleptic_Insomniac on 2007-04-25
Hey c'mon guys I really don't want to screw up my computer here. Do I just change all things in sources.list that say Edgy to Feisty or do I do anything else?

---

### Post by Narcoleptic_Insomniac on 2007-04-25
Please someone help me. I dont want to break my computer.

---

### Post by Narcoleptic_Insomniac on 2007-04-25
Ok really... theres like how many people on this board? Is it really that hard for one person to say I'm right or wrong and what I do after I change all things in sources.list from edgy to feist?

---

### Post by Sef on 2007-04-25
Have some patience please.   Yes you can change your sources list from Edgy to Feisty and that will upgrade your system.  

**Back up** your data first.   Then download the alternate cd or the Live cd or both.    Often the upgrade works just fine.  However, sometimes, there can be problems upgrading - sometimes minor, somtimes major.

---

### Post by zvacet on 2007-04-26
Comment (put # sign in front of line) all unofficial repos you have in your source list.Your Edgy have to be up-to-date to perform upgrade.

```
sudo aptitude update
```

Try upgrade again.
For changing source list
```
  sudo sed -e 's/\sedgy/ feisty/g' -i /etc/apt/sources.list 
```

---

