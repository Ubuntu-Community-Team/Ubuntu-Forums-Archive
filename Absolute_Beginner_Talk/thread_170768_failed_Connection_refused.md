---
title: "failed: Connection refused"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by Isoss on 2006-05-05
I don't think th server is down! 
I've just changed my repositories list into the one recommended by ubuntu_demon : [http://www.ubuntuforums.org/showthread.php?t=92672](http://www.ubuntuforums.org/showthread.php?t=92672)

I was trying to install Easy aMSN the way aysiu suggested: [http://www.ubuntuforums.org/showpost.php?p=978766&postcount=47](http://www.ubuntuforums.org/showpost.php?p=978766&postcount=47)

When I tried to install it gave me this error:
```
isos@ubuntu:/$ sudo ./getamsn.sh
--15:55:06--  http://superb-west.dl.sourceforge.net/sourceforge/amsn/amsn_0.95-3.ubuntu.deb
           => `amsn_0.95-3.ubuntu.deb'
Resolving superb-west.dl.sourceforge.net... 209.160.59.253
Connecting to superb-west.dl.sourceforge.net|209.160.59.253|:80... failed: Connection refused.
--15:55:06--  http://archive.ubuntu.com/ubuntu/pool/universe/t/tcltls/tcltls_1.5.0-2_i386.deb
           => `tcltls_1.5.0-2_i386.deb'
Resolving archive.ubuntu.com... 85.133.25.7, 85.133.25.8
Connecting to archive.ubuntu.com|85.133.25.7|:80... failed: Connection refused.
Connecting to archive.ubuntu.com|85.133.25.8|:80... failed: Connection refused.
dpkg: error processing tcltls_1.5.0-2_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 tcltls_1.5.0-2_i386.deb
dpkg: error processing amsn_0.95-3.ubuntu.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 amsn_0.95-3.ubuntu.deb
mv: cannot stat `amsn_0.95-3.ubuntu.deb': No such file or directory
mv: cannot stat `tcltls_1.5.0-2_i386.deb': No such file or directory

```

WHY failed: Connection refused ? is it the repositories? this happened in more than one installation. so I don't think it's bcoz the server is down! ... Errors keep on showing  ... I am really pissed off. I love linux, but this is one reason why I can't just switch to it 100%.

---

### Post by sYs^ on 2006-05-05
Well, it's working for me: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) and this one too: [http://superb-west.dl.sourceforge.net/](http://superb-west.dl.sourceforge.net/)

---

### Post by halfvolle melk on 2006-05-05
Did you install a firewall or something? From that I gather reading your various connectivity problems port 80 ie. browsing works fine, but wget and such do not. I don't no very much about firewalls, but who knows that's it.

---

### Post by Isoss on 2006-05-12
[QUOTE=halfvolle melk]Did you install a firewall or something? From that I gather reading your various connectivity problems port 80 ie. browsing works fine, but wget and such do not. I don't no very much about firewalls, but who knows that's it.[/QUOTE]
No I am not using a firewall! and can you please explain more about the port 80 thing? 

Thanks

---

### Post by carverj on 2006-05-12
In your computer there are a range of ports from 0? to 60000 or so
port 80 is just like a doorway that allows you to access the internet using tcp/ip internet protocol.
I cant remember of hand what the ftp port is by default. Perhaps you need to open the ftp port?

---

### Post by Isoss on 2006-05-12
[QUOTE=carverj]In your computer there are a range of ports from 0? to 60000 or so
port 80 is just like a doorway that allows you to access the internet using tcp/ip internet protocol.
I cant remember of hand what the ftp port is by default. Perhaps you need to open the ftp port?[/QUOTE]
It is open. But dunno where to see that port 80 is open.

By the way, my Network Proxy Preferences is set to Direct internet connection, while I am connected to a networ that is connected to the internet. so everthing looks fine, network, internet, everything ... I have edited apt.conf and  added this:
```
Acquire::http::Proxy "http://proxy.net.sy:3128/";

```
This is a proxy server. so, do I have to add Manual proxy configuration through  Network Proxy Prerences?

---

### Post by halfvolle melk on 2006-05-12
Port 80 is fine because you can use http. Here's a long list of what port is commonly used for what service:
[http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers)

As for your problem, maybe it's the proxy then, I don't know a great deal about that. Do you need to connect through a proxy? If not, try to connect without.

---

### Post by Isoss on 2006-05-12
Actually, I can't connect with out it. before editting /etc/apt/apt.conf I couldn't install anything using synaptic or apt-get, but browsing worked fine cuz Connection Settings were added. 

But I am starting to doubt it's my ISP proxy server. They have disabled FTP few days ago and I have to register for a real ip. could it be because I don't have a real IP? I mean like all these connection failures and refused?

I really need an answer for this. could it be the REAL IP issue?
Thanks.

---

### Post by halfvolle melk on 2006-05-12
I'm not sure what you mean by real IP, but here is some guessing; maybe now you get your IP assigned dynamically, ie. everytime you want to connect to internet, your computer/modem will request any one IP available(not in use at that moment) from the server. You can use that for one 'session'. Next day you turn on your compu again and ask for an IP. You're likely to get different one.
This is not so with static IPs. If you get 1.2.3.4 you will always keep 1.2.3.4

Both types are as real as can be.

From what you describe it's not unlikely to be related to their proxy. A proxy can be used to restrict internet access. Ask your ISP for their policy on this. Some can be realy **** about it. If they don't feel like cooperating I don't think you'll be apt-getting anytime soon.
Though I could be wrong on all of the above ;)

