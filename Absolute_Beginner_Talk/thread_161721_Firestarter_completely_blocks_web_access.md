---
title: "Firestarter completely blocks web access"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by carloyyz on 2006-04-17
Firestarter blocks my access to the web completely when I enable it.  How can I remedy this situation.

---

### Post by GarethMB on 2006-04-17
Check first of all you haven't locked the firewall. That won't let traffic through under any circumstances.

Click the policy tab. Change to outbound policy. Make it permissive by default. This should let connections out unless you specify them to be blocked.

If you want to have *very* tight control over outbound traffic then keep it on restrictive by default setting and whitelist the ports and sevices you want to let out. This is overkill in my opinion. Most linux software on linux is open source (which tends to be seen as more trustworthy), every user will tell you that there is no spyware so there is no need to be this uptight about outbound traffic.

Regards GarethMB

---

### Post by 5-HT on 2006-04-17
Did you set restrictive permissions on outgoing traffic without whitelisting traffic on port 80?

If you go to the policy tab, and select outgoing traffic policy there are two options.

i) Permissive: Blacklist traffic
For this, only services and ports listed will be denied.
If you select the permissive option, make sure ports 80 and 443 are not listed*

ii) Restrictive: Whitelist traffic
For this, only services and ports listed will be allowed.
If you select this restricitve option, make sure ports 80 and 443 are listed*

*Ports 80 and 443 are for http and https protocols, respectively.

Also make sure that the firewall is not locked, as this state will block all traffic.

Edit: too slow

---

### Post by carloyyz on 2006-04-17
Thank you for your replys, but I won't be able to check the settings until I get home from work in a few hours.  I will reply asap.

---

### Post by GarethMB on 2006-04-17
[QUOTE=5-HT]Did you set restrictive permissions on outgoing traffic without whitelisting traffic on port 80?

If you go to the policy tab, and select outgoing traffic policy there are two options.

i) Permissive: Blacklist traffic
For this, only services and ports listed will be denied.
If you select the permissive option, make sure ports 80 and 443 are not listed*

ii) Restrictive: Whitelist traffic
For this, only services and ports listed will be allowed.
If you select this restricitve option, make sure ports 80 and 443 are listed*

*Ports 80 and 443 are for http and https protocols, respectively.

Also make sure that the firewall is not locked, as this state will block all traffic.

Edit: too slow[/QUOTE]
Heh, you filled in the gaps i left out about the appropriate ports ;)

Between the pair of us his problem should be fixed. :)

Look forward to hearing how you get on Carloyyz

---

### Post by carloyyz on 2006-04-17
One thing I forgot to mention is that it takes Firestarter 3 minutes to load.  Anyway, the firewall is not locked.  Outbound traffic policy is set to permissive by default.  As for the port settings, well you've lost me at this point.
In summary, I still can't access the web when firestarter is running.

---

### Post by GarethMB on 2006-04-17
[QUOTE=carloyyz]One thing I forgot to mention is that it takes Firestarter 3 minutes to load.  Anyway, the firewall is not locked.  Outbound traffic policy is set to permissive by default.  As for the port settings, well you've lost me at this point.
In summary, I still can't access the web when firestarter is running.[/QUOTE]
Does the outbound policy screen look like this?

Or are there any entries in the last 3 boxes?

One thing i forgot to add. Don't forget to click apply policy when you choose permissive by default.

---

### Post by carloyyz on 2006-04-17
[QUOTE=GarethMB]Does the outbound policy screen look like this?

Or are there any entries in the last 3 boxes?

One thing i forgot to add. Don't forget to click apply policy when you choose permissive by default.[/QUOTE]
Yes it looks exactly like your screen shot and there are no entries in the other boxes.

---

### Post by AndyCooll on 2006-04-17
Do you have a router?

For my network I add "192.168.2.0/24" to the allow connections in inbound traffic policy.

It may also be worth unticking:
Edit-->Preferences-->Advanced-->Block broadcasts from external network
I think I have to do that to get any Internet traffic

:cool:

---

### Post by carloyyz on 2006-04-17
[QUOTE=AndyCooll]Do you have a router?

For my network I add "192.168.2.0/24" to the allow connections in inbound traffic policy.

It may also be worth unticking:
Edit-->Preferences-->Advanced-->Block broadcasts from external network
I think I have to do that to get any Internet traffic

:cool:[/QUOTE]
I do not have a router.

Unticking: Edit-->Preferences-->Advanced-->Block broadcasts from external network unfortunately did not work.

Maybe i'll just forget about the firewall for now until I can find someone to personally set it up for me.

Thanks to all.

---

### Post by CameronCalver on 2006-04-18
Do you really need firestarter?

---

### Post by GarethMB on 2006-04-18
Open a terminal

```
sudo iptables -L
```

Post the result of that. That will be all the rules affecting your internet traffic. Someone here should be able to work it out :)

As Carloyyz doesn't have a router he does need to set up iptables.

---

