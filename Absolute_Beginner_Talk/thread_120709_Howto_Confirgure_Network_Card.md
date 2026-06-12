---
title: "Howto Confirgure Network Card?"
date: 2006-01-23
forum: Absolute Beginner Talk
---

### Post by Kevbb on 2006-01-23
Hi,
I need to ask two seemingly dumb questions:
1.
I need to know where to go to configure my network card properly. (I read in the forums this may be the reason im having the below problems) I can gain internet access and get google site etc up in Firefox (Im sharing internet connection on another computer) but cant run "sudo apt-get update", just errors occur..I can ping my other computer fine, but if i type in ping [www.goole.com](www.goole.com) for instance, it cant find it.
2.
So another question arises, how do I ping the sites in the repository list to see if I can reach them also?

Thanks....Kevbb.

---

### Post by Kevbb on 2006-01-23
Hi Can anyone help me here please.., maybe point me in the right direction to go? Especially where to look to configure the network card, so I can eliminate that at least....Im a bit lost. Cheers...Kevbb.

---

### Post by Leigh on 2006-01-23
Sounds like you might have a DNS problem, i.e. you can PING the IP address, but not the name. have a look at this thread which is a [troubleshooting guide for wired ethernet connections]("http://ubuntuforums.org/showthread.php?t=87643").

Post back here with the latest results.

---

### Post by cayamara on 2006-01-23
[QUOTE=Kevbb]Hi,
I need to ask two seemingly dumb questions:
1.
I need to know where to go to configure my network card properly. (I read in the forums this may be the reason im having the below problems) I can gain internet access and get google site etc up in Firefox (Im sharing internet connection on another computer) but cant run "sudo apt-get update", just errors occur..I can ping my other computer fine, but if i type in ping [www.goole.com](www.goole.com) for instance, it cant find it.
2.
So another question arises, how do I ping the sites in the repository list to see if I can reach them also?

Thanks....Kevbb.[/QUOTE]
Hi!
I assume that you have just one network card and that it is called eth0. Since you share a connection I also assume that you will get a dynamic IP from you router over DHCP. If this is true (it is in most cases), open /etc/network/interfaces:
```
$ sudo gedit /etc/network/interfaces
```
and make sure it contains the line
```
iface eth0 inet dhcp
```
After that, you should be able to bring the interface up by typing
```
$ sudo ifup eth0
```
Check if it went all good by typing
```
$ sudo ifconfig
```
This should print some information abouth eth0.

Hope that works ... ;)

---

### Post by cayamara on 2006-01-23
sorry, double post

---

### Post by _mobius_ on 2006-01-23
You'll need to talk more about your setup.  You may want to try **system > administration > networking ** to configure your card for DHCP or static IP, but it sounds like you already do have an ip.  If you're not running DHCP on your LAN, you can enter a static IP like 192.168.0.x, 255.255.255.0 for netmask, and don't forget to include your gateway and nameservers.  From the sound of your post you don't have these last two.

Good luck.

---

### Post by Kevbb on 2006-01-23
Running a static IP address, going through my XP computers internet connection (broadband) I still have no joy in being able to update anything in my Ubuntu Box. I can surf the internet in my Ubuntu box, but cant ping any domains in the terminal, ip or domain name. Any help on where to go from here is appreciated.
Ta Kevbb

---

### Post by stream303 on 2006-01-24
Hmm.. take a look at your **/etc/resolv.conf**

Although you say you can't domains **or** ip's sooo maybe it's a gateway configuration problem.

Is your gateway address is set up to point to the windows box, or the cable/dsl modem?  I don't run a shared connection myself, but perhaps someone else can point to whether your gateway should be one or the other...

---

### Post by Kevbb on 2006-01-24
Hi...This is what it says in my resolv.conf file:
```

search mshome.net
nameserver 192.168.0.1

```
it is set up to point at the Windows Box through the LAN, and internet sharing using Winproxy.
Hope someone can point me in the right direction.
Thanks heaps

Kevbb.

---

### Post by alamba on 2006-01-24
There's your answer buddy...winproxy. If I understand correctly you are able to open sites but not able to ping them. That's because your gateway (in this case your XP box) is'nt acting like a router and passing traffic, your proxy is, and it's only routing http traffic for you.

Akshay

---

### Post by stream303 on 2006-01-24
> 
search mshome.net
nameserver 192.168.0.1


Aha!  Looks like your setup is picking up an internal nameserver instead of your isp's nameserver(s).  I'm used to seeing this with some soho routers....

If you can obtain the real dns addresses of your isp, let's prevent your /etc/resolv.conf from being overwritten with an invalid nameserver and point it to the right ones.

You'll want to edit **/etc/dhcp3/dhclient.conf**    (sudo gedit /etc/dhcp3/dhclient.conf)

and just before the request line, add this:

**prepend domain-name-servers 123.45.678.90, 123.45.678.91;**
(use your isp's real dns addresses of course)
Just separate multiple addresses with commas, and don't forget the semicolon at the end.

Now instead of rebooting, you can bring the interface down and up again from the terminal:

sudo ifdown eth0
sudo ifup eth0

Let's see if this works for you.

---

### Post by BruschiOnTap on 2006-01-24
Ok, I am  having a weird  problem with my wireless/LAN cards.  I assume I have two separate cards since they are eth0 and eth1  respectively

In the last two weeks my wireless says it is on Network Connection: lo

I  think this is loopback.  Does this mean it's sending and receiving its own signal???  When I go to a hotspot it doesn't detect any other signals and  never gets going.  When I plug in to eth1,  it also won't recognize any networks.  

I did sudo ifup eth0 and got some information:
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:12:3f:f9:0a:cc
Sending on LPF/eth0/00:12:3f:f9:0a:cc
Sending on Socket/fallback

Then it says no DHCPOFFERS received, which I guess means it doesn't sense a network?

This is driving me crazy becuase I am in a foreign  country and having to pay for internet.  Please  help!

---

### Post by BruschiOnTap on 2006-01-24
[QUOTE=stream303]Aha!  Looks like your setup is picking up an internal nameserver instead of your isp's nameserver(s).  I'm used to seeing this with some soho routers....

If you can obtain the real dns addresses of your isp, let's prevent your /etc/resolv.conf from being overwritten with an invalid nameserver and point it to the right ones.

You'll want to edit **/etc/dhcp3/dhclient.conf**    (sudo gedit /etc/dhcp3/dhclient.conf)

and just before the request line, add this:

**prepend domain-name-servers 123.45.678.90, 123.45.678.91;**
(use your isp's real dns addresses of course)
Just separate multiple addresses with commas, and don't forget the semicolon at the end.

Now instead of rebooting, you can bring the interface down and up again from the terminal:

sudo ifdown eth0
sudo ifup eth0

Let's see if this works for you.[/QUOTE]

I used this info to go in and find that my computer is looking for ahvl.nc.charter.com  just like his is looking for msnhome

Soooo... how do I tell it to look for any network???

---

### Post by Kevbb on 2006-01-24
Thanks for all your help people...it turned out to be a mxture of DNS being incorrect and Zone alarm on my other pc not configured properly.

Excelent people....thanks again.

---

