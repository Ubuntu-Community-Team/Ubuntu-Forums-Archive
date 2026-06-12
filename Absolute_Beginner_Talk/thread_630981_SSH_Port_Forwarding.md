---
title: "SSH Port Forwarding"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by seattle vic on 2007-12-03
This is driving me crazy.  So I'm trying to connect to my Ubuntu computer from outside my local network (ie, from work) with SSH.  I currently have a Linksys wrt54gl router with two hard connections and a wireless that I use with my laptop.

I can SSH (and VNC) from my laptop to the ubuntu box, as well as from the other internal desktop.  Everything works fine within the LAN.  However, if I try to connect either from work or from another linux shell (externally, which I ssh into from my laptop) with either putty or ssh, I get a connection refused.

The router has enabled and "Block Anonymous Internet Requests is disabled (ie, not blocked).  Under applications and gaming/port range forward menu, I have port 22 enabled and forwarded to my ubuntu computer, which is 192.168.2.101.  Nothing works.

Here is the ssh command I've been trying from the external linux shell I'm using to test:

vic@li12-123:~$ ssh -L 1234:192.168.2.101:22 207.xxx.xx.xxx
ssh: connect to host 207.xxx.xx.xxx  port 22: Connection refused

(Could it be that by using ssh from my laptop to go out to the external linux shell ties up port 22 so I can't come back in to the ubuntu desktop???  I'm not a wizard on ports, yet.)

Also, if I use canyouseeme.com and test for open ports, it cannot find any, even ones that I've opened in the router.

where xxx is for privacy, but that is the ip address that my ISP provides.  IE, if I use whatismyip.com, that is what I get back.

I've called the ISP and verified that they do not block ports.

I've read just about every article and thread on this and still cannot make it work, so would REALLY appreciate some help.  I've been at this for a week.

One other question.  When I was talking to linksys via a chat, they indicated that the assigned ip of the router - which is 10.0.0.6 - is what I should use to access my internal machine.  That is what is shown in the router admin page, but I can't get to it from the outside at all.

Thanks in advance...

---

### Post by kelbizzle on 2007-12-03
Fortunately you have a router that supports loopback connections so troubleshooting this will be easy. Try this command on another computer from inside your LAN using your WAN address. I think the problem lies within the command. 

```
ssh user@69.191.72.425
```

If you have port 22 forwarded to the right machine. The above code will reach it's target. You don't have to specify the port. The default is 22.

---

### Post by Severun on 2007-12-03
I was just going to say that.  I don't think you need to use port fowarding in SSH, you just need to set your linksys up to forward connections from the outside world into your linux box on tcp port 22.

So if you have

Outside IP -> Linksys Outside IP | Linksys Inside IP -> Unbuntu Inside Ip

You set up your linksys to forward any incoming connections on port 22 to your Ubuntu inside IP.

Then you just do as stated above ssh user@Linksys Outside IP and the linksys will foward to your Ubuntu box on port 22 and you should get a connection.

If I understand what you are trying to do correctly, this should work for you.

---

### Post by seattle vic on 2007-12-04
> **kelbizzle said:**
> Fortunately you have a router that supports loopback connections so troubleshooting this will be easy. Try this command on another computer from inside your LAN using your WAN address. I think the problem lies within the command. 

```
ssh user@69.191.72.425
```

If you have port 22 forwarded to the right machine. The above code will reach it's target. You don't have to specify the port. The default is 22.

If by the above address (69.191.72.425) you really meant the ip that I see if I do a "whatsmyip.com", ie, 207.xxx. etc, I tried it and got a connection refused.

---

### Post by seattle vic on 2007-12-04
> **Severun said:**
> I was just going to say that.  I don't think you need to use port fowarding in SSH, you just need to set your linksys up to forward connections from the outside world into your linux box on tcp port 22.

So if you have

Outside IP -> Linksys Outside IP | Linksys Inside IP -> Unbuntu Inside Ip

