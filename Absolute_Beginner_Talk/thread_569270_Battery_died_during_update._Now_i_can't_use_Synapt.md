---
title: "Battery died during update. Now i can't use Synaptic Manager PLEASE HELP!"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by XxSRMxX on 2007-10-06
I was installing the updates from a fresh install of xubuntu 7.04 and my battery died on my laptop. I turn it back on sign in and now i can't finish updating or i can not get into the Synaptic Manager i get this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

so i open the terminal and i type in sudo dpkg --configure -a and this is what i get

stacey@stacey-laptop:~$ su
Password: 
root@stacey-laptop:/home/stacey# sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0010' near line 1:
 newline in field name `padding'
root@stacey-laptop:/home/stacey# 

i've looked the forums and i still can't find a answer that works for me...can some one please help?

thanks in advance
XxSRMxX

---

### Post by overdrank on 2007-10-06
> **XxSRMxX said:**
> I was installing the updates from a fresh install of xubuntu 7.04 and my battery died on my laptop. I turn it back on sign in and now i can't finish updating or i can not get into the Synaptic Manager i get this error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

so i open the terminal and i type in sudo dpkg --configure -a and this is what i get

stacey@stacey-laptop:~$ su
Password: 
root@stacey-laptop:/home/stacey# sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0010' near line 1:
 newline in field name `padding'
root@stacey-laptop:/home/stacey# 

i've looked the forums and i still can't find a answer that works for me...can some one please help?

thanks in advance
XxSRMxX

Hi and welcome, you can try the command in the terminal 
```
sudo apt-get install -f 
```

---

### Post by XxSRMxX on 2007-10-07
Ok i tried that and this is what i get

```
stacey@stacey-laptop:~$ sudo apt-get install -f
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
stacey@stacey-laptop:~$ sudo dpkg --configure -a
dpkg: failed to open package info file `/var/lib/dpkg/status' for reading: No such file or directory
stacey@stacey-laptop:~$
``` 

btw thanks for replying

---

### Post by bodhi.zazen on 2007-10-07
Now try:```
sudo dpkg --configure -a
```

note: there are two - - (without a space) between dpkg and configure

---

### Post by Celegorm on 2007-10-07
> **XxSRMxX said:**
> stacey@stacey-laptop:~$ su
Password: 
root@stacey-laptop:/home/stacey# sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0010' near line 1:
 newline in field name `padding'
root@stacey-laptop:/home/stacey# 

I don't know if this would mess things up, but when you have switched to root with su you don't need to use sudo. (su = super user, sudo = super user do, sudo is a way to do something as root without being logged in as root)

---

### Post by michiel.patrick on 2007-10-07
I posted this earlier tonight because the same thing happened to me. I just backed everything up and reloaded ubuntu since it takes less than 30 minutes and now my probs are solved. I thought my laptop was plugged in but when i got home it wasnt and had stopped right in the middle causing instability as well as things just simply not working

---

