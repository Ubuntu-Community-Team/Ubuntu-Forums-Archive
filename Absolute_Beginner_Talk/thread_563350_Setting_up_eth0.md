---
title: "Setting up eth0"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by godsfshrmn on 2007-09-29
I can't get eth0 to install. I manually entered the information into the config file at /etc/network/interfaces and still no luck. When i try to run ifup eth0, I get:
/etc/network/interfaces:2: misplaced option
ifup: couldn't read interfaces file

I also got an error that the network device was unable to install during a reinstall I just performed. I also see some failures on boot related to networking: ifup not able to read the said file, and configuring network interfaces.

---

### Post by godsfshrmn on 2007-09-29
I managed to get it installed and no error messages now. However, I cannot ping a website nor can I run an apt-get update command because the website cannot be resolved. Where do I need to go from here?

---

### Post by HermanAB on 2007-09-29
'Not resolved' means that the Domain Name System is configured wrong.

In file /etc/resolv.conf you should have something like:
search aeronetworks.ca
nameserver 142.59.19.120
nameserver 142.59.19.115

Those addresses must the DNS addresses of your ISP and the search parameter is optional.

'Hope that helps!

Herman

---

### Post by godsfshrmn on 2007-09-29
I'm using the two IPs for the nameservers which I found on an xp machine when I ran a ipconfig /all in cmd.exe. That is what I need to use right?


EDIT: actually those DNS servers are for opendns.com

EDITx2: I tried the default DNS and still a no go

---

### Post by godsfshrmn on 2007-09-30
Anyone have a clue? ifconfig shows the ethernet configured correctly, i can run a route and it connects to the router (i'm guessing). I tried to ping another computer on the network but that did not work.

---

### Post by Sunforge on 2007-09-30
Can you post the output from the following commands:

ifconfig (your IP address configuration)
route -v (your current routing table)
cat /etc/resolv.conf (print of your DNS resolvers)

It may be that you've typo'd a subnet mask, which can cause all sorts of fun and games or that you have an incorrect gateway, dependent on the number of gateways on your network.

---

### Post by godsfshrmn on 2007-09-30
ifconfig
eth0 showing up, broadcast, multicast, mutu:1500
inet addr:192.168.1.5 bcast: 192.168.1.255, mask:255.255.255.0

and lo is showing up also

route -v
dest: 192.168.1.0; default
gateway: * ; 192.168.1.1
genmask 255.255.255.0; 0.0.0.0
flags: u; ug
iface: eth0;eth0


cat /etc/resolv.conf
nameserver 208.67.222.222
nameserver 208.67.222.202


Thanks

---

### Post by Rui Pais on 2007-09-30
> **godsfshrmn said:**
> I can't get eth0 to install. I manually entered the information into the config file at /etc/network/interfaces and still no luck. When i try to run ifup eth0, I get:
/etc/network/interfaces:2: misplaced option
ifup: couldn't read interfaces file
...

 and cat /etc/network/interfaces too... seems to be bad line on it.

---

### Post by godsfshrmn on 2007-09-30
> **Rui Pais said:**
> and cat /etc/network/interfaces too... seems to be bad line on it.

I think that has been fixed now because that error doesn't show up anymore:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.5
netmask 255.255.255.0
network 192.168.1.1
gateway 192.168.1.1

Something i noticed, when its trying to do a route command, there is nothing at 192.168.1.0, the router is at 192.168.1.1

---

### Post by Rui Pais on 2007-09-30
> **godsfshrmn said:**
> I think that has been fixed now because that error doesn't show up anymore:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.5
netmask 255.255.255.0
network 192.168.1.1
gateway 192.168.1.1

Ok. But that line 'network 192.168.1.1' is weird... i never seen that before. Are you sure that you need that (i tried and seems to be harmless)?

Just 1 more question, whats the output of:
lspci |grep net
?

---

### Post by godsfshrmn on 2007-09-30
I found that on a tutorial somewhere. I removed it and restarted networking and still a no go.

output:

ethernet controller: davicom semiconductor, inc 21x4x DEC-tulip compatible 10/100 ethernet

If i run dmesg | grep eth, I get a huge list of the same thing: tx timeout - resetting

---

### Post by godsfshrmn on 2007-09-30
OK I noticed that I am able to ping myself, but I am not able to ping the gateway. I am able to do this on this machine, which is on the same network. This should be useful

---

### Post by Rui Pais on 2007-09-30
uhmm... sorry i don't know your net card.
maybe doing a google search on it a check if it has any knowing problems on Linux.

About your config, all seems alright.
Don't worry with thew 192.168.1.0 on route output. That's correct.
You are using the OpenDNS IPs for DNS servers, which are safe and known for working good.
All the rest info is ok.

So should be an hardware or a module (driver) problem. 

Just of curiosity, did network worked on livecd, when you installed?

---

### Post by godsfshrmn on 2007-09-30
If I can ping the card itself it should be working correct? I replaced the patch cable with another one and still the same problem: destination host unreachable. It would not automatically configure it during setup, I had to manually.

Under windows the card lists as Cnet Pro2000.

---

### Post by Rui Pais on 2007-09-30
> **godsfshrmn said:**
> OK I noticed that I am able to ping myself, but I am not able to ping the gateway. I am able to do this on this machine, which is on the same network. This should be useful

are you sure that your router has IP 192.168.1.1?

---

### Post by godsfshrmn on 2007-09-30
If its the same as what I enter in my browser to get into its config tool, yes :D

---

### Post by Rui Pais on 2007-09-30
> **godsfshrmn said:**
> If I can ping the card itself it should be working correct? I replaced the patch cable with another one and still the same problem: destination host unreachable. It would not automatically configure it during setup, I had to manually.

Yes, i think so. If net card answer with 0% loss, then should be working. But not sure if there aren't weird issues even with net card apparently working. 
So when you install it worked from liveCD after you manually set it up, but failed when you reboot to the installed system, thats it? or i understand you incorrectly?


> **godsfshrmn said:**
> If its the same as what I enter in my browser to get into its config tool, yes :D

Then it's that, yes.

Are you using Dapper or Feisty?
I found this bug report here:
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg432790.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg432790.html)
[https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/31914](https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/31914)

