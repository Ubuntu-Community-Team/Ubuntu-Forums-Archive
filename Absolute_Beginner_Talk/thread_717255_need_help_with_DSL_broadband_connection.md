---
title: "need help with DSL broadband connection"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by swarup on 2008-03-06
I am in India, and have DSL connection set up through the VSNL company. I know it works fine, because I am using it right now with my XP desktop. I have purchased a DELL laptop and set up Ubuntu Gutsy on it. I need some help getting the DSL broadband to work with it. 

Here is what I did so far:

I connected the LAN wire connection from my broadband modem. Gutsy recognized it just fine. But it did not go on line.

So I clicked on the network icon, and went into manual configuration. There I went into "connection settings", and selected "static IP address" for configuration, then for IP address I typed our address (192.168.1.1), then Gutsy automatically set the Subnet mask to 255.255.255.0. The "Gateway address" window remains empty. Do I need to put something there?

I have selected "wired connection" under the Network Settings window. But I do not know what to do next. I have a DSL network username and password, but Gutsy has not asked me for that and I know it is needed to get on line.

Please help....thanks!

---

### Post by exneo002 on 2008-03-06
So you're in via ethernet. hm check the network proxy under prefernfces. try network problems section.

---

### Post by swarup on 2008-03-06
> **exneo002 said:**
> So you're in via ethernet.

Yes

> **exneo002 said:**
> hm check the network proxy under prefernfces. try network problems section.

ok, I am in the Network Proxy window. Please tell me what I should do there. There are options for "Direct internet connection", "Manual Proxy Configuration", and "Automatic proxy configuration". There is also an "advanced configuration window". Is something needed there?

And kindly tell me where the "network problems section" is.

Also: I've added the "network monitor" icon to the upper applet. When I click on that, it shows the connection as "lo", and the status as "idle". The "Network Device" shows as type "Local Loopback". Is this proper?

---

