---
title: "sudo not working"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by richardkemp on 2006-05-12
Hey all, I am pretty new to linux. I installed Ubuntu on a partition of my hard drive yesterday, after finding a guide for how to make my wireless ethernet card work..

I finished the ubuntu install and logged in, all fine, but when i (eventually!) found the command line interface, i found i couldnt follow the instructions in the guide, specifically: sudo -i ndiswrapper *driver location*

Most bash commands dont work, they turn up an error saying 'Richard-U' (the workstation name) cannot be found with getiplocation() or something similar 9thats not it, i just cant remember it).


Other info: sudo updatedb doesnt work either. Nothing sudo works.. I will update this with clearer info when I get back from work later, any help appreciated!

---

### Post by hardXcore on 2006-05-12
reinstall

---

### Post by 23meg on 2006-05-12
Check to make sure your /etc/hosts file looks like this
```
127.0.0.1 localhost.localdomain localhost **MACHINE_NAME**

#The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by richardkemp on 2006-05-12
Thanks, I had considered a re-install.

As to the more helpful reply, the first line is right, its the first thing I tried (searched the forum before I asked :) ), but i haven't got any of the ipv6 stuff.. is it essential?

---

### Post by amir_u on 2006-05-16
Hi,
I happen to have the same problem. None of my Administration applications will run, not even when I try to run them from the command line.

The file /etc/hosts contains a single line which is a comment:

#The following lines are desirable for IPv6 capable hosts

I had read the above reply but I need some more detailed explanation.
running a command like sudo echo hi at the prompt returns:

sudo: unable to lookup uri via gethostbyname()

thanks,
Amir

---

### Post by WrathofthePenguin on 2006-05-16
[QUOTE=richardkemp]Hey all, I am pretty new to linux. I installed Ubuntu on a partition of my hard drive yesterday, after finding a guide for how to make my wireless ethernet card work..

I finished the ubuntu install and logged in, all fine, but when i (eventually!) found the command line interface, i found i couldnt follow the instructions in the guide, specifically: sudo -i ndiswrapper *driver location*

Most bash commands dont work, they turn up an error saying 'Richard-U' (the workstation name) cannot be found with getiplocation() or something similar 9thats not it, i just cant remember it).


Other info: sudo updatedb doesnt work either. Nothing sudo works.. I will update this with clearer info when I get back from work later, any help appreciated![/QUOTE]


Just out of curiosity, are you trying to run sudo under the same account you installed ubuntu under? In other words, let's say you enter 'richard' as your username when you install ubuntu. Are you currently logged in under 'richard'? I found that when I created a new account for somebody else I had to specifically tell it to allow system administration (under 'user priveleges' in the properties for the user. This is when you're configuring the user using 'Users and Groups' under System Administration') or the sudo command just did not work. Hope that helps.

---

