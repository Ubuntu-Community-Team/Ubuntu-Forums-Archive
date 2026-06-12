---
title: "superuser problem."
date: 2005-06-27
forum: Absolute Beginner Talk
---

### Post by roach of discord on 2005-06-27
Hi.

This is my first time using kubuntu..and I'm having problems.  I'm use to having a superuser to do things..so I used kuser to add a password to root.  Bad idea?

Well, in a console..if I type 

$su

and put in my password...it goes to:

ravencrow@ubuntu:~$ su
Password:

sh-3.00#

Also..now, I can no longer open programs that need root access..like kynaptic.  They do nothing :(.  However..I can open them from command line.  

This is probably all my fault.  Hopefully someone can help :).  Thanks!

-edit

Also..now when trying to run something via command I get

root@ubuntu:/home/ravencrow# kynaptic
Aborting. $HOME is not set.

:???: 

-RoaCh

---

### Post by Seti on 2005-06-27
Why don't you try ```
sudo passwd
``` 
enter YOUR USER'S Password.
Then change superuser password to something and don't forget it.
It should work.
You should be able to do most admin stuff using sudo, ex:

```
sudo apt-get update
``` 

hope it helps!

---

### Post by roach of discord on 2005-06-27
hey.  Thanks!

I did your first suggestion.  It did change the password..however..if I do a '$su' from my ravencrow account..it goes to a bash prompt instead of root...like

ravencrow@ubuntu:~$ su
Password:
sh-3.00#      

I also found out..that I can enter /root with my regular user account  :???: 

Sorry for my total lack of knowledge on this.  I haven't delt with this before :p

---

