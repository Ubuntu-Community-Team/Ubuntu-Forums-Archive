---
title: "Cannot sync iphone 2.2 with Amarok ...HElp"
date: 2009-02-17
forum: Apple Hardware Users
---

### Post by nicholls15 on 2009-02-17
Hi Folks

I'v been trying to solve this problem for the last 2 days , 

I cannot sync my iphone with amarok , I read all the articles on the subject but nothing works , I've reinstalled everything still the same results .

Basically when I start up amarok , I configure the device in amarok, then up pops an ssh login root@192.x.x.x , I enter in the alpine password the login reappers & re-appears 

So I tried opening up a terminal and running the iphone-mount command , 

I get this 

Permission denied (publickey,password,keyboard-interactive)

So I tried logging in as sudo ssh root@192.x.x.x
and it gives me this 

[sudo] password for paul: 
root@192.168.10.19's password: 
Permission denied, please try again.
root@192.168.10.19's password: 
iPhone:~ root# 

It seems to connect but won't let me on amarok

Help I really want to get this sorted

Any help will be greatly appreciated

---

### Post by Gliitch on 2009-04-04
> **nicholls15 said:**
> Hi Folks

I'v been trying to solve this problem for the last 2 days , 

I cannot sync my iphone with amarok , I read all the articles on the subject but nothing works , I've reinstalled everything still the same results .

Basically when I start up amarok , I configure the device in amarok, then up pops an ssh login root@192.x.x.x , I enter in the alpine password the login reappers & re-appears 

So I tried opening up a terminal and running the iphone-mount command , 

I get this 

Permission denied (publickey,password,keyboard-interactive)

So I tried logging in as sudo ssh root@192.x.x.x
and it gives me this 

[sudo] password for paul: 
root@192.168.10.19's password: 
Permission denied, please try again.
root@192.168.10.19's password: 
iPhone:~ root# 

It seems to connect but won't let me on amarok

Help I really want to get this sorted

Any help will be greatly appreciated

You have to be logged in as paul, not as root(on your account, not your iphone) Do you have a 3G iphone or is it the 2nd Gen?
With Amarok does it tell you to put your password in twice, and still die off?

If you have a 3G iphone here is what the link [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone) just follow these directions that are on the right pane. : ) goodluck.

---

