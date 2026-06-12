---
title: "Router Confusion"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by mconway0003 on 2007-02-20
Hey guys,

I was wondering if anyone could tell me what this command means, and what the information displayed after I executed the command means...



```
 GET / HTTP/1.0

<HTML>
<HEAD>
<TITLE>Directory /</TITLE>
<BASE HREF="file:/">
</HEAD>
<BODY>
<H1>Directory listing of /</H1>
<UL>
<LI><A HREF="./">./</A>
<LI><A HREF="../">../</A>
<LI><A HREF="bin/">bin/</A>
<LI><A HREF="boot/">boot/</A>
<LI><A HREF="cdrom/">cdrom/</A>
<LI><A HREF="dev/">dev/</A>
<LI><A HREF="etc/">etc/</A>
<LI><A HREF="home/">home/</A>
<LI><A HREF="initrd/">initrd/</A>
<LI><A HREF="initrd.img">initrd.img</A>
<LI><A HREF="initrd.img.old">initrd.img.old</A>
<LI><A HREF="lib/">lib/</A>
<LI><A HREF="lost%2Bfound/">lost+found/</A>
<LI><A HREF="media/">media/</A>
<LI><A HREF="mnt/">mnt/</A>
<LI><A HREF="opt/">opt/</A>
<LI><A HREF="proc/">proc/</A>
<LI><A HREF="root/">root/</A>
<LI><A HREF="sbin/">sbin/</A>
<LI><A HREF="srv/">srv/</A>
<LI><A HREF="sys/">sys/</A>
<LI><A HREF="tmp/">tmp/</A>
<LI><A HREF="usr/">usr/</A>
<LI><A HREF="var/">var/</A>
<LI><A HREF="vmlinuz">vmlinuz</A>
<LI><A HREF="vmlinuz.old">vmlinuz.old</A>
</UL>
</BODY>
</HTML>

<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en-US" lang="en-US">
<head>
<title>HTTP.COM</title>
<meta  name="description" content="" />
<meta  name="keywords" content="" />
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">
</head>
<frameset rows="*,0" frameborder="NO" border="0" framespacing="0">
  <frame name="mainFrame" src="http://www.searchmachine.com/index-http.html">
</frameset>
<noframes>
<body bgcolor="#FFFFFF">
Please visit <a href="http://www.searchmachine.com/index-http.html">this link</a> since your browser does not support frames.
</body>
</noframes>
</html>

```


Thanks,
MC

---

### Post by ashmew2 on 2007-02-20
Yo , which command did u run for getting that output and its completely HTML-based , are u doing soething like web-designing ?

---

### Post by mconway0003 on 2007-02-22
Hey, this is the forum that I got the idea from and 

 mssever  
Grande Half-n-Half Cinnamon Ubuntu
   Join Date: Jun 2006
Location: /dev/chair
Beans: 994
Ubuntu 6.10 Edgy User
   

 
Re: Cant log on to my router set-up page 

--------------------------------------------------------------------------------

Quote:
Originally Posted by Epperly  
> I just got a new WRT54G ver. 6 and I can't access 192.168.1.1 at all, I called up Linksys and they said their router "is not compatible with Linux" 

That's the same router I have, and I can assure you that it's compatible with Linux. What does Linksys tech support know?  I've confused my share of their techs.

