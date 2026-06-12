---
title: "Novice needs help setting up a file server"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by EddySanders on 2008-02-17
Okay. This topic has been trying my patience for the last three days. :-( 
I have three computers; two of them run Ubuntu 7.10, and the last one runs Ubuntu 7.10 Server. I need to know how to make the server computer work. I want to use it as a file server that i can access from the internet. it needs to have password security, but nothing strong. I have NO clue how to do this. I keep getting errors when i try to configure Apache2. I'm so new, i dont even know how to save a file using VIM.. Someone please help.

---

### Post by Dennis on 2008-02-17
Any help?

[http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10)

---

### Post by StooJ on 2008-02-17
Less of an ISP server and more of a home user place to share files (and can be seen from online securely - although not via a webbrowser)

[http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1)
And then
[http://www.bit-tech.net/bits/2007/07/24/build_your_own_better_server/1](http://www.bit-tech.net/bits/2007/07/24/build_your_own_better_server/1)

Great guides, step-by step instructions.

I hope this helps.

---

### Post by mytwobears on 2008-02-17
Hi,

Another option is  installing Ubuntu Server and choosing the LAMP installation, this way you don't have to mess around with complicated apache configurations.  Here are some easy to follow instructions.  Hope this helps.

[http://www.ubuntugeek.com/ubuntu-710-gutsy-gibbon-lamp-server-setup.html]("http://www.ubuntugeek.com/ubuntu-710-gutsy-gibbon-lamp-server-setup.html")

---

### Post by EddySanders on 2008-02-17
I installed WebMin on my server, but i cannot yet access   my server via [https://EddyServer:10000/](https://EddyServer:10000/)    <<< this is what the guide said do

it says server not found

Please Help!!

---

### Post by EddySanders on 2008-02-17
[http://www.bit-tech.net/bits/2007/06...r_own_server/1](http://www.bit-tech.net/bits/2007/06...r_own_server/1)


used this, but once i get to the part where i edit smb.conf, i cant go any further, because when i test t from another machine, it says cant find server.

Edit: Also note that I am trying to connect multiple Ubuntu machines, and the guide gives instructions for configuring a windows machine

Edit:  It works!... from a windows machine. How can i get to it from my ubuntu computers..

the guide says type \\<ip address>\homes
this works in windows explorer, but not in firefox(ubuntu)

---

### Post by StooJ on 2008-02-18
Glad to hear you got Windows sorted.

Here's a guide on how to do it in Ubuntu:
[http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

Hope that helps as well.

With that guide you used, Webmin is not configured to be accessible externally.
I would stick with Putty & possibly VNC for now, as they have less security implications.

---

### Post by hyper_ch on 2008-02-18
What kind of access do you want?

Most simple would be to install openssh-server and forward port 22 from the router to the server. Then you can connect through a normal ssh session or use (Win)SCP for a graphical 2-pane conneciton.

---

### Post by StooJ on 2008-02-20
> **hyper_ch said:**
> What kind of access do you want?

Most simple would be to install openssh-server and forward port 22 from the router to the server. Then you can connect through a normal ssh session or use (Win)SCP for a graphical 2-pane conneciton.

If he followed the guides I posted previously, he should have that set up already.

Webmin frightens me. I've never bothered with it, but I use Putty to SSH to my server all the time (just set it up on my new Nokia E90 :D )
Putty was a brilliant way of forcing me to learn the terminal, which I now love.
WinSCP is great for my dad to upload files to his user account on the server as well, which he uses quite often.

---

### Post by hyper_ch on 2008-02-20
you could setup now mysecureshell and restrict/chroot your dad to his user folder only.

---

