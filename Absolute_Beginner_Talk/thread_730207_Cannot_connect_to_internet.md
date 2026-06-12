---
title: "Cannot connect to internet"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by DinosaurKnight on 2008-03-20
Hi folks, I'm brand-new to Ubuntu, but I've experimented a bit with other Linux distros in the past, so I'm not completely clueless.  Just mostly clueless.

I just installed Gutsy today on an Averatec 3250 laptop, and so far I like what I see...  But I can't connect to the internet.  Neither wired nor wireless connections work, though I'm only worried about wired for now.  I'll work on wireless later.

It had no trouble auto-detecting and connecting to the internet during installation, and it can see my local network, so I now my ethernet port is working, but no internet.  Also, I have several other computers in the house, all of which work just fine, so it's not a problem with the router or DSL modem.  It successfully auto-detected the correct DNS settings, which I've double-checked, and they're the same as on my other computers.  Still no go.

After browsing the forums a bit, I found that ipv6 is a common culprit, so I disabled it.  Still no go.

Any other ideas?  Browsing the forums hasn't given me any more hints.

Thanks in advance.

---

### Post by fela on 2008-03-20
maybe you have an obscure network card and don't have a driver for it.you could try googling your network card for linux drivers.

although having wired network not working 'out-of-the-box' is pretty damn rare these days. I think your best bet is just googling your network card and see if anyone else has had your problem. keep me posted :guitar:

---

### Post by disk11 on 2008-04-03
[http://ubuntuforums.org/showpost.php?p=3752219&postcount=3](http://ubuntuforums.org/showpost.php?p=3752219&postcount=3)

This'll get the wired working, wireless seems to be another story.

And to get wireless working:> reinstall NetworkManager and then go in to "/etc/network/interfaces" and see if your wireless card is manually configured at all (mine is ra0). If so, comment out those lines and restart network manager. This is what finally got wireless working. The "problem" is that the drivers for the rt25xx drivers are part of the kernel now and are able to work with network manager - so a lot of the old hacks won't work anymore.

---

### Post by nsrao2k on 2008-04-03
I am facing the same problem of not getting connected to the network - wired & wireless.

Am using Averatec 3200 laptop and its not that am installing this for the first time. I was so excited about an year back that I erased by working laptop for Ubuntu. Network was working great.

I have to switch back to Windows for few important applications, that I cannot use on Ubuntu at that time.

Now, I got 7.10 version and network is completely dead. 

The icon on desktop shows - connected wired network connection, and firefox cannot to internet at all.

Tried Ifconfig, and it shows me 

eth0, eth0:avah

Only eth0:avah has ip address - 169.254.5.48 with BCast as 169.254.255.255 and mask as 255.255.0.0

This is the same IP address I received at home and work - and neither of the domain ip start from 169.*

Definitely, its not my hardware - as earlier version of Ubuntu was working great on my m/c. 

Any suggestions how to solve the issue of getting connected to network. 

Thanks in advance
Srinivas

---

### Post by nsrao2k on 2008-04-03
I got this working from this post

[http://ubuntuforums.org/showpost.php?p=3752219&postcount=3](http://ubuntuforums.org/showpost.php?p=3752219&postcount=3)

Thanks Guys.

Wireless is still an issue. Any Help

Rgds,
Srinivas

---

### Post by bumanie on 2008-04-03
This is a fix that sometimes and sometimes doesn't. The good news is that by trying it, you can't hurt your system, because it can be reversed.
Open firefox. In the address bar type 
about:config --> enter. In the filter type 
ipv6 --> enter
Right click on the text that appears and then left click on toggle to change the value to true. You should now connect.
If you still can't connect, ipv6 is not a problem for you and you can go back through the steps and toggle the value back to false.

---

### Post by disk11 on 2008-04-03
> **nsrao2k said:**
> I got this working from this post

[http://ubuntuforums.org/showpost.php?p=3752219&postcount=3](http://ubuntuforums.org/showpost.php?p=3752219&postcount=3)

Thanks Guys.

Wireless is still an issue. Any Help

Rgds,
Srinivas

Look back at my first post, I added a fix for the wireless.

---

### Post by nsrao2k on 2008-04-03
thanks guys, for a quick response.

Will check this once, I am at home. Cannot acess cerficate based WIFi - requires IE to do the job

Rgds,
Srinivas

---

### Post by freund on 2008-04-30
I had to pass the kernel option acpi=noirq to make the network cards to work. That is I edited the file menu.lst file in the /boot/grub directory

kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=82d409b96e141d62b ro [COLOR="Red"]**acpi=noirq**[/COLOR] quiet splash

then rebooted and everything should work then.

---

