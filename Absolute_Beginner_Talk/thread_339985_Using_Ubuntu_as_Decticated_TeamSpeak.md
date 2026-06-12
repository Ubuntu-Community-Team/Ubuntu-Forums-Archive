---
title: "Using Ubuntu as Decticated TeamSpeak"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by Elte on 2007-01-16
Hello all. I am very new to the Linux world. Some of my friends use it and they say they like it. So bare with me because I've been running windows my whole life. Ok

My Buddy wants to run a Team Speak server that is deticated 24/7. His machine is a PII with a 40gb hard drive. He also has Window$ ME installed on it. ME is prolly one of the worst versions of windows and now it wont connect to his network. So we can to conclusion to try something new. 

My friends told me about ubuntu and say it is a good descision to use it as a deticated TS server. So I figure all I have to do is

*Burn the 6.10 Ubuntu iso to a cd
*Boot up with cd inside. use the GUI ubuntu and install it permanently

Now what do I do from here? How easy is it to conenct to the internet to install Firefox and Teamspeak Server. He is also behind a wired router. I know its not like an .exe file, you have to use commands.](*,) 

*Then I found a tutorial to auto start any program. So all he will ahve to do is put the server in his closet and push the on button. And TS will automatically start.

In reality, would all of this work? Use ubuntu as a decticated server for Team Speak? and dont have any monitors or keyboards attached to computer? Thanks.

---

### Post by evilghost on 2007-01-16
It'll work great, as a matter of fact I used to do just this.

If his router is handing off DHCP it should work fine with the Internet.  Firefox comes loaded with Ubuntu.

Just create a new user called teamspeak, install teamspeark there, and add the startup script to /etc/rc.local

---

