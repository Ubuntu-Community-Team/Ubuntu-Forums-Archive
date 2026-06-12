---
title: "ubuntu server"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by ct-momz on 2006-11-09
hi i'm new to the linux community and really dont know much about ubuntu but anyways

i've been playing with ubuntu for a few days now and really like it 
so a friend of mine wants to install the server from remote, but i need to make him a root user and dont really now how i've been looking up on google but didnt really help.

ive already made him a normal user account but how do i change it to a root account any help would be great thnx

---

### Post by kidders on 2006-11-09
Hi there,

Strictly, there should only be one root account. Users who need to do things as root tend to use utilities like sudo to do it.

If you check /etc/sudoers, you should see that members of the "admin" group have permission to run any command with sudo. So, if you add your friend to that group, he should have everything he needs :-)

---

### Post by taurus on 2006-11-09
You can add him to groups adm & admin in /etc/group so he can use sudo instead of becoming root!  It's safer that way...

```
sudo nano -Bw /etc/group
```

---

### Post by tmountain on 2006-11-09
It's generally a dangerous practice to do a remote login as root. You should have set a root password when you installed Ubuntu. Your best bet is to login via ssh under your normal user account. From there, you can do "sudo su" to become root. Also, if it's just a single command you need to run, you can just do "sudo command", and the command will execute as root.

---

### Post by ct-momz on 2006-11-10
hi thnx for the help but could u help me some more before i really screw it up :D

i got into sudo nano -Bw /etc/group so shuold i put it behind admin ??

btw how the hell do i get otu off the group  ( sry i'm a real linux noob)

---

### Post by ct-momz on 2006-11-10
btw i tryde getting it to /etc/sudoers and i cant get in even if i login with root  why is that ?

nevermind i did :D so happy love linux and ubunut communty for there help :)

---

### Post by taurus on 2006-11-10
Just so you would understand it a little better, the first user that you created can use sudo; anybody else after can't.  Therefore, if you want somebody else to execute sudo, you must add that user to groups adm & admin...

That's why you can run sudo while your friend can't (or couldn't).

---

### Post by ct-momz on 2006-11-10
yeah i learnd that to day :) 

wel i thought that would be all but it isnt well its never with a noob uh :P. anyways i opend the port but i dont know how to make it so that he can get into the server ( dont know how u call it in english) help would be great thnx anyways ( and for the stuff u guys told me before)

---

### Post by taurus on 2006-11-10
You need to install sshd so your friend can ssh, connecting, to your machine.  

```
sudo aptitude update
sudo aptitude install openssh-server
```

---

### Post by ct-momz on 2006-11-11
thnx did that but didnt help reaally he still cant get in becouse the servers ip isnt like my normal ip ( i think i gave him my network ip) could u guys tell me how to make so i can give him my ehternet ip and he can get into the server ??

btw i'm using ubuntu 5.10

---

### Post by taurus on 2006-11-11
Is your computer hooked up to a router?  If it is, then you need to go into your router and open a port to allow incoming traffic...

---

