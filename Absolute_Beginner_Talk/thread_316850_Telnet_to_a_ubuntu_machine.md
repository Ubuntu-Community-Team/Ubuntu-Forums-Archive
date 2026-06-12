---
title: "Telnet to a ubuntu machine"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by bhavesh on 2006-12-11
Hello folks , 
             I know telnet is a archiac technology , but i just want to experiment with it 

I have 2 virtual machine , both running ubuntu . They are behind NAT and are running on 2 different machines. 

The problem is that i want to telnet from one machine to another . Can some one tell me how do i do this .

Thanks in advance,
Bhavesh

---

### Post by taurus on 2006-12-11
Didn't you have a same thread a couple of hours ago with some replies too???

---

### Post by bhavesh on 2006-12-11
got no replies , everyone suggested using SSH . But the thing is that i want to learn using telnet.

Sorry if i broke any rules

---

### Post by scrooge_74 on 2006-12-11
Every body is doing you a good favor by telling you to forget telenet and use SSH, is going to be a lot more secure for you, and you have full control of your machine.

Why open a new thread when you already had one?

---

### Post by taurus on 2006-12-11
Learning telnet!!!  This is not the 90's anymore so I recommend you start looking into ssh which is more secure than the old way--telnet...

---

### Post by haxer on 2006-12-11
I must say that okay ssh is the most used and best security but some services are still using telnet. I often use ssh between to machines but telnet in some. But still ssh is the best!! Like they say this is not the 90&#347; its 2006 soon 2007 we got blueray :)

---

### Post by bhavesh on 2006-12-11
Ok i agree on using SSH , so can some one tell me how do i use SSH to a virtual machine from another virtual machine . 

Thanks for your suggestions,
Bhavesh

---

### Post by taurus on 2006-12-11
> **haxer said:**
>  we got blueray :)
Or HD-DVD!!!  ;) 

It's like VHS vs betamax back then...

---

### Post by taurus on 2006-12-11
You need to install the server first before you can log in remotely...

```
sudo aptitude update
sudp aptitude install openssh-server
```
Then from the other machine, do

```
ssh -l **username** **IP**
(where **IP** is the IP address of the machine you want to connect to...)
```

---

### Post by scrooge_74 on 2006-12-11
> **bhavesh said:**
> Ok i agree on using SSH , so can some one tell me how do i use SSH to a virtual machine from another virtual machine . 

Thanks for your suggestions,
Bhavesh

First go ahead and install the SHH server package from the repositories since ubuntu comes by default only with the client

then from command line from one machine you do ssh user@ipaddressoftheotherPC
give password and you should be in the other machine

---

### Post by bhavesh on 2006-12-11
Can i use apt-get to install SSH server package . If so what is the command . If not how do i install it ( i have not installed anything without using apt-get ) 

Thanks for your response ,
Bhavesh

---

### Post by taurus on 2006-12-11
> **bhavesh said:**
> Can i use apt-get to install SSH server package . If so what is the command . If not how do i install it ( i have not installed anything without using apt-get ) 

Thanks for your response ,
Bhavesh
I just showed you in Post #9!!!

---

### Post by bhavesh on 2006-12-11
Sorry taurus , i overlooked the post in exitement. I have installed the opensshserver on both the virtual machine .

But since the machines are running behind NAT there is no significance of the IP addresses , so how do i go about doing a SSH from one virtual machine to the other

---

### Post by scrooge_74 on 2006-12-11
> **bhavesh said:**
> Sorry taurus , i overlooked the post in exitement. I have installed the opensshserver on both the virtual machine .

But since the machines are running behind NAT there is no significance of the IP addresses , so how do i go about doing a SSH from one virtual machine to the other

those machines do have ip address, even in a LAN 
do ifconfig and find out the ip address of each machine

---

### Post by taurus on 2006-12-11
Maybe you should have a look at your other thread about IP!!!

---

### Post by bhavesh on 2006-12-11
Yes i have the Ip address , but i dont know what is the procedure to do the SSH . Since these are NAT ip's they dont work the way normal LAN ip's would do.

---

### Post by houstonbofh on 2006-12-11
If you run synaptic you can search for telnet.  It is insecure, but some things still require it.

---

### Post by bhavesh on 2006-12-11
Yes telnet is present , but on the recomendations of the folks on the forum i have decided to use SSH and have installed open-ssh server on both of my virtual machines . I have also done SSH port forwarding . 

But i dont know how to ssh from one m/c to another

---

### Post by steve.horsley on 2006-12-11
On one machine, you issue the command:
**ssh 1.2.3.4**
but of course you need to give the IP address of the other machine. Since you are using a NAT setup, you will have to give the **apparent** address of the other PC for it to connect to. You may have to set up the NAT gateway to forward TCP port 22 to the destination server.

---

### Post by bhavesh on 2006-12-11
I am posting what i did so that it can be helpful for some one else who might face the same problem :

1] On a unix box ( this can be a virtual machine ) places --> connect to server 

2] choose the service type as "SSH" 

3] In the server field choose the IP adress of the host machine on which the virtual machine is a guest.

4] Mention the port number on which you have done the SSH port forwarding using the virtual network wizard.


And that's it this would give you a short cut to the machine on your Unix desktop.

For windows u can use putty , since i used it to connect to a virtual unix box

Thanks for your help everyone. :)

---

