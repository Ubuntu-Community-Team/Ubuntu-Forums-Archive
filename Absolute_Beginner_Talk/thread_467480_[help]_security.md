---
title: "[help] security"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by pcandpc on 2007-06-07
Hi,

I'm using ce 3.2 (christian edition 3.2).

How do I enable security features such as
firewall and antivirus in this edition?

Thanks.

---

### Post by Nekiruhs on 2007-06-07
1. You don't really need antivirus, there are no real viruses out there for linux (only some proof of concept ones, but you needn't worry)
2.Firewall is already enabled by default.

---

### Post by ramjet_1953 on 2007-06-08
The only time that you may need an anti-virus scanner is if you are forwarding-on emails to Windows users that have attachmenets that have embedded executable files.

However, in most cases this isn't even required, as most email providers scan emails, before forwarding anyway.

As was previously stated, you have a very secure firewall, by default with iptables and I suggest you leave it well alone, unless you really know what your are doing.

Loosen-up and enjoy, you are running Linux now, not Windows. You no longer need paranoia!

Regards,
Roger :cool:

---

### Post by Wim Sturkenboom on 2007-06-08
To check if a the firewall is configured, you can run the following command in a terminal:
```

root@btd-techweb01:~# **sudo iptables -L -n**
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
root@btd-techweb01:~#
```
If you get above output, the firewall is [COLOR="Red"]**NOT**[/COLOR] configured.

---

### Post by RomeReactor on 2007-06-08
Hi. As has been said before, you don't need an antivirus program on Linux unless you forward mail with attachments or transfer files to windows boxes. Also, the included firewall (iptables)  is good enough if you don't need to forward ports. If you *do* need to, then install Firestarter, which is a very easy to use graphical interface to iptables. Look for Firestarter in Synaptic, or from the terminal:
```
sudo apt-get install firestarter
```

---

### Post by pcandpc on 2007-06-08
Thanks.

I've installed the firestarter.

 Now then, how do I start it during boot automatically?

I've looked carefully into its preferences settings but
couldn't find anything related to autostarting during boot.

---

### Post by RomeReactor on 2007-06-08
> **pcandpc said:**
> Thanks.

I've installed the firestarter.

 Now then, how do I start it during boot automatically?

I've looked carefully into its preferences settings but
couldn't find anything related to autostarting during boot.

You can add it to the startup programs: Go to "System-->Preferences-->Sessions", and on the first tab (Startup Programs) click "New"; Then fill out the fields: **Name: Firestarter** and **Command: firestarter**. If Firestarter does not start after booting into Ubuntu, then try changing the **Command: firestarter** entry to **Command: sudo firestarter**. However, note that it really isn't necessary to have Firestarter start at boot, since Firestarter **is not** the firewall, only the graphical interface. **iptables** is the firewall and is always on.

---

### Post by Wim Sturkenboom on 2007-06-08
> **RomeReactor said:**
> **iptables** is the firewall and is always on.It might be always on, but it's [COLOR="Red"]**NOT**[/COLOR] always configured; see my post above.

---

### Post by RomeReactor on 2007-06-08
> **Wim Sturkenboom said:**
> It might be always on, but it's [COLOR="Red"]**NOT**[/COLOR] always configured; see my post above.

True; however, my comment was in the context of having Firestarter run at boot, so I showed him the difference between the actual firewall (iptables) and the gui (Firestarter), and that there was no need to do that. One only runs Firestarter to make changes to iptables' configuration, and it can then be closed; iptables starts with the system, and it will still be running after closing Firestarter (the graphical interface). All this is as far as I know; I could be wrong, though. ;)

---

### Post by pcandpc on 2007-06-08
Hi,

Thanks for your comments.

Basically, I have eth0, eth1, and eth2 on my
system and only eth1 is connected to the internet
via a router.

I may be using just eth1 now but I could also
use the others in future as the need arises.  

So, what I'd like to do is to ensure that all ports
are protected by firewall.

In another distro, I was able to enable firewall
for all three ports; I believe it was shorewall or
something like that via gui.

Anyway, it's kind of a long listing for iptables -L -n
below, but I want to know if the firewall/iptables is
protecting all ports; if not, can you tell me how I can
enable the firewall for all ports as in shorewall?

Thanks.

ubuntuce@ubuntuce:~$ sudo iptables -L -n
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           
in_world   0    --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           state RELATED 
LOG        0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 5 LOG flags 0 level 4 prefix `IN-unknown:' 
DROP       0    --  0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           state RELATED 
LOG        0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 5 LOG flags 0 level 4 prefix `PASS-unknown:' 
DROP       0    --  0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
DROP       tcp  --  0.0.0.0/0            127.0.0.1           tcp dpt:3128 ! OWNER UID match 111 
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           
out_world  0    --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           state RELATED 
LOG        0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 5 LOG flags 0 level 4 prefix `OUT-unknown:' 
DROP       0    --  0.0.0.0/0            0.0.0.0/0           

Chain in_world (1 references)
target     prot opt source               destination         
DROP       0    --  0.0.0.0/0            0.0.0.0/0           state INVALID 
pr_world_fragments  0    -f  0.0.0.0/0            0.0.0.0/0           
pr_world_nosyn  tcp  --  0.0.0.0/0            0.0.0.0/0           state NEW tcp flags:!0x17/0x02 
pr_world_icmpflood  icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8 
pr_world_synflood  tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 
pr_world_malxmas  tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x3F 
pr_world_malnull  tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x00 
pr_world_malbad  tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x03/0x03 
pr_world_malbad  tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x06/0x06 
pr_world_malbad  tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x37 
pr_world_malbad  tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x3F/0x29 
in_world_all_c1  0    --  0.0.0.0/0            0.0.0.0/0           
in_world_irc_c2  0    --  0.0.0.0/0            0.0.0.0/0           
in_world_ftp_c3  0    --  0.0.0.0/0            0.0.0.0/0           
in_world_cups_s4  0    --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           state RELATED 
LOG        0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 5 LOG flags 0 level 4 prefix `IN-world:' 
DROP       0    --  0.0.0.0/0            0.0.0.0/0           

Chain in_world_all_c1 (1 references)
target     prot opt source               destination         
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           state ESTABLISHED 

