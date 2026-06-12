---
title: "can't access internet"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by ddg41 on 2007-04-22
Hi, I am sure this comes up abit but I have just formatted one of my pc's and have installed Ubuntu Version 6.06 LTS.
It looks good and everything seems to work but I can not get my email or browser to work.
I can ping I tried pining www,yahoo.com and it worked. everything seems ok but it just times out while trying to access something simple as google.com.au and also when trying to send and receive email.
I would appreciate it if someone could steer me in the right direction as I am very computer literate but only with windows based machines and now want to learn something new which I think is pretty good.
Thanks in advance.
Craig

---

### Post by DSn0wMan on 2007-04-22
It sounds like a DNS issue. Make sure your name servers are set correctly.

---

### Post by medad on 2007-04-22
Are you linked via an ethernet or USB by a router or directly to the dsl/cable modem?  When you were using live were you able to connect?

---

### Post by ddg41 on 2007-04-22
I am not fully conversant with what you are saying that is why Icame to the absolute beginer section. but if you can give me directions on how to check these things I will be able to follow them.
I have two computers linked via a cascadable fast ethernet hub to a DSL-502T Dlink adsl modem. this setup works great when they are both installed with windows. they both are able to access the net. I am not sure what you mean by using live. I brought the devices up and it says protocol = IPv4 IP Address = 10.1.1.3 Netmask/prefix 255.0.0.0  broadcast 10.255.255.255also under that it says IPv6 fe80::214:85ff:fe1b:2acd 64. I don't know if this is helpful or not to you. The conection configuration id set to DHCP.
lets work on the browser first and then if we are successful we can fix the email.
I appreciate the help.

---

### Post by Patrick K on 2007-04-22
I just resolved a connection problem. I've no idea if your's is the same. Take a look here:
[http://ubuntuforums.org/showthread.php?t=417598](http://ubuntuforums.org/showthread.php?t=417598)
I'm going to bed shortly but will check back in the morning. Hopefully, you'll have it resolved by then.

---

### Post by DSn0wMan on 2007-04-22
It is probably your DNS settings. Here is a good guide that includes how to set DNS.

[http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html](http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html)

---

### Post by medad on 2007-04-22
Sorry...

The version of the CD that you used to install Ubuntu Dapper (6.06), was it the "Live" version?  This version allows you to see what the Distro looks like and you can get a chance to see how the programs handle.  You even can get on the internet through FireFox.

Did you get a chance to play with the programs prior to downloading Dapper?  This would just indicate that you were able to have access to the internet prior to the installation.

The only other thing that comes to mind is checking the cables and reconnecting the plugs (I am sure that you already did this).  I would also turn off both the modem and the hub to reset (It is just one thing to say you have done as we try to figure this out).

---

### Post by ddg41 on 2007-04-22
I installed the program straight from the cd.all seems to be working I can ping sites but can not access them with firefox
It says it is conecting to [www.google.com.au](www.google.com.au) but just sits there and eventually times out.I have it on Auto-detect proxy settings for this network.
I am sure it is something I am missing I followed the link to dns settings and all seems ok it just does not seem to find any web address in firefox

---

### Post by Patrick K on 2007-04-22
Did you cehck the Hosts file. It's in the /etc directory.

---

### Post by ddg41 on 2007-04-24
check the hosts file? ok what am I looking for?

---

### Post by ddg41 on 2007-04-24
> **Patrick K said:**
> Did you cehck the Hosts file. It's in the /etc directory.

ok here is what is in the hosts folder.(yes I found it this is fun learning something new).

127.0.0.1 localhost craig-desktop
127.0.1.1 craig-desktop

#the following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I hope this means something to someone and they can tell me where the problem is as I really like this linux operating system and would like to use it fulltime online if I can get it sorted out.

---

### Post by bikeboy on 2007-04-24
That looks normal to me. As others have said, this is probably a Domain Name Server (DNS) issue. The DNS sort of converts a number address (IP) such as 213.15.42.253 into the word address such as [www.example.com](www.example.com).

If DNS isn't working, you can still ping, but not connect to actual websites via their name.

To try and fix the problem there are a few things I can think of.

1. Found out your ISP's DNS server addresses. These may already be listed in your Dlink adsl modem. Open the Ubuntu networking admin tool, System > Admin > Network. Click the DNS tab and enter the address/es your ISP gave you.

2. Try a static IP rather than DHCP, then do as above with the DNS in the network admin tool. Your router might not be giving the DNS servers correctly when using DHCP.

After both of these, post the contents of /etc/resolv.conf
```
cat /etc/resolv.conf
```

---

### Post by ddg41 on 2007-04-24
I have resolved my issues. I just wanted to thank everyone for their kindness and help. I did a search and found a forum where they were disscussing the problem and apparently yes it was DNS related I found this and it fixed it.

I was using the wrong static ip address -- was trying to use 10.1.1.1 -- I changed it to 10.1.1.2. Gateway address is 10.1.1.1. DNS set to 203.8.183.1. When I rebooted settings stayed for the first time and everything seems okay

thank you everyone once again.
I am so happy.

---

### Post by n3tfury on 2007-04-24
i'm not around my ubuntu box or i would check mine for you.  i'm not sure what a default hosts file looks like, but perhaps [[COLOR="SandyBrown"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=3397") will shed some light.

---

### Post by n3tfury on 2007-04-24
> **ddg41 said:**
> I have resolved my issues. I just wanted to thank everyone for their kindness and help. I did a search and found a forum where they were disscussing the problem and apparently yes it was DNS related I found this and it fixed it.

I was using the wrong static ip address -- was trying to use 10.1.1.1 -- I changed it to 10.1.1.2. Gateway address is 10.1.1.1. DNS set to 203.8.183.1. When I rebooted settings stayed for the first time and everything seems okay

thank you everyone once again.
I am so happy.

heh, i suppose i should've clicked on the number 2.  nevermind my last post :D

---

### Post by ddg41 on 2007-04-25
Now that I can access the internet I am trying to learn how to install programs that I download like I just downloaded realplayer 10gold.bin. How do I install it??? thanks

---

### Post by ddg41 on 2007-04-25
ok thats installed. boy things sure are different. now I am trying to work out these comands people talk about doing is that done in terminal or somewhere else? I downloaded ogle-0.9.2.tar.gz and rarlinux-3.6.tar.gz but have absoluterly no idea how to install these I managed to extract them to the desktop but that is as far as I got. now I have a heap of files in each folder but no idea what to do with them.

---

### Post by Parmenion on 2007-04-25
It would be easier to create a new thread to discuss a new topic so that its easier for other users to search.
EDIT: Yeah, its meant to be done in the terminala
Now that thats out of the way,

> sudo apt-get install build-essential
sudo apt-get install checkinstall

build-essential is basically all the packages required to compile anything.
Checkinstall makes it easier to uninstall later.

> tar -xzvf ogle-0.9.2.tar.gz
cd ogle-0.9.2
./configure
make
checkinstall 

Thats basically what you need to do. 
1.tar untars the package
2.cd changes the directory
3../configure ... configures?
3.make compiles the thing
4.checkinstall installs it.

Note: sudo is basically allowing you to temporarily become root for just that command. It makes it safer from a security standpoint and prevents accidents from happening



[Install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually")

---

