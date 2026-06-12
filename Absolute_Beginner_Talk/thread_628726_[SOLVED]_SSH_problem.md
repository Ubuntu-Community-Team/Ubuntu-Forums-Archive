---
title: "[SOLVED] SSH problem"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by spydon on 2007-12-01
Hi.
I can't ssh into my computer through my router. I've set my router to forward port 22 to my computer's IP address, but it just says:  ssh: connect to host username.is-a-geek.net port 22: Connection refused. I know that username.is-a-geek.net works because i get to my router if I write it in a web browser.

My router is a Zyxel G-2000.
My NAT settings is: ssh start port: 22 end port: 22 Server IP address: 192.168.1.39

I hope someone can help me!

---

### Post by spupy on 2007-12-01
I have the same problem with a Netgear router. The strange thing is that i can ssh to my comp FROM my comp, by typing the IP of the router. From outside it doens't work?! 
Better find out the ip of your router. You can do this by visiting any webpage that shows your ip - while you are behind the router, the page shows the ip of the router.

---

### Post by Dr Small on 2007-12-01
Make sure port 22 is open on your firewall, on your SSH Server.

---

### Post by xeth_delta on 2007-12-01
> **spydon said:**
> Hi.
I can't ssh into my computer through my router. I've set my router to forward port 22 to my computer's IP address, but it just says:  ssh: connect to host username.is-a-geek.net port 22: Connection refused. I know that username.is-a-geek.net works because i get to my router if I write it in a web browser.

My router is a Zyxel G-2000.
My NAT settings is: ssh start port: 22 end port: 22 Server IP address: 192.168.1.39

I hope someone can help me!

Make sure the ssh server is running on that machine and that it is listening through an open port. Can you ssh from within that computer?

---

### Post by spydon on 2007-12-01
My router has port 22 open and I can access my computer on the network if I just write the computers local IP but not if I write the IP of the router or my external IP. ssh-add runs on startup on my machine so it should be running, shouldn't it?

---

### Post by CrypticDweller on 2007-12-01
You need to make sure that you also have some sort of port forwarding enabled on your router... ie, if you simply open the port, and you try to access somewhere.net your router won't know which computer you want to hit. So lets say you machine is 192.168.0.100 set port 22 to forward to that machine.

---

### Post by spydon on 2007-12-01
> **CrypticDweller said:**
> You need to make sure that you also have some sort of port forwarding enabled on your router... ie, if you simply open the port, and you try to access somewhere.net your router won't know which computer you want to hit. So lets say you machine is 192.168.0.100 set port 22 to forward to that machine.

> ssh start port: 22 end port: 22 Server IP address: 192.168.1.39
That looks like port forwarding to me... Or how should it look?

---

### Post by Dr Small on 2007-12-01
Where did you get that from ??

---

### Post by spydon on 2007-12-01
> **Dr Small said:**
> Where did you get that from ??

From my first post.... :P And on my first post I got it from my router.

---

### Post by spydon on 2007-12-01
Could there be something wrong with my router?

---

### Post by monte48lowes on 2007-12-01
What are the specific commands you are entering into the terminal?

 Are you trying to access from the internet or on the local network?

Mike

---

### Post by toasterofirony on 2007-12-01
Humour me, you are absolutely sure you have ssh-server installed?

I only ask as I had exactly this problem today and realised after hours of fiddling that I had not got the server installed, hence my problems with ssh'ing into my main box.

---

### Post by Dr Small on 2007-12-01
> **toasterofirony said:**
> Humour me, you are absolutely sure you have ssh-server installed?

I only ask as I had exactly this problem today and realised after hours of fiddling that I had not got the server installed, hence my problems with ssh'ing into my main box.
As an addition to your post, here is how you would install it, if you don't have it:
```
sudo apt-get install openssh-server
```

---

### Post by linuxusr50 on 2007-12-01
Make sure your ssh daemon is running by doing this:

```
ps -A | grep ssh
```

You should see sshd in the list.

```

daniel@daniel-desktop:~$ ps -A|grep ssh
 5237 ?        00:00:00 sshd

```

If you don't see this you may not have an ssh server running on your machine.

---

### Post by spydon on 2007-12-01
I have the openssh server installed and I can connect to my box over the local network but I can't connect to it through my external IP. :/

---

### Post by spydon on 2007-12-01
> **linuxusr50 said:**
> Make sure your ssh daemon is running by doing this:

```
ps -A | grep ssh
```

You should see sshd in the list.

```

daniel@daniel-desktop:~$ ps -A|grep ssh
 5237 ?        00:00:00 sshd

```

If you don't see this you may not have an ssh server running on your machine.