Chain in_world_cups_s4 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:65535 dpt:631 state NEW,ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:631 dpt:631 state NEW,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spts:1024:65535 dpt:631 state NEW,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spt:631 dpt:631 state NEW,ESTABLISHED 

Chain in_world_ftp_c3 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:21 dpts:32768:61000 state ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:20 dpts:32768:61000 state RELATED,ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:1024:65535 dpts:32768:61000 state ESTABLISHED 

Chain in_world_irc_c2 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:6667 dpts:32768:61000 state ESTABLISHED 

Chain out_world (1 references)
target     prot opt source               destination         
out_world_all_c1  0    --  0.0.0.0/0            0.0.0.0/0           
out_world_irc_c2  0    --  0.0.0.0/0            0.0.0.0/0           
out_world_ftp_c3  0    --  0.0.0.0/0            0.0.0.0/0           
out_world_cups_s4  0    --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           state RELATED 
LOG        0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 5 LOG flags 0 level 4 prefix `OUT-world:' 
DROP       0    --  0.0.0.0/0            0.0.0.0/0           

Chain out_world_all_c1 (1 references)
target     prot opt source               destination         
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           state NEW,ESTABLISHED 

Chain out_world_cups_s4 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:631 dpts:1024:65535 state ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spt:631 dpt:631 state ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spt:631 dpts:1024:65535 state ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp spt:631 dpt:631 state ESTABLISHED 

Chain out_world_ftp_c3 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:32768:61000 dpt:21 state NEW,ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:32768:61000 dpt:20 state ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:32768:61000 dpts:1024:65535 state RELATED,ESTABLISHED 

Chain out_world_irc_c2 (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp spts:32768:61000 dpt:6667 state NEW,ESTABLISHED 

Chain pr_world_fragments (1 references)
target     prot opt source               destination         
LOG        0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 5 LOG flags 0 level 4 prefix `PACKET FRAGMENTS:' 
DROP       0    --  0.0.0.0/0            0.0.0.0/0           

Chain pr_world_icmpflood (1 references)
target     prot opt source               destination         
RETURN     0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 100/sec burst 50 
LOG        0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 5 LOG flags 0 level 4 prefix `ICMP FLOOD:' 
DROP       0    --  0.0.0.0/0            0.0.0.0/0           

Chain pr_world_malbad (4 references)
target     prot opt source               destination         
LOG        0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 5 LOG flags 0 level 4 prefix `MALFORMED BAD:' 
DROP       0    --  0.0.0.0/0            0.0.0.0/0           

Chain pr_world_malnull (1 references)
target     prot opt source               destination         
LOG        0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 5 LOG flags 0 level 4 prefix `MALFORMED NULL:' 
DROP       0    --  0.0.0.0/0            0.0.0.0/0           

Chain pr_world_malxmas (1 references)
target     prot opt source               destination         
LOG        0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 5 LOG flags 0 level 4 prefix `MALFORMED XMAS:' 
DROP       0    --  0.0.0.0/0            0.0.0.0/0           

Chain pr_world_nosyn (1 references)
target     prot opt source               destination         
LOG        0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 5 LOG flags 0 level 4 prefix `NEW TCP w/o SYN:' 
DROP       0    --  0.0.0.0/0            0.0.0.0/0           

Chain pr_world_synflood (1 references)
target     prot opt source               destination         
RETURN     0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 100/sec burst 50 
LOG        0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 1/sec burst 5 LOG flags 0 level 4 prefix `SYN FLOOD:' 
DROP       0    --  0.0.0.0/0            0.0.0.0/0           
ubuntuce@ubuntuce:~$

---

### Post by ubz on 2007-06-08
> **Wim Sturkenboom said:**
> To check if a the firewall is configured, you can run the following command in a terminal:
```

root@btd-techweb01:~# **sudo iptables -L -n**
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
root@btd-techweb01:~#
```
If you get above output, the firewall is [COLOR="Red"]**NOT**[/COLOR] configured.

I used the sudo iptables -L -n command  and the output was identical to that above.  So now what?
It's 'NOT CONFIGURED'.  What does that mean?  Is IPTABLES operating as it should given my default ubuntu installation?

---

### Post by kittyhawk63 on 2007-06-08
> **ubz said:**
> I used the sudo iptables -L -n command  and the output was identical to that above.  So now what?
It's 'NOT CONFIGURED'.  What does that mean?  Is IPTABLES operating as it should given my default ubuntu installation?

System->Administration->Synaptic Package Manager->
Now install firestarter.
Once installed you will find firestarter in System->Administration->Firestarter.
Start it and go through the wizard. Take your time. It works and firestarter will then be started.

Now go to System->Preferences->Sessions
Click on NEW and add Firestarter. Edit it and place in the first box **firestarter** and in the second box **sudo firestarter**. Save. Your fixed.  Log out and back in. Firestarter will be working in the background. Now run the command **sudo iptables -L -n** and you should see a post out similar to the one above.

---

### Post by trak87 on 2007-06-08
> **RomeReactor said:**
> True; however, my comment was in the context of having Firestarter run at boot, so I showed him the difference between the actual firewall (iptables) and the gui (Firestarter), and that there was no need to do that. One only runs Firestarter to make changes to iptables' configuration, and it can then be closed; iptables starts with the system, and it will still be running after closing Firestarter (the graphical interface). All this is as far as I know; I could be wrong, though. ;)

I'm no expert, but think you are wrong. Iptables may come installed with the system, but by default it's not configured to filter anything. Look at the default values by running "sudo iptables -L -n". They're set to ACCEPT everything:

```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```

9 out of 10 comments about a firewall is: "Don't worry, you're already protected." Please show me I'm wrong.

---

### Post by kittyhawk63 on 2007-06-08
It was not configured for me. In previous post, I gave what I did to get to the place where I could configure it. Now it is configured.

---

### Post by trak87 on 2007-06-08
> **pcandpc said:**
> Anyway, it's kind of a long listing for iptables -L -n
below, but I want to know if the firewall/iptables is
protecting all ports;

It doesn't look like it is set up correctly. You have to run through the firestarter wizard once to set it up properly.

In Firestarter, selcect: "Firewall"

"Run Wizard"

Most folks will select "IP address is assigned via DHCP" because your ISP or router is assigning your IP address.

Only select "Enable Internet connection sharing" if your box is acting as a router for other boxes on your home network.

"Start firewall now"

