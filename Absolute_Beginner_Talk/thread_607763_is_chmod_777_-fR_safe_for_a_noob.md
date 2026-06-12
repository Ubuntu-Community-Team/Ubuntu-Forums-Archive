---
title: "is chmod 777 -fR safe for a noob"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by afeasfaerw23231233 on 2007-11-09
i am new to linux. so whenever i encounter a read / write / execute permission i would sudo chmod 777 -fR to that folder or file. and the problem get solved. i would like to know if i do this oftenly [maybe 90% of my system is already 777] will my system get hacked and all my data losts? i am connecting the internet via my home router. i know there is a firewall call firestarted in the package. but i think it is too troublesome to set rules. will my ubuntubox become a windows box[unless there's no virus]? any idea?

---

### Post by beercz on 2007-11-09
> **afeasfaerw23231233 said:**
> i am new to linux. so whenever i encounter a read / write / execute permission i would sudo chmod 777 -fR to that folder or file. and the problem get solved. i would like to know if i do this oftenly [maybe 90% of my system is already 777] will my system get hacked and all my data losts? i am connecting the internet via my home router. i know there is a firewall call firestarted in the package. but i think it is too troublesome to set rules. will my ubuntubox become a windows box[unless there's no virus]? any idea?
I think you may need to learn about file permissions.  Does this link help?

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Dr Small on 2007-11-09
> **afeasfaerw23231233 said:**
> i am new to linux. so whenever i encounter a read / write / execute permission i would sudo chmod 777 -fR to that folder or file. and the problem get solved. i would like to know if i do this oftenly [maybe 90% of my system is already 777] will my system get hacked and all my data losts? i am connecting the internet via my home router. i know there is a firewall call firestarted in the package. but i think it is too troublesome to set rules. will my ubuntubox become a windows box[unless there's no virus]? any idea?
Firestarter is rather simple to setup rules and policies in it.
If you have all incoming ports blocked off for applications such as HTTP or SSH, then you should be pretty good to go, although you could potentially be hijacked from your browser by some script.

So, it would be safe to install Extentions such as NoScript and AdBlock to keep malicious scripts from ruining your system.

Dr Small

---

### Post by mikewhatever on 2007-11-09
> **afeasfaerw23231233 said:**
> i am new to linux. so whenever i encounter a read / write / execute permission i would sudo chmod 777 -fR to that folder or file. and the problem get solved. i would like to know if i do this oftenly [maybe 90% of my system is already 777] will my system get hacked and all my data losts? i am connecting the internet via my home router. i know there is a firewall call firestarted in the package. but i think it is too troublesome to set rules. will my ubuntubox become a windows box[unless there's no virus]? any idea?

What a dumb thing to do. From the standpoint of file permissions, your system is no longer protected, since you have allowed anyone full permissions. A firewall can protect you, but if it is penetrated, your system is wide open.

---

### Post by OoooMatron on 2007-11-09
it's not recommended to do that.

if i am lazy and it's not an important directory i often make myself the owner.

sudo chown -R yourname:yourname folder/

is probably a bit safer than 777 the whole system.

---

### Post by beercz on 2007-11-09
> **mikewhatever said:**
> What a dumb thing to do.
Steady on!! There is no need for insults.  The OP is new to linux, and has simply made a mistake.  We all learn through our mistakes.  We were all new at one time or other.

I think I would recommend that the OP backs up his/her data somehow and reinstalls Ubuntu and then restores his/her data.

---

### Post by mikewhatever on 2007-11-09
Insult? :-s I don't think so. While learning through mistakes is common, and sometimes there is no choice, it is not the only way. One could read 'man chmod' page for example, in fact, that's what I had to do to verify what chmod 777 -fR does, because I have not yet used chmod once.

---

### Post by chamberlain2006 on 2007-11-09
Probably the reason that you are doing this is to edit files, is it not?  If that is the case, then the best way to be able to edit them is: 
```

gksudo gedit filename

```
That will give temporary read/write access to a file, provided you have a password.  The reason that chmod 777 is unsafe is because that anyone that had access could edit any crucial file they wanted, potentially screwing your system, without knowing the password.  Next chance you get that it would make sense to do a fresh install, I would reccomend doing so to clean up the file permissions.

---

### Post by TadH on 2007-11-09
omg safe for a noob NO WAY! seriously are you trying to brick your computer??

---

### Post by chamberlain2006 on 2007-11-09
Give them a break.  Clearly they didn't understand the danger, which is why they were asking.  So unless you have something helpful to say, please lay off.

---