You set up your linksys to forward any incoming connections on port 22 to your Ubuntu inside IP.

Then you just do as stated above ssh user@Linksys Outside IP and the linksys will foward to your Ubuntu box on port 22 and you should get a connection.

If I understand what you are trying to do correctly, this should work for you.

No, didn't work.  And as I mentioned in my orig post, I was aware of the linksys inside ip, which is 10.0.0.6, but I assume I don't need to address that anywhere?

Now, I also learned about the nmap utility and tried it both from outside and from inside and got the same thing:

From inside:

vic@boxster:~$ nmap xxx.xxx.xx.xxx

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-12-03 22:38 PST
Interesting ports on uswa138.isomedia.com (207.xxx.xx.xxx):
Not shown: 1693 closed ports
PORT     STATE    SERVICE
21/tcp   open     ftp
23/tcp   open     telnet
80/tcp   open     http
1720/tcp filtered H.323/Q.931

Nmap finished: 1 IP address (1 host up) scanned in 3.319 seconds

From Outside:

vic@li12-123:~$ nmap 207.xxx.xx.xxx -P0

Starting Nmap 4.11 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2007-12-04 01:35 EST
Interesting ports on uswa138.isomedia.com (207.xxx.xx.xxx):
Not shown: 1677 closed ports
PORT   STATE    SERVICE
21/tcp filtered ftp
23/tcp filtered telnet
80/tcp filtered http

Nmap finished: 1 IP address (1 host up) scanned in 14.511 seconds

It kind of looks like I'm not getting through the router...

Also, I do appreciate you guys getting back to me so quickly.  This is something that makes Ubuntu a plus.

---

### Post by seattle vic on 2007-12-04
> **seattle vic said:**
> No, didn't work.  And as I mentioned in my orig post, I was aware of the linksys inside ip, which is 10.0.0.6, but I assume I don't need to address that anywhere?

Now, I also learned about the nmap utility and tried it both from outside and from inside and got the same thing:

From inside:

vic@boxster:~$ nmap 207.xxx.xx.xxx

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-12-03 22:38 PST
Interesting ports on uswa138.isomedia.com (207.xxx.xx.xxx):
Not shown: 1693 closed ports
PORT     STATE    SERVICE
21/tcp   open     ftp
23/tcp   open     telnet
80/tcp   open     http
1720/tcp filtered H.323/Q.931

Nmap finished: 1 IP address (1 host up) scanned in 3.319 seconds

From Outside:

vic@li12-123:~$ nmap 207.xxx.xx.xxx -P0

Starting Nmap 4.11 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2007-12-04 01:35 EST
Interesting ports on uswa138.isomedia.com (xxx.xxx.xx.xxx):
Not shown: 1677 closed ports
PORT   STATE    SERVICE
21/tcp filtered ftp
23/tcp filtered telnet
80/tcp filtered http

Nmap finished: 1 IP address (1 host up) scanned in 14.511 seconds

It kind of looks like I'm not getting through the router...

Also, I do appreciate you guys getting back to me so quickly.  This is something that makes Ubuntu a plus.
   
Vic

---

### Post by sammydee on 2007-12-04
You have a telnet port opened? I hope you aren't running a telnet service on that which is open to the world - I'm pretty sure telnet is notoriously insecure.

Also, publishing your ip address on a public forum along with a list of open ports is not to be recommended at all. I would edit your post if I was you.

As to your port forwarding problem, I think it could be a problem with dynamically allocated network addresses from your router. I'm going to start at the beginning so we can find out what your problem is. Here is what your network arrangement looks like (I think):


internet ----- router ----- ubuntu firewall ----- pc

Is that correct? We need to check each link in the chain to make sure that it's all doing what it should.

Firstly, check your ssh service is actually running. You can type:

```
netstat -l
```

