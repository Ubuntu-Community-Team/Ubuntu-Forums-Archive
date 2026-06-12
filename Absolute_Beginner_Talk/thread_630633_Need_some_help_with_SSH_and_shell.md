---
title: "Need some help with SSH and shell"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by jthm2030 on 2007-12-03
Alright here it is, i need to get a user on this ubuntu 7.10 system that is able to login using SSH and Shell (i guess) on port 22.  The person that is in need of this is out of the country and all he told me was to provide a shell account and access to port 22.  If anyone has anything that could push me in the right direction that would be great.  Oh yea this is the first time i have ever used ubuntu, so try to keep it easy.

Thanks,

Chris

---

### Post by vikram on 2007-12-03
Hope you are having fun exploring Ubuntu. Its very user-friendly and the people at the forums here are very helpful. A great place to start is 

[https://help.ubuntu.com/](https://help.ubuntu.com/)

Look at the official 7.10 documentation. theres lots more under community docs. a few that will help with what you are looking for are listed below

setting up ssh see link below

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

adding a user

[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

---

### Post by Hospadar on 2007-12-03
If you want to be able to log into a machine remotely there are a few things you need to be sure of:

that the ssh server is actually installed
```
sudo apt-get install ssh
```that port 22 is open, I'd use firestarter to configure your IPtables, that's probably the easiest way in my opinion.
First, install firestarter, then open it (System->Administration->Firestarter) then go to "Policy", right click in the bottom list area, click add rule, name it "SSH" (or whatever) use port 22, and choose "Anyone"
```
sudo apt-get install firestarter
```you may need to restart your machine at this point, I'm not sure.

then, you'll want to create a new user for the guy, and then he can log into your machine with the command
```
ssh <the username you just created>@<your IP address>
```Also if you want to register a domain name to your IP, he can use that domain name in place of your IP, but the IP should work fine.

Also, if you are going through a router, you'll need to go into the router's menu and foreward port 22 to your machine.  exactly how to do this will vary from router to router, check your manual if you don't know.  If this is the case, you'll want to give him the external IP of the router, not the local address of your machine (it should *not* look like 192.168.xxx.xxx.xxx, that's the local address)

furthermore, you can test your setup by trying to ssh into your machine locally or from a different machine in your house or at a friend's or something, if from your own machine, try typing "ssh localhost"

---

### Post by Dr Small on 2007-12-03
Here, check out my guide on setting up a SSH server:
[http://php.8ez.com/drsmall/blog/?p=124](http://php.8ez.com/drsmall/blog/?p=124)

---

