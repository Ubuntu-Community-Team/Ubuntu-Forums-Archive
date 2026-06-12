---
title: "Using IPTABLES (Please help)"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by guysmiley25 on 2007-05-15
Could someone please help me with IPTABLES.

I have already setup Internet Sharing (masquerading).

Now I have a few services running on my machine:
    Apache
    MYSQL
    TorrentFlux
    SSH
    DNS
    etc.

Setup
    eth0: Internet
    eth1: LAN

I want to use IPTABLES to block all ports from the internet, less SSH, Apache, etc.

Also I want to use IPTABLES if possible, to limit upload and download speed for certain ports.

For some services that I'm running that I do not want other people to access, I plan on using SSH port forwarding.

How can I go about doing this?

Thanks

---

### Post by compiledkernel on 2007-05-15
[http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)

Try that.

---

### Post by guysmiley25 on 2007-05-15
I'm still confused and this stuff is hard. However I am very worried about the safety of my system.

Also I still need to control the upload and download speed of some services as I am charged per traffic. Can I do this using IPTABLES? if not then what? I looked into tickle, but I want to do it based on port.


Now if I am correct, the IPTABLES rules work down the rows. So the first rule is checked, then the second then the third.

So what I think I want to do is have my table like this:
        allow port 1234 on eth0
        allow port 4321 on eth0
        drop all other ports on eth0

Then I can specify what ports I want open, and the rest will be closed.

I think it's something like this:
        iptables -A INPUT -i eth0 -j ACCEPT.... Can not work out what the rest is
        iptables -A INPUT -i eth0 -j DROP...      Can not work out what the rest is

Can anyone help me out?

---

### Post by guysmiley25 on 2007-05-29
Have we no experts on IPTABLES that can help me out?

---

### Post by Paul Mitchell on 2007-05-29
Off the top of my head you could try something like:

```
iptables -P INPUT -j DROP
iptables -I INPUT -i eth0 -dport 1234 -j ACCEPT
iptables -I INPUT -i eth0 -dport 4321 -j ACCEPT
iptables -I INPUT -i eth1 -j ACCEPT 
```

This should set the default policy to be to drop all incoming packets, then insert two rules ahead of that to allow the two ports you require. The last rule allows all access from your LAN.

If you're going to use this more than once per boot you'll want to look at the "-F" option to flush out the rules before you reapply them.

You can use the "-m" option to apply a list of (comma separated) port numbers in one rule if you with.

---

### Post by guysmiley25 on 2007-05-29
Awesome thank you, So would I do something like this for a comma separated list?
```

iptables -I INPUT -i eth0 -dport -m 1234,1235,1236 -j ACCEPT

```

What about a port range? eg 4000-4100?

So I gather that I need to have a script that starts up on boot, this I can do. So would my script be something like
```

iptables -F
iptables -A INPUT -i eth0 -j DROP
iptables -I INPUT -i eth0 -dport 1234 -j ACCEPT
iptables -I INPUT -i eth0 -dport 4321 -j ACCEPT

```

I am also confused on why the iptable rules have to be applied each time, because when I setup a rule for masquerading awhile ago, I do not have to reapply the rule for that?

**Edit:** In other words, what is applying the rules that are already there when I start my computer? And why does it not apply any changes I make also?

---

### Post by Paul Mitchell on 2007-05-29
> **guysmiley25 said:**
> Awesome thank you, So would I do something like this for a comma separated list?
```

iptables -I INPUT -i eth0 -dport -m 1234,1235,1236 -j ACCEPT

```

What about a port range? eg 4000-4100?

So I gather that I need to have a script that starts up on boot, this I can do. So would my script be something like
```

iptables -F
iptables -A INPUT -i eth0 -j DROP
iptables -I INPUT -i eth0 -dport 1234 -j ACCEPT
iptables -I INPUT -i eth0 -dport 4321 -j ACCEPT

```

I am also confused on why the iptable rules have to be applied each time, because when I setup a rule for masquerading awhile ago, I do not have to reapply the rule for that?

A port range is just number:number with no extra options.

How did you appy your masquerading rule then?

---

### Post by guysmiley25 on 2007-05-29
I used [this]("http://doc.gwos.org/index.php/Share_Internet_Connection") gudie. It is for Breezy, however I'm using Feisty and it worked.

Basically the iptables part is
```

iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE 

```

---

### Post by cferthorney on 2007-05-29
Could you post contents of iptables -L --line-numbers - the order the rules are printed is important in iptables.

---

### Post by Paul Mitchell on 2007-05-29
> **guysmiley25 said:**
> I used [this]("http://doc.gwos.org/index.php/Share_Internet_Connection") gudie. It is for Breezy, however I'm using Feisty and it worked.

Basically the iptables part is
```

iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE 

```