if you type [http://192.168.1.1](http://192.168.1.1) into your browser you should be able to access it. If you can't, double-check your connection to the router. Failing that, restart networking: 

```
sudo /etc/init.d/networking restart 
```> You can also use telnet to troubleshoot your connection by talking directly to the router. Type 

```
telnet 192.168.1.1 80
```> You should see something like 
```
Trying 192.168.1.1...
Connected to 192.168.1.1.
```
Escape character is '^]'.> If you don't, then you're not able to connect to the router at all. If you see that, type the following (NOTE: there won't be any prompt!). "<enter>" means to hit enter. Note also that your backspace key doesn't work here; if you make a mistake, you have to start over from scratch. 

```
GET / HTTP/1.0<enter><enter>If the first line of the output looks like "HTTP/1.0 401 Unauthorized Access Denied" then your connection is fine and the router is working fine. In that case, the problem is with your browser.
```
__________________
Registered Linux user #419974. 

--------------------------------------------------------------------------------
Last edited by mssever : November 30th, 2006 at 07:34 AM. 
    

mssever 
View Public Profile 
Send a private message to mssever 
Send email to mssever 
Visit mssever's homepage! 
Find all posts by mssever 
Add mssever to Your Buddy List 

  #22       1 Day Ago  
mconway0003  
5 Cups of Ubuntu
   Join Date: Dec 2006
Beans: 31 

 
 Re: Cant log on to my router set-up page 

--------------------------------------------------------------------------------

Quote:
Originally Posted by mssever  
That's the same router I have, and I can assure you that it's compatible with Linux. What does Linksys tech support know?  I've confused my share of their techs.

if you type [http://192.168.1.1](http://192.168.1.1) into your browser you should be able to access it. If you can't, double-check your connection to the router. Failing that, restart networking: 
Code:
sudo /etc/init.d/networking restartYou can also use telnet to troubleshoot your connection by talking directly to the router. Type 
Code:
telnet 192.168.1.1 80You should see something like 
Code:
Trying 192.168.1.1...
Connected to 192.168.1.1.
Escape character is '^]'.If you don't, then you're not able to connect to the router at all. If you see that, type the following (NOTE: there won't be any prompt!). "<enter>" means to hit enter. Note also that your backspace key doesn't work here; if you make a mistake, you have to start over from scratch. 
Code:
GET / HTTP/1.0<enter><enter>If the first line of the output looks like "HTTP/1.0 401 Unauthorized Access Denied" then your connection is fine and the router is working fine. In that case, the problem is with your browser. 

I tried it with telnet and all I got was this...

telnet 192.168.1.1
Trying 192.168.1.1...
telnet: Unable to connect to remote host: Connection refused

So does this mean that even though I'm hardwired to my Linksys router, my computer thinks that it's directly connected to my cable modem?

---

### Post by steve.horsley on 2007-02-22
So I presume that the command that you entered was 
**telnet 192.168.8.1**
followed by 
**GET / HTTTP/1.0**

But it looks very much like a linux system you've connected to, and not a Linksys router. I wonder if you have connected to a web werver on your own box. What is your own IP address? Find it with the command
**ifconfig**
Actually, posting the output of the command 
**ip route list**
woud be helpful. Also the output from
**netstat -ltn**

---

### Post by mconway0003 on 2007-02-22
> **steve.horsley said:**
> So I presume that the command that you entered was 
**telnet 192.168.8.1**
followed by 
**GET / HTTTP/1.0**

But it looks very much like a linux system you've connected to, and not a Linksys router. I wonder if you have connected to a web werver on your own box. What is your own IP address? Find it with the command
**ifconfig**
Actually, posting the output of the command 
**ip route list**
woud be helpful. Also the output from
**netstat -ltn**


Here it is, thanks
```

marcus@Marcus:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:20:E0:69:AA:37  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::220:e0ff:fe69:aa37/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30819 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17540 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14136087 (13.4 MiB)  TX bytes:2885009 (2.7 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

marcus@Marcus:~$ netstat -itn
Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0   1500 0     30826      0      0      0    17546      0      0      0 BMRU
lo    16436 0         2      0      0      0        2      0      0      0 LRU
marcus@Marcus:~$ 
```

---

### Post by steve.horsley on 2007-02-23
Can you confirm that the telnet connection was to IP address 192.168.1.1? That would seem not to be your own machine, which looks to be 192.168.1.101. If it really is the router, then I would say the router is knackered, faulty, stuffed, snafu and broken. 

Can you confirm that when you try to browse the router with our web brwser, [http://192.168.1.1](http://192.168.1.1) you get a directory listing? That would tent to confirm what you are seeing with the telnet connection. Anything different would suggest we're getting conflicting info for some reason. 

However, I don't see why a router would ever try to send you a frameset from [www.searchmachine.com](www.searchmachine.com), so I'm still not sure we're getting the whole truth. I have to ask again, are you sure the IP address you connected to with that telnet connection was the IP address of the linksys router? 

The other two commands I asked for were:
**netstat -ltn ** 
(that's a lower-case L), which will tell me if your own Linux box is listening for HTTP connections - I was wondering if you were perchance connecting to yourself, and
**ip route list**
which will tell me both your IP address and that of your default gateway.

In summary, that stuff you got with telnet wasa a file listing from a linux based web server. It may have been your own machine, it might have been a different machine, but if it was from a router then that router is busted. Another possibility I suppose is that the router and a Linux box have the same IP address, in which case you may be talking to the Linux box when you thing you're talking to a router.

---

### Post by mconway0003 on 2007-02-23
> **steve.horsley said:**
> Can you confirm that the telnet connection was to IP address 192.168.1.1? That would seem not to be your own machine, which looks to be 192.168.1.101. If it really is the router, then I would say the router is knackered, faulty, stuffed, snafu and broken. 

Can you confirm that when you try to browse the router with our web brwser, [http://192.168.1.1](http://192.168.1.1) you get a directory listing? That would tent to confirm what you are seeing with the telnet connection. Anything different would suggest we're getting conflicting info for some reason. 

However, I don't see why a router would ever try to send you a frameset from [www.searchmachine.com](www.searchmachine.com), so I'm still not sure we're getting the whole truth. I have to ask again, are you sure the IP address you connected to with that telnet connection was the IP address of the linksys router? 

The other two commands I asked for were:
**netstat -ltn ** 
(that's a lower-case L), which will tell me if your own Linux box is listening for HTTP connections - I was wondering if you were perchance connecting to yourself, and
**ip route list**
which will tell me both your IP address and that of your default gateway.

In summary, that stuff you got with telnet wasa a file listing from a linux based web server. It may have been your own machine, it might have been a different machine, but if it was from a router then that router is busted. Another possibility I suppose is that the router and a Linux box have the same IP address, in which case you may be talking to the Linux box when you thing you're talking to a router.

Hey sorry, i thought it was an i for some reason ha. But I can just tried to telnet 192.168.1.1 80 as well as netstat -ltn and ip route list

```
marcus@Marcus:~$ telnet 192.168.1.1 80
Trying 192.168.1.1...
Connected to 192.168.1.1.
Escape character is '^]'.
Connection closed by foreign host.
marcus@Marcus:~$ netstat -ltn
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:2784          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:2208          0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
marcus@Marcus:~$ ip route list
192.168.1.0/24 dev eth0  proto kernel  scope link  src 192.168.1.102 
default via 192.168.1.1 dev eth0 
marcus@Marcus:~$ 
```


Thanks again

---

### Post by steve.horsley on 2007-02-23
Rumbled it!

I tried to do the telnet trick to a a linksys router here. I got the same result as you! But I finally figured out that the router closes the telnet call a few seconds after you connect with telnet. So the command **GET / HTTP/1.0** is accepted by the shell. And if you type that command into the shell, you get the file list that you see. It's not coming from the router at all. There is a program GET in Ubuntu - use the command **man GET** to read about it.

So I can't tell you anything about your router other than you shoud be able talk it by entering this URL into your browser:
[http://192.168.8.1](http://192.168.8.1)

---

### Post by mconway0003 on 2007-02-27
> **steve.horsley said:**
> Rumbled it!

I tried to do the telnet trick to a a linksys router here. I got the same result as you! But I finally figured out that the router closes the telnet call a few seconds after you connect with telnet. So the command **GET / HTTP/1.0** is accepted by the shell. And if you type that command into the shell, you get the file list that you see. It's not coming from the router at all. There is a program GET in Ubuntu - use the command **man GET** to read about it.

So I can't tell you anything about your router other than you shoud be able talk it by entering this URL into your browser:
[http://192.168.8.1](http://192.168.8.1)

Hey, what exactly is GET going to accomplish? Also, I tried 192.168.8.1 and nothing happens, it just loads forever. Any suggestions? 

Also this is what I tried, not sure I'm even close to doing it right though...

```
marcus@Marcus:~$ man get
Reformatting GET(1p), please wait...
marcus@Marcus:~$ man GET
Reformatting GET(1p), please wait...
marcus@Marcus:~$ get 192.168.1.1
bash: get: command not found
marcus@Marcus:~$ GET 192.168.1.1
500 Server closed connection without sending any data back
marcus@Marcus:~$ GET 192.168.8.1

marcus@Marcus:~$ GET 192.168.8.1 -C : admin

marcus@Marcus:~$ telnet 192.168.8.1
Trying 192.168.8.1...
```



Thanks 
MC

---

