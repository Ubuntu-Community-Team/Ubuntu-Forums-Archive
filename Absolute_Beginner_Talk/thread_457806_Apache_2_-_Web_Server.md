---
title: "Apache 2 - Web Server"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by fulanitok on 2007-05-29
HI guys,

I trying for the first time configure an Apache2 web server but I can't connect from another PC!

I don't understand when I ping my IP adress I get response!

But from my PC I get this page: [http://localhost/apache2-default/](http://localhost/apache2-default/) "It works"

Can somebody help me with a 'Newbie' tutorial.


Thx

---

### Post by SoulinEther on 2007-05-29
Are you trying to connect within your own LAN like on a router or something? Or if you have a router, are you trying to connect from outside?

---

### Post by fulanitok on 2007-05-29
No I trying to connect from my friend's PC! From my other LAN PC it's working ...

---

### Post by SoulinEther on 2007-05-29
If its behind a router, a firewall is probably preventing the correct ports from forwarding to your Apache server on your computer.......

Unless you opened port 80 on your computer / router?

---

### Post by fulanitok on 2007-05-29
Yeah it's using the port 80 behind router!

I really don't know what to do!

---

### Post by esoterica on 2007-05-29
First start by making sure your configuration is allowing a connection. In this set up documentation you'll see there are protective ways you can edit the configuration file to purposely prevent what you're trying to do. Make sure you didn't inadvertently set this to do so...

See the section all the way at the bottom called "Securing Apache"
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

It would be accessible by default so unless you have changed that it should be ok as is.

Now try to connect to it from another computer on your same LAN (or if another computer is not available use this one, but in the web abrowser address bar use the actual LAN IP address to connect (not [http://localhost](http://localhost) and not [http://127.0.0.1](http://127.0.0.1))

You can find out what the actual LAN IP is by opening a terminal window and typing in...

ifconfig

This will tell you what your Non Routable or local LAN IP address is, if on a wireless it's probably listed under the name eth1 and should be something like 10.0.0.2 or 192.0.0.2 as an example. Use this IP address preferably from another computer that is on your same wireless router or what ever you are using. You can test from both this computer and another one even. Type this IP what ever it is into the web browser like so (the actual IP address will be different of course)

[http://10.0.0.2](http://10.0.0.2)

This should open up a web page, you'll see a link to Apache-default or something and your "It Works" web page.

If all that works, and it should, then it's time to look at your router you use to connect to the internet with. Just about all routers used for connecting to your cable or DSL modem also contain built in firewalls.

Your going to need to read your specific routers documentation to learn how to place your web server (Apache) in what's going to be called the "DMZ" of your routers firewall settings. This will make your web server publicly accessable.

Note: You may also have to set your router up to route outside requests to this specific computer your using as the web server. Otherwise, your friend trying to connect to your server will get his packets dropped at your firewall router because it will not know where to send these packets on your internal private network (LAN).

Also, when your friend tries to connect, he will have to use the public IP address (which is actually assigned to your router), he can not connect directly to you using just your LAN IP address (the 10. or 192. number).

There are a milion places out there to find out what your actual public IP address is, just go to google and search "What's My IP Address".

Also, to not have to reconfigure everything each time you reboot, you may also want to set a static IP address on your web server computer and configure this as such in your router as well. Otherwise you run the risk of dynamic IP's getting assigned and a different computer possibly landing unsafely in the DMZ, that would be bad.

You should also spend your time first reading about how to secure Apache and do so long before you make it publicly accessible. It's cool to want to get it up and see it working, but it's very important to not get ahead of yourself, out of the box your Apache install is not very secure at all, it was intended to be used as a private production testing server, not a publicly accessible web server. If it gets hacked by not securing it, and it will get hacked, you'll have an even bigger and more time consumeing mess on your hands.

---

### Post by fulanitok on 2007-05-29
Hei **esoterica** thx for your post very interesting.

Now a question should I install PHP and MySQL? I just want to work with .swf and html files.

And this when I put this line on de terminal:

> sudo vi /etc/network/interfaces

I get this:

> E325: ATTENTION
Found a swap file by the name "/etc/network/.interfaces.swp"
          owned by: root   dated: Mon May 28 09:45:26 2007
         file name: /etc/network/interfaces
          modified: YES
         user name: root   host name: foxtrot-desktop
        process ID: 11350
While opening file "/etc/network/interfaces"
             dated: Mon May 28 11:14:50 2007
      NEWER than swap file!

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /etc/network/interfaces"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/etc/network/.interfaces.swp"
    to avoid this message.
"/etc/network/interfaces" 19 lines, 195 characters
Press ENTER or type command to continue

and than this:

> auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


iface eth0 inet dhcp

auto eth0
~                                                                               
~                                                                               
~                                                                               
~         

What am I doing wrong?

Thx Guyos

---

### Post by esoterica on 2007-05-29
I'll look at that config info you posted in a minute, to answer your other question though, no, don't install MySQL and PHP unless you need to use these. This will make securing your Apache2 web server so much easier if you don't need them (I unfortuneately did because I do web development work and needed a local platform to test my PHP script work on).

If down the road you wish to start learning PHP you can add PHP and MySQL in later, so for now don't do it, it will also just complicate your installation.

Like I said, if you haven't edited anything in the actual Apache config files yet you'll be working out of the box for just your html pages. I can't give you, nor can anyone else here, specific directions to get your new web server publicly accessable because the instructions to do so with specific routers are all going to be different. In every router I've ever used though the documentation to make what your trying to do is very clear and very easy to follow as long as you know what in the documentation to look for. The key word here for you is probably going to be found in your documentation listed as "DMZ", this is the industry standard term used for placing a web server or game server etc... on a publicly accessible point of your firewall, while still keeping everything else behind your firewall secure (like your other computers).

I know it sounds like a very confusing and possibly complicated thing to do, but in reality it's very easy and straightforward. For example, on my own router all I have to do is assign a static IP address to my Apache server, then in my router set up I just enter that IP address in the DMZ list, boom, done, that easy.

You don't have to even mess with static or dynamic IP addresses if you don't want to, but it makes it easier for you so everything doesn't have to be redone each time you reboot your computer or router. 

Most routers let you make these changes by connecting to it from your web browser on any PC you are using. Go to the router manufactures web site and find the documentation in case you no longer have it. It probably is as easy to connect into it for making these changes as typing in [http://192.0.0.1](http://192.0.0.1) or [http://10.0.0.1](http://10.0.0.1) into your web browser to connect into the router settings. You'll need their documentation though to know what your default user name and password are to make changes (make sure you change these default username and passwords on your router, that is very important!)

---

### Post by esoterica on 2007-05-29
Ok, I'm not sure what your trying to do with this...

sudo vi /etc/network/interfaces

All you need to mess with is finding out what your IP address is on your LAN so we can test it and make sure Apache2 is accessable by other computers.

You don't need to type anything more into the terminal Window than this...

```

ifconfig

```

That one simple line will tell us everything you need to know, if you have another computer on your network that uses Windows then the same command at the Windows command line would be this...

```

ipconfig

```

This will tell you the local IP addresses of the computer you run the command on. These "local" IP addresses though are only good for connecting local computers that are using the same router. Since your using a router, it has been assigned it's own internal IP address, which will be simular to the IP's you see on your Apache server and any other computers using this router. The router will also have an external, routeable, or public IP address (choose your favorite name for it they all mean the same thing). You won't be able to see what this IP is from your local computers using ifconfig or ipconfig. This public IP address though is the IP address your friend who you say is outside your router will need to know to connect to your new web server. L:ike I said, there are web sites that will give you your public IP address if you don't know what it is. So if he's at his house, if you tell him your public IP address, he can type [http://(that](http://(that) IP) into his web browser and see your web pages. Don't forget though, you need to read that router documentation, and you want to read how to secure your new Apache server. Not using PHP and MySQL will make that job a whole lot easier for you.

You are in a somewhat very lucky position though if your needs are this simple (I so wish my own needs were this easy, just html pages, what a dream that would be!)

If you think there's a chance you did something wrong, though I don't think you did, just need to set up your router for this, and do want to start over, for what your wanting to do I'd take a different approach.

This may at first sound more complicated, but in reality it's so much easier, and gets you a good secure Apache2 installation. Don't let compiling from source code scare you here, these step by step instructions are better than any instructions I've seen yet! If you were able to follow the Ubuntu instructions to get Apache working, like it sounds like you did, then these instructions will be a walk in the park compared to those (plus the Ubuntu instructions do very little to get you a publicly accessible and secure web server).

If it was me, and had just your needs, I'd use the synaptic installer thing in Ubuntu to first remove the Apache install you just made, then I'd do it over from scratch the right way like this...

[http://www.securityfocus.com/infocus/1786](http://www.securityfocus.com/infocus/1786)

---

### Post by fulanitok on 2007-05-29
Ok, **esoterica** I really thank you for your time!

Now, can't access to my Apache Web Server from another PC, I get always a timed out error, coun't find the page or someting like that. I was way back home and I decide to try to access from my telephone (I have the E900 from Samsung) and guess what? Yes I get a connection with my Apache Web Server :shock: I'm really confused now, why can I connect from my telephe and not from another desktop.

I did unistall and reinstall the Apache2 package and still no working from the outside ...

Oups forgot something: I have disconnected my router and connect my Web Server directly from the source cable modem but the result.

---

### Post by fulanitok on 2007-05-29
Another thing that's really confusing me, why is the:

```
 /etc/apache2/httpd.conf
```

just empty, no configuration of the web server?

---

### Post by fulanitok on 2007-05-29
Hei guys

I just found that the folder
```
/etc/httpd/
```
don't existe!

I should to configure it but it just don't existe!!

---

### Post by fulanitok on 2007-05-30
Hi guys,

I really don't know what to do. Now when I try to restart Apache2 with:

```
/etc/init.d/apache2 restart
```

I get this:

```

* Forcing reload of web server (apache2)...                                    apache2: apr_sockaddr_info_get() failed for **foxtrot-desktop**
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
[COLOR="Navy"]httpd (no pid file) not running[/COLOR]
apache2: apr_sockaddr_info_get() failed for **foxtrot-desktop**
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]

```

Am I that dumb? I goodness. :(

---

### Post by fulanitok on 2007-05-30
Hei guys,

how normal is this;

```

kelvin@kelvin-foxtrot:~$ sudo /etc/init.d/apache2 restart
 * Forcing reload of web server (apache2)...                                    apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
kelvin@kelvin-foxtrot:~$ 

```

For 2 days am I trying to make public my Apache Web Server but can't.

Any suggetions are welcome

---

