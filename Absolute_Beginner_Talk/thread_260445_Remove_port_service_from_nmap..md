---
title: "Remove port service from nmap."
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by scott_ttocs46 on 2006-09-18
I have been trying to install a different irc servers. I have discovered that, when all are removed from my system, there are three services running under the "nmap localhost" command.

How do I remove services listed under nmap?

](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,) 


Scott

---

### Post by skymt on 2006-09-18
Post the nmap output, so we can see what needs to be removed.

---

### Post by scott_ttocs46 on 2006-09-18
administrator@zeus:~$ nmap localhost

Starting Nmap 4.10 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2006-09-18 19:19 CDT
Interesting ports on localhost (127.0.0.1):
Not shown: 1673 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
6666/tcp open  irc-serv
6667/tcp open  irc
6668/tcp open  irc

Nmap finished: 1 IP address (1 host up) scanned in 0.161 seconds


---------------
need to remove 6666,6667,6667

---

### Post by scott_ttocs46 on 2006-09-19
lol... rebooting works. The service didn't stop after I removed it.
[-X :-({|= [-X :-({|= [-X :-({|= [-X

---