"Save"

Now run "sudo iptables -L -n" and you should NOT see things like "in-unknown", "out-unknown", "malformed this" and "malformed that".

---

### Post by DBStevens on 2007-06-08
trak87,

I'd put it this way iptables is indeed running and it is actually configured, it is configured to allow normal non filtered traffic.

In other words it doesn't even filter martains or any other nasties in that mode.

---

### Post by kittyhawk63 on 2007-06-08
TRAK87,
Thanks for your additional input.
kh

---

### Post by RomeReactor on 2007-06-08
**pcandpc**: By default, iptables does not listen to any inbound traffic, meaning it does not open ports automatically without being told to (by issuing commands to it from the command line or by using a graphical interface). If you want a bit more info about which ports are open on your PC at any given time, run this command from the terminal:
```
netstat -t -u
```
Netstat is a tool that informs you of network connections (type **man netstat** in the terminal for a very comprehensive--though complex--list of options and parameters for that command). You can also install [Nmap]("http://insecure.org/"), which is a "Network exploration tool and security / port scanner":
```
sudo apt-get install nmap
```
To scan all of your PC's ports using Nmap:
```
sudo nmap -v -p- **YOUR_IP_HERE**
```
To get more information about Nmap, try **man nmap** from the terminal. Sorry I can't be more specific about all this, but I know little else apart from what is posted here, though these tools have been very useful for me.

---

### Post by trak87 on 2007-06-08
> **DBStevens said:**
> trak87,

I'd put it this way iptables is indeed running and it is actually configured, it is configured to allow normal non filtered traffic.

In other words it doesn't even filter martains or any other nasties in that mode.

That's double talk. People install a firewall for protection and by default it doesn't protect anything. Show me that I'm wrong.

---

### Post by RomeReactor on 2007-06-08
> **trak87 said:**
> I'm no expert, but think you are wrong. Iptables may come installed with the system, but by default it's not configured to filter anything. Look at the default values by running "sudo iptables -L -n". They're set to ACCEPT everything:

> **DBStevens said:**
> trak87,

I'd put it this way iptables is indeed running and it is actually configured, it is configured to allow normal non filtered traffic.

In other words it doesn't even filter martains or any other nasties in that mode.

I might be wrong, of course, but I think that while outbound connections are permissive by default, inbound connections must be ruled in (using iptables or any of its frontends such as Firestarter). Anyone here not using Firestarter or any other GUI for iptables can run Nmap to see if there are any open ports in a default Ubuntu installation. I've not done that, since I always install Firestarter right after a fresh install, so I'm not sure if what I claim is true; I'd be interested in knowing if that's the case. ;)

---

### Post by DBStevens on 2007-06-08
trak87,

I told you precisely what the case is, if you need to be told that someone should dictate the rules for a firewall then fine tell me who should dictate the rules the system owner or someone else. 

When you take it upon yourself to install something that can be configured I'd suggest that you should learn to how it operates and how to configure it otherwise you are at the mercy of someone who just might not have your best interests in mind.

I see way too much of the point and click mentality and making assumptions without first even understanding what one is installing.

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-06-08 21:13 EDT
Interesting ports on localhost (127.0.0.1):
Not shown: 1696 closed ports
PORT    STATE SERVICE
631/tcp open  ipp

Nmap finished: 1 IP address (1 host up) scanned in 0.146 seconds

That is a current scan of my system and my IPTABLES configuration is:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Now all that means is that port 631 is open (CUPS server port is running) you can try all you want to SSH or TELNET locally and get nowhere since those ports are not active.  Further if I gave you my IP address or my domain name you couldn't get port 631 to be visible even though it is runing.

Remember if you make assumptions do so in a manner that doesn't allow for bad things (tm) to occur.

Sort of like opps I didn't know it was loaded.

---

### Post by trak87 on 2007-06-08
I just ran nmap on all ports on a local machine with the iptables set to the default ACCEPT. It didn't find anything open. I'm still skeptical that a firewall is not needed though.

---

### Post by DBStevens on 2007-06-08
If there are no ports open it isn't need since there are no commuinication paths availible.

The fact there are no deny, drop, tarpit or other rules inforce doesn't mean it isn't installed, running, or configured.

That is one of the faults with defaults and with configurations, a system given an empty configurtaion file by a user frequently writes it's defualt configuration to a brand new configuration file.  Funny how that works.

BTW as an aside I have a more than a few rules in IPTABLES firewalls on several servers.  I have used KISS for several years and it has served my purposes well.

The reason that from the outside that open port 631 will not respond is because my router will not forward port 631 trafic.

What one should do is block all ports that would cause disruption to a system from outside network addresses provided the port is open.  

Those ports should only be open to private network ip address.
 
Most home users that install Ubuntu if they don't install  the various services like a webserver, mysql, ssh  server, etc. are normally quite well locked down out of the box.  Installing every pakage availible would of course open one's system up to all kinds of potential avenues of "attack".

Another reason to be aware of what you are installing and its implications.

---

### Post by trak87 on 2007-06-08
> **DBStevens said:**
> I told you precisely what the case is, if you need to be told that someone should dictate the rules for a firewall then fine tell me who should dictate the rules the system owner or someone else. 

When you take it upon yourself to install something that can be configured I'd suggest that you should learn to how it operates and how to configure it otherwise you are at the mercy of someone who just might not have your best interests in mind.

I see way too much of the point and click mentality and making assumptions without first even understanding what one is installing.

I understand and agree with your points. I may be freaking out a bit unnecessarily here, but my concern is that just installing apache will open port 80 to the outside, and if a user doesn't know there's an open port and they don't have a router acting as a firewall, I think that without something like firestarter (iptables) they've made their system more vulnerable to attack. Am I wrong about this? because I admit I'm no networking expert.

---

### Post by DBStevens on 2007-06-08
If you install apache you do so for a reason don't you and that reason is to host a website normally.

That usually means outside access via port 80 which is exactly what apache uses (well normally anyway).

That in turn means you need to know how that server functions and how to secure that facility.



Hint: If you do it correctly the server operates as a separate user and can only destroy what that user has permission for or can likewise access.

Edited to add the hint.

---

### Post by trak87 on 2007-06-08
I install Apache for in**TRA**net purposes. It's also great as a glorified bookmark system. So I don't need port 80 opened automatically just by installing it. I guess I would prefer a firewall as the final arbiter for what gets in and out rather than relying on a bunch of different programs and how securely they are written.