### Post by carloyyz on 2006-04-18
[QUOTE=CameronCalver]Do you really need firestarter?[/QUOTE]
Probably not while using Linux, but after many years of being conditioned when using Windows, I feel paranoid without one.

---

### Post by carloyyz on 2006-04-18
[QUOTE=GarethMB]Open a terminal

```
sudo iptables -L
```

Post the result of that. That will be all the rules affecting your internet traffic. Someone here should be able to work it out :)

As Carloyyz doesn't have a router he does need to set up iptables.[/QUOTE]
I'm not at my computer right now, so I won't be able to post the info until this evening.

---

### Post by GarethMB on 2006-04-18
[QUOTE=carloyyz]Probably not while using Linux, but after many years of being conditioned when using Windows, I feel paranoid without one.[/QUOTE]You do not necessairily need the GUI of firestarter. You do need to configure IP tables as you don't have a router. Otherwise all ports into your PC are open.

---

### Post by carloyyz on 2006-04-18
[QUOTE=GarethMB]Open a terminal

```
sudo iptables -L
```

Post the result of that. That will be all the rules affecting your internet traffic. Someone here should be able to work it out :)

As Carloyyz doesn't have a router he does need to set up iptables.[/QUOTE]
Here is the output:
carlo@carlo:~$ sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN tcpmss match 1400:1536 TCPMSS clamp to PMTU

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
carlo@carlo:~$

How do nI set up iptables?

---

### Post by Ozitraveller on 2006-04-18
Nice 'HowTo' guys!

---

### Post by carloyyz on 2006-04-18
[QUOTE=Ozitraveller]Nice 'HowTo' guys![/QUOTE]
I read the How-too for iptables and it makes no sense to me.

---

### Post by CameronCalver on 2006-04-18
i installed fire starter to see if it was any good but how do i uninstall it

---

### Post by GarethMB on 2006-04-19
[QUOTE=Ozitraveller]Nice 'HowTo' guys![/QUOTE]
Constructive.

