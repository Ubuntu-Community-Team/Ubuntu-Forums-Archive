---
title: "Should I try to use Ubuntu for a home server??"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by zac_haryy on 2008-02-06
I have had a home server for a couple of years now and I just got 5x1tb hdd's and am wondering how I should set this up.

I have had Windows 2003 Server running on my server computer for those couple of years and it has worked perfect for me. I don't really do much with my server besides let it share me files with the rest of the house. So now that I have these tb hard drives I am wanting to set them up in a RAID 5 array but I would also like to be able to add onto the array in the future, which is something that I believe I can't do in Windows 2003 Server very easily. That's what made me start looking at Linux and realizing that it looked a bit easier to do with Linux, but there is one thing, I am not very good with Linux. I installed Ubuntu as my OS on my desktop machine and tried to force myself to use it but ended up dropping it and moving back to WinXP (which I can work lot better (ease)).

So my lack of knowledge within Linux is limiting me to moving to it. The server machine sits in a room by itself with only a network wire and power wire hooked to it. So is there anyway that I can login to the Linux server through the network from a Windows PC? This is what I have running in my house:
- Windows XP on my main machine
- Windows 2003 Server on my server machine
- I have three laptops running (osX, WinpXP x 2)
- My xbox using XBMC (used all the time to watch videos and such from the server)

So basically I would need to be able to access the server (have access to the files) (be able to login with all if possible) from all of these machines with ease. So really I am thinking about moving to Linux only if I will be able to add to a RAID 5 array down the road, if I can't add onto it then it doesn't matter much to me. I am open to other ideas with what I should do here so if anybody has any please let me know, Thanks!

BTW, I am using two of these cards to hook up the SATA hard drives to my motherboard:
[eBay auction PCI SATA cards]("http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&rd=1&item=250209873044")
So those cards would have to be compatible with ubuntu.

-Zac

---

### Post by hyper_ch on 2008-02-06
You can share the server with samba... that would allow you to locally mount the server shares as network drives in your computers.

---

### Post by njparton on 2008-02-06
I use ubuntu as a home server (see my sig) and it works well.

However, I've also invested in a 3ware hardware raid card to keep my data safe, also allowing me to migrate from raid 1 to raid 5 in the future with the addition of another hard drive.

I've no experience of how reliable linux raid is or whether there are issues when upgrading the distro, which is why I decided to go for hardware raid instead.  Of course this may bring different issues if the card dies...

You just need to decide if you'll need a desktop from time to time (desktop version) or just the command line (sever version).

---

### Post by bwtranch on 2008-02-06
A *nix machine is really what you need. You are right about that or you wouldn't be asking. You are, however, going to have to do some research. No one on this forum will give you all the answers you need. Windows servers suck and that's why all the servers use Linux/Unix.For some friendly support for only $6.95 a month try [www.bluehost.com](www.bluehost.com) they use Unix servers and the support is awesome.

---

### Post by zac_haryy on 2008-02-06
So the server edition is all comand line (I didnt know that)? I really dont want to have to do everything with comand lines as I am completely use to have a nice GUI there for me.

---

### Post by zac_haryy on 2008-02-06
> **bwtranch said:**
> A *nix machine is really what you need. You are right about that or you wouldn't be asking. You are, however, going to have to do some research. No one on this forum will give you all the answers you need. Windows servers suck and that's why all the servers use Linux/Unix.For some friendly support for only $6.95 a month try [www.bluehost.com](www.bluehost.com) they use Unix servers and the support is awesome.

This is just for home usage so I dont really want to have to spend money for support, that's why there is such a great Linux community, right?

---

### Post by Trail on 2008-02-06
You should use a live CD to see if your hardware is recognised. If it isn't, don't bother.

Other than that, you could set up a samba server, for sharing your files in a windows network, and an ssh server for logging in and controlling your machine through a console (and also sharing files if you want). Putty for Windows can handle the ssh connection.

Alternatives are setting up an ftp server for sharing, telnet for controlling, and a vnc server for controlling the machine graphically.

After than that, there is the motto "if it ain't broke, don't fix it, unless it's linux and you are doing it for fun". From what I understand, you don't really need to do the switch, so it's up to how much time and effort you want to spend.

