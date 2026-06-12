---
title: "How to Enter ROOT Account"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by osama_b on 2008-03-27
hello 

i'm install ubuntu 7 desktop but during install do not make root account .

log in my account only ,( su )command to require root account .

what is road enter root account .

thanks

---

### Post by wormser on 2008-03-27
Ubuntu is set up to run with using **sudo** instead of logging in as root.  Just put sudo infront of the command that needs root privileges.  If you have to get into root then use sudo -i.  If you are opening a graphical application then use gksudo instead.

---

### Post by cwmoser on 2008-03-27
Here is an example:


Below, I logged in as user carl:
Note that I tried to do the traditional 'su' and it failed both ways I tried it.
Then, I got a root shell via sudo -i and got the root # prompt.

Now I consider this dangerous and you better be careful.

The better approach that Ubuntu recommends and I do too is to prefix your command with sudo like in the example below where I issued the apt-get command.  That command would not fully run if I tried it as the normal user 'carl'.  The idea behind sudo is to allow a normal user to temporarily run a command that requires root privileges if he knows the root password.

The idea behind the sudo schema is that you have to be proactive and know that the command you are issuing needs root privileges -- that prevents you from making a big mistake with a mistyped command.

Carl



carl@klaatu:~$ 

carl@klaatu:~$ su
Password: 
su: Authentication failure
Sorry.
carl@klaatu:~$ su root
Password: 
su: Authentication failure
Sorry.

carl@klaatu:~$ sudo -i
[sudo] password for carl:
root@klaatu:~# 

root@klaatu:~# exit
carl@klaatu:~$

carl@klaatu:~$ 
carl@klaatu:~$  sudo apt-get install mono
carl@klaatu:~$

---

### Post by exup1000 on 2008-05-25
Hi
thanks this expalined alot why su would not work but sudo would. Could I ask how I edit a text file as a "su" that I suspect is not able to be saved under a normal user account EG etc/fstab

Cheers Exup

---

### Post by aysiu on 2008-05-25
> **exup1000 said:**
> Hi
thanks this expalined alot why su would not work but sudo would. Could I ask how I edit a text file as a "su" that I suspect is not able to be saved under a normal user account EG etc/fstab

Cheers Exup
```
sudo nano *nameoffile*
``` Read more here:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by aysiu on 2008-05-25
> **exup1000 said:**
> Hi
thanks this expalined alot why su would not work but sudo would. Could I ask how I edit a text file as a "su" that I suspect is not able to be saved under a normal user account EG etc/fstab

Cheers Exup
```
sudo nano *nameoffile*
``` Read more here:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by d.kusummmanth@gmail.com on 2008-05-25
> **cwmoser said:**
> Here is an example:


Below, I logged in as user carl:
Note that I tried to do the traditional 'su' and it failed both ways I tried it.
Then, I got a root shell via sudo -i and got the root # prompt.

Now I consider this dangerous and you better be careful.

The better approach that Ubuntu recommends and I do too is to prefix your command with sudo like in the example below where I issued the apt-get command.  That command would not fully run if I tried it as the normal user 'carl'.  The idea behind sudo is to allow a normal user to temporarily run a command that requires root privileges if he knows the root password.

The idea behind the sudo schema is that you have to be proactive and know that the command you are issuing needs root privileges -- that prevents you from making a big mistake with a mistyped command.

Carl



carl@klaatu:~$ 

carl@klaatu:~$ su
Password: 
su: Authentication failure
Sorry.
carl@klaatu:~$ su root
Password: 
su: Authentication failure
Sorry.

carl@klaatu:~$ sudo -i
[sudo] password for carl:
root@klaatu:~# 

root@klaatu:~# exit
carl@klaatu:~$

carl@klaatu:~$ 
carl@klaatu:~$  sudo apt-get install mono
carl@klaatu:~$

Superb Reply. It was v.clear and easy to understand. I and my frnds were having the same problem.

I want to know what -i after sudo means? Also what is the default root password?

Any useful command list I can type in Terminal?

---

### Post by aysiu on 2008-05-25
There is in essence no root password, and there is no way to log into the root account directly and no need to, as you can use ```
sudo -i
``` or just plain *sudo*.

---

