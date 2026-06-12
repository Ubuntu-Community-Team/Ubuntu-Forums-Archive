---
title: "Noob Questions on networking/LAMP/Serving"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by walmartboi on 2008-03-17
where to begin...

I have my os freshly installed, have it running well or so it seems.

during the installation it failed to install lamp server

i went through the process step by step with documentation i found
and installed mysql/php to the best of my abilities im sure ill run into more
issues when i get to that point.

I now have my box connected to my network and that seems to be working ok, i have a small set up and i have a linksys router running dhcp.

i guess my goal will explain my problem a bit(hopefully)

i design/develop etc. and i want this machine to serve locally for me for testing purposes. i dont intend to actually host anything on the internet... at least not at this point in time, yet another thing i will get to when i reach that point. I am a noob when it comes to servers so i have been collecting information online to help me set this server up. a lot of what i have found is for ubuntu GUI and doesnt help all that much except for where it tells you terminal commands.

the other problem i encounter is that a lot of documentation and forums and what not is usually relative to an old version of ubuntu. where i am running ubuntu 7.10 server edition.

I need some assistance with what steps to follow so i can get this server functional and load my work on to test/view on my xp machine.

ie;

step 1-set up server/and whatever it needs to allow me to test my work
step 2-test that it is working properly
step 3-start working on it

some of this stuff i just dont know where to begin.

okay i have probably rambled to much.

can anyone point me in the right direction?

---

### Post by handydan918 on 2008-03-17
Yeah, install the regular Ubuntu system. That way you get a GUI, and it'll still run any server programs you need. The server version assumes familiarity with the command line. If you don't have that, use the Gnome or KDE desktop instead. 
Sorry, there just isn't a 100 page answer for everything you'll need to know...

besides, the other questions are:
What kind of server? What exactly do you want to do? Are you talking about a file server, a local http server, etc....?
There are many different servers in the linux world; indeed, virtually all of linux is based on client/server roles, right down to your currently missing xserver.

---

### Post by walmartboi on 2008-03-17
I know im making it hard on myself by installing the server edition but i have my reasons for that... i used to work on a friends linux box in the past so i do have some familiarity with the interface and i actually prefer it to that of a GUI. but that is rather here no there.

I know there isnt a 100 page answer to my woes, i didnt expect one. i am completely aware that this is all going to be a trial and error process. Im looking forward to it.

As i had said, i design and develop websites/projects etc. I need a local testing environment so i dont have to sit around uploading constantly. i guess my needs fall under that of a local http server, eventually when i do get my skills up to par and understand security a bit better i do plan on hosting my own server/sites.

---

### Post by handydan918 on 2008-03-18
OK, install apache and knock yerself out. 
I'm not a coder, so I just maxed out my knowledge meter....doesn't take much, does it?

BTW, ```
sudo apt-get install apache2 apache2-doc
```
That ought to keep you out of trouble for a while...

:)

---

### Post by walmartboi on 2008-03-18
handydan918,

thanks... i just got apache installed and running properly and directed where it needs to be.
i did the install on apache and php yesterday but actually had the time to finish configurations today. i can actually locally test now... yay."i totally feel like a noob, i should have gone through this years ago... heres to procrastination".

now i just need to fix mysql and i think ill be cool for a while. picking up linux again has been a little confusing but not to bad cause i had used it some time ago so at least i didnt have to start from square 0. thanks for taking the time to respond. if you have any input on installation tips for myql let me know. or even setting up a network drive for file transfer or something of that nature.

---

### Post by handydan918 on 2008-03-18
I'm afraid I'm a bit of a troglodyte. I know nada about sql and I use ssh/scp for file transfers...

scp is like this...
scp <source> <target_IP:/path/to/target>

---

### Post by hyper_ch on 2008-03-18
if you follow that:  [http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10) you'll get a full-featured ISP-like setup...

The only thing you then need to do is to add "domains" to the server and edit the hosts file on your desktop computer so that the domain entry points to your server IP... that way you can setup a live testing server...

---