---

### Post by ramjet_1953 on 2007-06-08
Why do you want to have Firestarter running all of the time?

it is merely a configuration tool for iptables.

It is also a serious security risk to have it running all of the time, as it requires root privileges to run.

Hence, to have it running full-time, you are shooting yourself in the foot, as you are opening-up your system, by running this application in root mode.

As I said in my previous post, loosen-up and leave the paranioa behind.

Regards,
Roger :cool:

---

### Post by trak87 on 2007-06-08
> **ramjet_1953 said:**
> Why do you want to have Firestarter running all of the time?

I don't run it at all except to set it up during installation. But I think you are referring to somebody else. The purpose of firestarter for me is to load iptables on bootup. I hardly run the gui.

---

### Post by DBStevens on 2007-06-08
Then a nice simple rule in your apache system can be used in place of a firewall. 

There is more than one place and one way to fence off your system or part of it.   

However don't expect anyone from the outside providing you with a single covers all set of rules.

In the case of port 80 it is even possible that your ISP has that blocked.   Apache need at least one port open to run and the last time I installed Apache on Unbuntu it fired up on port 80.  

You also have to understand that I just switched to Unbuntu and it does a few things a bit differently than any of the other Distros I've used.  I have to double check everything I do just to make certain I have the bases covered.   I haven't gotten to the point of reloading my web site test environment yet. Just checked out that the server works.

---

### Post by DBStevens on 2007-06-08
pcandpc,

Could you explain to me what you mean when you ask if all of your ports are protected?

Exactly what do you wish to be protected from?

It may not be in any realm that a firewall would provide any protection from.

---

### Post by pcandpc on 2007-06-09
Hi,

Creating a new firestarter session in system > preferences > session
doesn't appear to run the service automatically upon system reboots
as a regular user.  

So, how do I automatically start this firestarter on system starts 
for a regular user?

By the way, I installed shorewall via adept-manager.  Now, what
do I do to run it, again automatically on system starts for a regular user?

Thanks.

---

### Post by trak87 on 2007-06-09
See message #9 here:

