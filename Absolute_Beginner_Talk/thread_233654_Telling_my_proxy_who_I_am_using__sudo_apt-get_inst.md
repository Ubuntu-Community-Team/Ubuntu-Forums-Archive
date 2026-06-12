---
title: "Telling my proxy who I am using  sudo apt-get install"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by Uber_Puc2ion on 2006-08-10
HI
'nother n00b, I have a functioning linux system for the first time ever and I am as chuffed as anything.

I am on Ubuntu (Dapper Drake) and I use a windows proxy that requires authentication, I have been to the network proxy setting under system preferences, but there is no field for username and password.   My firefox prompts me so it works fine but when i try to use sudo apt-get install type commands in the termial the proxy gives me the finger, an I tell the atp thing what my username and pasword are or have I missed something along the way... I have read hundereds and more forums and how tos and stuff... stuck

---

### Post by arjun.shankar on 2006-08-10
Give this command before calling apt-get:

**export http_proxy=http://username:secretword@proxyIP:ProxyPortNumber/**

For example, if your proxy username is "spectre" and password is  "ubunturules", and your proxy 172.16.16.2 serves on port 3128:

**export http_proxy=http://spectre:ubunturules@172.16.16.2:3128/**

Does it work?

If it does, you can permanently export http_proxy by adding the above line at the end of your /etc/profile. You wont need to type it anymore.

---

