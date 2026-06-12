---
title: "run server scripts from web browser"
date: 2008-03-27
forum: Absolute Beginner Talk
---

### Post by whycantihavemyusername on 2008-03-27
Hello, im relativly new to ubuntu. 
I have been attempting to learn linux by command line so i have installed server edition and been hammering away for a week or so now. I've installed the packages for a webserver and im looking to manage scripts from the server remotely through web browser. Only i cant seem to find any resorces on this/perhaps im looking in the wrong place or somthing.. 

Thanks in advance

---

### Post by DBrocks on 2008-03-27
> **whycantihavemyusername said:**
> Hello, im relativly new to ubuntu. 
I have been attempting to learn linux by command line so i have installed server edition and been hammering away for a week or so now. I've installed the packages for a webserver and im looking to manage scripts from the server remotely through web browser. Only i cant seem to find any resorces on this/perhaps im looking in the wrong place or somthing.. 

Thanks in advance

Okay, no your not in the wrong place
HOWEVER: you are going about it wrong. But that's okay, we all start somewhere.
So, what you are trying to do is get in, and access/run scripts. What you are looking for is NOT in the web-browser. If you are looking to access it remotely, you need to use SSH. SSH is a way to open a secure, encrypted tunnel over the internet to your server. It is quite easy to set up. Simply enter
```
sudo apt-get install sshd
```
This will enable the server-side of SSH. Now are you attempting to access it remotely, or is the computer on your network? AND, are you trying to access it from a Windows machine, or another Linux machine?

Also, props to you for running linux Command Line. Not something alot of folks are comfortable with doing.

---

### Post by whycantihavemyusername on 2008-03-28
I currently have a few systems on my lan windows and linux, i am using SSH to access the Ubuntu server currently as its in an unconfortable corner.. lol

I was hoping to control the scripts by web browser, obviously write in some sort of authentication, the purpose of the server for the time is to host a program which id like to be able to start running from any platform i have nat and pat setup and some knowlage of apache.. just resorces for the 'middle' part seem to be scarse.. 

Thanks for your reply, ill have a poke around with SSHD tommorow O_O

---

### Post by lswest on 2008-03-28
also, there are vnc java applets you can integrate into a web page, which gives you remote access to the desktop, but i'm not sure about security or such.

---

