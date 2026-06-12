---
title: "[SOLVED] Repository index"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by boldexplorer on 2007-07-05
Hello, 
I have just installed Ubuntu 7.04 on my laptop and all seems to be well. I can not, however, connect to the server to update my repositories.

I am connected to the internet through my campus net work and Firefox is working fine. When I try running the Update manager it gives me an error saying: 
[I]Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences. [/I]
[I]
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory[/I]

When I tried running it through the terminal the terminal reads:
[I]brett@brett-laptop:~$ sudo apt-get update
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg    
  Could not connect to archive.ubuntu.com:80 (91.189.88.31), connection timed out [IP: 91.189.88.31 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_ZA
  Could not connect to archive.ubuntu.com:80 (91.189.88.31), connection timed out [IP: 91.189.88.31 80]
0% [Connecting to archive.ubuntu.com (91.189.89.6)] 
[/I] 

what am I doing wrong and how does one fix it? 
cheers

---

### Post by tartarian on 2007-07-05
Its possible that the proxy on your campus is blocking the repositories
If it is that, then you can't do anything about it
Mine at school did that
Had to talk to my network admin
Maybe you should go and pop him a visit?

---

### Post by coolen on 2007-07-05
Did you need to use any proxy settings for Firefox? If so, copy them into System -> Preferences -> Network Proxy.
apt-get should work after that, although Synaptic uses its own proxy settings, so you'll need to put them in again to get it working.

If not...talk to someone in charge.

---

### Post by por100pre1 on 2007-07-05
You can also tweak the Software Origins Administration to use another Ubuntu repositories server, even use a faster one.

---

### Post by boldexplorer on 2007-07-05
Cheers guys!
 I have managed to sort out the problem! The campus was blocking the server from which I was trying to download from! There is a mirror site that seems to be working! Yay!! 

Thanks for you help!

Have a great day and awesome weekend!
ciao!

---