On another post i found (in Portuguese Brazilian, so i won't put a link) a user of fedora with that netcard said it can only make it work if it blacklist tulip module (instead of default blacklist de4x5 on feisty)... 

Just 2 shoots in the dark,
Good luck.

---

### Post by HermanAB on 2007-09-30
The trick is to debug things using a very simple tool so that you get very specific error messages:
$ sudo -i
password

Ping your own IP address:
# ping 192.168.1.5

Ping your router:
# ping 192.168.1.1

Ping your DNS server:
# ping 208.67.222.222

Test the DNS:
# nslookup [www.yahoo.com](www.yahoo.com)

Connect to Yahoo:
# telnet [www.yahoo.com](www.yahoo.com) 80

At each step of the way above a failure will give precise information on what the matter is.

Cheers,

H.

---

### Post by godsfshrmn on 2007-09-30
Thanks for the replies guys. I was able to ping the ethernet card itself. When I tried the router or NS I got an error saying host unreachable with 100% loss.

Rui, how do I exactly blacklist that module? I tried the blacklist command but says it is not found.
No, during the install, it gave me a red screen saying the network device could not be configured. I had to do it from the command line.

---

### Post by Rui Pais on 2007-09-30
> **godsfshrmn said:**
> Thanks for the replies guys. I was able to ping the ethernet card itself. When I tried the router or NS I got an error saying host unreachable with 100% loss.
Thats the part i find intriguing. Everything seems alright, but you can't ping router... so it seems that net card is not working so well after all (i may be wrong here).
> 
Rui, how do I exactly blacklist that module? I tried the blacklist command but says it is not found.

do:
```
sudo nano /etc/modprobe.d/blacklist
```
search for something like:
```
# replaced by tulip
blacklist de4x5

```and replace by:
```
# replaced by tulip
blacklist tulip
#blacklist de4x5
```
Don't forget to put it back again if that don't solve the problem 
> 
No, during the install, it gave me a red screen saying the network device could not be configured. I had to do it from the command line.
But after you change it from command line it worked?

---

### Post by godsfshrmn on 2007-09-30
My blacklist file doesnt exist. When I try to save it, it tells me no such file exists and won't let me create a new file (or im not doing that part right).

Yeah after the command line it could find eth0 just fine.

---

### Post by Rui Pais on 2007-09-30
> **godsfshrmn said:**
> My blacklist file doesnt exist. When I try to save it, it tells me no such file exists and won't let me create a new file (or im not doing that part right).
sorry godsfshrmn, late here i'm tired...
its ```
sudo nano /etc/modprobe.d/blacklist
```
don't forget the sudo, of course, or it will not allow to save changes.

> Yeah after the command line it could find eth0 just fine.
then it seems that the issue can be solved only by configuration. 
You can try to repeat the process with the  liveCD and check /etc/network/interfaces to see how it looks and use lsmod to check which module it uses (tulip or de4x5)

good luck

---

### Post by godsfshrmn on 2007-09-30
No luck with the blacklist. I inserted a live cd for ubuntu desktop and it configured the network ok, but I was still unable to ping the router or anything outside of it. I'm lost??

---

### Post by Sunforge on 2007-10-01
The only other thing that would occur to me given your description of the problem is a duplicate IP on your network.
 
Is there another machine with the same IP address as you on your local network? That'd give you the symptoms of being able to ping yourself and not being able to ping other machines. 
 
It is a long shot and I'm only suggesting it because you appear to have exhausted other possibilities.

---

### Post by godsfshrmn on 2007-10-01
No I checked that out earlier. This laptop was the only other device on the network and its ip was 192.168.1.2

---

