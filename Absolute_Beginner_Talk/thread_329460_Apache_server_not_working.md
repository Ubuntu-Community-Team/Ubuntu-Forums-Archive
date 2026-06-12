---
title: "Apache server not working"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by Skyler0 on 2007-01-01
I followed the ubuntuguide.org apache installation guide (which was just one apt-get command), and everything seemed to install correctly. But when I go to [http://localhost](http://localhost), it doesn't connect.

Thanks

---

### Post by MrHorus on 2007-01-01
> **Skyler0 said:**
> I followed the ubuntuguide.org apache installation guide (which was just one apt-get command), and everything seemed to install correctly. But when I go to [http://localhost](http://localhost), it doesn't connect.

Thanks

Need a bit more information than that i'm afraid.

Exactly what package did you tell apt-get to install?

When you say it doesn't connect does it time out?

---

### Post by Jeremy Jackins on 2007-01-01
do you have an external firewall or router?

---

### Post by seijuro on 2007-01-01
you can also try [http://127.0.0.1](http://127.0.0.1) if you are trying to access the server via the machine it is on. also if you set it up for a port other than 80 you will need to include that at the end of the ip like so [http://127.0.0.1:8383](http://127.0.0.1:8383) If you created a public_html directory in your home directory on the macine the address includes ~<username> like so [http://127.0.0.1/~john/](http://127.0.0.1/~john/) If you are trying to access the server across a home lan you need to use the 192.168.... address that the router gave the machine you can look up the address in the router or on the server machine with ifconfig

---

### Post by PilotJLR on 2007-01-01
Let's also see if it's actually running! Please post the results from:
```

ps -ef | grep apache

```

If it results with only a single line with the word "grep" in it, then also do this:
```

sudo /etc/init.d/apache2 start

```
And then let us know the output from that...

---

### Post by Skyler0 on 2007-01-01
output from the ps command:

> sky      20223 20201  0 20:58 pts/0    00:00:00 grep apache


Yes it times out, and I installed "sudo apt-get install apache2", and if I try it again it says it's installed. I'm using port 80, and I use to have a Apache server setup on my windows box before I converted it over to Ubuntu. 

And if I have an external firewall or router, it would not affect localhost or 127..., but yes the port is forwarded accordingly.

---

### Post by digen on 2007-01-01
Hello,

From the ps output you posted it appears Apache the webserver daemon isn't running.

Start the apache daemon :

#/etc/init.d/apache2 start

I hope you have put the files in the DocumentRoot which you can find by looking at the apache2.conf or httpd.conf.

---

### Post by Skyler0 on 2007-01-02
i think i might have messed something up lol. I installed apache (not apache2) at first by accident, so i think it might be conflicting. How would I go about removing both of them completely and restarting?

---

### Post by seijuro on 2007-01-02
if you navigate your way to them in synaptic you can simply tell it to remove them from there.

---

### Post by Skyler0 on 2007-01-02
ya, there were some left over apache 1 stuff. I got rid of that and all the apache2 stuff, and reinstalled it, and its working now.

Thanks :)

---