```
 4335 ?        00:00:00 sshd
 4709 ?        00:00:00 ssh-agent
 4710 ?        00:00:00 ssh-agent

```

Should there really be 3 of them? :P

---

### Post by monte48lowes on 2007-12-01
Is this 192.168.1.39 your external IP? Check here: [http://www.whatismyip.com]("http://www.whatismyip.com") to make sure.

Mike

---

### Post by Dr Small on 2007-12-01
The ssh agents are connections to your ssh box.
By the way, try reading this (starting at step #6) and try to get your box open on the internet:
[http://php.8ez.com/drsmall/blog/?p=124](http://php.8ez.com/drsmall/blog/?p=124)

The Full Circle Magazine even had something in it about setting up a SSH Server, for this month.

Dr Small

---

### Post by spydon on 2007-12-01
> **monte48lowes said:**
> Is this 192.168.1.39 your external IP? Check here: [http://www.whatismyip.com]("http://www.whatismyip.com") to make sure.

Mike

No that is my internal IP, My internal ip is 90.227.34.***.

---

### Post by monte48lowes on 2007-12-01
So to access your server from the internet you would use the second IP address. That will provide directions to your router. Your router will provide directions through port forwarding to the server.

Mike

---

### Post by spydon on 2007-12-01
> **monte48lowes said:**
> So to access your server from the internet you would use the second IP address. That will provide directions to your router. Your router will provide directions through port forwarding to the server.

Mike

Ive already done that but i just get "connection refused".

---

### Post by linuxusr50 on 2007-12-01
Are you testing from a computer outside your network, or are you simply entering ssh username@yourexternalip

Some routers are firewalled by default to prevent the latter.


Also I am not sure how comfortable you are with you router and its port forwarding commands.  So I thought I would throw in a link that describes in detail how to do it.


[http://portforward.com/english/routers/port_forwarding/ZyXEL/ZyAIRG-2000/Echolink.htm]("http://portforward.com/english/routers/port_forwarding/ZyXEL/ZyAIRG-2000/Echolink.htm")

---

### Post by Dr Small on 2007-12-01
If port 22 is open on your router and pointing to your internal IP, it is your Firewall on your system. If the port is open on your firewall, then it has to be your router.

---

### Post by limac on 2007-12-01
> **Dr Small said:**
> The ssh agents are connections to your ssh box.
By the way, try reading this (starting at step #6) and try to get your box open on the internet:
[http://php.8ez.com/drsmall/blog/?p=124](http://php.8ez.com/drsmall/blog/?p=124)

The Full Circle Magazine even had something in it about setting up a SSH Server, for this month.

Dr Small

Great Tutorial Dr.Small!!!

---

### Post by spydon on 2007-12-01
> **linuxusr50 said:**
> Are you testing from a computer outside your network, or are you simply entering ssh username@yourexternalip

Some routers are firewalled by default to prevent the latter.


Also I am not sure how comfortable you are with you router and its port forwarding commands.  So I thought I would throw in a link that describes in detail how to do it.


[http://portforward.com/english/routers/port_forwarding/ZyXEL/ZyAIRG-2000/Echolink.htm]("http://portforward.com/english/routers/port_forwarding/ZyXEL/ZyAIRG-2000/Echolink.htm")

I've tested from outside my network and from the inside, connection refused on both.

And ive already done portforwarding and I did it with that webpage.

---

### Post by Dr Small on 2007-12-01
> **limac said:**
> Great Tutorial Dr.Small!!!
Thank-you. You just made my day :)

---

### Post by monte48lowes on 2007-12-01
I think you have a working ssh server. I would move next to the router to ensure that port forwarding is pointed to the server and enabled.

Mike

---

### Post by spydon on 2007-12-01
> **Dr Small said:**
> If port 22 is open on your router and pointing to your internal IP, it is your Firewall on your system. If the port is open on your firewall, then it has to be your router.

I'm almost sure that the port is open on my router and I don't know if I even got a firewall on my box... :P

---

### Post by Dr Small on 2007-12-01
You do. Try installing Firestarter and opening port 22:
```
sudo apt-get install firestarter
```

---

### Post by kevdog on 2007-12-01
What is your external IP address??  Im fairly certain the external address does not start with 192.

---

### Post by spydon on 2007-12-01
> **kevdog said:**
> What is your external IP address??  Im fairly certain the external address does not start with 192.

It doesn't, it start's with 90.

---

### Post by spydon on 2007-12-01
> **Dr Small said:**
> You do. Try installing Firestarter and opening port 22:
```
sudo apt-get install firestarter
```

How do I open the port with firestarter, I can't find it... :P

---

### Post by Dr Small on 2007-12-01
> 7.) Launch Firestarter, from the System > Administration menu, and then click on the &#8220;Policy&#8221; tab.

Click inside the &#8220;Allow Service&#8221; section, at the bottom, then go up and click &#8220;Add Rule&#8221;.

You will be prompted with a dialog box, of where you can choose your service. Under the &#8220;Name&#8221; selection box, select &#8220;SSH&#8221;. This will automatically fill in the port field with 22. &#8220;When the source is&#8230;&#8221; needs to be selected for &#8220;Anyone&#8221;. Then click &#8220;Add&#8221;.

Also note, you have to click in the white space (Allow Service) in the policy tab, to click on Add Rule.
Also, apply the policy when you are finished for it to take effect.

---

### Post by monte48lowes on 2007-12-01
Try this in a terminal:

```
 cat /etc/ssh/sshd_config | grep 22
```

You should get:

```
Port 22
```

If you do not, then ssh-server is not waiting on port 22.

Mike

---

### Post by monte48lowes on 2007-12-01
If you did not install a firewall then ssh-server should be free to receive requests from the network. I did not install a firewall, nor did I have to open port 22. It was opened by installing ssh-server.

Mike

---

### Post by spydon on 2007-12-01
> **Dr Small said:**
> Also note, you have to click in the white space (Allow Service) in the policy tab, to click on Add Rule.
Also, apply the policy when you are finished for it to take effect.

The options under the policy tab is grayed out... :S

---

### Post by Dr Small on 2007-12-01
Click in the "Allow Services" area (at the bottom) and then the "Add Rule" at the top will become avaliable.

---

### Post by linuxusr50 on 2007-12-01
Based on your reply you may be fighting a double firewall issue.  The can be quite frustrating until found.

Sounds like you are  comfortable with your routers firewall and its forwarding rules.

My next suggestions would be to make sure you don't have any firewalls running on your machine you were not aware of.

Do the ```
ps -A | less
``` command again and look through your processes carefully to make sure you don't have shorewall or some other firewall running.  If you do have another running you will need to add a port 22 rule to it as well.


> I've tested from outside my network and from the inside, connection refused on both.

And ive already done portforwarding and I did it with that webpage. 

---

### Post by spydon on 2007-12-01
> **linuxusr50 said:**
> Based on your reply you may be fighting a double firewall issue.  The can be quite frustrating until found.

Sounds like you are  comfortable with your routers firewall and its forwarding rules.

My next suggestions would be to make sure you don't have any firewalls running on your machine you were not aware of.

Do the ```
ps -A | less
``` command again and look through your processes carefully to make sure you don't have shorewall or some other firewall running.  If you do have another running you will need to add a port 22 rule to it as well.

I get a long list with stuff, can i grep something?

---

### Post by Dr Small on 2007-12-01
> **spydon said:**
> I get a long list with stuff, can i grep something?
Have you tried allowing port 22 in firestarter yet ?

---

### Post by spydon on 2007-12-01
> **monte48lowes said:**
> Try this in a terminal:

```
 cat /etc/ssh/sshd_config | grep 22
```

You should get:

```
Port 22
```

If you do not, then ssh-server is not waiting on port 22.

Mike

It returns Port 22, yes.

---

### Post by spydon on 2007-12-01
> **Dr Small said:**
> Have you tried allowing port 22 in firestarter yet ?

Yup, still connection refused.

<b>I should maybe mention that this machine runs edgy</b>

---

### Post by Dr Small on 2007-12-01
> **spydon said:**
> Yup, still connection refused.

<b>I should maybe mention that this machine runs edgy</b>
I know this sounds dumb, but did you Apply the Policy ?

---

### Post by linuxusr50 on 2007-12-01
> I get a long list with stuff, can i grep something?

try these:

shorewall
guarddog
smoothwall

---

### Post by spydon on 2007-12-01
> **Dr Small said:**
> I know this sounds dumb, but did you Apply the Policy ?

Yes I did and I can see it under the policy tab.

But I really think this was weird:

```
spydon@spydon:~$ ps -A | grep ssh
 4345 ?        00:00:00 sshd
 4721 ?        00:00:00 ssh-agent
 4722 ?        00:00:00 ssh-agent
```

Should there really be 2 ssh-agent's running when I'm not connected to the machine?

---

### Post by Dr Small on 2007-12-01
> **spydon said:**
> Yes I did and I can see it under the policy tab.

But I really think this was weird:

```
spydon@spydon:~$ ps -A | grep ssh
 4345 ?        00:00:00 sshd
 4721 ?        00:00:00 ssh-agent
 4722 ?        00:00:00 ssh-agent
```

Should there really be 2 ssh-agent's running when I'm not connected to the machine?
No, but you could try killing them:
```
sudo kill 4722
```
and so forth

---

### Post by spydon on 2007-12-01
> **linuxusr50 said:**
> try these:

shorewall
guarddog
smoothwall

I didn't have any of them.

---

### Post by xeth_delta on 2007-12-01
Try restarting the server:
```
sudo /etc/init.d/ssh restart
```

Sorry if I missed it in the previous posts, can you login through ssh from inside the machine?

---

### Post by spydon on 2007-12-01
> **Dr Small said:**
> No, but you could try killing them:
```
sudo kill 4722
```
and so forth

I killed them and now I get this:
```
 4345 ?        00:00:00 sshd
 4721 ?        00:00:00 ssh-agent <defunct>
 4722 ?        00:00:00 ssh-agent <defunct>

```

---

### Post by spydon on 2007-12-01
> **xeth_delta said:**
> Try restarting the server:
```
sudo /etc/init.d/ssh restart
```

Sorry if I missed it in the previous posts, can you login through ssh from inside the machine?

Still connection refused after restart.
yes, ssh localhost works.

---

### Post by linuxusr50 on 2007-12-01
Try running NMAP against your internal and external IP to see if the port is open in both cases..

If you don't have nmap you can load it as follows:

```
sudo apt-get install nmap
```

After installing nmap on your internal and external machine do the following command on both IP's and report results here.

```
nmap -P0 yoursshservermachineip
```

```
nmap -P0 thewanipofyournetworkfromanexternalmachine
```

---

### Post by linuxusr50 on 2007-12-01
should be a capital P in both nmap command lines.

sorry.

---

### Post by Dr Small on 2007-12-01
> **linuxusr50 said:**
> should be a capital P in both nmap command lines.

sorry.
You can edit posts ;)

---

### Post by monte48lowes on 2007-12-01
I think it is something with the router like you had mentioned on the first page. The server is set to port 22 and so is the router. Something is not working with the router.. imho

Mike

---

### Post by spydon on 2007-12-01
> **linuxusr50 said:**
> Try running NMAP against your internal and external IP to see if the port is open in both cases..

If you don't have nmap you can load it as follows:

```
sudo apt-get install nmap
```

After installing nmap on your internal and external machine do the following command on both IP's and report results here.

```
nmap -p0 yoursshservermachineip
```

```
nmap -p0 thewanipofyournetworkfromanexternalmachine
```

spydon@spydon:~$ nmap -P0 192.168.1.39

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-12-02 03:22 CET
Interesting ports on 192.168.1.39:
Not shown: 1688 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
443/tcp  open  https
445/tcp  open  microsoft-ds
654/tcp  open  unknown
2049/tcp open  nfs
5900/tcp open  vnc

Nmap finished: 1 IP address (1 host up) scanned in 0.663 seconds
spydon@spydon:~$ nmap -P0 spydon.is-a-geek.net

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-12-02 03:22 CET
Interesting ports on 90-227-34-143-no42.tbcn.telia.com (90.227.34.143):
Not shown: 1696 closed ports
PORT   STATE SERVICE
80/tcp open  http

Nmap finished: 1 IP address (1 host up) scanned in 4.566 seconds


Note: The second machine is in the same local network.

---

### Post by linuxusr50 on 2007-12-01
thx Dr Small.

Had not been doing much in the forums for awhile and forgot.

---

### Post by Dr Small on 2007-12-01
Wait mac, before you try anything else!!!

Is this your IP ?
90.227.34.143

If so, I can connect to you from my server :)

---

### Post by spydon on 2007-12-01
> **Dr Small said:**
> Wait mac, before you try anything else!!!

Is this your IP ?
90.227.34.143

If so, I can connect to you from my server :)

Yes that is my IP, that is so weird :P

---

### Post by linuxusr50 on 2007-12-01
> Note: The second machine is in the same local network.

This may be the problem.  As I stated earlier some routes will need special rules to allow you to try and access from a local IP out to an wan IP and then back in on the wan IP.

Openwrt is a classic example.  It sets the ports up on VLAN's and prevents this type of activity by default.

Sounds like Dr. Small was able to connect to your server from the outside.

---

### Post by spydon on 2007-12-01
Well I guess this case is pretty solved then! :D I must have had my computer turned off or something when I tried from school...

THX EVERYBODY FOR HELPING! Now I'm going to bed the clock is 03:40 here |-).

---

### Post by spydon on 2007-12-02
A got a pretty good explanation on IRC why it doesm't work on some router's:
>  < IcePic_> many fws wont bounce traffic back in, so ssh-ing to your 
                 external ip wont work if it is supposed to be rewritten to 
                 some internal host.

---

### Post by Dr Small on 2007-12-02
Glad to see you got everything sorted out and working ;)

Dr Small

---

