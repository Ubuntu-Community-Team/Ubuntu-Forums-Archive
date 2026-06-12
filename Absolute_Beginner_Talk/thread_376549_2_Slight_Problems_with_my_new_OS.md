---
title: "2 Slight Problems with my new OS"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by piratejim on 2007-03-05
Hi there!
I've just recently installed Ubuntu and so far I am pretty happy. After looking through all of your documentation I was even able to get my wireless network to work... I was expecting to have a lot more trouble then I did!
Anyway to my small problem....  (note I am quite new to Linux and the CLI but I am trying to learn!)
I have learned that my DNS information is stored in /etc/resolv.conf However my the file gets modified every few minutes from the nameserver I want to use and nameserver 10.1.1.1 (which is obviously not the right one to use) I therefore keep having to go into the CLI and changing the file (at the moment I am copy and pasting these two commands

 rm /etc/resolv.conf
 cp /home/brad/resolv.conf /etc


Does anyone know why my my resolv.conf file is continuiously overwritten? And what I can do to stop it?

And one other small problem which I am hoping someone could help me with.... Firefox shutsdown/crashes(?) if I visit a page with a lot of information (possibly animations/flash etc, eg [www.apple.com)](www.apple.com)). I can avoid those pages but it is a bit annoying, especially because I am not 100% sure what is causing it.... Has anyone had this problem before?

Thanks!

---

### Post by chewearn on 2007-03-05
> **piratejim said:**
> Does anyone know why my my resolv.conf file is continuiously overwritten? And what I can do to stop it?


Are you using DHCP?  I am guessing it is updating you nameserver?


> And one other small problem which I am hoping someone could help me with.... Firefox shutsdown/crashes(?) if I visit a page with a lot of information (possibly animations/flash etc, eg [www.apple.com)]("http://www.apple.com%29"). I can avoid those pages but it is a bit annoying, especially because I am not 100% sure what is causing it.... Has anyone had this problem before?

Thanks!Nope.  Have not see this problem before.
Are you using the lastest Firefox 2.0.0.2?  
Type about:plugins in the address bar.  Did you see an entry for Shockwave Flash?  What version is it?

---

### Post by piratejim on 2007-03-05
> **AstalaVista said:**
> Are you using DHCP?  I am guessing it is updating you nameserver?


Yes, or at least I think I am...... Is there a way to stop it from updating my nameserver? 

> **AstalaVista said:**
> Nope.  Have not see this problem before.
Are you using the lastest Firefox 2.0.0.2?  
Type about:plugins in the address bar.  Did you see an entry for Shockwave Flash?  What version is it?
I am using Firefox 1.5.0.10 and Shockwave version: Shockwave Flash 9.0 r31

Excuse my newbieness for a moment, how can I update to Firefox 2.0.0.2? I tried searching for it in Synaptic but can't find it....

Thanks!

---

### Post by killaray on 2007-03-05
firefox updates itself.. atleast for me.... if anything go to Help>Check for Updates

---

### Post by chewearn on 2007-03-05
> **piratejim said:**
> Yes, or at least I think I am...... Is there a way to stop it from updating my nameserver? 


One way is to check your router, see if you can remove the IP you don't want, and add the IP you want.  I assumed you are using your router as the DNS.  Else check the machine you are using as DNS.  One more method is to disable DHCP and use static IP.

> 
I am using Firefox 1.5.0.10 and Shockwave version: Shockwave Flash 9.0 r31
I have the same Shockwave Flash version.


> 
Excuse my newbieness for a moment, how can I update to Firefox 2.0.0.2? I tried searching for it in Synaptic but can't find it....

Thanks!Ok, it seems you are using Dapper.  Firefox 2 is not available in Dapper repo.  Here is the installation howto:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by piratejim on 2007-03-06
> **AstalaVista said:**
> One way is to check your router, see if you can remove the IP you don't want, and add the IP you want.  I assumed you are using your router as the DNS.  Else check the machine you are using as DNS.  One more method is to disable DHCP and use static IP.

Ok I think I know what I'm doing (think being the operative word) I have set my router to have the nameserver ip address that I want I have tried all 3 settings for DNS on the router (basically, auto, user defined and disable) and still the resolv.conf is being replaced. I'm afraid that if I disable DHCP I will no longer have access to my router (I only have wireless connection to it no wired at all!). Since I don't really know what DHCP does I hope you can see my hesitation.....

> **AstalaVista said:**
> Ok, it seems you are using Dapper.  Firefox 2 is not available in Dapper repo.  Here is the installation howto:
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

I have done that but still I crash... on the plus side firefox 2 has a feedback function for just this instance so at least that's something.

Thanks for you help so far!

---

### Post by chewearn on 2007-03-06
> **piratejim said:**
> Ok I think I know what I'm doing (think being the operative word) I have set my router to have the nameserver ip address that I want I have tried all 3 settings for DNS on the router (basically, auto, user defined and disable) and still the resolv.conf is being replaced.

Ok, seems like it might not be due to DHCP.  In that case, someone else will have to step in, as I have not knowledge in this area.  Sorry.

> I'm afraid that if I disable DHCP I will no longer have access to my router (I only have wireless connection to it no wired at all!). Well, I use static IP for my network, which consists of two access points, multiple clients, a router and a few PCs.  So,  DHCP is not really required for wireless, if you know how to configure static IPs.  Though, as I said above, DHCP is probably not the cause.

> Since I don't really know what DHCP does I hope you can see my hesitation.....DHCP (Dynamic Host Configuration Protocol) - quote from Wikipedia:
"DHCP is a protocol used by networked computers (*clients*) to obtain IP addresses and other parameters such as the [default gateway]("http://en.wikipedia.org/wiki/Default_gateway"), [subnet mask]("http://en.wikipedia.org/wiki/Subnet_mask"), and IP addresses of [DNS]("http://en.wikipedia.org/wiki/Domain_name_system") servers from a DHCP server. It facilitates access to a network because these settings would otherwise have to be made manually for the client to participate in the network."
 
> I have done that but still I crash... on the plus side firefox 2 has a feedback function for just this instance so at least that's something.Are you running the AMD64 version of ubuntu?  This could be another possibility; I have seen some threads in this forum about people having problem with flash in the 64-bit ubuntu.  If that is so, sorry again, I have no experience to help you.  While I have the AMD64 CPU, I have installed the 32-bit ubuntu version as it appeared to have less problems.  My first attempt to install ubuntu 64-bit a while back ended with multiple unresolved failures.:( 

> Thanks for you help so far!No problemo. :)

---