I'm new to Ubuntu, so I'm going to have to look that up, but my guess is that the following line makes it permenant:
```
dpkg-reconfigure ipmasq
```

---

### Post by raul_ on 2007-05-29
Why don't you use a frontend like firestarter?

---

### Post by guysmiley25 on 2007-05-29
> **raul_ said:**
> Why don't you use a frontend like firestarter?
My server is headless, and I'm trying to keep it lite weight. As well as wanting to understand the process.

> **Paul Mitchell said:**
> I'm new to Ubuntu, so I'm going to have to look that up, but my guess is that the following line makes it permenant:
```
dpkg-reconfigure ipmasq
```

Thanks Paul, I will look into that. Do you think that it makes the IPTABLE permanent or just the masquerade?

> **cferthorney said:**
> Could you post contents of iptables -L --line-numbers - the order the rules are printed is important in iptables.

Sure here goes
```

Chain INPUT (policy DROP)
num  target     prot opt source               destination         
1    ACCEPT     0    --  anywhere             anywhere            
2    LOG        0    --  127.0.0.0/8          anywhere            LOG level warning 
3    DROP       0    --  127.0.0.0/8          anywhere            
4    ACCEPT     0    --  anywhere             255.255.255.255     
5    ACCEPT     0    --  192.168.0.0/24       anywhere            
6    ACCEPT    !tcp  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
7    LOG        0    --  192.168.0.0/24       anywhere            LOG level warning 
8    DROP       0    --  192.168.0.0/24       anywhere            
9    ACCEPT     0    --  anywhere             255.255.255.255     
10   ACCEPT     0    --  anywhere             hostname.mydomain  
11   ACCEPT     0    --  anywhere             myip.cable.telstraclear.net 
12   DROP       0    --  anywhere             ALL-SYSTEMS.MCAST.NET 
13   LOG        0    --  anywhere             anywhere            LOG level warning 
14   DROP       0    --  anywhere             anywhere            

Chain FORWARD (policy DROP)
num  target     prot opt source               destination         
1    ACCEPT     0    --  192.168.0.0/24       anywhere            
2    ACCEPT     0    --  anywhere             anywhere            state RELATED,ESTABLISHED 
3    LOG        0    --  anywhere             192.168.0.0/24      LOG level warning 
4    DROP       0    --  anywhere             192.168.0.0/24      
5    DROP       0    --  anywhere             ALL-SYSTEMS.MCAST.NET 
6    LOG        0    --  anywhere             anywhere            LOG level warning 
7    DROP       0    --  anywhere             anywhere            

Chain OUTPUT (policy DROP)
num  target     prot opt source               destination         
1    ACCEPT     0    --  anywhere             anywhere            
2    ACCEPT     0    --  anywhere             255.255.255.255     
3    ACCEPT     0    --  anywhere             192.168.0.0/24      
4    ACCEPT    !tcp  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
5    LOG        0    --  anywhere             192.168.0.0/24      LOG level warning 
6    DROP       0    --  anywhere             192.168.0.0/24      
7    ACCEPT     0    --  anywhere             255.255.255.255     
8    ACCEPT     0    --  hostname.mydomain    anywhere            
9    ACCEPT     0    --  myip.cable.telstraclear.net  anywhere            
10   DROP       0    --  anywhere             ALL-SYSTEMS.MCAST.NET 
11   LOG        0    --  anywhere             anywhere            LOG level warning 
12   DROP       0    --  anywhere             anywhere 

```

If I do a flush all this stuff comes back, but I think that might be because of the reason Paul said.

P.S. I removed my external IP and my domain name from the output

---

### Post by cferthorney on 2007-05-30
As far as I can see that looks OK.  If (from Outside) you do (say) telnet <your ip> 23 (Yes the real telnet port) You should get denied and something written to the logs.  Do you?  You could also temporarily change drop to REJECT and see what message you get from something like ping or traceroute.

---

### Post by guysmiley25 on 2007-05-30
I'm not sure if I follow you cferthorney?

I do ssh into my server, and that is how I gain access.

When I tried telnet <my ip> 23, I get ```
Trying <my ip>...
telnet: Unable to connect to remote host: Connection refused
```

What is telnet?

---

### Post by cferthorney on 2007-05-31
I was trying to see if other services were blocked.  You said you had mail, Apache and ssh open.  I figured if you try to connect via somethign like telnet we could see if your rules were working for you.  It appears they do.  Now with that in mind we can look at SSH port forwarding.    According to [Hackorama](http://www.hackorama.com/network/portfwd.shtml) the command you need is: 
iptables -t nat -A PREROUTING -p tcp -i eth0 -d xxx.xxx.xxx.xxx --dport 8888 -j DNAT --to yyy.yyy.yyy.yyy:80 to forward port 8888 to port 80.  Does this help or are you after ssh -L 8888:yyy.yyy.yyy.yyy:80 ?

---

