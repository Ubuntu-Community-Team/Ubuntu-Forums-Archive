---
title: "Linux Server"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by hawky on 2008-03-08
Hello everyone,

I have decided that I wanted to learn more about networking than the current knowledge that I have regarding my DLink router. Ideally, I would like to use a PC to act as the router, allowing me to setup server's such as a web server, an FTP server, a mail server, etc. But mainly, I'd use it as a way to learn more about security, mostly being able to control the network that I would be in. I also planned to use it for multimedia storage, and to download torrents.

Is a Ubuntu server for me? Should I look into other things such as IPCop? Xserve? Windows Server?

Remember that for me this is a learning experience, so the levels of difficulty aren't really a problem.

Thank you,
Marc

---

### Post by Nythain on 2008-03-08
have used or currently use ubuntu server to do all of that except act as a router because well, my belkin is much more efficient than my old pentium machine in all reality.

in fact, i would say that for what you want to accomplish, ubuntu server is perfect for you... stable, secure, vast amounts of resources and applications, etc... give it a go man

---

### Post by psycardis on 2008-03-08
Are you also planning on using this machine for a desktop or just a server?

Also imho I wouldn't recommend using it as a router, I would just add rules to your existing router to open/redirect ports to that machine. That at least keeps the machine from being totally open to the net.

---

### Post by Dr Small on 2008-03-08
This thread should be moved to [Server Platforms]("http://ubuntuforums.org/forumdisplay.php?f=7").

---

### Post by Nythain on 2008-03-08
bah, untill it gets into the technicalities of how to set up the daemons i think it still falls under:
The perfect starting place to find out more about computers, Linux and Ubuntu.
i mean, right now the question posed was, is this the right step... besides, that thread isnt near as active as this one :P

i've seen much worsely placed threads in the Desktop Environments thread anyways

---

### Post by mrsteveman1 on 2008-03-08
You can certainly use ubuntu server as a network appliance for firewall/routing/web services etc, but its not the easiest thing to maintain, particularly the firewall part.

Once hardy comes out the firewall will be easy because of UFW, and there may be some other tools already available right now for this sort of thing, but i haven't used any of them.

If you just want to get a good server setup for whatever you want, ubuntu server is the place to start for sure. As an entry into maintaining your own router and firewall, you should keep an embedded box for now.

If you want some more control over things you can always load a firmware like [tomato]("http://www.polarcloud.com/tomato") onto your device if it is supported. You can get one of the supported linksys boxes pretty easily (WRT54GL or WRT54G V4 or below). They make nice stable firewalls that can still be experimented with.

---

### Post by hawky on 2008-03-08
thanks for the replies guys,

i've been using ubuntu as my desktop for a few years now, and have been using linux for a while on and off. so i doubt setting up firewall or things related to that are going to be a problem. mostly getting the documentation and the direction as to which programs should be used would be my main concern.

also, i kinda wanted to use the computer as a way to throttle the bandwidth, and do other nifty things such as inspecting packets. that's why i kinda wanted it to be my router, or be before the router. since my router can't do those things.

i also don't plan to use it daily as a desktop, it would mostly be setup once, and then access via other computers to download torrents, change settings etc.

what do you think?

marc

---

### Post by An_Dynas on 2008-03-08
> **mrsteveman1 said:**
> 
Once hardy comes out the firewall will be easy because of UFW, .

I apologize for my ignorance, but could you please explain what in the world this means.

---

### Post by Hendrixski on 2008-03-08
> **hawky said:**
> what do you think?

marc

I think you're about to embark on a very exciting journey of technological discovery!  Remember, the forums are your friends when you have specific questions provided that you've already googled the answer.

---

### Post by hawky on 2008-03-08
> **Hendrixski said:**
> I think you're about to embark on a very exciting journey of technological discovery!  Remember, the forums are your friends when you have specific questions provided that you've already googled the answer.

Thanks, but do you think that using Ubuntu will allow me to throttle the internet for specific computers?

---

### Post by mrsteveman1 on 2008-03-09
UFW is a new script for hardy, [Uncomplicated Firewall]("http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html#more-418"), that will let you easily setup a system to be used as a firewall, like if you wanted to setup an Ubuntu router. Right now you either have to use one of the GUI tools or write iptables rules yourself.

On systems where there is no GUI, like routers and servers, this is a very useful tool.

---

