---
title: "resolv.conf keeps resetting itself"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by Doccykins on 2006-07-11
Hi all,

I'm a recent convert to Ububtu and have one of those dodgy routers (Guru GART2-4115/Safecom equivalent) that thinks that IPv4 traffic is IPv6 traffic. I've managed to sort that out through reading previous threads but every time my 'root' logs out (ie I have to re-enter my sudo password to make admin changes) the nameserver in /etc/resolv.conf reverts back to 10.0.0.1 and traffic dies again. Am I doing something wrong/saving in the wrong place?

Cheers for any help

---

### Post by inf0c0m on 2006-07-11
> **Doccykins said:**
> Hi all,

I'm a recent convert to Ububtu and have one of those dodgy routers (Guru GART2-4115/Safecom equivalent) that thinks that IPv4 traffic is IPv6 traffic. I've managed to sort that out through reading previous threads but every time my 'root' logs out (ie I have to re-enter my sudo password to make admin changes) the nameserver in /etc/resolv.conf reverts back to 10.0.0.1 and traffic dies again. Am I doing something wrong/saving in the wrong place?

Cheers for any help

by chance are you using DHCP? this i believe is a common occurance with this

---

### Post by Doccykins on 2006-07-11
yes it is configured using DHCP. I'm trying it out with static now to see if there's any change, but if there's a way around it still using DHCP it would be a great help :)

---

### Post by inf0c0m on 2006-07-11
> **Doccykins said:**
> yes it is configured using DHCP. I'm trying it out with static now to see if there's any change, but if there's a way around it still using DHCP it would be a great help :)

this thread is what fixed it for me

[http://ubuntuforums.org/showthread.php?t=208231&highlight=static+dns+ubuntu+dhcp](http://ubuntuforums.org/showthread.php?t=208231&highlight=static+dns+ubuntu+dhcp)

---

### Post by MaximB on 2006-07-11
no problem ! I had the same thing
it's the dns ip you concernd about I think.
just type it in (networking) use dhcp - then make the resolv file "read-only"
and continue using dhcp - like I am
problem solved !

---

### Post by Doccykins on 2006-07-11
This appears to have cured it :D Thanks a lot guys

---

### Post by Doccykins on 2006-07-11
> **Doccykins said:**
> This appears to have cured it :D Thanks a lot guys

bah, spoke too soon... Even when chmod -wx it restored to 10.0.0.1 when I restarted :( Switching back to static IP for now

---

### Post by MaximB on 2006-07-11
could not be.
did you make the resolv.conf file **"read only"** after you setup the DNS ip address ???
what happened ?

---

### Post by Doccykins on 2006-07-11
> **MAXDDARK said:**
> could not be.
did you make the resolv.conf file **"read only"** after you setup the DNS ip address ???
what happened ?

the steps that I took were

>set ip address to static, IP 10.0.0.2, Subnet 255.0.0.0, Gateway 10.0.0.1
everything works fine here
>sudo chmod 777 /etc/resolv.conf
>sudo gedit /etc/resolv.conf
>change resolv.conf from 10.0.0.1 to 212.159.6.9
>save resolv.conf
>sudo chmod 444 /etc/resolv.conf
>add dns 212.159.6.9 to eth0
>change eth0 to DHCP

everything works fine until restart, when resolv.conf is still chmod 444 and has returned to 10.0.0.1. Is it me mistaking read only? Is there another way to make files read only in ubunto?

Thanks :)

---

### Post by MaximB on 2006-07-11
right click on the file - properties - premissions
then unchek the "write" and the "execute" premissions from EVERYONE
including the "owner" (yourself).
only leave the READ premission.

try that AFTER you change that file.
goodluck !

---

### Post by yuv on 2006-07-11
I had a similar problem for a static IP and I did:
# gksudo gedit /etc/network/interfaces
and added in eth0 section:
"dns-nameservers x.y.z.1 x.y.z.2"
(put real dns instead of xyz..)

---

### Post by Doccykins on 2006-07-12
Tried all of the above this morning and even though I can't edit the read only files from the terminal something is still overriding it and editing the nameserver to 10.0.0.1. Typically I'd set to read/write/execute all, edit the file to my dns, save the file, set permissions to read only and save (for both /etc/resolv.conf and /etc/resolv.conf~) Once I restart doing a less /etc/resolv.conf shows 'nameserver 10.0.0.1' even though the permissions are still read only. Adding the dns-nameservers to the /etc/network/interfaces does nothing (but when I set the devices to static IP they work ok and the nameserver doesnt change on restart)

---

### Post by MaximB on 2006-07-12
very strange...overwrites in read-only...somthing is wrong.

---

### Post by MrHorus on 2006-07-12
My concearn would be why you are getting that from your DHCP server.

Is it a home network or is it an ISP's DHCP server?

---

### Post by MaximB on 2006-07-12
well...I tell you excactly what I did - do the same :
1.enter "networking" (system>administrator>networking)
2.in the properties of your ethernet card set DHCP in the configuration
and enable this connection and click "ok"
3.go to the "DNS" tab and add your ISP DNS , DON'T FORGET to remove other DNS's as well. click ok to close this window
4.go FAST (before it changes again) to the resolv.conf file (the original not the backups) right click on it and make it "read-only" for everyone.

that's what I did - and it worked for me
try it again as I explained.

---

### Post by Doccykins on 2006-07-13
I think I've finally got this nailed by adding the ISP's DNS to the Search server as well as the name server. Even though nameserver reverts back to 10.0.0.1 I can still download updates/surf the net etc. Thanks a lot for your help guys :)

---

### Post by MaximB on 2006-07-13
no problem...an hour ago some great guy spent 4-5 hours to help me...and finally he did it
so I feel obligated to help other ppl if I know how.

just tell me 2 thing.
1.did I manage to help you somehow ?
2.why do you want dhcp and not a static IP ?

---

### Post by JamesB on 2006-07-13
> **Doccykins said:**
> Hi all,

I'm a recent convert to Ububtu and have one of those dodgy routers (Guru GART2-4115/Safecom equivalent) that thinks that IPv4 traffic is IPv6 traffic. I've managed to sort that out through reading previous threads but every time my 'root' logs out (ie I have to re-enter my sudo password to make admin changes) the nameserver in /etc/resolv.conf reverts back to 10.0.0.1 and traffic dies again. Am I doing something wrong/saving in the wrong place?

Cheers for any help

Hi
This is a common problem and the only way I've found that works so far is:

As a temp solution a edited /etc/dhcp3/dhclient.conf
prepend domain-name-servers <IP-FOR-YOUR-DNS-SERVER> (removing the #) and deleting 'domain-name-servers' from the request line 

Mine looks like this:

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
prepend domain-name-servers 212.74.112.66, 212.74.112.67;
request subnet-mask, broadcast-address, time-offset, routers,
domain-name, host-name,
netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;

Hope this helps

James

---

### Post by archon256 on 2008-02-01
I realised that my router was resetting the DNS to the wrong 192.168.1.1 every 10 seconds and even if I wrote via Network Settings (KDE) or directly into resolv.conf to use an alternative good one (194.72.6.51) after 10 seconds it got overwritten again to the 192.168.1.1  I was getting desperate and furious. Windows machines kept the alternate DNS in IP configuration without problems. 
Then I found out (through a OpenSuse Live CD and YAST configuration) that to turn off the setting DNS via DHCP I had to change the resolv.conf instead of 

search -name-
nameserver 192.168.1.1

to 

domain site 
nameserver 192.168.1.1
nameserver 194.72.6.51

That helped, since then the DNS stays as it should and my internet is working 100%

---

