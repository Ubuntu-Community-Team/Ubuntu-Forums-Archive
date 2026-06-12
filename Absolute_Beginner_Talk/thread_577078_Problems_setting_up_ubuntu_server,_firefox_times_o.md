---
title: "Problems setting up ubuntu server, firefox times out when trying to connect"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by rcsfloater on 2007-10-15
I have 2 computers...my server is running ubuntu 7.04 and my operating desktop is running Win XP. I'm trying to set up some church database software on the server computer, and setting up the other computer running Windows to connect to this software. I have them currently set up through a crossover cable, but I also have a switch to use in case I didn't crimp the cable well. I've defined static IP addresses for both machines (changing the interfaces file on the LAMP) and have been able to use putty to ssh into the LAMP server.

The problem is that I can't seem to connect to the Apache component (by typing in the IP address in firefox browser on my desktop computer running Windows) It basically times out saying it cannot find the server. I'm not sure what I'm doing wrong. I don't want this to be an internet connection but rather a local one since it will have financial information on it. That's why I have the crossover. Any suggestions as to what I am missing because I know it should work?

---

### Post by [S|G] on 2007-10-15
Can you connect to your apache server from the LAMP server? Once you ssh in you can try this:

```
telnet localhost 80
```

If you get a connection refused error then your server isn't set up correctly. Now, if it actually connects you'll get a message like this one:
```

diego@SnowGust:~$ telnet localhost 80
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.

```
If you do get one, then your server is running, and you should check to see if you have a firewall running. If in doubt and the server isn't connected to the internet, you can do this:
```

$ sudo iptables -I INPUT -j ACCEPT
$ sudo iptables -I OUTPUT -j ACCEPT

```
This will override any firewall restrictions that you might have.

---

### Post by Keith_Burton on 2007-10-15
First, let's verify your webserver is working. On the LAMP server, open a browser and try to connect to [http://localhost](http://localhost)

Once that works, then on the Windows browser make sure the statusbar is visible. Then try to connect to the server and post what message is showing when it stalls, before the "cannot find the server" page gets displayed.

---

### Post by rcsfloater on 2007-10-15
I got it working now...I believe it was my crossover cable. Once I plugged them into a switch, it seems to be working now. Thanks for the help!

---

