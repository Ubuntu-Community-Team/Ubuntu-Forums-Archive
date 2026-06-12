---
title: "Network + Internet Issues"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by mmhmm on 2007-12-01
hi, i have just recently installed ubuntu on my desktop (yesterday) and i am having some issues with my connecting to the net, i cant. I am not experienced at all with linux, and need some help.

I cant connect to the internet with firefox, but i managed to find 'Network Tools' and have been able to ping [www.google.com](www.google.com) and it showed up and said it succeded. 

I have looked at the help in ubuntu, and read the section on connecting an ethernet ADSL network. It didnt help, so then i looked up my issue on the forums, still no luck. 

Im an unsure what is wrong, but i have a feeling that it hasnt installed the drivers. So i need some expert advice.

Thanks Very much, am looking foward to the reply

---

### Post by mmhmm on 2007-12-01
bump

---

### Post by fineas on 2007-12-01
In firefox bar menu, check at edit>preferances>advanced>network>settings. The problem might be there.Can you connect to the internet with other applications?

---

### Post by mmhmm on 2007-12-01
ive tryed pidgin messenger, hasnt worked. Ping still works...

firefox just shows the loading bar for ages, and never actually loads up the page. I have 512kbps internet, so it shouldnt take long to load...

any other ideas??

---

### Post by Romin-1 on 2007-12-02
Have you looked in Options-Advanced-Network- Settings to make sure that 'Direct Connection to the Internet' is checked? FF may be waiting for a dial-up connect.

HTH

Jon

---

### Post by mmhmm on 2007-12-02
yep, i have, still not working, im having a few problems with hardware though. The sound wont work, the internet wont work properly, and also my Nvidia graphics card drivers wont work.... lol, kinda hard 2 deal with atm

---

### Post by PointyWombat on 2007-12-02
hmm, lets stay focused on the internet problem first... so, what does the following reveal, in a terminal, type:

```
wget [www.google.com](www.google.com)
```

---

### Post by mmhmm on 2007-12-02
thanks for the help, sorry about the wait, but ill brb in 15 min

Thanks though

---

### Post by PointyWombat on 2007-12-02
no worries, i may or may not be here... but i'll continue to check and help where I can..

---

### Post by mmhmm on 2007-12-02
<Back Online>

the command tries to connect, but doesnt, but keeps retrying.

hasnt connected yet.

got any ideas?

---

### Post by PointyWombat on 2007-12-02
Can you post the output... it will show if it's resolving properly.....

Also, can you post output for:

ifconfig -a

and

netstat -ian

and

netstat -r

---

### Post by Romin-1 on 2007-12-02
My next step would be to look and see if your firewall has stopped FF. Next would be to check my DSL Modem/Router has it blocked. Also, some routers have a software firewall as well as a hardware one.

There's a jillion routers out there but this should open it up for you. Type 192.168.1.1 in the addy bar and go. If your router opens up it should show the status of your connection. If it says 'Not Connected' then try to make one. It should be pretty much a straight forward process. Have your ISPs info handy.

HTH

Jon

---

### Post by mmhmm on 2007-12-02
Yeah, sure.

