---
title: "Connection timed out (problem with one particular website)"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by erdomi on 2007-02-06
Hi.  I'd be grateful if anyone could help me with this problem.  I cannot connect to my university's website ([www.bu.edu](www.bu.edu)) on ubuntu.  For a while, the BU computer support team was trying to help me, but they eventually gave up saying that they don't support ubuntu operating systems.  (I use Dapper.)  

On foxfire, I get the error message:

The connection has timed out
The server at [www.bu.edu](www.bu.edu) is taking too long to respond.
# The site could be temporarily unavailable or too busy. Try again in a few
    moments.

#   If you are unable to load any pages, check your computer's network
    connection.

#   If your computer or network is protected by a firewall or proxy, make sure
    that Firefox is permitted to access the Web.

I have found a lot of advice online about how to deal with this message, but I don't think I have found anything applicable to my case.

I thought it might be a problem with my settings in foxfire, so I also installed opera but I still get the same problem.  However, when I run windows via vmware, I can connect to [www.bu.edu](www.bu.edu) with no problems.  This is the ONLY website I have ever had this problem with.  I am pretty sure that when I first installed Dapper, the connection was OK.  But then I installed a lot of other stuff and probably some updates and then I could never get back to this website.  I also had this problem (with the same website) on a different computer where I was running Breezy.  That was a laptop which I took into campus and so I assumed that the problem came from using the campus connection and then still having some weird leftover settings.  But the computer that I'm having problems with now is a desktop and has never been to campus.

I've tried a few things:

I try to ping this site:

> erdomi@erdomi:~$ ping [www.bu.edu](www.bu.edu)
PING [www.bu.edu](www.bu.edu) (128.197.26.35) 56(84) bytes of data.

--- [www.bu.edu](www.bu.edu) ping statistics ---
38 packets transmitted, 0 received, 100% packet loss, time 37030ms



And so I try traceroute:

> erdomi@erdomi:~$ ping [www.bu.edu](www.bu.edu)
PING [www.bu.edu](www.bu.edu) (128.197.26.35) 56(84) bytes of data.

--- [www.bu.edu](www.bu.edu) ping statistics ---
38 packets transmitted, 0 received, 100% packet loss, time 37030ms


and I get the following (very slowly):

> traceroute: Warning: [www.bu.edu](www.bu.edu) has multiple addresses; using 128.197.26.4
traceroute to [www.bu.edu](www.bu.edu) (128.197.26.4), 30 hops max, 40 byte packets
 1  dslrouter (192.168.1.1)  0.525 ms  0.497 ms  0.394 ms
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *

and so on.  So obviously I have a problem, but I have no idea how to fix it.

I do a lot of class work and grade maintenance on this website and I hate to have to switch to windows every time I need to access it.  I would be most appreciative if someone could help me fix this.

---

### Post by wildseven on 2007-02-06
does your internet work in general in Ubuntu? Is it pretty much everything works except that website?

[edit] heh sry i didnt read it fully. So just that website doesnt work huh? It worked for me, let me think somemore




p.s my cousins go there heh~ i hope you give them a good grade!

---

### Post by lloyd_b on 2007-02-06
Could you post the following info:

The output from running the "ifconfig" command.
The output from running the "route" command.
The contents of the file "/etc/resolv.conf"
The contents of the file "/etc/hosts"
In addition, could you run the traceroute equivalent (tracert.exe?) under Windows and post that as well?

My first guess (admittedly based on inadequate information) is that you have a bogus entry in "/etc/hosts" for that domain, which is causing your computer to look for it at the wrong IP address.

To confirm this, do a "ping" from Windows, and see if it shows the same IP address as you get when running the "ping" from Ubuntu.

If that is not the problem, then the other info I've asked for may provide a clue as to what is going wrong.

Lloyd B.

---

### Post by wildseven on 2007-02-06
Just wondering, how would he get a bogus /etc/host ?

---

### Post by lloyd_b on 2007-02-06
> Just wondering, how would he get a bogus /etc/host ?

Maybe at some point one of the University's IT staff told him to "add such and such to /etc/hosts"?  Or some application that he installed fiddled with /etc/hosts for some unknown reason. 

As stated in the previous message, that's just my best guess based on the information provided.  It *does* explain the problem, but I won't be too surprised if my guess turns out to be wrong.

Lloyd B.

---

### Post by erdomi on 2007-02-06
wildseven-

Yes, this is the only problem.  Everything else works fine.

And I am a pretty nice grader.



lloyd_b-

here it is:

