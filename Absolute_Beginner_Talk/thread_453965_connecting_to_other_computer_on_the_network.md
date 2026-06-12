---
title: "connecting to other computer on the network"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by Dave B on 2007-05-24
First let me say that i have theroughly enjoyed the UBUNTU experience.  

I am trying to connect to another computer(windows) through the net.

can you please help 

Dave

:popcorn:

---

### Post by scrooge_74 on 2007-05-25
if both computers are in the same IP range and you have share folders in the windows system, plus they belong to the same network group, then clicking on network should let you see the windows share.  This is what you are doing using the samba client

To see the ubuntu system you need to install and configure the samba server

---

### Post by ffderrick on 2007-05-25
I'm guessing that your connecting through a home network and not using the internet for a remote connection.  The first is usually pretty easy with ubuntu.  Click on Places and then click Network.  Your existing windows network should be visible.  A remote connection I haven't tried yet, but I know it's possible.
Hope this helps.
Derrick

I'm not sure if samba is installed by default.   Install samba with (add programs) if the above does not work for you.

---

### Post by Dave B on 2007-05-25
the windows network shows up but i cant see any of the machines on the net

---

### Post by scrooge_74 on 2007-05-25
Remember to give the same group name to all PCs, also check that your windows firewall allows connection from your internal network.  

Also if you are by any chance using Firestarter to manage your firewall settings in Ubuntu you are going to need to check this info  [http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138](http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138)

---