The wiki has a page about configuring iptables by hand. [https://wiki.ubuntu.com/IptablesHowTo?highlight=%28iptables%29](https://wiki.ubuntu.com/IptablesHowTo?highlight=%28iptables%29)
Although firestarter should be far easier. Before you go setting it up by hand just check the events list in firestarter. Is there any IP occuring multiple times? If so add this to the allowed incoming connections. Other than this i'm fresh out of ideas.](*,)

One more slightly random idea. When you used the wizard to set up firestarter are you sure that you enabled it for the device you use to connect to the internet? Its eth0 by default, so if you connect via a USB modem you'll need to set it to whatever that is. If you connect wirelessly you need it on ra0

---

### Post by steve.horsley on 2006-04-19
[QUOTE=carloyyz]Here is the output:
carlo@carlo:~$ sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN tcpmss match 1400:1536 TCPMSS clamp to PMTU

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
carlo@carlo:~$
[/QUOTE]
That says your firewall isn't stopping anything. Try enabling the firewall and then doing **sudo iptables -L**. 

One possibility is that you forgot to allow DNS name queries/answers through.

Can you also post the output from **sudo netstat -lutp**, and we'll see if you need a firewall at all. To be honest, I doubt that you do.

> 
How do nI set up iptables?

iptables is the underlyng command-line driven firewall. Firestarter is a GUI front-end that issues those commands to iptables for you, making your life somewhat simpler.

---

### Post by carloyyz on 2006-04-19
[QUOTE=steve.horsley]That says your firewall isn't stopping anything. Try enabling the firewall and then doing **sudo iptables -L**. 

One possibility is that you forgot to allow DNS name queries/answers through.

Can you also post the output from **sudo netstat -lutp**, and we'll see if you need a firewall at all. To be honest, I doubt that you do.


iptables is the underlyng command-line driven firewall. Firestarter is a GUI front-end that issues those commands to iptables for you, making your life somewhat simpler.[/QUOTE]
Here is the output with the firewall enabled for **sudo iptables -L**

carlo@carlo:~$ sudo iptables -L
Password:
Chain INBOUND (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
LSI        all  --  anywhere             anywhere

Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  67.69.184.227        anywhere            tcp flags:!SYN,RST,ACK/SYN
ACCEPT     udp  --  67.69.184.227        anywhere
ACCEPT     tcp  --  67.69.184.75         anywhere            tcp flags:!SYN,RST,ACK/SYN
ACCEPT     udp  --  67.69.184.75         anywhere
ACCEPT     all  --  anywhere             anywhere
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
DROP       all  --  anywhere             255.255.255.255
DROP       all  --  anywhere             192.168.2.255
DROP       all  --  224.0.0.0/8          anywhere
DROP       all  --  anywhere             224.0.0.0/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5
INBOUND    all  --  anywhere             anywhere
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input'

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward'

Chain LOG_FILTER (5 references)
target     prot opt source               destination

Chain LSI (2 references)
target     prot opt source               destination
LOG_FILTER  all  --  anywhere             anywhere
LOG        tcp  --  anywhere             anywhere            tcp flags:SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:SYN,RST,ACK/SYN
LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST
LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound '
DROP       icmp --  anywhere             anywhere            icmp echo-request
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound '
DROP       all  --  anywhere             anywhere

Chain LSO (0 references)
target     prot opt source               destination
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound '
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable

Chain OUTBOUND (1 references)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere
ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  192.168.2.10         67.69.184.227       tcp dpt:domain
ACCEPT     udp  --  192.168.2.10         67.69.184.227       udp dpt:domain
ACCEPT     tcp  --  192.168.2.10         67.69.184.75        tcp dpt:domain
ACCEPT     udp  --  192.168.2.10         67.69.184.75        udp dpt:domain
ACCEPT     all  --  anywhere             anywhere
DROP       all  --  224.0.0.0/8          anywhere
DROP       all  --  anywhere             224.0.0.0/8
DROP       all  --  255.255.255.255      anywhere
DROP       all  --  anywhere             0.0.0.0
DROP       all  --  anywhere             anywhere            state INVALID
OUTBOUND   all  --  anywhere             anywhere
LOG_FILTER  all  --  anywhere             anywhere
LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output'
carlo@carlo:~$

---

### Post by carloyyz on 2006-04-19
[QUOTE=steve.horsley]That says your firewall isn't stopping anything. Try enabling the firewall and then doing **sudo iptables -L**. 

One possibility is that you forgot to allow DNS name queries/answers through.

Can you also post the output from **sudo netstat -lutp**, and we'll see if you need a firewall at all. To be honest, I doubt that you do.


iptables is the underlyng command-line driven firewall. Firestarter is a GUI front-end that issues those commands to iptables for you, making your life somewhat simpler.[/QUOTE]
Here is the out put for **sudo netstat -lutp**

carlo@carlo:~$ sudo netstat -lutp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State PID/Program name
tcp        0      0 localhost.localdo:32769 *:*                     LISTEN     7208/hpiod
udp        0      0 *:bootpc                *:*                                7885/dhclient3
carlo@carlo:~$


Looking forward to your reply.

---

### Post by prezbedard on 2006-04-20
I have a question relating to this topic.

I am setting up a 'nix box to act as a web content filter.
I have the 'nix box set up and the filter working on it problem is getting network traffic to run through it before leaving the network. I do have a dsl router set up.

My current setup is running fedora but I may switch to ubuntu.

Can firestarter be setup to take outbound http traffic and filter it though a different port? i.e. the port the web filtering runs on and then let it leave the network? 


for example my current setup doesn't work when I set the default gateway on the client machines to the nix box IP address. It refuses the connections.

any help is appreciated.

Thanks

---

### Post by steve.horsley on 2006-04-23
Sorry for the delay - I've been out.

I can't read those iptables lists very easily, but it looks to me as though everything is being allowed through because of the line **ACCEPT all -- anywhere anywhere**. This appears in both the INPUT and OUTPUT chains, and I really can't see how the firewall is filtering anything with those there.

I notice the addresses 67.69.184.227 and 67.69.184.75 are specifically permitted - do these mean anything to you? 

If anyone can shed more light I would be grateful.


> Here is the out put for sudo netstat -lutp

carlo@carlo:~$ sudo netstat -lutp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address Foreign Address State PID/Program name
tcp 0 0 localhost.localdo:32769 *:* LISTEN 7208/hpiod
udp 0 0 *:bootpc *:* 7885/dhclient3
carlo@carlo:~$

That shows only 2 services listening. The tcp one is listening only on localhost, so cannot be connected to from other machines. The UDP one is listening for DHCP events, and I think it is harmless. So I don't think you actually need a firewall at the moment - there is nothing to block anyway.

---

### Post by carloyyz on 2006-04-23
[QUOTE=steve.horsley]Sorry for the delay - I've been out.

I can't read those iptables lists very easily, but it looks to me as though everything is being allowed through because of the line **ACCEPT all -- anywhere anywhere**. This appears in both the INPUT and OUTPUT chains, and I really can't see how the firewall is filtering anything with those there.

I notice the addresses 67.69.184.227 and 67.69.184.75 are specifically permitted - do these mean anything to you? 

If anyone can shed more light I would be grateful.




That shows only 2 services listening. The tcp one is listening only on localhost, so cannot be connected to from other machines. The UDP one is listening for DHCP events, and I think it is harmless. So I don't think you actually need a firewall at the moment - there is nothing to block anyway.[/QUOTE]
The addresses addresses 67.69.184.227 and 67.69.184.75 mean nothing to me.
If you don't thik I need a firewall then I won't bother with it anymore.

Thanks for you help.

---

### Post by auroraborealis on 2006-04-24
I would try using Bastille (apt-get bastille). It not only sets up some basic firewall rules, but also hardens other parts of your system. It comes with an interactive GUI, and if you don't like the changes just run bastille -r to revert everything back the way it was before.

---

