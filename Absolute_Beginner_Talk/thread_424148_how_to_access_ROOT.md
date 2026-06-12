---
title: "how to access ROOT"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by SikEnCide on 2007-04-26
i am to understand Ubuntu creates the root account.. but how can a user access it. i know you can use the "sudo" command but i want direct roote access.    im running feisty

---

### Post by RobsterUK on 2007-04-26
If you really want root access you can do:
sudo su

however this is not recommended. You can run anything that you might want to as root using the sudo command

---

### Post by taurus on 2007-04-26
Is there any reason you need to log in as root?  It's not recommended.  If you need to move or copy something outside your $HOME directory, use sudo or 

<Alt>F2 -> gksudo nautilus

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by steevk on 2007-04-26
As other people have said, why do you need to do this? What you're trying to do can probably be accomplished without logging in as root....

---

### Post by SikEnCide on 2007-04-26
im doing this because i would just like root access im tired of typing sudo

---

### Post by pndragon on 2007-04-26
sudo -i

---

### Post by compmodder26 on 2007-04-26
Again as others have stated, if you want to run commands with root privileges for an extended period of time, just type "sudo su" or "sudo -i".  After you type your password, you will be operating as root.  When you are finished, just type "exit".  You will return back to your normal account.

---

### Post by 51m0n on 2007-04-26
Or

sudo -i

Or even

sudo bash

I get really bored of typing sudo - sorry but if I'm going to be doing some serious under the hood admin I'm a big boy, I know what the risks are, I'll decide when its a good idea to login with root priveleges :)

---

### Post by aysiu on 2007-04-26
Another vote for *sudo -i* or *gksudo nautilus*

---

### Post by compmodder26 on 2007-04-26
If you are still determined to use the traditional method of root access, here are your instructions:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_set.2Fchange.2Fenable_root_user_password](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_set.2Fchange.2Fenable_root_user_password)

---

### Post by Calash on 2007-04-26
I have seen this question a lot the past few days.

The answer on how to do it have already been posted by the fine people here :)


One thing that it took me a while to realize is that the sudo setup is a feature, not a hurdle.  Coming from an XP, then Fedora background I was very use to ether having total Admin access, or having a quick way to get to it (SU ).  Personally, the Sudo idea just felt...wrong at first.

Before you go changing things around, have you spent time using sudo?  Have you put the effort to adjust your methods to it?  Even Vista is going to this type of model (Over done and buggy, but it is there).

The choice is yours, but personally I think it is worth the time to learn how to use it.  Especially if you have more than one system...SSH and Sudo make admin jobs on a remote system a breeze.

---

### Post by aysiu on 2007-04-26
> **Calash said:**
> 
One thing that it took me a while to realize is that the sudo setup is a feature, not a hurdle.   Same here.

---

### Post by SikEnCide on 2007-05-03
i understand all of this and that sudo is powerful.. i just noticed under users it gives root a login name.. and a password you cant change.

---

### Post by 5-HT on 2007-05-03
> **SikEnCide said:**
> i understand all of this and that sudo is powerful.. i just noticed under users it gives root a login name.. and a password you cant change.
Apart from getting a root shell with 'sudo -i', you can always unlock the root account if you like: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