---

### Post by Isoss on 2006-05-12
Thanks a lot for your guessing. But I need some certainty .. static ip I guess is what I know fixed IP .. this is really expensive here in Syria. while I can get real ip which gives a lotta advantages like enabling Gnomemeeting, FTP and some other stuff.

Thanks again halfvolle melk, but I still need more explaination and clarification concerning the proxy-server and IP .. maybe some user who works with ISP's can answer.

Thanks.

---

### Post by halfvolle melk on 2006-05-12
Again, this is ISP specific.  Call your ISP for their policy on this(don't mention linux "We only provide support for MS x, y and z", just ask about the ports) or look for clues in their FAQ.

---

### Post by carverj on 2006-05-12
Is your computer connected to a router?
What is your current IP address?
Have you talked to your ISP about the problem?

---

### Post by Isoss on 2006-05-12
yes, my PC is connected to router. it's a Laptop and everything works fine when I am in windows. Why do u wanna know my IP address?
And concerning the ISP, I don't really know what to ask them. I don't think the support can answer such a question since I only face the problem with linux. and since - according to [Linux Users Statistics]("http://www.counter.li.org") - there are only 45 Syrian linux users, I don't think my ISP support team would conprehend the problem.

---

### Post by dewclaw82 on 2006-05-12
Is your connection wireless?  I kept getting the same message trying to set up my wireless connection to a Belkin router.  It works on Windows, but I can't get it to assign an IP address in kubuntu.  I finally just bought a longer ethernet cord ... not a very sophisticated solution but it works.

---

### Post by macdo on 2006-05-12
What happens if you connect your PC under Linux directly to the Internet (if that is possible)?

---

### Post by carverj on 2006-05-13
oh sorry 
> Why do u wanna know my IP address?
not to be taken literally. What I mean is if you are having problems attaining a dynamic IP address from DNS, have you tried entering a static ip address in System> Admin> Networking ?

---

### Post by Isoss on 2006-05-13
Of course ... other wise I won't be able to access internet through LAN!
I just have a question here. how do I know how many IP's available for use on the same network?

---

### Post by Isoss on 2006-05-14
[QUOTE=dewclaw82]Is your connection wireless?  I kept getting the same message trying to set up my wireless connection to a Belkin router.  It works on Windows, but I can't get it to assign an IP address in kubuntu.  I finally just bought a longer ethernet cord ... not a very sophisticated solution but it works.[/QUOTE]
No I am not using wireless.

[QUOTE=macdo]What happens if you connect your PC under Linux directly to the Internet (if that is possible)?[/QUOTE]
No I don't have a direct connection. I haven't tried that yet cuz I have ADSL, no need for dial-up

 I still think the problem is due to disabling the real IP. Tomorrow I'll apply for one and will see.

---

### Post by carverj on 2006-05-25
public IP addresses make use of the subnet mask 255.255.255.0 (Class C)
The 0 or last octet represents the host portion of the subnet mask and the rest is the network portion (unuseable). So if you go with something like 192.168.1.....
there are 254 useable host IP's
you can then start to subdivide if need be by subnetting.

---

