---
title: "I cannot start apache2"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by emprog on 2006-09-09
When just trying to start apache with apache2 -k start I get this error message back.

erick@wolf:/etc/init.d$wolf:/etc/init.d$ sudo apache2 -k start
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
erick@wolf:/etc/init.d$

I was having problems with apache before but I think this is the problem?

---

### Post by jordanmthomas on 2006-09-09
I am pretty sure it started.  Test it out and see.
[http://127.0.0.1](http://127.0.0.1)

---

### Post by emprog on 2006-09-09
Yes you are correct, localhost opens my site. I just assumed since I cannot open my site outside my network maybe it was not running. Now I know that it is running I'm completely lost as to why it wont open outside my network.

---

### Post by jordanmthomas on 2006-09-09
Are you behind a router?
If so, have you forwarded port 80 to your IP?

---

### Post by emprog on 2006-09-09
I have a router and I believe I did this correctly. Here are my settings.

name: http
ip: 192.168.0.105
port start: 80
port end: 80
traffic type: TCP
schedule: always

I then created a dyn dsn account with emarquez.homelinux.net directing over to what (whatismyipaddress) gave me. Now within my local network I can open my site using either of the following... localhost, 127.0.0.1, 192.168.0.105 emarquez.homelinux.net or the ip given my whatismyipaddress. However, my dad is not on our network and uses dial up so I try to access my site through his computer but I get nothing. :/

---

### Post by jordanmthomas on 2006-09-09
Well, I have no idea what is wrong.  Everything seems to be in order.  Can your dad get in by going to what (whatismyipaddress) gave you.  If not, then the problem is before anything to do with you dyn dsn account.

---

### Post by emprog on 2006-09-09
I have tried that using his computer but it does not open my site. I heard something about isp's blocking port 80 so I will call them to see if this is the problem. If they block it do I just need to change the port in ports.conf? Or would I also have to change the settings in the router? port start and port end would both be set to something else like 1111?

---

### Post by jordanmthomas on 2006-09-09
Yes.  I haven't used apache in a while, so I can't remember if it is in ports.conf or in the main conf file.

Either way, it isn't that difficult and it should be easy to figure out.  It's true that a lot of ISP's do block port 80 so that very may well be what is wrong.  

And you were right about reconfiguring your router.

---

### Post by emprog on 2006-09-09
Thanks a lot for the help, I will try it.

---

### Post by emprog on 2006-09-09
I tried to call my isp many times today but they seem very busy so I get disconnected. Must be because adelphia is moving over to time warner? Anyways, I thought I would try another port so I edited ports.conf changing 80 to 1111. I then opened up my router settings and changed port start 80 to port start 1111, and I changed port end 80 to port end 1111. But this too does not work outside my network. I think I have a smaller problem I'm overlooking. After I changed the port in ports.conf I tried restarting apache but this is what I got.

erick@wolf:/etc/apache2$ apache2 -k restart
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd not running, trying to start
(13)Permission denied: apache2: could not open error log file /var/log/apache2/error.log.
Unable to open logs
erick@wolf:/etc/apache2$

Could this have something to do with the problem?

---

### Post by jordanmthomas on 2006-09-09
you forgot sudo when starting apache.  Also, you may need to do this instead since you edited the files
```
sudo /etc/init.d/apache2 force-reload
```

Remember, after doing this, you'll need to tack on :1111 to your IP if you're going that route
ie
[http://192.168.1.105:1111](http://192.168.1.105:1111)
[http://127.0.0.1:1111](http://127.0.0.1:1111)

I'm not so sure about emarquez.homelinux.net though.  You may need to let them know you've changed ports?

---

### Post by emprog on 2006-09-09
I feel closer to getting this to work. When I entered the command you showed me this is what I got back from terminal.

erick@wolf:/etc/apache2$ sudo /etc/init.d/apache2 force-reload
Password:
 * Forcing reload of apache 2.0 web server... apache2: Could not determine the server's fully qualified domain name, using 127 .0.1.1 for ServerName
apache2: Could not determine the server's fully qualified domain name, using 127 .0.1.1 for ServerName
                                                                         [ ok ]
erick@wolf:/etc/apache2$


Now the only way I can access my site within my network is adding the port 1111 like you said. So I know my port forwarding is working right? Very interesting as to why it still cannot be accessed outside my network. I tried my local ip:1111 and even whatismyip:1111 but still only works within my network. This is so weird. I appreciate all the help by the way, I am not much of a networking person.

---

### Post by jordanmthomas on 2006-09-09
I'm not a big networking person either, and unfortunately I've done everything to help that I can think of (which really wasn't much).  

Now that I think of it, it may be your port forwarding that is messed up.  This would explain why outsiders can't get in

Try going to [http://www.portforward.com/routers.htm](http://www.portforward.com/routers.htm) to make sure you are forwarding your ports correctly.

Good luck!

---

### Post by emprog on 2006-09-09
Thanks for the link, it seems as I did it correctly, however it mentioned I need to first set a static ip address but only shows how to do it with windows and mac. Do you know how I can set up a static ip address in ubuntu?

EDIT: I found an older thread on this I will try to follow, thanks!

---

### Post by jordanmthomas on 2006-09-09
System --> Administration --> Networking
Select your card and go to properties.
You can set a staic IP here.

---

### Post by az on 2006-09-09
> **emprog said:**
>  I can open my site using either of the following... localhost, 127.0.0.1, 192.168.0.105 emarquez.homelinux.net or the ip given my whatismyipaddress. However, my dad is not on our network and uses dial up so I try to access my site through his computer but I get nothing. :/

Your ISP is blocking port 80.

---

### Post by emprog on 2006-09-09
Hi, yes but I believe I changed the port correctly? I edited ports.conf from 80 to 1111 and changed it also in my router settings so now to access my site I use ip:1111 but it still wont work outside my network.

---

### Post by emprog on 2006-09-09
jordanmthomas, thanks. Do I set any ip I want? like 192.168.0.111? And what about the other fields like gateway ip, mask? Sorry for so many questions.

---

### Post by jordanmthomas on 2006-09-09
run this in a terminal
```
ifconfig etho
```
You should be able to use the values from there when setting your static address.

There's no such thing as too many questions.  If I didn't want to answer them, I wouldn't.

**edit**
And, yes, you can set whatever IP you want.  Just make sure your router knows it's you.

---

### Post by emprog on 2006-09-09
eth0      Link encap:Ethernet  HWaddr 00:90:F5:33:72:B4
          inet addr:192.168.0.105  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::290:f5ff:fe33:72b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21032 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10167 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:16845065 (16.0 MiB)  TX bytes:1348638 (1.2 MiB)
          Interrupt:11 Base address:0x6000


Would my gateway be what is returned from whatismyip? or is it listed here? Also, you mentioned to make sure my router knows of the static ip so I would have to add this into my router settings correct?

---

### Post by jordanmthomas on 2006-09-09
Your gateway would be the address of your router (likely 192.168.1.1)
You would need to tell the router which MAC address gets the IP.  I can't tell you how to do that for your router, but it should be in there somewhere.

---

### Post by emprog on 2006-09-09
I assume I successfully created a static ip because I can still go online. I set it to 192.168.0.222 so I can access my site with that ip and 1111 as the port. Still no luck outside my network so I guess the last thing to do would be setting the router to this ip which I was not able to do. I will google for some instructions for my router which is a D-Link WBR-2310. Somehow though I feel this is not the problem because before I set a static ip my dynamic did not change in all the time I was testing things out so I am so lost as to why this will not work. I really cannot think of anything else to try. My isp cannot be blocking a port I set, I also dissabled the router firewall and clearly directed for 1111 to forward to my ip. This is so strange but I'm sure there is some small reason as to why it's not working. I appreciate all the help you have given me though.

---

### Post by jordanmthomas on 2006-09-09
I guess you might just have to keep talking to your ISP to see if there may be something weird on their end.  

Or maybe somone else knows what the problem is...

---

### Post by emprog on 2006-09-09
One last thing. When browsing some settings in my router I came across a field similar to port forwarding.

***
Virtual server Rules :
The Virtual Server option allows you to define a single public port on your router for redirection to an internal LAN IP Address and Private LAN port if required. This feature is useful for hosting online services such as FTP or Web Servers.
***

Would I also need to set this? Not only the port forwarding? It looks the same as port forwarding but instead of port start and port end it says port public and port private. Would I also set those both to 1111?

---

### Post by jordanmthomas on 2006-09-10
Shouldn't hurt and it does seem relevant...

Sorry it took a while to reply, the forums are a little screwy for me here.

---

### Post by emprog on 2006-09-10
no problem, just for sake of completeness I will add that it was wishfull thinking. It didn't work but I will try to contact my isp tomorrow. Maybe they can give me some clues.

---

