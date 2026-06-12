---
title: "Ending a sudo -s session"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by anitract on 2008-01-22
Ok, so sudo -s  basically switches your session to the root account.  
Is there a sudo command to return you to the initial user session?  
(Like an equivalent to su <your username>, which seems to do the trick).

---

### Post by gvartser on 2008-01-22
ctrl + d

/G

---

### Post by philinux on 2008-01-22
sudo -k  according to man sudo

---

### Post by p_quarles on 2008-01-22
"sudo -k" just ends the timeout period for sudo.

To get out of the root shell (or any shell session, for that matter), just type "exit."

---

### Post by anitract on 2008-01-22
I could have sworn I tried exit...ctrl-d will be handy as well.  Well, thanks.  Mystery solved.

---

### Post by bodhi.zazen on 2008-01-22
exit ftw \o/

Also you should probably sudo -i rather then sudo -s

---

### Post by anitract on 2008-01-22
man explains that option, but I'm not exactly sure what it is saying. :)  why is -i a better alternative if you need to be root for a prolonged period of time?

---

### Post by bodhi.zazen on 2008-01-22
-s uses your USERS environmental variables

-i uses root's environemtal variables.

> bodhi@VirtualUbuntu:~$ [color=red]sudo -s[/color] 

root@VirtualUbuntu:~# whoami                             
root
root@VirtualUbuntu:~# echo $HOME                            
[color=red]/home/bodhi[/color]

[color=blue]sudo -i[/color]
root@VirtualUbuntu:~# whoami
root
root@VirtualUbuntu:~# echo $HOME
[color=blue]/root[/color]

so the risks of sudo -s are both :

1. Security. You do not want root to use your environment.

2. Function. You do not want root to save to /root not your $HOME sudo -s may overwrite config files and rarely change permissions of files in $HOME.

---

### Post by Joeb454 on 2008-01-22
Thanks Bodhi, I'd forgotten what the difference was, it'd been bugging me for a couple of days :)

---

### Post by anitract on 2008-01-23
Great explanation.  Thanks!

---