[http://ubuntuforums.org/showthread.php?t=457655](http://ubuntuforums.org/showthread.php?t=457655)

---

### Post by pcandpc on 2007-06-09
Hi,

Thanks.  I'll keep that in mind.

By the way, looking at system > preferences > 
session > current session, I see sudo firestarter
in settings style with ? state.

Does this mean firestarter is running at backgroud?

If so, still, I don't see firestarter running notification 
on the system tray.

---

### Post by trak87 on 2007-06-09
> Does this mean firestarter is running at backgroud?

Sorry, I mainly use the GUI part of firestarter to initially set up the firewall, and iptables is the real firewall, not firestarter per se. Firestarter is jut a gui that is used to control iptables and I only use that portion of the program occasionally. If you've gone through the firestarter wizard and you then run "sudo iptables -L -n" then on the command line you should see about 79 lines of text. That means iptables (the real firewall) is running in the background and you should be firewalled every time you boot up. Additionally, I mentioned a fix for firestarter in a link above. This ensures firestarter (the portion that loads the iptables rules, not the GUI) starts at boot because there is a bug that prevents this sometimes. And as others have suggested, I don't think the GUI portion of firestarter needs to be running at all times, as long as firestarter successfully loads iptables on boot up.

There's been some confusion about this and I hope this clears it up.

---

### Post by djchandler on 2007-06-09
> **trak87 said:**
> Sorry, I mainly use the GUI part of firestarter to initially set up the firewall, and iptables is the real firewall, not firestarter per se. Firestarter is jut a gui that is used to control iptables and I only use that portion of the program occasionally. If you've gone through the firestarter wizard and you then run "sudo iptables -L -n" then on the command line you should see about 79 lines of text. That means iptables (the real firewall) is running in the background and you should be firewalled every time you boot up. Additionally, I mentioned a fix for firestarter in a link above. This ensures firestarter (the portion that loads the iptables rules, not the GUI) starts at boot because there is a bug that prevents this sometimes. And as others have suggested, I don't think the GUI portion of firestarter needs to be running at all times, as long as firestarter successfully loads iptables on boot up.

There's been some confusion about this and I hope this clears it up.

If you're worried about security, you can go to Shields Up at 
**[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)**
and they will scan your ports for a vulnerability. If you start playing around with Firestarter, you could block some things you may not want blocked. I wouldn't fool around with it unless you have some reason to believe you've been hacked or you are particularly vulnerable. Get your ports scanned and then you will know.

---

### Post by trak87 on 2007-06-10
> **djchandler said:**
> If you start playing around with Firestarter, you could block some things you may not want blocked.

Blocking is the nature of a firewall and firestarter gives you the ability to open the ports of your choosing.

---

### Post by baracuda68 on 2007-06-10
OK...
I installed GuardDog... couldnt get it to work.
Uninstalled GuardDog. Installed Shorewall.
Installed Firestarter. Configured with the wizard.
As long as I have iptables and Firestarter, do I really need Shorewall installed?:p

---

### Post by pcandpc on 2007-06-10
Hi,

Consulting with the firestarter's online manual,
the firestarter will automatically start irregardless
of gui or system restarts if it's installed via rpm or
dep package.

Well, I have installed the firestarter via adept and
I believe the package form was either rpm or dep.

Besides, I see numerous references to the firestarter
in various rc folders in /etc.

So then, how do I visually check that it's running properly
besides looking at some large listings of iptables -L -n?

Thanks.

---

### Post by trak87 on 2007-06-10
> **pcandpc said:**
> So then, how do I visually check that it's running properly
besides looking at some large listings of iptables -L -n?

Firestarter is one of the more difficult to understand how it works programs. Assuming one went through the FS setup wizard, when you boot up, all the firstarter scripts in /etc/rc?.d/ do is run the iptables script at /etc/firestarter/firestarter.sh. This script gives iptables all the information it needs to maintain the firewall.

The GUI program in the menu system isn't running at all when the script is running and it doesn't need to. But when you do run the GUI to make modifications to the firewall, it simply writes a new /etc/firestarter/firestarter.sh script and executes that, thus updating iptables. The GUI is basically just a configuration tool for iptables. However, it does watch the logs in real time for potential hits on system ports. But other than that it's just a configuration tool and for the most part doesn't need to run constantly.

So when you ask how do you know if it's running properly? Run "sudo iptables -L -n" to see if iptables has definitions that turn on it's capabilities. You don't really need to know if the GUI is working, because if you can run it and see it, it's working!

---

### Post by pcandpc on 2007-06-11
Thanks.

---

### Post by Kiwilad on 2007-06-13
> **djchandler said:**
> If you're worried about security, you can go to Shields Up at 
**[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)**
and they will scan your ports for a vulnerability. If you start playing around with Firestarter, you could block some things you may not want blocked. I wouldn't fool around with it unless you have some reason to believe you've been hacked or you are particularly vulnerable. Get your ports scanned and then you will know.

I tried this and got the following message when I scanned Common Ports:
Ping Reply: RECEIVED (FAILED) — Your system REPLIED to our Ping (ICMP Echo) requests, making it visible on the Internet. Most personal firewalls can be configured to block, drop, and ignore such ping requests in order to better hide systems from hackers. This is highly recommended since "Ping" is among the oldest and most common methods used to locate systems prior to further exploitation.

I've been into the Firestarter GUI preferences and ticked the "Enable ICMP filtering" box. At the moment, everything except "Unreachable" is unticked meaning it should be filtered...doesn't it?? It doesn't make any difference to the above report whether I tick or untick the "Echo request (ping)" and "Echo reply (pong)" boxes.

Any ideas? 

Thanks

Stu

---

### Post by fromgi on 2007-06-13
In Firestarter's preferences, click only "Enable ICMP filtering".  Don't have anything else on this page selected (don't allow anything).   This worked for me.  Hope this helps.

---

### Post by djchandler on 2007-06-13
> **fromgi said:**
> In Firestarter's preferences, click only "Enable ICMP filtering".  Don't have anything else on this page selected (don't allow anything).   This worked for me.  Hope this helps.

What fromgi says is correct. Keep it simple to keep it safe. Then check with Shields Up again.

If you keep having trouble, capture the screens in Firestarter as you have them set up and let us see them.

---

### Post by Kiwilad on 2007-06-14
> **djchandler said:**
> What fromgi says is correct. Keep it simple to keep it safe. Then check with Shields Up again.

If you keep having trouble, capture the screens in Firestarter as you have them set up and let us see them.

tried that and I still fail the last test on common ports... how do I "capture the screens"

---

### Post by trak87 on 2007-06-14
> tried that and I still fail the last test on common ports... how do I "capture the screens"

Have you checked to see if iptables is running properly? What's the output from "sudo iptables -L -n"  ??

There is a bug related to NetworkManager that can cause Firestarter not to run properly at boot up. Have you implemented the fix for this here as described in message #9? :

[http://ubuntuforums.org/showthread.php?t=457655&highlight=50firestarter](http://ubuntuforums.org/showthread.php?t=457655&highlight=50firestarter)

---

### Post by Kiwilad on 2007-06-15
[QUOTE=trak87;2842729]Have you checked to see if iptables is running properly? What's the output from "sudo iptables -L -n"  ??

OK, this is my output..

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.2          0.0.0.0/0           tcp flags:!0x17/0x02 
ACCEPT     udp  --  192.168.1.2          0.0.0.0/0           
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           
LSI        udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:33434 
LSI        icmp --  0.0.0.0/0            0.0.0.0/0           
DROP       0    --  0.0.0.0/0            255.255.255.255     
DROP       0    --  0.0.0.0/0            192.168.1.255       
DROP       0    --  224.0.0.0/8          0.0.0.0/0           
DROP       0    --  0.0.0.0/0            224.0.0.0/8         
DROP       0    --  255.255.255.255      0.0.0.0/0           
DROP       0    --  0.0.0.0/0            0.0.0.0             
DROP       0    --  0.0.0.0/0            0.0.0.0/0           state INVALID 
LSI        0    -f  0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
INBOUND    0    --  0.0.0.0/0            0.0.0.0/0           
LOG_FILTER  0    --  0.0.0.0/0            0.0.0.0/0           
LOG        0    --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
LSI        udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:33434 
LSI        icmp --  0.0.0.0/0            0.0.0.0/0           
LOG_FILTER  0    --  0.0.0.0/0            0.0.0.0/0           
LOG        0    --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.4          192.168.1.2         tcp dpt:53 
ACCEPT     udp  --  192.168.1.4          192.168.1.2         udp dpt:53 
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0           
DROP       0    --  224.0.0.0/8          0.0.0.0/0           
DROP       0    --  0.0.0.0/0            224.0.0.0/8         
DROP       0    --  255.255.255.255      0.0.0.0/0           
DROP       0    --  0.0.0.0/0            0.0.0.0             
DROP       0    --  0.0.0.0/0            0.0.0.0/0           state INVALID 
OUTBOUND   0    --  0.0.0.0/0            0.0.0.0/0           
LOG_FILTER  0    --  0.0.0.0/0            0.0.0.0/0           
LOG        0    --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
LSI        0    --  0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (6 references)
target     prot opt source               destination         
LOG_FILTER  0    --  0.0.0.0/0            0.0.0.0/0           
LOG        tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 
LOG        tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 
LOG        icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8 
LOG        0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       0    --  0.0.0.0/0            0.0.0.0/0           

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  0    --  0.0.0.0/0            0.0.0.0/0           
LOG        0    --  0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound ' 
REJECT     0    --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     0    --  0.0.0.0/0            0.0.0.0/0 

There is a bug related to NetworkManager that can cause Firestarter not to run properly at boot up. Have you implemented the fix for this here as described in message #9? :

I can find the folder dispatcher.d/ but I can't create a text file in it...??

[http://ubuntuforums.org/showthread.php?t=457655&highlight=50firestarter](http://ubuntuforums.org/showthread.php?t=457655&highlight=50firestarter)[/QUOTE

---

### Post by djchandler on 2007-06-15
> **Kiwilad said:**
> tried that and I still fail the last test on common ports... how do I "capture the screens"

You can capture the entire screen by pressing the "print screen" button on your keyboard. The foreground window (the one on top) can be captured by pressing the key combination "alt-print screen." Make sure you are posting in advanced mode so you can see the paper clip tool while posting. Click on the paper clip to upload your files. Once they are uploaded, click on it again, to the right side of it, and you will get a drop down menu of the graphic files you just uploaded to place the thumbnails in the body of your message.

Running Firestarter to configure the iptables should not be this difficult. That's why I would like to see the screens while your running Firestarter. I'm getting the impression something is being overlooked. What you are telling us should be working.

Is Ubuntu the only operating system installed on the computer in question? I don't remember if we asked that before or not. :(

---

### Post by djchandler on 2007-06-15
Kiwilad,

OK, I just went back and skimmed the whole thread. In one of your earliest posts, you mention having three ethernet ports. That alone confuses me. Are you running a server or bridge, or are you just needing to connect to computers using different means of implementing ethernet, therefore participating in multiple domains, networks, or subnets? It would seem to me that there should be an ip table for each ethernet port and that is where we are all becoming confused. **If I am wrong about needing multiple ip tables, someone please correct me**, as I have only run multiple ethernet cards once, to bridge between a Macintosh network, and a Windows workgroup about 15 years ago. If I remember correctly, the binding sets were entirely separate for each port, and they also ran different protocols, Appletalk or ethertalk on one, and netbui or netbios on the other. Could you please explain the necessity and utility of your three ethernet ports?

I also confirmed that the question of multiple operating systems had not been asked before my last post.

Regards,
D. J. Chandler

---

### Post by Kiwilad on 2007-06-16
> **djchandler said:**
> Kiwilad,

OK, I just went back and skimmed the whole thread. In one of your earliest posts, you mention having three ethernet ports. That alone confuses me. Are you running a server or bridge, or are you just needing to connect to computers using different means of implementing ethernet, therefore participating in multiple domains, networks, or subnets? It would seem to me that there should be an ip table for each ethernet port and that is where we are all becoming confused. **If I am wrong about needing multiple ip tables, someone please correct me**, as I have only run multiple ethernet cards once, to bridge between a Macintosh network, and a Windows workgroup about 15 years ago. If I remember correctly, the binding sets were entirely separate for each port, and they also ran different protocols, Appletalk or ethertalk on one, and netbui or netbios on the other. Could you please explain the necessity and utility of your three ethernet ports?

I also confirmed that the question of multiple operating systems had not been asked before my last post.

Regards,
D. J. Chandler

Sorry, it wasn't me that had three ethernet ports.....perhaps I should've started a new post, sorry. I have an ADSL router that is connected to internet. I have two computers hooked up to the router, one running WinXP, and this one which is a dual boot WinXP/Ubuntu.

---

### Post by trak87 on 2007-06-16
It's possible that the open ports you are seeing are coming from the modem and not from your Ubuntu box. You might try logging in directly to your modem (or router) and poking around the configuration areas. Look in the device's documentation or online for the modem or router address. It is usually something like 192.168.1.100 or similar. Use Firefox and surf to that address and you'll connect to the local device where you can make adjustments to it, like checking ports, etc. Not all devices have this kind of http access and some that do don't allow for much configuration.

---

### Post by djchandler on 2007-06-16
> **trak87 said:**
> It's possible that the open ports you are seeing are coming from the modem and not from your Ubuntu box. You might try logging in directly to your modem (or router) and poking around the configuration areas. Look in the device's documentation or online for the modem or router address. It is usually something like 192.168.1.100 or similar. Use Firestarter and surf to that address and you'll connect to the local device where you can make adjustments to it, like checking ports, etc.

Kiwilad,

There are two things that draw my attention from the configuration screens you uploaded. On the Network Settings screen, if you are going through a router, the local network connected device area shouldn't be gray and you should be able to make some choices there. This may mean that there is a problem with the eth0 network settings. Configure it for dhcp as well as your router. Also make choices on the Type of Service (ToS) screen to optimize throughput.

Please draw a diagram for us showing how your ADSL modem, router, and two computers are connected together. Answers to the following questions may also help.

1. How is the dual boot machine set up? Do you get a grub prompt asking which operating system to run at boot-up?

2. Have you tried going to Shields Up running Windows?

3. Do you play online games which ask for certain ports to be available unrestricted under Windows?

4. Are you doing any port forwarding with your router?

Your router probably has an http interface for changing its settings. You can reach those settings by typing in [http://192.168.x.y](http://192.168.x.y) where x and y symbolize the last two parts of its local ip address. Mine is:

192.168.1.1

Sorry about the identity mix-up. I had been away for a couple of days and forgot who was who. :o

---

### Post by trak87 on 2007-06-16
Oops. Above I meant to say "Use **Firefox** and surf to that address..." and not "Use Firestarter..."

---

### Post by Kiwilad on 2007-06-17
Thanks Guys, your help is very much appreciated

First though, I'm pretty sure that everything is configured for automatic dhcp.  I've tried getting into my router address using firefox, and unfortunately, I can't remember my user name and password...which is unusual, cos I'm usually pretty good with these.... anyway, I've also tried using the reset button on the router so that I can go back to factory defaults and start again....and even that's not working at the moment. I've written to the ADSL supplier and asked about this since the book states that the router should be off when reset button is pushed and then switched on again for at least 3 seconds to reset. I'm wondering whether the router should be ON rather than off... I digress, sorry.

I've attached a small photo showing the front and back of the router with all the cables labelled.

I've set the ToS options to "workstations" and "reliabiltiy"... haven't really got a clue about this.

The dual boot computer is set up so that I get asked at bootup whether I want to load windows or ubuntu... I presume that's the grub prompt?

I haven't used windows XP at all since I loaded Ubuntu apart from when I set up the router, so no, I haven't tried Shields Up on Windows... I will have a go at this though.

Not into playing online games. More into photography and the online photo sharing group, flickr.

Incidentally, even though Firestarter is configured to start automatically upon connection, I always have to go to Systems/administrator/firestarter to get it to start.

Thanks again

Stu

---

### Post by djchandler on 2007-06-17
> **Kiwilad said:**
> Thanks Guys, your help is very much appreciated

First though, I'm pretty sure that everything is configured for automatic dhcp.  I've tried getting into my router address using firefox, and unfortunately, I can't remember my user name and password...which is unusual, cos I'm usually pretty good with these.... anyway, I've also tried using the reset button on the router so that I can go back to factory defaults and start again....and even that's not working at the moment. I've written to the ADSL supplier and asked about this since the book states that the router should be off when reset button is pushed and then switched on again for at least 3 seconds to reset. I'm wondering whether the router should be ON rather than off... I digress, sorry.

I've attached a small photo showing the front and back of the router with all the cables labelled.

I've set the ToS options to "workstations" and "reliabiltiy"... haven't really got a clue about this.

The dual boot computer is set up so that I get asked at bootup whether I want to load windows or ubuntu... I presume that's the grub prompt?

I haven't used windows XP at all since I loaded Ubuntu apart from when I set up the router, so no, I haven't tried Shields Up on Windows... I will have a go at this though.

Not into playing online games. More into photography and the online photo sharing group, flickr.

Incidentally, even though Firestarter is configured to start automatically upon connection, I always have to go to Systems/administrator/firestarter to get it to start.

Thanks again

Stu

Stu,

Great job on the pics. There's certainly nothing wrong in the way things are connected. I wish my network was so simple. Where you have one device, it takes three for me. The adsl, router, and ethernet switch are separate devices on mine.

I think you are right about power having to be on when you hold in the reset button. Something tells me that when everything resets to factory defaults, some of your troubles will cease.

I use AT&T in the US. With my setup, the filters are for telephones and answering machines. The adsl gets the cable unfiltered. I suppose it could be different with your ISP.

Your IP Tables and firewall should already be up without running Firestarter. It is just a GUI frontend for firewal/ip table configuration. The backend should be up even if you have never installed Firestarter.

Heading off to church for cantor duty. I'll check in later.

Dan

---

### Post by trak87 on 2007-06-17
Why not download the manual for the device rather than writing to the company for advice? The manual should mention how to reset, default passwords and a possible http interface address.

---

### Post by djchandler on 2007-06-18
Stu,

The model # for your device must be on the bottom, so I can't be sure if this helps or not. If you get the reset to work, 

user name = admin
password = password
router ip address = 192.168.1.2
router can be set as dhcp server

If you got to DSE's website, you can probably get the manual in PDF format. Xpdf read the couple of files I found with no problem, I just don't know which is specific to your device. Their website is 

[http://www.dse.co.nz/](http://www.dse.co.nz/)

Good luck!

---

### Post by Kiwilad on 2007-06-18
> **djchandler said:**
> Stu,

The model # for your device must be on the bottom, so I can't be sure if this helps or not. If you get the reset to work, 

user name = admin
password = password
router ip address = 192.168.1.2
router can be set as dhcp server

If you got to DSE's website, you can probably get the manual in PDF format. Xpdf read the couple of files I found with no problem, I just don't know which is specific to your device. Their website is 

[http://www.dse.co.nz/](http://www.dse.co.nz/)

Good luck!

Thanks again for all your help Guys, think it's all sorted now.

To reset the router, the reset button needs to be pushed in when power is off, and it needs to be HELD in for at least 3 seconds after power is switched back on again. Even the help desk dude said that the instructions needed to be clearer! So, I can log into the router now, and I've taken care to record the details this time ;)

I've attached a screen shot for future reference in case anyone else has this problem. The problem setting (at least in terms of consistently failing the on-line Shields-Up test) was that the ICMP tick box in the WAN column was ticked. When it's ticked, I fail the test. When it's unticked, I pass with flying colors. I'm not sure if this will have any other effects, but I guess I'll find out soon enough. For now, I'm happy knowing that my pc is secure.

I also see what you mean about how Firestarter is working even without the little blue arrow... the Shields-Up tests were run without the arrow...very reassuring!

Thanks again, much appreciated :D

Stu

---

### Post by djchandler on 2007-06-18
Stu,

It's good to see that all is well. It's our pleasure to help. We always learn a little something more too.

You live in a beautiful country. It's another of my places to see before I leave this mortal coil. Peter Jackson, the film director, has only made the urge to visit even greater.

With the time differential, this was a little tough for you. Way to hang in there.

See you on the bitstream!

Dan

---

### Post by Pugwash on 2007-06-18
> **Wim Sturkenboom said:**
> To check if a the firewall is configured, you can run the following command in a terminal:
```

root@btd-techweb01:~# **sudo iptables -L -n**
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
root@btd-techweb01:~#
```
If you get above output, the firewall is [COLOR="Red"]**NOT**[/COLOR] configured.

This is what I get! So my firewall isn't working or isn't on? :shock::shock::shock:

---

### Post by trak87 on 2007-06-20
> **Pugwash said:**
> This is what I get! So my firewall isn't working or isn't on?

Your iptables doesn't have anything defined to tell it to block anything. By default, everything is open. However, don't freak out because if you haven't installed any networking programs your ports will be in a closed state.

So you may not a firewall installed or if you've installed Firestarter you didn't go through the Wizard to set it up, or you didn't apply the Firestarter bug fix as mentioned way above...

---

### Post by Pugwash on 2007-06-21
> **trak87 said:**
> Or you don't have a firewall installed or if you've installed Firestarter you didn't go through the Wizard to set it up, or you didn't apply the Firestarter bug fix as mentioned way above...

I don't get it, I was told that Ubuntu had an excellent firewall in the form of iptables, which was shipped with all ports closed. That led me to open a port on my router for port forwarding (for bittorrent). So far the last couple of months I've had an open port on my computer, and hence vulnerable to attaks?

---

### Post by trak87 on 2007-06-22
> I don't get it, I was told that Ubuntu had an excellent firewall in the form of iptables, which was shipped with all ports closed. That led me to open a port on my router for port forwarding (for bittorrent). So far the last couple of months I've had an open port on my computer, and hence vulnerable to attaks?

When you install Ubuntu all ports are in a closed state. However, this is not because of any firewall. In fact the default firewall, iptables, defaults to an ACCEPT state, accepting data from the outside if a port is open. The reason Ubuntu is generally safe by default is because the packagers of Ubuntu don't have any programs running by default with open (open to the outside) web services. Now if you install Apache or a DNS cache or SSH or some other networking program, and because iptables defaults to ACCEPT (rather than DROP or REJECT) unless told otherwise, this will open ports on your computer to the outside world. Apache opens port 80, ssh 22, DNS 53, etc. However, this still may not pose a threat because many people use routers with built in firewalls which protect them from anything outside of their local network.

One way to test for open ports on your own computer is to go to another computer on your local net and scan your computer using nmap. (nmap is in the repositories) If I do this and my own computer is NOT running a firewall, I'd see this:

```
$ nmap 192.168.1.3

Starting Nmap 4.20 ( http://insecure.org ) at 2007-06-22 15:28 EDT
Interesting ports on 192.168.1.3:
Not shown: 1692 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
53/tcp   open  domain
80/tcp   open  http
631/tcp  open  ipp
3306/tcp open  mysql

Nmap finished: 1 IP address (1 host up) scanned in 0.212 seconds
```

Now if I turn ON my firewall (Firestarter) and run the same thing on a local computer, I don't see anything. No ports are visible.

So when you use a firewall you may want some ports visible on your local net because you are sharing some service with other people, but not visible on the wider Internet. A firewall lets you control this.

There are Internet sites which provide scanning services like the above nmap example, but of course the scan occurs from outside of your local network, from the other side of your router. Here's one such service: [http://www.auditmypc.com/](http://www.auditmypc.com/)

If you have a router, this may be providing firewall protection of your entire local net. But if you've just got a modem, no router and thus no firewall or no iptables based firewall like Firestarter, and you install networking programs like Apache, it's possible that the world can see your local network's apache home page just by surfing to your particular ip address. Maybe you want this to be the case because after all Apache IS for serving up web pages to the outside world. Or maybe you're like me and you just use Apache as a glorified bookmarks maintainer and play toy and you don't want port 80 open to the world. That's just one reason for using a firewall.

---

### Post by Pugwash on 2007-06-25
> **trak87 said:**
> When you install Ubuntu all ports are in a closed state. However, this is not because of any firewall. In fact the default firewall, iptables, defaults to an ACCEPT state, accepting data from the outside if a port is open. The reason Ubuntu is generally safe by default is because the packagers of Ubuntu don't have any programs running by default with open (open to the outside) web services. Now if you install Apache or a DNS cache or SSH or some other networking program, and because iptables defaults to ACCEPT (rather than DROP or REJECT) unless told otherwise, this will open ports on your computer to the outside world. Apache opens port 80, ssh 22, DNS 53, etc. However, this still may not pose a threat because many people use routers with built in firewalls which protect them from anything outside of their local network.

One way to test for open ports on your own computer is to go to another computer on your local net and scan your computer using nmap. (nmap is in the repositories) If I do this and my own computer is NOT running a firewall, I'd see this:

```
$ nmap 192.168.1.3

Starting Nmap 4.20 ( http://insecure.org ) at 2007-06-22 15:28 EDT
Interesting ports on 192.168.1.3:
Not shown: 1692 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
53/tcp   open  domain
80/tcp   open  http
631/tcp  open  ipp
3306/tcp open  mysql

Nmap finished: 1 IP address (1 host up) scanned in 0.212 seconds
```

Now if I turn ON my firewall (Firestarter) and run the same thing on a local computer, I don't see anything. No ports are visible. 


Ah, ok thanks. I understand now, I currently don't have my laptop on me and the other pc on the network is running windows xp. But this is what I get  when i run "nmap localhost" :

```
 Starting Nmap 4.20 ( http://insecure.org ) at 2007-06-25 19:53 BST
Interesting ports on localhost (127.0.0.1):
Not shown: 1692 closed ports
PORT     STATE SERVICE
111/tcp  open  rpcbind
631/tcp  open  ipp
673/tcp  open  unknown
989/tcp  open  ftps-data
2049/tcp open  nfs

Nmap finished: 1 IP address (1 host up) scanned in 0.193 seconds

```

I've got my router firewall on so I presume everything should be ok here.



> So when you use a firewall you may want some ports visible on your local net because you are sharing some service with other people, but not visible on the wider Internet. A firewall lets you control this.

There are Internet sites which provide scanning services like the above nmap example, but of course the scan occurs from outside of your local network, from the other side of your router. Here's one such service: [http://www.auditmypc.com/](http://www.auditmypc.com/) 

If you have a router, this may be providing firewall protection of your entire local net. But if you've just got a modem, no router and thus no firewall or no iptables based firewall like Firestarter, and you install networking programs like Apache, it's possible that the world can see your local network's apache home page just by surfing to your particular ip address. Maybe you want this to be the case because after all Apache IS for serving up web pages to the outside world. Or maybe you're like me and you just use Apache as a glorified bookmarks maintainer and play toy and you don't want port 80 open to the world. That's just one reason for using a firewall.



Ok, this is what's got me worried. I've done a port scan with the above site, and it tells me that the following ports are open - 1864 , 4443, 5190, 5566 (There may be more, I've only checked ports 1-7500). I'm very sure that my router firewall is on. I've only portfowarded port 54872 to this computer for bittorrent. I'm not quite sure what's going on. I'm on a netgear router/modem. Thanks for the detailed reply, I appreciate the help.

---

### Post by trak87 on 2007-06-26
> **Pugwash said:**
> Ok, this is what's got me worried. I've done a port scan with the above site, and it tells me that the following ports are open - 1864 , 4443, 5190, 5566 (There may be more, I've only checked ports 1-7500). I'm very sure that my router firewall is on. I've only portfowarded port 54872 to this computer for bittorrent. I'm not quite sure what's going on. I'm on a netgear router/modem. Thanks for the detailed reply, I appreciate the help.

If you are using a router with a firewall, the open ports that an external security scan finds are probably at the router and not at your Ubuntu box. However, if you've specified a forwarded port on the router (edit: and opened that port on your firewall), that *would* reach your linux box. At any rate, it would be good to know what those open ports are for.

---

### Post by Pugwash on 2007-07-09
> **trak87 said:**
> If you are using a router with a firewall, the open ports that an external security scan finds are probably at the router and not at your Ubuntu box. However, if you've specified a forwarded port on the router (edit: and opened that port on your firewall), that *would* reach your linux box. At any rate, it would be good to know what those open ports are for.

Hi, sorry for the late reply, I've been a bit busy. This is what auditmypc mentions for the open ports on the router. Any advice would be appreciated.

1864	Paradym 31 Port.
4443	Pharos
5566	A description of this port is not available
5190	America-Online Server Port. Primary AOL Internet-connect port; also used in Instant Messaging. Alternate ports: 5191; 5192; 5193.

Thanks

---