If it's worth it? Well I'd set up a machine with an ssh, samba, ftp, telnet, web, mail and whatever else type of server I need, without an unneeded graphic interface. But then again I am familiar with it, have done it before, and I also know how to take advantage of the extra functionality :) (and cron rules).

---

### Post by zac_haryy on 2008-02-06
The main reason that I was thinking about switching was for the ability to expand a RAID 5 array as I think that I will be adding more tb hard drives within a 1/2 year or so. So I just kind of figured that the hard drives are brand new and not setup much yet that I would try to figure out things right now instead of being stuck with a RAID 5 array that can't be added to.

---

### Post by Trail on 2008-02-06
> **bwtranch said:**
> No one on this forum will give you all the answers you need.

And why is that, if I may ask? ....

@OP: yes the server is by default console only, and I agree with that. But you can install a desktop easily afterwards:

sudo apt-get install ubuntu-desktop 

(or kubuntu-desktop etc depending on your preferences)

---

### Post by bwtranch on 2008-02-06
Re #6 Well true. But, you know, this stuff gets addicting and before you know it. Your're gonna want to have more. You're gonna want to have MySQL and other stuff and learn more about PHP, etc. Been there, done that. What's $6.95 a month anyway for a REAL server?:)

---

### Post by Trail on 2008-02-06
> **bwtranch said:**
> Re #6 Well true. But, you know, this stuff gets addicting and before you know it. Your're gonna want to have more. You're gonna want to have MySQL and other stuff and learn more about PHP, etc. Been there, done that. What's $6.95 a month anyway for a REAL server?:)

An unnecessary cost. If he gets "addicted", he can ask us.

---

### Post by hyper_ch on 2008-02-06
> **zac_haryy said:**
> So the server edition is all comand line (I didnt know that)? I really dont want to have to do everything with comand lines as I am completely use to have a nice GUI there for me.

What do you want a gui for on a server? Most configuration is done through editing config files and for that it doesn't really matter if you open the config files in gedit or nano.

---

### Post by njparton on 2008-02-06
> **zac_haryy said:**
> So the server edition is all comand line (I didnt know that)? I really dont want to have to do everything with comand lines as I am completely use to have a nice GUI there for me.

I use the desktop edition for my server, no problems.  Now that it's setup I've just stopped gdm starting automatically on reboot to save a bit of juice, I can always turn it back on via putty/ssh before logging into an X session remotely.

Go with the desktop edition if you're a n00b :)  Check out "xming" for windows as a nice free X client.

---

### Post by bwtranch on 2008-02-06
Yeah, ok, I like cheap too. What did that array cost? Oh, never mind.  My time is cheap, too. Go with SAMBA. Google for it. Use Add/Remove for the software, if you can't find it there use Synaptic. If you can't find it there unpack a tarball.

---

### Post by AndyCooll on 2008-02-06
There's always this section of our forums that might be of help: [Servers & Security]("http://ubuntuforums.org/forumdisplay.php?f=7").

And this thread in particular: [Useful Links on Servers, System Administration, and Security]("http://ubuntuforums.org/showthread.php?t=681267")

:cool:

---

### Post by zac_haryy on 2008-02-06
I am not going to pay for service as I see no point in it, and I am not out to spend money at all. All that I really need is a server that will make me a RAID 5 array that can watch it constantly and give me information about the array at all times (if something would fail). I just need a machine that will basically let me serve files throughout a internal network. As of right now I have no plans for a web server or anything but would like to within a year or so get something up and running. I would like to be able to remote access the computer to view the information about the drives and such and just make sure that everything is working right.

So really my main need is a OS that will make me a RAID 5 array and allow me to add more hard drives to it in the future. Other then that I will manage to figure out the little things (burning images, seting up a web server, serve files through windows network, etc). I would really like a guide on the RAID 5 setup and how to add to it and everything also. I have found some guides on this, but if anybody knows of some please let me know! Also I am not just stuck on Ubuntu, I will work with any OS to get my RAID 5 going and be able to expand it.

Please let me know what you think! I accept all opinions.

---

### Post by njparton on 2008-02-07
It's probably worth you investing in a 3ware 9650SE series card in that case.  Check out eBay for used examples as they can be quite expensive.  Worth every penny though in my book. 3ware's 3DM2 software allows you to watch the integrity of the array via a browser, even over the web if necessary.

---