> erdomi@erdomi:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:18:8B:7A:86:1E
          inet addr:192.168.1.32  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::218:8bff:fe7a:861e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:194064 errors:0 dropped:0 overruns:0 frame:0
          TX packets:170984 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:125143773 (119.3 MiB)  TX bytes:43986790 (41.9 MiB)
          Interrupt:58

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:59 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3806 (3.7 KiB)  TX bytes:3806 (3.7 KiB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01
          inet addr:172.16.1.1  Bcast:172.16.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08
          inet addr:172.16.35.1  Bcast:172.16.35.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



> erdomi@erdomi:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.35.0     *               255.255.255.0   U     0      0        0 vmnet8
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
172.16.1.0      *               255.255.255.0   U     0      0        0 vmnet1
default         dslrouter       0.0.0.0         UG    0      0        0 eth0


> erdomi@erdomi:/etc$ more resolv.conf
search myhome.westell.com
nameserver 192.168.1.1
nameserver 192.168.1.1


> erdomi@erdomi:/etc$ more hosts
127.0.0.1       localhost
127.0.1.1       erdomi

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


A windows tracert gives me:

> Tracing route to [www.bu.edu](www.bu.edu) [128.197.26.34]
over a maximum of 30 hops

1    11 ms     8 ms      <1 ms   dslrouter  [192.168.1.1]
2    *             *            *          Request timed out


and so on.

And a ping returns:

> pinging [www.bu.edu](www.bu.edu) [128.197.26.34] with 32 bytes of data:

Request timed out.
Request timed out.
Request timed out.

Ping statistics for 128.197.26.34:
     Packets sent = 4, Received = 0, Lost = 4 (100% loss),

hmmm.  Is that weird that ping times out in windows even though the website works ok?

Thanks for your response.

-erdomi

---

### Post by lloyd_b on 2007-02-06
Okay, first guess WRONG.  Let's try again.

I do understand how "ping" can fail while the browser works - most likely the IT folks have the machine configured to not respond to pings.  The fact that traceroute can't establish a path is a bit more troubling - while the final point in the connection may not be responding, I would expect most if not all of the intervening routers to respond.  Weird.

Works from Windows, but not Ubuntu - Nothing in /etc/hosts to indicate a problem.  "route" looks okay (I have not clue what those "vmnet" entries are, but they aren't conflicting - it's genuinely trying to establish the connection via the DSL link, which is the same that Windows is using).  "resolv.conf" looks okay.
 
Time for an experiment...:) 
I ran into a similiar issue in the forums, where a particular host was accessible from Windows but not Ubuntu.  Turns out to have been a bit of weirdness in the intervening network.  The solution in that case was to decrease the MTU (Max Transmission Unit) for the interface (the intervening network had problems if the packets were above a certain size). So, in a terminal:
```
sudo ifconfig eth0 MTU 1400
 <try web browser>
sudo ifconfig eth0 MTU 1300
 <try web browser>

```
Keep trying that until you either get a response, or you get the MTU down to 500 (if it hasn't worked by that point, it's not going to).

If that doesn't work, I'm out of ideas - hopefully somebody else will wander by with some insight into the problem.

Lloyd B.

---

### Post by RomeReactor on 2007-02-06
Hi. I tried loading the page and that went just fine on my system; pinging the site returned the appropriate response, so i think the issue is elsewhere. have you tried disabling ipv6? if not, it might be worth a try. On a terminal, write:

```
sudo gedit /etc/modprobe.d/aliases
```

then search for

```
alias net-pf-10 ipv6
```

and change that to

```
alias net-pf-10 off
```

save and reboot.

---

### Post by erdomi on 2007-02-06
Thanks for your responses.  Decreasing MTU didn't seem to work.  I also tried tried disabling ipv6 and that didn't seem to work either.  But thanks for the ideas.

erdomi

---

### Post by lloyd_b on 2007-02-07
A question:  When you connect to the website in Windows, are you using Firefox or Internet Explo rer?  If the answer is IE, could you try installing the Windows version of Firefox and see if it can access the site?

The reason I ask - you mention that you're able to connect *via Windows running in VMware*, which is using the exact same network connection (VMware just adds an extra layer between the Windows session and Ubuntu).  So you may be looking at an IE/Firefox issue (with the issues of not being able to ping/traceroute the site being red herrings).

Lloyd B.

---

### Post by erdomi on 2007-02-07
I am using IE in windows.  I'll try installing foxfire tonight in my windows machine and see if that helps.  (But note that I also had the problem in opera in ubuntu.)  Thanks for your reply,

erdomi

---

### Post by erdomi on 2007-02-07
I just installed foxfire on windows and I can access [www.bu.edu](www.bu.edu) with no problems.

Thanks,
erdomi

---

### Post by wildseven on 2007-02-07
are you doing this at home or at campus? If it's on campus, college websites usually work on intranet right? So it should work on campus. But i think ping might not work because they disabled recieving icmp packets on the router. If that is the case, won't traceroute not work either since that uses icmp packets aswell?

dont take anything i say as correct. I am just throwing out ideas, and i am still a network student so i am not 100% sure if i am correct.

---

### Post by wildseven on 2007-02-07
i just tried pinging the website and it timed out.
i also tried traceroute and it was fine until it left my networks routers. 

i think that just the servers disabled icmp requests

---

### Post by erdomi on 2007-02-07
I'm not sure what an icmp request is.  Is that what ping sends?  I am having problems on my home computer.  I have never had this problem on campus.

Thanks for your reply,
erdomi

---

### Post by erdomi on 2007-02-16
Hello, all.  Thanks for the help and suggestions.  Unfortunately, my issue is still unresolved and I would love to hear any new ideas that anybody has.

Thanks,
erdomi

---

### Post by jeffers@bu.edu on 2007-03-01
I too would LOVE a solution to this problem as i have the exact same one. I haven't encountered any websites yet that don't work except for [www.bu.edu](www.bu.edu), been running 6.10 for about a week.

The funny thing is I remember this happening with other distros (SUSE? Can't remember exactly, but I tried it several months ago.) Seems to be a linux-wide issue. Or maybe the ISP? I'm using Verizon DSL here in Boston off campus.

But I have found a half solution: establish a vpn connection (but use the off-campus vpn settings. BU's website has them.) When I do this, I CAN connect to [www.bu.edu](www.bu.edu) from off campus. (But it's a pain to have to run vpnc every new session. Set up an alias at least.)

---

### Post by erdomi on 2007-03-01
Thanks for your comment, [email]jeffers@bu.edu[/email].  I have Verizon DSL off campus also.  I've been connecting on Windows via VMWare, but this is also pretty annoying.  Thanks for the vpn idea- I'll give that a try.

erdomi

---

