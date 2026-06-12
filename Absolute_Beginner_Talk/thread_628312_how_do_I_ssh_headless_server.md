---
title: "how do I ssh? headless server"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by Jason Weiss on 2007-12-01
Hi I am trying to set up a mail server with this how to.
[http://www.howtoforge.com/perfect_server_ubuntu7.10_p3]("http://www.howtoforge.com/perfect_server_ubuntu7.10_p3")
Which by the way is a very good how to.

well anyways, I can't seem to be able to install putty to connect to my headless open ssh server.

I am not sure if there is a problem with the repo or something. 

Well anyways, I am not sure I need it, from what I understand I can just use the ssh client. 

But I don't know how, is there anyone that could tell me anotherway install putty or how to conect to the headless sever another way.

---

### Post by ajopaul on 2007-12-01
are you trying to access this open ssh server from a linux client? then this would work 
```
ssh ipaddress
``` if the headless server has X installed then u can do X forwarding using ```
ssh -X ipaddress. 
```

---

### Post by Jason Weiss on 2007-12-01
I thought I could try to do something simple like this. but I am getting this meesage. 
> Permission denied, please try again.

am I missing something here?

---

### Post by ajopaul on 2007-12-01
> **Jason Weiss said:**
> I thought I could try to do something simple like this. but I am getting this meesage. 

am I missing something here?
try ssh username@ipaddress

---

### Post by Jason Weiss on 2007-12-01
I tried that to.

I am not sure what I am doing wrong here.

---

### Post by ajopaul on 2007-12-01
not sure if u have to use sudo for this, but what exactly happens when u type ssh ipaddr

---

### Post by Jason Weiss on 2007-12-01
This is one of those annoying things when I know I am so close. 

> root@openbooks-desktop:/home/openbooks#  ssh server1@192.168.1.107
server1@192.168.1.107's password: 
Permission denied, please try again.
server1@192.168.1.107's password: 
Permission denied, please try again.
server1@192.168.1.107's password: 
Permission denied (publickey,password).


it is a bit frustrating i have done it over and over again

---

### Post by DezSP on 2007-12-01
You must be entering the wrong password/username. Are you sure they're right?

---

### Post by Jason Weiss on 2007-12-01
no I have checked and re checked. 

is anyone aware of an alternative to putty?

---

### Post by monte48lowes on 2007-12-01
ssh is the simplest way to access the server. Putty uses ssh. If you cannot get ssh to work, none of the other programs will work either. You may have to attach a keyboard and monitor to the server to access it directly to check for problems on the server. 

Mike

---

### Post by nhandler on 2007-12-01
The ip address you are using will only work if that computer is on the same network as the one you are connecting from. Otherwise, you will not be able to connect. There should be another ip address somewhere for that computer that you can use to access it from anywhere.

---

### Post by prodezigner on 2007-12-01
if your using an outside box... try...

ssh -l <USERNAME> <IPADDRESS>

for example...

ssh -l root xxx.xxx.xxx.xxx

then it'll ask for root password (if you set one)... then viola, you should be in.

I find Tunnelier to be a decent alternative. I just like PuTTy for fullscreen.

---

### Post by monte48lowes on 2007-12-01
Is 'server1' the hostname for your server? If so, what is the user name that you placed on it? Have you tried:

 ```
ssh administrator@192.168.1.107
```

Mike

---

### Post by xeth_delta on 2007-12-01
If the computer you are trying to connect to, is indeed in the same network, check that the ssh server is running and that the port it is listening from is open.

You can find out which port the server is using from the file **/etc/ssh/sshd_config**.

Xeth

---

### Post by Jason Weiss on 2007-12-01
Hi I just found out the problem. 

the problem is that I am an idiot, I was using the wrong user name. 

I am really emaaresed. 

Sorry for wasting everyones time.

---

### Post by Dr Small on 2007-12-01
When connecting with SSH to a headless server (or any of your servers, for that matter), always make sure you are connecting to the correct Host, with the correct Username, and that port 22 is open on your firewall to allow incoming connections on SSH.

---

