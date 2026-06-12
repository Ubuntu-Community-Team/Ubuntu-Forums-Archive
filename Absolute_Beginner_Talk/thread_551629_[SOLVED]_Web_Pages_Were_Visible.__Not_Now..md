---
title: "[SOLVED] Web Pages Were Visible.  Not Now."
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by skeeler on 2007-09-15
Hello everyone.  I apologize if this question has been asked before, but I couldn't find my exact issue by using the search function.
 
I'm trying to build a web server as an educational project for myself (and so my family can have its own web presence):

1  I've set up a desktop with Ubuntu (Fiesty) Server Edition.  I installed lamp during OS installation.

2  The server has a statuc IP address of 192.168.0.2 on my home network (192.168.0.0).  (My router's address is 192.169.0.1.)

3  I've set up port forwarding on my router so port 80 (http) and 20-21 (FTP) are forwarded to my server address.

4  I have installed Samba and Firestarter.  Firestarter is configured to allow HTTP, FTP, Samba, and a few other services to everyone.

5  I own a domain name, lets call it [www.mydomain.com](www.mydomain.com), and have set up ez-ipupdate to update my DNS servers with the external IP address of my router, since I didn't spring for a static IP from my ISP.

Last weekend, when I last worked on the project, I was able to to not only see my test web page from inside my network by typing 192.168.0.2 into the address bar of my browser, but also by typing in the FQDN, [www.mydomain.com](www.mydomain.com).

This weekend, I booted up the server, so I could start adding real content, and I was unable to see the test page from computers on this network, even when typing in the internal IP address ofthe server.  I even tried viewing the pages by typing the IP address of the server in the server's browser, but that didn't work either.

Can anyone suggest where I should look for the source of my problem?  I'm quite new to this kind of project, and I would greatly appreciate any guidance you could give me.

---

### Post by Mud.Knee.Havoc on 2007-09-15
Go to one of the other computers in the network and try pinging 192.168.0.2.  
Also try pinging your [www.yourdomain.com](www.yourdomain.com).

Post your results and we can go from there.

EDIT: Just read that more carefully... so you can't even load your content on the server's own browser?  Are you sure you've got a static IP address on the server?  Try 127.0.0.1 instead of 192.168.0.2 from the server's browser.  If this doesn't work, I'd say that apache isn't running.  Are you running something like Webmin to administer your server?

---

### Post by skeeler on 2007-09-15
Mud.Knee.Havoc,

Thanks for your reply.

Hmm.  Putting 127.0.0.1 in my browswer window also gives me the "unable to connect" error.  the ifconfig command shows that this is indeed my local loopback address.  (I'm not sure if it could be anything else.)  Any suggestions?

Thanks again.

---

### Post by schorsch on 2007-09-15
Have you started the webserver after booting for the last time? What is the output of
```
ps -ef|grep apache
```
If you do not see any apache processes please start it with
```
sudo /etc/init.d/apache2 start
```

---

### Post by skeeler on 2007-09-15
schorsh,

ps did not show any apache processes, so I started it as you suggested:

```


michael@penguin:/var/www$ sudo /etc/init.d/apache2 start
Password:
 * Starting web server (apache2)...                                             apache2: apr_sockaddr_info_get() failed for penguin
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
(99)Cannot assign requested address: make_sock: could not bind to address 192.169.0.2:80
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]


```

So, Apache wouldn't start.  Can you help me understand why it could not determine the server's FWDM?  (I have seen this before, even when it was working.)

Thanks for any help you can render.

---

### Post by skeeler on 2007-09-15
Anyone else have any ideas?

Thanks.

---

### Post by schorsch on 2007-09-16
Don't worry about the missing FQDN entry, your apache should start without it and listen to  127.0.0.1 at least.
What I do not understand is which IP range you are using. You wrote your server has an IP 192.168.0.2 but your router has the IP 192.169.0.1. Normally both IPs should be in the same subnet. Now you get the message that your apache could not bind to 192.169.0.2 .... weird ...
Can you please post the output of:
```
ifconfig -a
cat /etc/network/interfaces
netstat -nr
```

---

### Post by skeeler on 2007-09-16
You have a good eye, schorsch.

My server's IP address is indeed 192.168.0.2 as I said.
I mistyped my router's address.  It is 192.168.0.1, which is, as you suggest, on the same network.
What I don't understand is why the output I get when I sart Apache shows the address with 169 in it.  Strange.

ifconfig -a gives this:

```

eth0      Link encap:Ethernet  HWaddr 00:0E:A6:C4:60:C0  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:a6ff:fec4:60c0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:85006 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73889 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:71404487 (68.0 MiB)  TX bytes:12359647 (11.7 MiB)
          Interrupt:20 Base address:0x6c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:54 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2772 (2.7 KiB)  TX bytes:2772 (2.7 KiB)

ra0       Link encap:Ethernet  HWaddr 00:0F:66:ED:5B:A6  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2858037 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:114321480 (109.0 MiB)
          Interrupt:17 Base address:0x8000 

```

/etc/network/interfaces looks like this:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.2
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        # dns-* options are implemented by the resolvconf package, if installed

```

netstat -nr gives this:

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0

```

By the way, did I mention that this machine can connect to the internet perfectly well?

Thanks for your replies to my cries for help.  Keep them coming.

---

### Post by schorsch on 2007-09-16
Your network settings seem to be alright. Perhaps you have someting misconfigured in your apache conf. Can you find anything with "192.169." in the apache config directory with this command:
```
 sudo grep -ir "192.169." /etc/apache2/* 
```

---

### Post by skeeler on 2007-09-16
shorsch,

The grep command gave me this output

```
/etc/apache2/ports.conf:Listen 192.169.0.2:80
```

Clearly, I had made a typo when editing this file (or something else) before.  So, I edited /etc/apache2/ports.conf to say

```
Listen 192.168.0.2:80
```

So then I restarted Apache:

```
root@penguin:/var/www/apache2-default# /etc/init.d/apache2 start
 * Starting web server (apache2)...                                                        apache2: apr_sockaddr_info_get() failed for penguin
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
                                                                                    [ OK ]

```

I still get that FDQN error.  Also, the apr_sockaddr_info_get(), whatever that is, failed.  I don't know what that means.  Can anyone help me?

I tried looking at 127.0.0.1 with my browser.  No luck.  So, I restarted my networking, which seemed to go well:

```

root@penguin:/var/www/apache2-default# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                              [ OK ]
 
```

Again, I tried 127.0.0.1 in my browser, with no luck.  

Just for grins, I tried 192.168.0.2 (my server's internal address) and that worked:  I was able to see the index of my /var/www directory.  So, feeling reckless, I tried mydomain.com, and I was able to see the index again.

So, it seems to be more-or-less fixed.  The problem was the incorrect listen directive (?) in /etc/apache2/ports.conf.  I still get an error or two when I restart Apache.  Can someone tell me what this means?

```
apr_sockaddr_info_get() failed for penguin
```

Another question:  How can I ensure that Apache is started everytime I boot?

Thanks again for everyone's help.

---

### Post by schorsch on 2007-09-16
About the sockaddr error .... sorry, I have no idea.
But when you add
```
Listen 192.168.0.2:80
```
to ports.conf the apache server will listen ONLY on this private address and port 80 and not longer on localhost. If you want it to listen on every IP the line has to look like
```
Listen 80
```
To ensure that it starts on every boot there has to be a link in /etc/rc2.d called S50apache2 pointing to /etc/init.d/apache2. If this does not exist you can create it with
```
sudo ln -s /etc/init.d/apache2 /etc/rc2.d/S50apache2
```

Edit: Well, and if you think your thread is solved could you please mark it as solved?

---

