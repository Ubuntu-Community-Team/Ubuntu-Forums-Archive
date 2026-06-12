---
title: "Sick of typing in password [Resolved]"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by erk on 2007-02-22
How can I stop having to type in a su password every time I run a software update, or make settings changes? It's my computer, nobody touches it, so there is no need for GUI passwords.

---

### Post by Titus A Duxass on 2007-02-22
You can remove the passwd option with passwd -d username.
But I would not recommend it, how long does it take to enter your password?

It is good practice.

But it is your box so you do what you want.

---

### Post by xyz on 2007-02-22
I can understand you as I used to feel the same way!
But you should not remove it and I don't think you can.
[RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by fenderjaguar on 2007-02-22
just out of interest, does anybody know how to remove the auto login?

---

### Post by orb9220 on 2007-02-22
That is not true. Anybody can break into computer from the internet. That is how windows gets owned.

If a person wants to do all kinds of bad things to linux machine all they need is your user/admin password and lo and behold you have just turned your linux box into a unsecured computer just like windows.

I have just had to make up my mind. For a secure computer you have to have it this way. Just like Vista is doing now. And window's machines could be secured just like Linux.

But because people are lazy and don't want to spend the 3 secs to type password is why the internet is the breeding ground for unsecured machines waiting to be infected and controlled.

Other Linux distro's will allow you to run Root user where it is just like windows unsecure and waiting for new person's not knowing what they are doing to mess up their machines.

I know it is frustrating at first I to was spoiled and didn't want to have to enter a passwords all 
the time. But I got over it and now feel better knowing some hacker will not find my system worth the time.

---

### Post by orb9220 on 2007-02-22
Go to system>admin>logon there is a tab for auto logon from restart. But if you log off only then
you will have to enter password.

But starting up cold or reboot will auto logon for you.

---

### Post by fenderjaguar on 2007-02-22
oh sorry, i meant how to turn to auto login on. but yes, i see now, thanks

---

### Post by bob-aptllc on 2007-02-22
> **fenderjaguar said:**
> just out of interest, does anybody know how to remove the auto login?

See tip #8 at [http://www.linux.com/article.pl?sid=06/06/08/1651225](http://www.linux.com/article.pl?sid=06/06/08/1651225). However, I also recommend not removing the password option.

---

### Post by erk on 2007-02-23
I think people misunderstand. I am not trying to remove my user password, i know that is critical, I am trying to make the system no ask for it when doing admin functions.  I don't use a root password so it shouldn't ask. I suspect there is a sudo thing going on in the GUI, instead of an su.  su does not ask for a password at the command line.

---

### Post by Bachstelze on 2007-02-23
```
sudo visudo
```

should open the /etc/sudoers file in nano, find a line that should say

```
%admin    ALL=(ALL) ALL
```

and edit it like this :

```
%admin    ALL=(ALL) NOPASSWD:ALL
```

then save the file (Ctrl+O), exit nano (Ctrl+X) and you should not be propted for your password when using sudo anymore.

---

### Post by aysiu on 2007-02-23
You can also change the *sudo* timeout from 15 minutes (the default) to something longer--like 30 minutes or 60 minutes:
[http://doc.gwos.org/index.php/Change_default_timeout_in_sudo](http://doc.gwos.org/index.php/Change_default_timeout_in_sudo)

---

### Post by pirothezero on 2007-02-23
just wondering anyway to make it so you just do it on one user name? 

Question on security, it seems like if one does that the only way for someone to get into su would be if they had your password the username that could just jump into su without password, and if you had a good password are security concerns at a minimum??

---

### Post by Bachstelze on 2007-02-23
Yes, just replace %admin with your username. In a nutshell, a line beginning with "%foo" - mark the percent sign - will apply to the *group* foo and a line beginning with "bar" - without percent sign - will apply to the *user* bar.

---

### Post by rgp-02 on 2007-02-23
HA  HA  HA.........

what a name!

TITUS A DUXASS

that's the funniest thing i heard all day.........owe you a beer dude!

---

### Post by erk on 2007-02-24
> **HymnToLife said:**
> ```
sudo visudo
```

should open the /etc/sudoers file in nano, find a line that should say

```
%admin    ALL=(ALL) ALL
```

and edit it like this :

```
%admin    ALL=(ALL) NOPASSWD:ALL
```

then save the file (Ctrl+O), exit nano (Ctrl+X) and you should not be propted for your password when using sudo anymore.

Thanks, that did it, your a wizard !

---

