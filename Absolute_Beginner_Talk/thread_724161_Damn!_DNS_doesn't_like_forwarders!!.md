---
title: "Damn! DNS doesn't like forwarders!?!"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by NeonSamurai on 2008-03-14
Here's my /etc/bind/named.conf.options file:

> options {
        directory "/var/cache/bind";

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

forwarders {
      194.164.6.112;
};


When I run $ named-checkconf /etc/bind/named.conf.options I get this response:

> /etc/bind/named.conf.options:8: unknown option 'forwarders'

So any ideas why's it doing that? I'm guessing there's something wrong with my syntax. Also, could it be causing this:

>  * Stopping domain name service... bind                                                                                              rndc: connect failed: 127.0.0.1#953: connection refused
                                                                                                                              [fail]
 * Starting domain name service... bind                                                                                       [fail] 


This is my first attempt at building a DNS using ubuntu and it's a bit hit and miss so far. I've been using the tutorial someone kindly posted [[COLOR="DarkOrange"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=236093&highlight=connection+failed+DNS").

---

### Post by SpaceTeddy on 2008-03-14
forwarders should be IN the options section.. i.e. it should look like this

```
options {
directory "/var/cache/bind";

auth-nxdomain no; # conform to RFC1035
listen-on-v6 { any; };

forwarders {
[INDENT]194.164.6.112;[/INDENT]
};
};

 
```

---

### Post by NeonSamurai on 2008-03-14
Ahhh....

Thank you SpaceTeddy a rogue '};' was causing all the problems.

Cheers for your help.


Mark

---

