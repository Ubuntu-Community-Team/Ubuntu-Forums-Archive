---
title: "server in multi-platform environment"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by butt3rflyNessa on 2006-10-05
Hello all!
  I have a few questions about Ubuntu server. 

First a little background. I am not a server expert. I am extremely familiar with PC's and Windows/DOS environments (I grew up with DOS), I have some general networking and security knowledge. I am not fluent in UNIX or Linux, but am learning.

I am currently researching options for replacing an old server in a small business environment. There are approximately 30-40 users on the network, running both Apple and PCs, at about a 75%/25 % Apple to PC ratio. The current server is an Apple, which works adequately for all the Apples on the network, but the PCs cannot talk to it without getting specialized software, which can be complicated. There are a few things that the server is going to have to be able to do:
1) Fileserver for PC & Apple
2) Print server for PC & Apple
3) Application sharing for Apple

At this point, the server should be only accesible from within the intranet, although there is a possiblity of in the future providing external access ONLY for a few authorized users via VPN or some other sort of tunneling method.

It has been decided to use PC hardware for the server, but we are still considering options for software. 

How well does Ubuntu server operate in a multi-platform environment? 

How does it compare to Debian or other Linux based server packages in setup, ease of use, security an reliability?

-Vanessa

---

### Post by dmizer on 2006-10-05
as a server, linux will be as reliable as your hardware.  debian is excellent (and lighter) as a server but doesn't have the support community of ubuntu, and doesn't have the hardware support of ubuntu.

if you're connecting the server to a router (which you should be), there should be no problem insuring that the server will not be available to external access.  alternatively, you can configure your iptables via a handy webmin interface.

but i'm not sure linux is your right choice because of your three requirements.  most notably application sharing for apple.  i suspect this aspect will be next to impossible.

print sharing will be a nightmare as well depending on your printer/s.  the printer will need to be able to work in linux, so you'll want to check out cups.org to see if the printer you want to use will be compatible or not.

file server will be no problem using the samba guide in my sig.

---

### Post by rccharles on 2006-10-05
> **butt3rflyNessa said:**
> Hello all!
I am currently researching options for replacing an old server in a small business environment. There are approximately 30-40 users on the network, running both Apple and PCs, at about a 75%/25 % Apple to PC ratio. The current server is an Apple, which works adequately for all the Apples on the network, but the PCs cannot talk to it without getting specialized software, which can be complicated.


Sounds like you are running classic Mac OS on the server.  

The Mac OS X servers have SAMBA built in.  SAMBA is the windows file sharing software.

> 
 There are a few things that the server is going to have to be able to do:
1) Fileserver for PC & Apple
2) Print server for PC & Apple
3) Application sharing for Apple


Mac application have a resource and data fork. Mac OS X has the ability of splitting files in a resource and data fork on vfat file systems.  Perhaps you could split the files and put them on the Ubuntu server.
> 

At this point, the server should be only accesible from within the intranet, although there is a possiblity of in the future providing external access ONLY for a few authorized users via VPN or some other sort of tunneling method.

It has been decided to use PC hardware for the server, but we are still considering options for software. 


Macs now run on Intel hardware.


Have you looked the software price?  Microsoft has a per clien fee. 

Apple has a client and a server distribution.  The client distribution contains all the frequently used server software.  The server distribution contains easy to use software for managing a client computer network.

I assume you have a Mac OS X client.  On the Mac OS client, goto:
system peferences -> sharing.  Turn on:

 windows file sharing ( samba )
 printer sharing ( cups )


goto:
 system perferences -> network  to find out your ip address


You can do the same thing with Ubunto.  I'd install the desktop version for playing around at first.  They way you can do things from the gui.


On a windows box check out how well the sharing of the files and printers work


Oh, can't test drive windows. 


Robert



And

---

### Post by butt3rflyNessa on 2006-10-05
Thank you for the prompt replies!

Personally, most my experience is with Windows. I have rarely used Mac/Apple and am in the process of learning them because in my new job I am expected to troubleshoot Mac and PC problems.

On the current Mac server, every time we have turned windows file sharing on, the network grinds to a halt because the server starts eating up excessive amounts of bandwidth.
The server is an older machine that was set up because someone said, "Hey we should have a server." There was no real plan in place for support/upgrades/backup etc.

As for application sharing on the Mac, I may try and just leave the old server up for apple applications only. Over the next few years, as computers are replaced, I am hoping to convert the majority over to PC, for various reasons. There will always be Macs on the network though, anyone who can justify their need for a Mac will continue to use them.

At this point, the biggest issues are print and filesharing.
I think I will set up Ubuntu on a networked PC and play around with it for a bit to get a feel for how it works.

---

### Post by rccharles on 2006-10-06
> **butt3rflyNessa said:**
> Thank you for the prompt replies!

Personally, most my experience is with Windows. I have rarely used Mac/Apple and am in the process of learning them because in my new job I am expected to troubleshoot Mac and PC problems.


I'd suggest using a Mac OS and Unbuntu for a month each and see what you like. With the new intel based Macs and a program called  Parrallels you can run Windows and Ubuntu in a virtual machine.  

[http://www.parallels.com/en/products/desktop/](http://www.parallels.com/en/products/desktop/)

> 

On the current Mac server, every time we have turned windows file sharing on, the network grinds to a halt because the server starts eating up excessive amounts of bandwidth.
The server is an older machine that was set up because someone said, "Hey we should have a server." There was no real plan in place for support/upgrades/backup etc.


You might want to check with:
  [http://groups.google.com/group/comp.sys.mac.system](http://groups.google.com/group/comp.sys.mac.system)



Robert

---

