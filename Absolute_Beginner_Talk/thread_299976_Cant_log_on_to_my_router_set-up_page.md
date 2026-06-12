---
title: "Cant log on to my router set-up page"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by phelixnyc on 2006-11-15
I recently installed Dapper, I tried to access my router set-up page and couldn't. I connect to the net trough my main pc that is connected to my router (Linksys WRT54G v.5). I have two hard dives in my main pc, one Windows, one Ubuntu. I have no problem logging into my set-up page(using the address bar)trough Windows. I have no luck with Dapper. Iam not even sure if it recognizes my router, I believe it does since I can surf the net. Can someone tell me where to begin to solve this problem.

---

### Post by Leonivek on 2006-11-15
> **phelixnyc said:**
> I connect to the net trough my main pc that is connected to my router (Linksys WRT54G v.5). 

I'm sorry if this sounds stupid, but why would you connect to the net  through another computer when you have a router?  If I understood you correctly, I'm assuming that the Windows machine is between the router and your Ubuntu machine?

My guess is that Windows is preventing your Ubuntu machine from accessing the router's private IP (192.168.X.X or whichever), since it's the middle-man... maybe a firewall?  Not sure...:confused:

---

### Post by phelixnyc on 2006-11-15
No both os are on one pc. I choose the os I would like to boot to using my mobo boot utility. I just want to be able to acces the router through Ubuntu as well.

---

### Post by mahy on 2006-11-15
> **phelixnyc said:**
> No both os are on one pc. I choose the os I would like to boot to using my mobo boot utility. I just want to be able to acces the router through Ubuntu as well.

Do you connect via cable or wirelessly? I have the same model and all it ever took was typing "sudo dhclient eth0" to get it connected. Replace eth0 with actual name of your network interface, but most likely it is eth0.

---

### Post by CatKiller on 2006-11-15
> **phelixnyc said:**
> I recently installed Dapper, I tried to access my router set-up page and couldn't.

You might want to specify some more information about the symptoms you experienced. For example, a 404-style message would suggest that you haven't managed to set up your network card yet, whereas a Forbidden message might imply that you've put in the wrong password. Without knowing what error messages, if any, you're getting it is difficult for anyone that might be able to help you to do so.

---

### Post by Leonivek on 2006-11-15
> **phelixnyc said:**
> No both os are on one pc. I choose the os I would like to boot to using my mobo boot utility. I just want to be able to acces the router through Ubuntu as well.

Ah, okay!  That makes more sense!  ;)  It's odd that you can't access your router config, but you can access the Internet... 

Have you tried pinging your router's IP address?  My guess is something in Ubuntu is preventing access to private IP addresses, like **moblock** or a firewall or something, or you are accessing your router but your router itself is preventing your computer from accessing it's config for some reason...  

Does your router have a setting somewhere that only allows connections to it's config from a certain IP address on the LAN?

---

### Post by phelixnyc on 2006-11-16
I connect via cable. I a new to Linux and dont know were to ping my routers ip address. Not sure where to look for the settings your talking about (Leonivek).

---

### Post by jimbob on 2006-11-16
Try to ping the router by entering:

    $sudo ping 192.168.1.1

If this works, does entering 192.168.1.1 in the address bar of your browser bring up the router login screen?
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by tospig on 2006-11-26
Hi jimbob - I don't mean to hijack this thread but I can ping my router from the terminal window, but I can't access it by typing the address into my browser (firefox).

do you know why?

---

### Post by WinterWeaver on 2006-11-26
I have the same problem as the author (phelixnyc).

This is a very funny problem, because, it used to work. Then after a while it stopped. Originally I thought it may have been Firestarter, because it stopped working right after I installed it, and after I removed it, it worked again. A day later though, it stopped working again O.o ??

here is the description of the error, as I have it atm. (btw there are no error messages like "not authorized" or "404 not found" etc)

I enter the router ip in the address bar, and it asks me for the user and pass. I enter this and, by the flip of a coin it seems, it sometimes shows me the main router page, or it just sits there and tries to load the page for ages, with no result T_T

