---
title: "Ssh Remote Login -- Please Help"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by Long_Live_Linux on 2007-12-28
Ok, to start off I am a total Noob when it comes to linux. I just downloaded Ubuntu 6.06 from a liveCD and I like it so far. I have been using terminal to try to remotely connect to my Mac; I put in ssh <Username>@<IP ADDRESS>. (My user name consists of two words does that matter) and it says there is an error somewhere. So then I tried this: ssh <User_Name>@<IP ADDRESS> and it asked for a password. When I type in my password it says that it is invalid! I can login just fine on my windows machine using puTTY, but ubuntu will not let me!! 

PLEASE HELP!!!!!:confused:

---

### Post by Dr Small on 2007-12-28
First off, the Mac you are you trying to connect to needs to have openssh-server installed on it.

Second, I don't know about usernames with spaces, so that may be messing things up.

Third, port 22 needs to be opened on the mac, to allow inbound connections to ssh.

Dr Small

---

### Post by (((X))) on 2007-12-28
Remote Desktop connection(krdc) is a tool to remotely login to the other computer. It supports VNC/RDP compatible servers.
It is easy to understand, create an invitation on pc you want to connect to.
Start ''krdc''
type ipaddress of remote desktop +'':0'', like this: 192.168.1.109:0
Press ''connect'', type the code you received from the pc you want to connect to, I use this tool to connect to my kubuntu box.

---

### Post by Trebaruna on 2007-12-28
The fact that it asks for a password and then denies you is encouraging: the two machines seem to be speaking the same language.
Password failure might be due to the space in the username... have you tried putting your username in quotes? I just quickly tried and it does let me in using quotes on my server (although my username doesn't contain spaces). Just for testing, see if a user without spaces in their name can login.

Also, if you just got Ubuntu, why not try the newest version (7.10)? It has lots and lots of improvements over its older siblings.

---

### Post by TheWizzard on 2007-12-28
a username cannot have spaces. 
what does the prompt show when you open a terminal on your mac?

---

### Post by Long_Live_Linux on 2007-12-28
Thank You so much! Putting the user name in quoats worked perfectly! Again, Thanks so much for your fast replies!!!!

---