There should be a service running on port 22 (if that's your ssh port. If it is, I recommend changing it to something more obscure otherwise you will be subject to a lot of brute force attacks).

Next up is to check that port 22 is open in your firewall. Ubuntu comes with all ports locked down by default, to change this, I like to use firestarter. I'll assume you are using firestarter. You need to go policy and make sure that under incoming traffic policy, port 22 is explicitly allowed from any host.

If you can connect to ssh from another machine on your lan, you know the above two are configured correctly.

Next up is getting the traffic past the router, which is what seems to be your problem. First up is to make sure that the lan ip address for your server is static. All routers have different ways of doing this, and some can't do it at all. You need to use mac address binding to make sure your server gets the same ip from the router every time it requests on via dhcp. You should be able to find out how to do this on the internet somewhere.

I am going to assume for the sake of this exercise that your router ip address is 192.168.0.1 and you have told it to give your server an ip address of 192.168.0.5 every time.

Now you need to enable a port forward on your router. If it asks you to specify a start port and end port, just put 22 for both of them. You need it to forward those ports to host 192.168.0.5. Once this is done there should be a clear channel for port 22 requests to come in from the internet to your server.

Incidently, you mentioned that you have a linksys wrt54gl. Are you running dd-wrt or openwrt on it? If not I highly recommend them, ridiculously configurable and powerful.

A couple of other things that could be causing your problem. Firstly, some nasty ISPs block incoming access on certain ports. Secondly, the linksys wrt54gl has no DSL connection. Are you using a separate modem? If so, is this separate modem applying nat and blocking connections?

Sam

---

### Post by Whiffle on 2007-12-04
How are you assigning your internal IP addresses?  

I know on my router here and my dad's router at home you can't assign a static IP address within the range that dhcp uses to assign addesses.  If you do, it will sort of kind of work sometimes, but tends to not work.  I've got dd-wrt on my router and its set to automatically assign ip's based on mac address, so I get the same ip every time for each computer, then I have port forwarding based on that.  Also, I accidentally did  what I just described and it looked like my port 22 was closed on my router, just like yours.

---

### Post by kelbizzle on 2007-12-04
Do you use dsl or cable? The reason I ask is because with dsl  and some cable ISP's started shipping modems that used a dhcp server to simplify things. It's possible that your modem has a built in firewall. My dsl modem has a 192.168.1.1 configuration page with a built in firewall. What you can do to find out is log into your linksys router, click status and check out the "Internet IP address" If it's a 192.xxx.xxx.xx address then your modem has a dhcp server and possible a firewall. If the ip address is your 207 then your fine your linksys connects directly to the internet. 

Did you install firestarter firewall on your dekstop or anything? Like sammydee said  What does netstat -l output?

---

### Post by Dr Small on 2007-12-04
Please read my blog post on how to setup a SSH Server with Port Forwarding:
[http://php.8ez.com/drsmall/blog/?p=124](http://php.8ez.com/drsmall/blog/?p=124)

---

### Post by kelbizzle on 2007-12-04
> **Dr Small said:**
> Please read my blog post on how to setup a SSH Server with Port Forwarding:
[http://php.8ez.com/drsmall/blog/?p=124](http://php.8ez.com/drsmall/blog/?p=124)

I don't think he's having problems setting it up. He has it setup already as he can connect from inside the LAN. We're  troubleshooting port connectivity issues. Check this Community doc on IPTABLES. Specifically the section on opening a specific port. [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by seattle vic on 2007-12-05
Folks,

thanks for the replies.  First, no, I do not have a telnet port opened, which is another reason why it's confusing.  I did edit my ip address; didn't know I could go back and do that, thanks.

I did the netstart -l and ssh is running on port 22.  Thanks for the advice; I will change that port number in the future.

Soooo, I did not realize that ubuntu has their ports locked.  I downloaded firestarter and enabled port 22.  No joy.

However, on reading Kelbizzle's reply, I did some checking and damn if my Zoom X3 DSL modem doesn't have a firewall.!!!!!  And one with menus so complicated that it's not straightforward how to just turn it off.  Looks like you can't.

Threre is a section called "Port Settings" that only has entries for HTTP, Telnet and FTP, coincidently what nstat showed.

There's another section called IP filtering, which has provisions for a lot of rules that I guess I need to understand.  I see rules for a lot of ports, but not 22, so I'm thinking I need to figure this out and add something for 22.

It smells like this is the issue, so if anybody knows a quick way to either disable the whole modem firewall (remember, I still have my router firewall and firestarter) or an easy way to enable 22, that would be great.

Vic

---

### Post by kelbizzle on 2007-12-05
> **seattle vic said:**
> Folks,
Soooo, I did not realize that ubuntu has their ports locked.  I downloaded firestarter and enabled port 22.  No joy.

However, on reading Kelbizzle's reply, I did some checking and damn if my Zoom X3 DSL modem doesn't have a firewall.!!!!!  And one with menus so complicated that it's not straightforward how to just turn it off.  Looks like you can't.


That explains the 10.0.xx.xx ip address that your linksys has. Check all the modems under the zoom category on this website. [http://portforward.com/english/routers/port_forwarding/routerindex.htm](http://portforward.com/english/routers/port_forwarding/routerindex.htm) One of the config pages are bound to be like yours. You should have a virtual servers buttons in the advanced setup page. Forward this port to your linksys's 10.0.xx.xx address.  If not you may have to add an NAT rule. 

> **seattle vic said:**
> 

Threre is a section called "Port Settings" that only has entries for HTTP, Telnet and FTP, coincidently what nstat showed.

There's another section called IP filtering, which has provisions for a lot of rules that I guess I need to understand.  I see rules for a lot of ports, but not 22, so I'm thinking I need to figure this out and add something for 22.

It smells like this is the issue, so if anybody knows a quick way to either disable the whole modem firewall (remember, I still have my router firewall and firestarter) or an easy way to enable 22, that would be great.

Vic

It's exactly your issue. The traffic for port 22 is not getting in through your dsl modem because it doesn't have the port opened. It's definitely doable. Show me a screenshot of your configuration page.

---

### Post by seattle vic on 2007-12-07
> **kelbizzle said:**
> That explains the 10.0.xx.xx ip address that your linksys has. Check all the modems under the zoom category on this website. [http://portforward.com/english/routers/port_forwarding/routerindex.htm](http://portforward.com/english/routers/port_forwarding/routerindex.htm) One of the config pages are bound to be like yours. You should have a virtual servers buttons in the advanced setup page. Forward this port to your linksys's 10.0.xx.xx address.  If not you may have to add an NAT rule. 



It's exactly your issue. The traffic for port 22 is not getting in through your dsl modem because it doesn't have the port opened. It's definitely doable. Show me a screenshot of your configuration page.

Boy, what a frustrating experience.  I've had three phone calls with Zoom tech support, and they can't figure it out.  I first asked if we can just disable the firewall, which in DSL-speak is a full bridge.  Tried that and it didn't work, so next I'm going to bypass the router and connect directly from one of my desktops computers to the modem and see if I can open port 22 via a remote shell that way.

If I can do that, then there's something about the wrt54gl router setup that I'm not doing right.  This is looking like deep science.

Vic

---

### Post by wormser on 2007-12-07
> **seattle vic said:**
> If I can do that, then there's something about the wrt54gl router setup that I'm not doing right.  This is looking like deep science.

Vic

Just in case that is the problem.  Here is a [guide]("http://portforward.com/english/routers/port_forwarding/Linksys/WRT54GL/default.htm") to port forward the WRT54GL.

---

### Post by kelbizzle on 2007-12-07
Show me some screen shots of your DSL modem configuration page I could walk you through setting up a rule that will forward traffic on  port 22 to your computer. In theory since your dsl modem  is forwarding port 23  to your linksys any...you could change the firewall on the linksys to forward traffic on port 23 to your computer. Then you'll need to change the sshd config to listen on port 23.

---