user@user-desktop:~$ wget [www.google.com](www.google.com)
--04:39:52--  [http://www.google.com/](http://www.google.com/)
           => `index.html'
Resolving [www.google.com](www.google.com)... 1.0.0.0
Connecting to www.google.com|1.0.0.0|:80... failed: Connection timed out.
Retrying.

user@user-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:17:31:78:C6:E3  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe78:c6e3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3864 (3.7 KB)  TX bytes:11177 (10.9 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


user@user-desktop:~$ netstat -ian
Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0   1500 0        35      0      0      0      105      0      0      0 BMRU
lo    16436 0         0      0      0      0        0      0      0      0 LRU

user@user-desktop:~$ netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     *               255.255.255.0   U         0 0          0 eth0
link-local      *               255.255.0.0     U         0 0          0 eth0

---

### Post by mmhmm on 2007-12-02
there isnt a firewall on there unless ubuntu has an inbuilt onethat i dont know about...

i checked the router settings, and it says that its connected. Also, i know its working fine, because im on it on the other conputer sending u this message:)

lol, thanks for the advice though

---

### Post by PointyWombat on 2007-12-02
interesting,,, are you sure that's the last line of netstat -r? If not, its missing the default route.

There should be a line such as:
default         192.168.0.1     0.0.0.0         UG        0 0          0 eth1
which defines how to get to your router.

Under System->Administration->Network, do you have a Gateway address assigned, or is it DHCP?

You will probably need to add your router as the default route. This should fix the issue here.

---

### Post by PointyWombat on 2007-12-02
You can add the route manually with:

sudo route add default gw 192.168.1.1

(if 192.168.1.1 is actually your gw address)

see if that works

---

### Post by mmhmm on 2007-12-02
oh, sorry, there was another line under netstat -r

adsfdefault 192.168.1.1 0.0.0.0 UG 0 0 0 eth0

Also, in network under connections i have 'Wired connection' and 'Modem connection'

is that what you mean, because as i said, im not that experienced with linux yet :P

thanks

---

### Post by PointyWombat on 2007-12-02
OK, now worries then. You have a default route. 

Can you get to the router web admin page from your browser?

Also, can you show the output of
```

nslookup www.google.com
```

---

### Post by quandary on 2007-12-02
What's the result of the following commands ?

root@googlebot:~# lspci | grep "Network controller"

and

root@googlebot:~# lspci | grep "Ethernet controller"

---

### Post by mmhmm on 2007-12-02
nslookup [www.google.com](www.google.com) brings up:

Server: 192.168.1.1
Address: 192.168.1.1#53

Non-authorative answer:
[www.google.com](www.google.com) canonical name = [www.l.google.com](www.l.google.com).
Name: [www.l.google.com](www.l.google.com)
Address: 74.125.19.104
Name: [www.l.google.com](www.l.google.com)
Address: 74.125.19.99
Name: [www.l.google.com](www.l.google.com)
Address: 74.125.19.147
Name: [www.l.google.com](www.l.google.com)
Address: 74.125.19.103

also, i am in my router settings now

---

### Post by mmhmm on 2007-12-02
> **quandary said:**
> What's the result of the following commands ?

root@googlebot:~# lspci | grep "Network controller"

and

root@googlebot:~# lspci | grep "Ethernet controller"

Nothing comes up for "network controller'

but 'ethernet controller' shows:

02:0d.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)

---

### Post by PointyWombat on 2007-12-02
Hmm..  This is really odd

Lets check if port 80 traffic is getting out. In a terminal type:
```

telnet www.google.com 80
```

You should get something like:
```
Trying 72.14.253.147...
Connected to www.l.google.com.
Escape character is '^]'.
```

---

### Post by mmhmm on 2007-12-02
says its trying '1.0.0.0'

hasnt come up with anything else yet, been about 2 mins

---

### Post by PointyWombat on 2007-12-02
Yeah, something is messing up with name resolution... 

if you type:

```
telnet 72.14.253.103 80
```

that will probably work...

Also, try  [http://72.14.253.99/](http://72.14.253.99/) in Firefox. Does that work

---

### Post by mmhmm on 2007-12-02
Trying 72.14.253.103.
Connected to 72.14.253.103.
Escape Character is '^]'
Connection closed by foreign host.

---

### Post by PointyWombat on 2007-12-02
yeah, this shows that port 80 (http) is working fine.. if you type 'get' after the 'Escape Character..." line, it will retrieve the raw html from the remote server.. so we see now the name resolution is messed up.

What we need to do is set up your name resolution configuration in /etc/resolv.conf, but you'll first need to find out what they are for your ISP.  You should be able to find this somewhere in your router web pages.

What kind of router do you have?

You'll need to find entries for at least the Primary DNS server and add it to /etc/resolv.conf.

The file /etc/resolv.conf should contain at least two lines,

search <your.domain>
nameserver <ip address of your DNS server>

You can add multiple nameserver entries if you have secondary or tertiary.


Out of curiosity, can you post the output from your other PC, I'm assuming it's windows XP. The output of 'ipconfig /all'. This will let me know if your windows XP is getting DNS from your router, or from your ISP.

---

### Post by PointyWombat on 2007-12-02
...anyway.. just know that it's typically not this troublesome to get networking working... it should have just worked out of the box. I don't know if it's becuase of your router, or if it's something with ubuntu. I'll check the thread tomorrow.

keep plugn' away & good luck.

---

### Post by mmhmm on 2007-12-02
Here is the raw info:

user@user-desktop:~$ telnet 72.14.253.103 80
Trying 72.14.253.103...
Connected to 72.14.253.103.
Escape character is '^]'.
get


<html><head>
<meta http-equiv="content-type" content="text/html;charset=utf-8">
<title>400 Bad Request</title>
<style><!--
body {font-family: arial,sans-serif}
div.nav {margin-top: 1ex}
div.nav A {font-size: 10pt; font-family: arial,sans-serif}
span.nav {font-size: 10pt; font-family: arial,sans-serif; font-weight: bold}
div.nav A,span.big {font-size: 12pt; color: #0000cc}
div.nav A {font-size: 10pt; color: black}
A.l:link {color: #6f6f6f}
A.u:link {color: green}
//--></style>
<script><!--
var rc=400;
//-->
</script>
</head>
<body text=#000000 bgcolor=#ffffff>
<table border=0 cellpadding=2 cellspacing=0 width=100%><tr><td rowspan=3 width=1% nowrap>
<b><font face=times color=#0039b6 size=10>G</font><font face=times color=#c41200 size=10>o</font><font face=times color=#f3c518 size=10>o</font><font face=times color=#0039b6 size=10>g</font><font face=times color=#30a72f size=10>l</font><font face=times color=#c41200 size=10>e</font>&nbsp;&nbsp;</b>
<td>&nbsp;</td></tr>
<tr><td bgcolor=#3366cc><font face=arial,sans-serif color=#ffffff><b>Error</b></td></tr>
<tr><td>&nbsp;</td></tr></table>
<blockquote>
<H1>Bad Request</H1>
Your client has issued a malformed or illegal request.

<p>
</blockquote>
<table width=100% cellpadding=0 cellspacing=0><tr><td bgcolor=#3366cc><img alt="" width=1 height=4></td></tr></table>
</body></html>
Connection closed by foreign host.


My router is a Netcomm NB5

how do i copy the output from command prompt?

also, do you have msn, might be easier?

---

### Post by quandary on 2007-12-02
> **PointyWombat said:**
> 
The file /etc/resolv.conf should contain at least two lines,

search <your.domain>
nameserver <ip address of your DNS server>

Out of curiosity, can you post the output from your other PC, I'm assuming it's windows XP. The output of 'ipconfig /all'. 
This will let me know if your windows XP is getting DNS from your router, or from your ISP


If you use a NAT router, there should only be the line:
nameserver 192.168.1.1

where 192.168.1.1 ist the IP of your gateway (ADSL router/modem).
You can use IPconfig from windows to get the IP of the gateway.
c:\windows\system32\ipconfig.exe
in start->run     type cmd then hit enter, then type ipconfig /all and hit enter, as suggested


> 
Nothing comes up for "network controller'


Good, so there is no wireless network card that interferes.

> 
how do i copy the output from command prompt?

To copy paste text from windows console, mark it with the mouse, and then hit enter 
it's then in your clipboard, and you can paste it to here.
--------

You can also just note the ip that is labeled: gateway
on a paper.

You then start ubuntu, open a termial, and type:
sudo gedit /etc/resolv.conf

and there you make sure it is written:
nameserver 192.168.1.1

where 192.168.1.1 is the IP you got from windows.

Afterwards, your network should work.

PS: You maybe have to restart Linux for the changes to take effect.

---

### Post by mmhmm on 2007-12-02
hey, thanks, ill look into this tomorrow, australian time... :P

---

### Post by quandary on 2007-12-02
> **mmhmm said:**
> 
hey, thanks, ill look into this tomorrow, australian time... :P


You're welcome.
Australian time, whatever that is :lolflag:

---

### Post by Romin-1 on 2007-12-02
When all else fails you might try what is suggested on this page concerning pppoe/dsl connections.

[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

Good luck,

Jon

---

### Post by PointyWombat on 2007-12-02
Could you also post the output for the following which shows how DHCP is being setup:

```
sudo /etc/init.d/networking restart
```

---

### Post by Romin-1 on 2007-12-02
Hmmmm; just wondering if the 'Wired Connection' is set to 'Roaming'? In my case it has to be in order for it to work.

Jon

---

### Post by mmhmm on 2007-12-03
quandary, i checked the default gateway, and then checked nameserver in linux, it was the same, but still doesnt work.

seems to be a really strange case?

---

### Post by mmhmm on 2007-12-03
Romin-1, the command 'sudo pppoeconf' said that the access concentrator did not respond.

it said that the cable might not be connected. so i checked if it was, both ends are, and the ehternet light is on at the router

---

### Post by mmhmm on 2007-12-03
PointyWombat, 'sudo /etc/init.d/networking restart' brought up:

*Reconfiguring Network Interfaces... [OK]

Nothing else

---

### Post by mmhmm on 2007-12-03
Romin-1, by the way roaming is on.

---

### Post by jimbean on 2007-12-03
i had to disable roaming
and check automatic dhcp

---

### Post by quandary on 2007-12-03
> **jimbean said:**
> 
i had to disable roaming
and check automatic dhcp


Oh yea, your router/modem should of course have dhcp activated...
But i think that's default config on ADSL routers, and you shouln't have gotten the raw webpage, if dhcp wasn't active.


Hm, strange.
it may also be that your router/modem is in bridge mode.
So maybe you should try an external nameserver in /etc/resolv.conf
try the IP
195.186.4.109

this is cns2.bluewin.ch, my ISP's nameserver. 
I can just look it up very fast on my router, so that's why i give you this one.
That IP should also work for you, at least i suppose so.


also, before doing the above, make sure you didn't misread/typed your gateway's ip.
there might be only a slight difference between the numbers, like
192.168.1.1
and
192.168.0.1
and 
192.186.1.1
and
192.186.0.1
which you can easily mix up ;-)


In all cases, don't forget to restart the network config / Linux for the changes to take effect.

---

### Post by gaylapdancer on 2007-12-03
Are you using Gutsy? If so, open firefox, type ```
about:config
``` into the address bar. A whole lot of text will show on the screen. In the filter bar, type ```
ipv6
``` The result "network.dns.disableIPv6" should be there. Double click that option so that under the Value column, it reads 'True'. Restart firefox, then try getting to google. If firefox now works, but other apps still don't, you are in thee same situation as me :) In that case, we wait for more help :)

---

### Post by PointyWombat on 2007-12-04
OK, just so I have this all straight. Here's what we know. Correct me if I'm wrong.

The behaviour we're seeing is:
Firefox and wget can get to an IP but not resolve a name.
nslookup and ping can resolve a name and works fine

Your box is wired, not wireless
It's using DHCP and gets the IP address of 192.168.1.101 from your router
Your using 192.168.1.1 for your router for DNS and gateway


I found this link which also may help with your situation, but doesn't explain why wget fails to resolve. [http://ubuntuforums.org/archive/index.php/t-53112.html](http://ubuntuforums.org/archive/index.php/t-53112.html)

Can you post the output of whatever you have in /etc/resolv.conf?

Thanks,

---

### Post by PointyWombat on 2007-12-04
Further to this, there are two things I'd like you to try.

First, use known good OpenDNS servers for name resolution instead of using your router. This can be done commenting out (putting a # sign at the start of the line) any existing nameserver lines, and put the following lines in your /etc/resolv.conf file:

```
nameserver 208.67.222.222
nameserver 208.67.220.220
```

Test it out by just doing a nslookup and you should see that it's now using those name servers.  Here's a link to some Ubuntu instruction from the [OpenDNS]("https://www.opendns.com/start?device=ubuntu") site.

Secondly, if that doesn't work, disable IPV6 on FireFox. I've read several other threads, both ubuntu and others, regarding this and some have had success with this. Depends on their router it seems.

Good luck.

---

### Post by 77_Chris on 2008-01-05
I had exactly the same problem, "Bad Request" in FF and on install/updates.
I am using a Netgear DG834G ADSL Modem/Router and Ubuntu 7.10..

After trying out some of the hints given here, I recogniced that my fault was to set my router as network-proxy under System->preferences.
When I changed this to direct connection to the internet, everything worked fine.

Further Settings:
-DHCP on (Roaming deactivated)
-Set Firefox to auto-detect Proxy-Settings
-Using original DNS-Server given by ISP
-IPv6 not disabled

Cheers!

---

### Post by 77_Chris on 2008-01-07
Sorry, I have to withdraw, the problem is still evident.
But it only appears sometimes. 
It is possible to update the system without any errors but I can not install the Java Firefox-Plugin for example.
If I try, "HTTP 400: Bad Request"-Error still apears.

Has anybody meanwhile solved this problem?

---

### Post by caravel on 2008-01-07
> **PointyWombat said:**
> Further to this, there are two things I'd like you to try.

First, use known good OpenDNS servers for name resolution instead of using your router. This can be done commenting out (putting a # sign at the start of the line) any existing nameserver lines, and put the following lines in your /etc/resolv.conf file:

```
nameserver 208.67.222.222
nameserver 208.67.220.220
```

Test it out by just doing a nslookup and you should see that it's now using those name servers.  Here's a link to some Ubuntu instruction from the [OpenDNS]("https://www.opendns.com/start?device=ubuntu") site.

Secondly, if that doesn't work, disable IPV6 on FireFox. I've read several other threads, both ubuntu and others, regarding this and some have had success with this. Depends on their router it seems.

Good luck.

I second this advice.  You should _disable ro***a***ming_, configure a static address (such as 192.168.1.100 and enter the address of your router/gateway (probably 192.168.1.1) as your primary DNS address.  Then log into your router and use the OpenDNS nameservers as your primary and secondary.  Also check the address range in your router and make sure you use a static address in that range.

I think Ubuntu does have a built in IPtables firewall, so if your router also has a firewall you may want to disable the Ubuntu one, though I'm not 100% sure about that so wait for someone that knows more about this to post.

---

### Post by limsengwee1988 on 2008-01-19
> **gaylapdancer said:**
> Are you using Gutsy? If so, open firefox, type ```
about:config
``` into the address bar. A whole lot of text will show on the screen. In the filter bar, type ```
ipv6
``` The result "network.dns.disableIPv6" should be there. Double click that option so that under the Value column, it reads 'True'. Restart firefox, then try getting to google. If firefox now works, but other apps still don't, you are in thee same situation as me :) In that case, we wait for more help :)

gaylapdancer, i have the same problem as u and disabledIPv6 and firefox works,but when i want to download any updates,i have a problem, any solution with that???

---

