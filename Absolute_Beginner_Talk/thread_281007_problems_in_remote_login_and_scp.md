---
title: "problems in remote login and scp"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by ojasvi rajpal on 2006-10-20
hi all ,
I am not able to "scp" or remote login to my system via lan . I tankshink it is a safety feature but it us really annoying . Can somebody help me removing this or suggest any other method 
thanks.
p.s. using drapper drake

---

### Post by Bachstelze on 2006-10-20
My crystal ball is currently under maintenance so please provide more details. What commands are you typing ? What error(s) do you get ?

---

### Post by ojasvi rajpal on 2006-10-22
> **HymnToLife said:**
> My crystal ball is currently under maintenance so please provide more details. What commands are you typing ? What error(s) do you get ?
:)
Thanks for correcting me. I am using "$scp filename username@172.(ip adress): " 
and then it gives the error meassage "ssh: connect to host 172.17.8.32 port 22: No route to host" but i can easily scp something from my system to the other server . so it is not a connection problem.
thanks
P.S. plz tell me when u get that crystal ball of yours repaired . I do need some:-D

---

### Post by vinnn on 2006-10-22
Do you have ssh server installed on your ubuntu machine?
```
sudo apt-get install openssh-server
```
If so, have you started the ssh server?
e.g.
```
sudo /etc/init.d/ssh start
```

---

### Post by ojasvi rajpal on 2006-10-22
> **vinnn said:**
> Do you have ssh server installed on your ubuntu machine?
```
sudo apt-get install openssh-server
```
If so, have you started the ssh server?
e.g.
```
sudo /etc/init.d/ssh start
```


Tried but of no use. I think this is a security feature to prevent illeagel acess etc. but don't know how to turn it off

---

### Post by dmizer on 2006-10-22
it's not a safety thing.

try this:
```
scp -r filename username@ipaddress:/location
```
if that doesn't work, then let us know a bit more about your situation.

are you trying to scp across your local network?  are you trying to scp from somewhere away from your local network?  if so, do you have a router? if you have a router, you will have to program it to forward port 22 to the machine you wish to scp into.

keep in mind, when you scp a file, that you will not be able to assign root privileges, so you will only be able to copy a file to your home folder username@ipaddress:/home/somewhere

---

### Post by ojasvi rajpal on 2006-10-22
@dmizer
tried still gives the same error message Help PLz
.
yes I am scping across Lan

---

### Post by dmizer on 2006-10-24
what is the output of ifconfig?

---