### Post by blastus on 2008-03-06
[Ubuntu India Broadband HowTo](http://www.ubuntu-in.org/wiki/Broadband_Howto) may be able to help you.

---

### Post by swarup on 2008-03-06
> **blastus said:**
> [Ubuntu India Broadband HowTo](http://www.ubuntu-in.org/wiki/Broadband_Howto) may be able to help you.

For some reason, that website is not functional--or at least I cannot open it. But I do not think this is really any sort of issue unique to India. Because my connection is a straightforward broadband DSL connection. I have all the IP address info etc. So if there is someone out there who knows about this stuff, then my guess is that with a little guidance this laptop should go right on line. 

Actually, I've heard that with Gutsy it is supposed to work out of the box, isn't it?

---

### Post by freebeer on 2008-03-06
> **swarup said:**
> Actually, I've heard that with Gutsy it is supposed to work out of the box, isn't it?

It does, pretty much, in my experience.  You mentioned a username and password to connect to your provider.  That implies to me that you've got a PPoE connection?  I'm less familiar with them but this [link]("http://packages.ubuntu.com/feisty/net/pppoe") might help.

---

### Post by swarup on 2008-03-07
> **freebeer said:**
> It does, pretty much, in my experience.  You mentioned a username and password to connect to your provider.  That implies to me that you've got a PPoE connection?  I'm less familiar with them but this [link]("http://packages.ubuntu.com/feisty/net/pppoe") might help.

Yes, yes that is right. It is a PPoE connection. Now I've got it to go online, but it will only search Google and refuses to go to any other website. I can search any subject on google as I say, but if I then try to click on any of the websites which google search found, I cannot go to ANY of the sites. And the gutsy Add/Remove application also does not recognize that the computer is on line. So what more do i need to do to get it working properly? It sounds like it may be some sort of permissions issue to me, because it can go to google but nowhere else.

---

### Post by The Titan on 2008-03-07
> **swarup said:**
> . The "Gateway address" window remains empty. Do I need to put something there?


I'm much a "Noob" but i had similar issues and i had to set the gateway address to my modems ip.... i could be way off.  Coulden't hurt to try i guess.  Hope that helps.

---

### Post by net-reg on 2008-03-07
hi,
   try re-installing ubuntu while keeping your modem on.

 or 

 try # sudo pppoeconf           (after turning on your modem and waiting for lights to stop blinking)

---

### Post by kleo skywalker on 2008-03-07
Try these steps:

Go to System-->Administration-->Network. Click on the "Properties" button next to "Wired Connection". Uncheck the "Enable roaming mode" box, set Configuration to "Static IP". Set the IP Address, Subnet Mask, Gateway Address. Back in the "Network Settings" menu, set DNS servers (primary and secondary). If you don't know what to put in these boxes, just call your local VSNL people and ask for them.

In the Terminal (Applications-->Accessories-->Terminal), run this command
```
sudo pppoeconf
```
Don't worry if it doesn't respond encouragingly - that is, tells you it can't find something etc. Just go through the procedure.

Once done, reboot. You should be able to connect to the internet.

---

### Post by kpkeerthi on 2008-03-07
> **swarup said:**
>  I can search any subject on google as I say, but if I then try to click on any of the websites which google search found, I cannot go to ANY of the sites. 

Are you able to surf the net with IP address instead of DNS names. Try this url [http://91.189.94.186](http://91.189.94.186) and that should lead you here. 

If you are able to surf with IPs, it could be IPv6. YOu need to disable it.
It could also be that your ubuntu is not resolving DNS names. There are ways to fix it. But first confirm if you are able to surf with IP addresses.

---

### Post by swarup on 2008-03-07
> **kpkeerthi said:**
> Are you able to surf the net with IP address instead of DNS names. Try this url [http://91.189.94.186](http://91.189.94.186) and that should lead you here. 

If you are able to surf with IPs, it could be IPv6. YOu need to disable it.
It could also be that your ubuntu is not resolving DNS names. There are ways to fix it. But first confirm if you are able to surf with IP addresses.

I just tried the IP url you listed above, but it would not go there. 

Within google, it flies all over the place without the slightest hesitation. But it won't go anywhere else.

As for IPv6, I've already disabled it both within Firefox using about:config and also inside ubuntu using instructions someone else gave. But it didn't make any difference. Perhaps it is the DNS name resolution issue you mention above? Please kindly let me know what I should do next.

---

### Post by kpkeerthi on 2008-03-07
If you are unable to surf with IP address, changing DNS server will NOT help. Can you post the contents of /etc/resolv.conf
```
 cat /etc/resolv.conf
```

---

### Post by kpkeerthi on 2008-03-07
Also let me know what happens when to run this command from a terminal
```
ping www.ubuntuforums.org 4
```

That would help me check if firefox is misbehaving.

---

### Post by kpkeerthi on 2008-03-07
To change the DNS Servers, go to System > Administration > Networking > Wired connection > Properties:

Under DNS, delete anything you have and add one of these:

208.67.222.222 and 208.67.220.220 or
4.2.2.1 and 4.2.2.2 or 

** You may have to reboot, recheck DNS and try internet.

---

### Post by swarup on 2008-03-07
kpkeerthi, many many thanks for your help. And I am going to try all those things you just gave in your above three letters, right now. One thing: I am now typing this to you on a separate computer from the one I am trying to set up. This one I am typing on, is a Win XP machine. If I put the output from  "cat /etc/resolv.conf" on a pen drive, will XP allow me to paste it onto this forum? 

You mentioned that if the browser is not working with url IP addresses, then it will not help to change the DNS server. But then in your last post you gave me a series of new DNS servers. Do you feel it may help to try doing this even though the browser did not work with url IP addresses? If you do feel it is worth a try, then I'll certainly do it.

And as for your "ping [www.ubuntuforums.org](www.ubuntuforums.org) 4"-- I need to be online in order to do this, right? ok that can be done, I'll just switch the LAN cable over from this computer to the other way, then try it and then come back to this one and let you know the result. It'll take me a few minutes, but I'll be back with you in the next 15  minutes I hope, with the results.:)

---

### Post by swarup on 2008-03-07
I just tried

```
cat /etc/resolv.conf
```

But it just goes to the next line in terminal, with no output. Nothing happens.

---

### Post by swarup on 2008-03-07
> **kpkeerthi said:**
> Also let me know what happens when to run this command from a terminal
```
ping www.ubuntuforums.org 4
```

That would help me check if firefox is misbehaving.

Here is the output when I do the above:

```
PING 4 (0.0.0.4) 56(124) bytes of data.
```

Is that what it is supposed to do?

---

### Post by swarup on 2008-03-07
> **kpkeerthi said:**
> To change the DNS Servers, go to System > Administration > Networking > Wired connection > Properties:

Under DNS, delete anything you have and add one of these:

208.67.222.222 and 208.67.220.220 or
4.2.2.1 and 4.2.2.2 or 

** You may have to reboot, recheck DNS and try internet.

When I go to the window you indicate above (System > Administration > Networking > Wired connection > Properties), there are the Connection Settings options for Configuration, IP address, Subnet mask, and Gateway address. But there is nothing listed as "DNS". Is one of the items I mentioned the "DNS"? Or if not, then where do I find the DNS, so I can try changing it to what you list above?

I have found a separate tab for "DNS Servers". It is not under "properties", but is a separate tab along with "wired connections". In the "DNS Servers" window, there is nothing listed. Is there supposed to be something there?

---

### Post by Het Irv on 2008-03-07
I think you need to set your proxy setting so that you connect to the Internet though the server that you log in to.  Do you know what IP address that server has?

---

### Post by swarup on 2008-03-07
> **Het Irv said:**
> I think you need to set your proxy setting so that you connect to the Internet though the server that you log in to.  Do you know what IP address that server has?

I was instructed by my server company (VSNL) to set the IP address as 192.168.1.1. But the Ubuntu.in (India) website instructs me to set it as 192.168.1.2. I tried both, and get the same result with either one. Is this the IP address you are inquiring about? Or is it instead the "Gateway address" about which you ask?

Up till now, I have not used the "proxy setting" option. I have only put the IP address etc settings in the "eth0 properties" window. Are you suggesting that I do go to the "proxy" window and set something up there?

Another question: On the previous page, someone suggested me to change the DNS, and suggested several. I could not find the DNS. But now I have found a separate tab for "DNS Servers". It is not under "properties", but is a separate tab along with "wired connections". In the "DNS Servers" window, there is nothing listed. Is there supposed to be something there? Should I type in one of the sequences he suggested there?

---

### Post by Het Irv on 2008-03-07
No, when you login using the username and password that was given to you it will authenticate your session, allowing you to access the Web,  the catch is that your session has to go through that server, the proxy settings will let you do that.  This will also allow you to use Synaptic and Add/Remove.  I am not exactly sure about how PPoE works, but I will do some reading on it so I can give you a better answer.

---

### Post by swarup on 2008-03-07
> **Het Irv said:**
> No, when you login using the username and password that was given to you it will authenticate your session, allowing you to access the Web,  the catch is that your session has to go through that server, the proxy settings will let you do that.  This will also allow you to use Synaptic and Add/Remove.  I am not exactly sure about how PPoE works, but I will do some reading on it so I can give you a better answer.

That is very kind of you, I am very grateful. I am sitting in a very poor part of India (in the state of Bihar), which gets only 2 hours of electricity per day. So I have had to borrow a gas generator to get enough continous electricity to solve the current problem. I am very anxious and eager to solve this, so I can return the generator. Then I can run my laptop and ASDL modem off a truck battery and I'll be fine. But right now until this gets solved, it is very difficult.

Also: On the previous page, someone suggested me to change the DNS, and suggested several. I could not find the "DNS". But now I have found a separate tab for "DNS Servers". It is not under "properties", but is a separate tab along with "wired connections". In the "DNS Servers" window, there is nothing listed. Is there supposed to be something there? Should I type in one of the sequences he suggested there?

---

### Post by Het Irv on 2008-03-07
Just to clarify, you have tried all the different methods in the India Broadband link in the 4th post.  Just skimming, it looked like what you needed.

This is past my knowledge, but I think if you follow the link in the fourth post and talk to some of the people connected to that site, you may be able to get a better answer.

---

### Post by swarup on 2008-03-07
> **Het Irv said:**
> Just to clarify, you have tried all the different methods in the India Broadband link in the 4th post.  Just skimming, it looked like what you needed.

This is past my knowledge, but I think if you follow the link in the fourth post and talk to some of the people connected to that site, you may be able to get a better answer.

Yes, you are right. It seems like it should work. I followed those instructions to the letter-- but the result was as I have described above. It goes online, but only to google. I'll try to connect with some of the people connected to that site, as you suggest. Do let me know if you have any further ideas. :)

---

### Post by kpkeerthi on 2008-03-07
1. No resolv.conf? 
- This means that you do not have DNS server setup in ubuntu. It should exists by default. Did you mess something? That is the reason why ping command did not work for you. It should print something similar to
```

--- www.ubuntuforums.org ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3998ms
rtt min/avg/max/mdev = 181.404/181.983/183.014/0.659 ms

```

2. > I have found a separate tab for "DNS Servers". It is not under "properties", but is a separate tab along with "wired connections". In the "DNS Servers" window, there is nothing listed. Is there supposed to be something there?
(I was typing the help from a windows box at work so I could not give you the exact location to DNS tabs. But glad you figured out.)

Yes. Delete any DNS servers already present there and add the DNS server IPs I provided earlier. Now restart.
And verify that DNS servers you configured still exists in DNS tab. If not add them again and check these out:
[http://ubuntuforums.org/showthread.php?t=581029](http://ubuntuforums.org/showthread.php?t=581029)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/92761](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/92761)

---

### Post by kpkeerthi on 2008-03-07
[quote=kpkeerthi]And verify that DNS servers you configured still exists in DNS tab. If not add them again and check these out:
[http://ubuntuforums.org/showthread.php?t=581029](http://ubuntuforums.org/showthread.php?t=581029)
[https://bugs.launchpad.net/ubuntu/+s...ger/+bug/92761](https://bugs.launchpad.net/ubuntu/+s...ger/+bug/92761)[/quote]

I just figured that if you are using static ip (which I think you are from your other thread) , then the DNS server IPs should stick across reboots.

So all you have to do is add the DNS server IPs to the DNS tabs, reboot and check your connection.

After reboot, check out the file /etc/resolv.conf Your new DNS servers should be listed there.

Good luck.

---

### Post by swarup on 2008-03-08
> **kpkeerthi said:**
> 1. No resolv.conf? 
- This means that you do not have DNS server setup in ubuntu. It should exists by default. Did you mess something? That is the reason why ping command did not work for you. [/code] 

I don't think I did anything. All I've done is install Gutsy. Since then, I've been stuck trying to get this broadband working.

> **kpkeerthi said:**
> 2. 

Yes. Delete any DNS servers already present there and add the DNS server IPs I provided earlier. Now restart.
And verify that DNS servers you configured still exists in DNS tab. 

I did it yesterday, actually. You gave four DNS server IPs, and I added the first two of these yesteday. I then rebooted, and rechecked there in the GUI and the DNS IPs were still there. And I then went to the actual resolv.conf file, and found the DNS IPs to be there as well. 

-- But after all this, the web browser problem remains-- limited to browsing in google. 

I could try adding the other two DNS IPs you gave as well, and see if that helps. Could it be that none of these four DNS IPs are the correct ones for me?

---

### Post by kleo skywalker on 2008-03-08
> **kleo skywalker said:**
> Try these steps:

Go to System-->Administration-->Network. Click on the "Properties" button next to "Wired Connection". Uncheck the "Enable roaming mode" box, set Configuration to "Static IP". Set the IP Address, Subnet Mask, Gateway Address. Back in the "Network Settings" menu, set DNS servers (primary and secondary). If you don't know what to put in these boxes, just call your local VSNL people and ask for them.

In the Terminal (Applications-->Accessories-->Terminal), run this command
```
sudo pppoeconf
```
Don't worry if it doesn't respond encouragingly - that is, tells you it can't find something etc. Just go through the procedure.

Once done, reboot. You should be able to connect to the internet.

Did you try following the above instructions?
In India, MTNL, BSNL and VSNL broadband internet works in pretty much the same way, and I've always been able to get MTNL working by doing this.
You need to call your local VSNL people and ask them the gateway address and the primary and secondary DNS servers (for MTNL, the area Junior Manager can usually provide this information).

Give this way a shot, it might save you all the grief.

---

