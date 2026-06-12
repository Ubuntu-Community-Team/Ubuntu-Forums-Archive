---
title: "Beginner network question"
date: 2005-10-10
forum: Absolute Beginner Talk
---

### Post by BizzyLizzy on 2005-10-10
Hi hope someone in here can help me.  

I am completely new to linux but have a basic understanding of windows networking stuff.

Right the situation is as follows:-

My company has office space within a larger company and we share their DSL connection to the outside world.

What I am trying to do with my Ubuntu box is use it to isolate our network and our windows SBS2003 server from their network as they also have SBS2003.  So in otherwords I am trying use it as a gateway (I think!).  :???: 

The ubuntu box has two NIC cards.  I know that in theory we use eth0 to connect to the main network and thus to the outside world - this works fine and I can get onto the internet.  The problem is  the second NIC eth1.  I have connected eth01 into our hub but I am completely unsure of how I should configure both the cards!.  

The gateway to the outside world has an IP address of 192.168.100.254 and eth0 has a static ip address of 192.168.100.210.  I want to set up the other pcs and the sbs server with ip addresses in the range 102.168.150.x.

Yesterday when I was playing around with things I connected my laptop to the ubuntu machine with a crossover cable (plugged in to eth1) and gave the laptop a static ip address of 192.168.150.101.  I gave eth1 an ip address of 192.168.150.1.  All was fine with this and I could ping eth1 fine from the lap top.  What I couldnt do was then get to the outside world.  I realise that somewhere along the line I have to get the two cards talking to each other, but I am blowed if I can think how to do it.   Presumably I have to put some sort of route information in somewhere??

Hope one of you wonderfull people out there can help me.

Cheers Lizzy

---

### Post by BizzyLizzy on 2005-10-10
Sorry people should have said using Hoary Ubuntu!

---

### Post by heimo on 2005-10-10
Hi!

Looks like you are pretty close to solve it - and you described the scenario very well. Thanks for that! :)

Yes, you want to use that Ubuntu box as a gateway (remember to make this setting to all the client computers). To enable internet sharing, you could install firestarter and use its preferences / wizard to set it up. (I've never done it this way, but I've heard it should work.) There are other ways to do the same thing - I believe the key is to have "ip forwarding" enabled. 

In firestarter Edit->Preferences->Firewall->Network Settings->"Enable internet connection sharing"

---

### Post by BizzyLizzy on 2005-10-10
Thanks for the quick reply Heimo :D .  One question - what on earth is firestarter and where do I get it from????

Cheers Lizzy

---

### Post by BizzyLizzy on 2005-10-10
Dur!!!  Use google of course :rolleyes:   Right will download now and see what happens!

---

### Post by heimo on 2005-10-10
Firestarter is a frontend to Linux's internal firewall (net filter). If you have universe section enabled (these instructions are a bit out of date, if I'm not mistaken:)
[https://wiki.ubuntu.com/UniversePackages](https://wiki.ubuntu.com/UniversePackages)
... you should be able to use System->Administration->Synaptic Package Manager to install it (search firestarter, select for install and hit apply). Or you can use this command on terminal:
```
sudo apt-get install firestarter
```

I must emphasize that I haven't done this on Ubuntu, but I've done it using Debian several years ago. Just for information... could you run this command before and after setting up firestarter's internet sharing? 
```
cat /proc/sys/net/ipv4/ip_forward
```
I think it should go from 0 to 1.

---

### Post by heimo on 2005-10-10
[quote=BizzyLizzy]Dur!!!  Use google of course :rolleyes:   Right will download now and see what happens![/quote] 
No no... Don't download and install - please use package manager to do that, it'll be a lot smoother and you'll get updates easier. Enable universe if not done already (using Synaptic or by editing /etc/apt/sources.list file) and use Synaptic Package Manager or apt-get install to install firestarter. :)

In synaptic package manager, settings->repositories.

EDIT: Found some instructions:
[https://wiki.ubuntu.com/forum/hardware/InternetConectionSharing]("https://wiki.ubuntu.com/forum/hardware/InternetConectionSharing")
[https://wiki.ubuntu.com/ShareInternetConnection](https://wiki.ubuntu.com/ShareInternetConnection)

---

### Post by BizzyLizzy on 2005-10-10
Hi Heimo

Right running that cat command gives the answer 0.  

when I try to find firestarter using apt-get I get the message couldnt find package firestarter.  

Can I just download it from the internet??

---

### Post by BizzyLizzy on 2005-10-10
ooops posts crossed.  Ok wont download it!!

---

### Post by BizzyLizzy on 2005-10-10
Right - have gone into package manager settings and added universe, but when it tries to download all the repository indexes I get a connection refused error message.  Its trying to connect to [http://archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz) Could not connect to archive.ubuntu.com:80(82.211.81.151).  Connection refused (and so on and so forth).

what am I doing wrong?

---

### Post by heimo on 2005-10-10
I have a different version of Ubuntu, but this should be quite similar (if you didn't already figure out how to enable universe).

[LIST]
[*]System->Administration->Synaptic Package Manager   
[*]Settings->Repositories   
[*]Settings->Show disabled software sources (select this)   
[*]On Software Sources window make sure you have Ubuntu 5.04 universe / binary enabled   
[*]Synaptic Packet Manager window -> Reload   
[*]Search for firestarter   
[*]Right click -> Mark for installation -> Apply [/LIST]

---

### Post by heimo on 2005-10-10
[quote=BizzyLizzy]Right - have gone into package manager settings and added universe, but when it tries to download all the repository indexes I get a connection refused error message. Its trying to connect to [http://archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz]("http://archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz") Could not connect to archive.ubuntu.com:80(82.211.81.151).  Connection refused (and so on and so forth).

what am I doing wrong?[/quote] 
Do you use proxy? If yes, you need to configure that setting to Synaptic too. Can you access that file above using browser?

alt+F2 -> xterm
```
 ping 82.211.81.151
```
ctrl+c to exit. Did it return pings?

---

### Post by BizzyLizzy on 2005-10-10
OK twas the proxy needed setting up :D .  Firestarter is now downloaded.  So going to have a play around and see what happens.

Many thanks for your help.  I could well be back with more questions very shortly. :)

---

### Post by BizzyLizzy on 2005-10-11
Ok progress of a sort!.  I ran that cat command again and this time it came back with 1.  I can now ping eth1 card ok but cannot ping eth0 - get message saying Destination is unreachable.

I have enabled Internet connection sharing ok using firestarter.

What do I do now?

---

### Post by BizzyLizzy on 2005-10-11
Pure GENIUS!!!

Heimo.  Got it all working now :D :D :D.  Thank you soooo much.  I would blow you a big sloppy kiss but there isnt an emoticon for it - lol.

You are wonderfull.  

One very happy user.  Of course now the fun starts cos I have to set up SBS2003 - windows YUK :(

Cheers Lizzy

---

