---
title: "VirtualBox ubuntu jboss cannot access app server remotely"
date: 2009-06-21
forum: Apple Hardware Users
---

### Post by bmhardy on 2009-06-21
Hello,

I recently installed VirtualBox on my mac and installed ubuntu on VirtualBox.
I installed jboss on ubuntu and I can access the appserver from ubuntu as [http://localhost:8080](http://localhost:8080)
but I cannot access the appserver from ubuntu with the full name of my virtual machine
[http://myvm.mynetwork:8080](http://myvm.mynetwork:8080). 

I want to access the app server from my mac with the address [http://myvm.mynetwork:8080](http://myvm.mynetwork:8080) but I cannot.  I can successfully ping my vm with the command 
ping myvm.mynetwork

Can anyone tell me what to configure and how to configure it so I can access the appserver on my vm from my real computer?

Is there a gui for firewall set up on ubuntu that would help or is this a routing problem and how could I configure?

Thanks so much.

Brian

---

### Post by vimodchandra on 2009-12-13
You can use the command 
  **sh run.sh -b 0.0.0.0   (in Linux)**
  in Windows,make a bat file..see below..
[B]@echo off
start D:\servers\jboss-4.2.3.GA\bin\run.bat -b 0.0.0.0[/B]
    The reason is JBoss will block the remote access using IP as a default setting.We need to change this settings as mentioned above.

---