IF you are so lucky as to get to the main page, the same principle applies to any of the other 'sub-pages' ... flip the coin, and it either works or it doesn't.

On my windows boot, it works 100%.
On the Ubuntu Live CD, it works 100%.
After the install, it works for a bit ... ?

Any Ideas anyone??

---

### Post by jimbob on 2006-11-26
Has anyone tried to reset the firmware in their router by depressing the reset button on the back?

---

### Post by 56phil on 2006-11-26
This is weird. I have a Linksys WRT54G (Firmware Version: v3.03.1) and everything is nominal.:-k

---

### Post by WinterWeaver on 2006-11-26
I have tried resetting the router. I also restored the factory defaults. didn't work :P

I forgot to mention, I actually have a different router (don't have the name and specs on me now), so this does not seem to be router specific.

---

### Post by houstonbofh on 2006-11-26
> **WinterWeaver said:**
> I have tried resetting the router. I also restored the factory defaults. didn't work :P

I forgot to mention, I actually have a different router (don't have the name and specs on me now), so this does not seem to be router specific.
Well there goes my answer...  I have seen this on a lot of wrt54g's with a software firewall.  You might look that direction.

---

### Post by venkatmangudi on 2006-11-26
Do you have any extensions on your Firefox? Some routers need Javascript for their router home page to function properly. If you have the NoScript extension, you might not see the home page. Just a thought... :-k

---

### Post by WinterWeaver on 2006-11-28
> Do you have any extensions on your Firefox? Some routers need Javascript for their router home page to function properly. If you have the NoScript extension, you might not see the home page. Just a thought... 

I'll check that quickly, but I don't think that's the problem. I've tried various other browsers also, because I thought it might be firefox, but all of them have the same result.

I feel I need to mention again. It's not that I can't access the page. The main problem is that, sometimes it loads, and sometimes it doesn't. This same Load/don't Load routine applies for all sub pages on the router.

so, for example: Let say the Router Home Pages loads succesfully. Now I click on WAN configuration... bam it doesn't work... I refresh a couple of times.. nothing.
- Tomorrow, I try again, and bam, success ??

It's the same in both Ubuntu and Kubuntu, but not in windoze.

T_T

---

### Post by mssever on 2006-11-28
I have a Linksys WRT54G router and I can confirm that it requires Javascript for some dumb reason. (This means that I can't use elinks to configure it.)

My router has been somewhat flakey. At one point, one of my Ubuntu machines couldn't get a connection, while the other one would. All this is to say that I think the problem is with your router. If you're in the US and still under warranty, I would suggest calling Linksys tech support. I got a replacement router from them that seems to be working OK so far.

BTW: Linksys is one of those companies that only wants you to use Internet Explorer.

---

### Post by STREETURCHINE on 2006-11-28
i dont know if you have the same problem as i did but it sounds the same ,
i had to turn of all virus protection and any firewall on my machine to get acces to that page it may work for you,
if you use a firewall outher than windows turn it of and make sure windows fire wall doesnt switch on.

---

### Post by Epperly on 2006-11-29
I just got a new WRT54G ver. 6 and I can't access 192.168.1.1 at all, I called up Linksys and they said their router "is not compatible with Linux"

---

### Post by Peepsalot on 2006-11-29
Are you putting "http://" at the beginning of your URL.  If you are leaving this out, maybe it is causing problems.

---

### Post by mssever on 2006-11-30
> **Epperly said:**
> I just got a new WRT54G ver. 6 and I can't access 192.168.1.1 at all, I called up Linksys and they said their router "is not compatible with Linux"

That's the same router I have, and I can assure you that it's compatible with Linux. What does Linksys tech support know? :) I've confused my share of their techs.

if you type [http://192.168.1.1](http://192.168.1.1) into your browser you should be able to access it. If you can't, double-check your connection to the router. Failing that, restart networking: ```
sudo /etc/init.d/networking restart
```You can also use telnet to troubleshoot your connection by talking directly to the router. Type ```
telnet 192.168.1.1 80
``` You should see something like ```
Trying 192.168.1.1...
Connected to 192.168.1.1.
Escape character is '^]'.
``` If you don't, then you're not able to connect to the router at all. If you see that, type the following (**NOTE: there won't be any prompt!**). "<enter>" means to hit enter. Note also that your backspace key doesn't work here; if you make a mistake, you have to start over from scratch. ```
GET / HTTP/1.0<enter><enter>
``` If the first line of the output looks like "HTTP/1.0 401 Unauthorized Access Denied" then your connection is fine and the router is working fine. In that case, the problem is with your browser.

---

### Post by mconway0003 on 2007-02-20
> **mssever said:**
> That's the same router I have, and I can assure you that it's compatible with Linux. What does Linksys tech support know? :) I've confused my share of their techs.

if you type [http://192.168.1.1](http://192.168.1.1) into your browser you should be able to access it. If you can't, double-check your connection to the router. Failing that, restart networking: ```
sudo /etc/init.d/networking restart
```You can also use telnet to troubleshoot your connection by talking directly to the router. Type ```
telnet 192.168.1.1 80
``` You should see something like ```
Trying 192.168.1.1...
Connected to 192.168.1.1.
Escape character is '^]'.
``` If you don't, then you're not able to connect to the router at all. If you see that, type the following (**NOTE: there won't be any prompt!**). "<enter>" means to hit enter. Note also that your backspace key doesn't work here; if you make a mistake, you have to start over from scratch. ```
GET / HTTP/1.0<enter><enter>
``` If the first line of the output looks like "HTTP/1.0 401 Unauthorized Access Denied" then your connection is fine and the router is working fine. In that case, the problem is with your browser.

I tried it with telnet and all I got was this...

telnet 192.168.1.1
Trying 192.168.1.1...
telnet: Unable to connect to remote host: Connection refused

So does this mean that even though I'm hardwired to my Linksys router, my computer thinks that it's directly connected to my cable modem?

---

### Post by MrKlean on 2007-02-20
Are you sure it's not 192.168.2.1   That's the one I use...just a thought ; )

---

### Post by mconway0003 on 2007-02-20
Well 192.168.1.1 is what I used to use for windows when I had the exact same router.

---

### Post by batholith on 2007-02-20
mconway0003,

just out of curiosity  what's the contents of your /etc/resolv.conf ?

---

### Post by mconway0003 on 2007-02-21
> **batholith said:**
> mconway0003,

just out of curiosity  what's the contents of your /etc/resolv.conf ?

batholith,

if i go to the etc folder there is resolv.conf and when I try to go there in the terminal it first denied me then I sudoed it and they say their is still nothing there.  So why would  it even ask me for my password in the first place?


```
marcus@Marcus:~$ /etc/resolv.conf 
bash: /etc/resolv.conf: Permission denied
marcus@Marcus:~$ sudo /etc/resolv.conf 
Password:
sudo: /etc/resolv.conf: command not found
marcus@Marcus:~$ 

```

---

### Post by batholith on 2007-02-21
I'd navigate there through a GUI (e.g. nautilus) and then double-click on the file....it should give you the option to "display".  then you can just cut and paste...

Basically the point I'm trying to get at is that your router address (192.168.1.1 or whatever it is) should be listed.

In my case, I had to make sure my router was listed before I could type the router address into the browser and get to the utility settings...

Another option to try is to go to System->Adminstration->Networking, under the DNS tab "add" your router address...hopefully you can then talk to your router...  

However, depending on how your system is setup, your resolv.conf gets re-written at each re-boot.  So this fix may only be temporary, but it should allow you to do the things you need to do....

---

### Post by mconway0003 on 2007-02-21
> **batholith said:**
> 

Another option to try is to go to System->Adminstration->Networking, under the DNS tab "add" your router address...hopefully you can then talk to your router...


OK, I did this and went to /ect and found a file name resolv.conf; and inside it displayed this...

```
nameserver 167.206.251.13
nameserver 167.206.251.14
nameserver 167.206.251.77
nameserver 192.168.1.1
```

and I noticed that it have the ip address I just added. So to answer you initial question of what is displayed in my resolv.conf file: there it is.

---

### Post by batholith on 2007-02-22
thanks for posting, I certainly don't see anything amiss there... We're getting outside the realm of my knowledge (which unfortunately isn't very hard to do ;)  ).  Are you sure you have the correct address for your router.  My routers address is, 192.168.0.1 ....  I'd try that and see what happens...  Good luck!

---

### Post by Ben Sprinkle on 2007-02-22
[http://192.168.15.1](http://192.168.15.1)
Or
[http://192.168.1.1](http://192.168.1.1)

Hope that helped.

---

### Post by kelbizzle on 2007-02-22
I have the same exact router. I can access the page just fine from ubuntu. I just booted my laptop running Edgy.  It's connected to the router via wifi on a wpa conntection. And it connects to the page fine. I think the issue may be your setup. Or hardware

---

### Post by kelbizzle on 2007-02-22
oh and the resolve.conf doesn't have to have your defualt gateways address as mine does not. I'm having no problem at all. 
```
kel@kelbizzle:~$ sudo cat /etc/resolv.conf 
search hsd1.md.comcast.net.
nameserver 68.87.73.242
nameserver 68.87.71.226

```

---

### Post by houstonbofh on 2007-02-22
Lets shoot some trouble... :)

Start by opening a terminal. (Applications -> Accessories -> Terminal)

Type "if config' and you should get...
```
user@system:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0A:48:07:19:C4  
          inet addr:192.168.64.155  Bcast:192.168.64.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:48ff:fe07:19c4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26812 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21715 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30790775 (29.3 MiB)  TX bytes:2915785 (2.7 MiB)
          Interrupt:209 Base address:0x9000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4456 (4.3 KiB)  TX bytes:4456 (4.3 KiB)

user@system:~$ 

```

This shows that you have an IP address, and both send and see data.

Now type 'route' and...
```
user@system:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.64.0    *               255.255.255.0   U     0      0        0 eth0
default         fw-boat.dnsalia 0.0.0.0         UG    0      0        0 eth0
user@system:~$ 
```
The fw-boat.dnsalia is a truncated fully qualified domain name for my router.  You may just have 192.168.1.1 there.  If not, ping the name.  'ping fw-boat.dnsalias.net' on my system returns "64 bytes from fw-boat.dnsalias.net (192.168.64.1)" so I know my gateway.

This is all just making sure your IP stack is correct.  Now ping the router by IP address.  You will have to hit ctl-c to stop it...
```
user@system:~$ ping 192.168.64.1
PING 192.168.64.1 (192.168.64.1) 56(84) bytes of data.
64 bytes from 192.168.64.1: icmp_seq=1 ttl=64 time=6.31 ms
64 bytes from 192.168.64.1: icmp_seq=2 ttl=64 time=0.317 ms
64 bytes from 192.168.64.1: icmp_seq=3 ttl=64 time=0.308 ms

--- 192.168.64.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 0.308/2.312/6.312/2.828 ms
user@system:~$ 

```
Now lets try wget...

```
user@system:~$ wget http://admin:password@192.168.1.1
--14:40:48--  http://admin:*password*@192.168.1.73/
           => `index.html'
Connecting to 192.168.1.1:80... connected.
HTTP request sent, awaiting response... 200 Ok
Length: unspecified [text/html]

    [ <=>                                 ] 48,603        --.--K/s             

14:40:48 (445.59 KB/s) - `index.html' saved [48603]

user@system:~$ 

```
Let me know if any of those steps break.

---

### Post by WinterWeaver on 2007-02-23
ok.... so I installed the Network Manager... and for some reason... I can now connect to my Router without any of the problems I had earlier.

I don't know if this will solve the original problem fro the author though.

ta

WW

---

