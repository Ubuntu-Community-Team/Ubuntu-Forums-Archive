---
title: "Can't install VMWARE tools. I don't understand"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by tigerplug on 2007-06-14
Hi everyone, 

I am at work running Windows XP professional with VMWARE Server installed running Ubuntu as the guest OS.

I can't install VMWARE tools at all. I have searched the forums and in particular I have been following this guide: [http://blog.sirkevi.com/2006/08/17/installing-vmware-tools-into-ubuntu-guest/](http://blog.sirkevi.com/2006/08/17/installing-vmware-tools-into-ubuntu-guest/)

Im having no luck, for example after I enter this command into the terminal:

**sudo apt-get update**

I am getting a long reply, the end of which is:

[B]Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/source/Sources.gz)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied.  )
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
shane@shane-desktop:~$ [/B]

Can anyone advise me? I have already set up the static IP for the machine and entered the Subnet Mask, DNS and Gateway by going to **System-> Administrator->Network** from the GUI. Is there anywhere else that I have to enter settings or is it an issue with ports?

:(

---

### Post by Clay_Banger on 2007-06-14
it looks like you are behind a proxy server, if you are try this:

type in a terminal:
```
sudo nano /etc/apt/apt.conf
```
then copy this into the newly created file and edit it suit your needs, replacing proxy with the name/ip of your proxy, replacing port with the port etc.

if you need to use a user name and password:
```
Acquire::http::Proxy
"http://username:password@proxy:port";
```
or if you dont need to use a user name:
```
Acquire::http::Proxy
"http://proxy:port";
```

---

### Post by tigerplug on 2007-06-15
> **Clay_Banger said:**
> it looks like you are behind a proxy server, if you are try this:

type in a terminal:
```
sudo nano /etc/apt/apt.conf
```
then copy this into the newly created file and edit it suit your needs, replacing proxy with the name/ip of your proxy, replacing port with the port etc.

if you need to use a user name and password:
```
Acquire::http::Proxy
"http://username:password@proxy:port";
```
or if you dont need to use a user name:
```
Acquire::http::Proxy
"http://proxy:port";
```


No, that doesn't seem to work. I have tried it a few times. 
When I enter:

[INDENT]Acquire::http::Proxy
"http://username:password@proxy:port";
[/INDENT]
and then press return nothing happens, is there something that maybe I am doing wrong?

Thats the HTTP port right, which is 8080

I have noticed that when I am using firefox and it asks me for details to access the proxy I usually have to enter 

[INDENT]Username:xyz\"myusername"
Password: "mypassword"[/INDENT]

I have tried both "xyz\myusername" and just "myusername" with this and still no luck.

---

### Post by Clay_Banger on 2007-06-17
> **tigerplug said:**
> No, that doesn't seem to work. I have tried it a few times. 
When I enter:

[INDENT]Acquire::http::Proxy
"http://username:password@proxy:port";
[/INDENT]
and then press return nothing happens, is there something that maybe I am doing wrong?

Thats the HTTP port right, which is 8080

I have noticed that when I am using firefox and it asks me for details to access the proxy I usually have to enter 

[INDENT]Username:xyz\"myusername"
Password: "mypassword"[/INDENT]

I have tried both "xyz\myusername" and just "myusername" with this and still no luck.
It sounds like you are typing this into the command prompt, and not into the file. for apt-get to retrieve files through a proxy server, you need to put the Aquire::Http::Proxy into the file /etc/apt/apt.conf then run sudo apt-get install program

---

### Post by tigerplug on 2007-06-20
Clay_Banger would you mind explaining it step by step? Sorry! Im completely new to it!

---

### Post by Clay_Banger on 2007-06-20
open up the terminal, applications > accessories > terminal
type this in the terminal:
```
sudo nano /etc/apt/apt.conf
```
then copy this into the newly created file and edit it suit your needs, replacing proxy with the name/ip of your proxy, replacing port with the port etc.

if you need to use a user name and password:
```
Acquire::http::Proxy
"http://username:password@proxy:port";
```
or if you dont need to use a user name:
```
Acquire::http::Proxy
"http://proxy:port";
```
so if my username=bill, password=cheese, proxy=tehproxy, port=1234, i would put in the file:
```
Acquire::http::Proxy
"http://bill:cheese@tehproxy:1234";
```
then, press ctl+x, y, [enter] and you should be all done. you can then see if your settings work doing:
```
sudo aptitude update
```
if you don't get any errors you should be safe to continue on installing vmware server!
i hope thats a bit clearer for you.

---

### Post by tigerplug on 2007-06-20
Thanks alot for that, I really appreciate it!

Im away from my Ubuntu machine at the moment, but as soon as I get to it again I will give it a go. 


Cheers!

---

