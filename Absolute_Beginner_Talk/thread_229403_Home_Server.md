---
title: "Home Server"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by derouge on 2006-08-04
I just want to know if this is possible before I go out and buy a network card ..

My family would like to setup a "server" so that we can share files between our five computers more easily. We have two PCs at my mom's house and a company laptop, one PC at my dad's house, and my brother's laptop which he is taking to college. It's a pain to always be transferring documents between the various computers, so I'm hoping to solve that. 

The limiting factor (maybe?) is that the server cannot be the domain controller. My mom's company laptop needs to remain invisible to the network so her firewall doesn't cause issues. What we're doing currently is her laptop is connected to the router. The other two computers have wireless cards and connect to the router through a switch. As you can tell I'm not very networking savvy so I hope that made sense. ;)

My dad is directly connected to his hi-speed cable internet, and I'm assuming my brother's connection will be similar. I think pretty much what we need is a server who's HDD can be accessed by all the computers through a desktop shortcut.

I'll list the computer's and their OS's below, just in case they're needed

Mom's House: company laptop with Windows XP Pro, Dell PC with Windows XP Home, Dell PC with Dapper Drake
Dad's House: Emachine PC with Windows XP Home
College Laptop: Windows Media Center

---

### Post by kb3hkg on 2006-08-04
I am guessing you are doing this behind a dynamic IP broadband connection, and then running NAT locally. If so it will be very difficult to get this working between the seperate locations. NAT is not designed to have servers to the outside world running within it.

---

### Post by T700 on 2006-08-04
> **kb3hkg said:**
> I am guessing you are doing this behind a dynamic IP broadband connection, and then running NAT locally. If so it will be very difficult to get this working between the seperate locations. NAT is not designed to have servers to the outside world running within it.

He could use a service like the free NoIP.com + port forwarding.  He'd have to be very careful to configure it properly, for security.

Paul

---

### Post by patrick295767 on 2006-08-04
If you manage to avoid the NAT (  'impossible' thing to pass) & to be in the same network:

If you need server for windoze machine, it s the samba that you need. 
 
In case you wanna set up too a server for linux/ mac/ unix machines, you may use the nfs.
Nfs is faster than samba. 
nfs how to : [http://www.ubuntuforums.org/showthread.php?p=1338551#post1338551](http://www.ubuntuforums.org/showthread.php?p=1338551#post1338551)

--
If you make the trial of erasing Windoze Partitions, after some time, you'll realize that Linux is much much better & allmighty OS !

---

### Post by patrick295767 on 2006-08-04
> **T700 said:**
> He could use a service like the free NoIP.com + port forwarding.  He'd have to be very careful to configure it properly, for security.

Paul
 
I never managed to pass NAT via ports 80 (or fully).
PC -80-- NAT -------- INTERNET ---------- NAT ------80 --- PC
You have any how to ?

--
I quite am sure that in his college (certainly under a NAT) they wont let him to have port forwarding. It wont be easy...

---

### Post by stormblue on 2006-08-04
This is what I would do.

1. Set up Ubuntu server with FTP server, webserver, Ubuntu Center:Hive.  Any would do it's up to you.

2. Run no-ip.com's client on your server and have a static domain name. For example you could get smithfamily.fileserver.com or something similar

3. Use Port forwarding on the router to forward the ports you need to get it working.

One small thing to be aware of is some ISP's don't like you using port 80 for a webserver and will block it.  Simply change your domain to smithfamily.fileserver.com:8080 or something similar.  I think solution would work for you.

---

### Post by patrick295767 on 2006-08-04
> **derouge said:**
> I just want to know if this is possible before I go out and buy a network card ..

My family would like to setup a "server" so that we can share files between our five computers more easily. We have two PCs at my mom's house and a company laptop, one PC at my dad's house, and my brother's laptop which he is taking to college. It's a pain to always be transferring documents between the various computers, so I'm hoping to solve that. 

The limiting factor (maybe?) is that the server cannot be the domain controller. My mom's company laptop needs to remain invisible to the network so her firewall doesn't cause issues. What we're doing currently is her laptop is connected to the router. The other two computers have wireless cards and connect to the router through a switch. As you can tell I'm not very networking savvy so I hope that made sense. ;)

My dad is directly connected to his hi-speed cable internet, and I'm assuming my brother's connection will be similar. I think pretty much what we need is a server who's HDD can be accessed by all the computers through a desktop shortcut.

I'll list the computer's and their OS's below, just in case they're needed

Mom's House: company laptop with Windows XP Pro, Dell PC with Windows XP Home, Dell PC with Dapper Drake
Dad's House: Emachine PC with Windows XP Home
College Laptop: Windows Media Center

What are the open ports in your college ? 
[PC_COLLEGE : PORTS? ]--------- INTERNET

---

### Post by stanz on 2006-08-04
Some reading, That might be helpful...

[UbuntuWirelessRouter]("https://help.ubuntu.com/community/UbuntuWirelessRouter")
[Ubuntu Server Guide]("https://help.ubuntu.com/ubuntu/serverguide/C/index.html")
 [LAMP Server]("https://help.ubuntu.com/community/ApacheMySQLPHP")
[Lamp for Newbies]("http://www.howtoforge.com/lamp_installation_ubuntu6.06")
[Setting Up Server]("http://www.linuxforums.org/servers/setting_up_a_server.html")
[Hosting]("https://help.ubuntu.com/community/WebServerHosting?")

You may have to adjust your design ideas/thoughts...
Ha... abunch of pros have entered the room...I bow & back away :)

---

### Post by stormblue on 2006-08-04
> **patrick295767 said:**
> What are the open ports in your college ? 
[PC_COLLEGE : PORTS? ]--------- INTERNET

It shouldn't matter in college.  He'd be allowed to FTP out, and port 80 is going to be open out.  Just host it at the house with the router.  Problem solved.

---

### Post by patrick295767 on 2006-08-04
> **stormblue said:**
> It shouldn't matter in college.  He'd be allowed to FTP out, and port 80 is going to be open out.  Just host it at the house with the router.  Problem solved.

I hope ! I recall at school I had all port blocks, ftp out too, but 80. Only 8080 were possible. And even worst, the access of some websites were blocked too... Imagine the pain in the ... like geocities for instance
  
Admin are crazy sometiems or parano...

---

### Post by stormblue on 2006-08-04
Well he can at least garuntee port 80 isn't blocked.  That'd allow for Hive and a webserver.  


Admins can be a bit crazy at times, but we can at least assume that port 80 will be open going out.  So will e-mail ports and IM ports too most likely.

---

