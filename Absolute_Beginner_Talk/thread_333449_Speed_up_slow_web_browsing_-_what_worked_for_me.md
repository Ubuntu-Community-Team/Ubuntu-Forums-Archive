---
title: "Speed up slow web browsing - what worked for me"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by Old Jimma on 2007-01-07
Ubuntuers:

Up to November 2006, I struggled with slow web browsing with Dapper. From reading the threads on Ubuntu forums, it seems that alot of people went back to the Death Star (Microsoft) from Ubuntu because they could not resolve this problem. 

**Here is what worked for me and what didn't seem to make any difference for me.**

1. Didn't make much of a difference: there is alot of discussion on speeding up Firefox by disabling ipv6. I found that following all of the prescriptions for disabling ipv6 did not make any difference in increasing web browsisng speed. Please see the entire discussion at [[COLOR="Sienna"]http://ubuntuforums.org/showthread.php?t=87798[/COLOR]]("http://ubuntuforums.org/showthread.php?t=87798"). That thread seems to confirm that disabling ipv6 doesn't do anything.

2. Didn't make much of a difference: I have DHCP and changed to static IP. I liked the idea... the discussion of how I did it is listed at: [[COLOR="Sienna"]http://www.ubuntuforums.org/showthread.php?t=309548[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=309548"). I thank bodh-zazen for being patient with me and providing advice for this.

3. **[B]HERE IS WHAT REALLY INCREASE WEB BROWSING SPEED FOR ME: **[/B]changing to OpenDNS. I edited the DNS settings on my router to be 
  208.67.222.222
   208.67.220.220
and then saved the router configuration. Then I edited my /etc/resolv.conf file as follows:
cp /etc/resolv.conf /etc/resolv.conf.bak
then using 
sudo gedit /etc/resolv.conf
I changed the file to look like this:
nameserver 208.67.222.222
nameserver 208.67.220.220

Check out [[COLOR="Sienna"]http://www.opendns.com/start/unix.php[/COLOR]]("http://www.opendns.com/start/unix.php") for further advice on the OpenDNS web page.

[B]
PLEASE NOTE:[/B] This worked perfectly for my i386 P4 ubuntu machine. Web browsing really became [COLOR="Red"]VERY FAST[/COLOR]. However, for my AMD64 machine editing the /etc/resolv.conf file was unnecessary. 64 bit ubuntu seems to pick up the new DNS settings automatically without manually editing the /etc/resolv.conf file. In fact, my 64 bit ubuntu machine would not open web pages after editing /etc/resolv.conf .... so if you have a 64 bit ubuntu machine, leave the /etc/resolv.conf file alone.... just change the DNS settings on your router.

I realize that there are many folks out there that don't like OpenDNS. There are some good reasons for their opinions. However, if you are in the position having dog-slow web browsing, using OpenDNS is a solution until you can find a local public DNS server to use.

I hope this helps somebody, I thank Bodi-zazen on the ubuntu-forums and Bjorn Gustofsson in the Atlanta Linux Enthusiasts club for their help and advice.

That is what worked for me and what didn't seem to make any difference for me.I must say that since using OpenDNS, I've switched to a local public DNS nameserver. Contact your local Linux club to find out where they are!!

If I have made errors in my advice, I hope that folks will please make corrections. I feel this is a very important problem for some people who are just getting started with Ubuntu.


All the best,
Phil Smith
Duluth, GA

---

### Post by kool4cats on 2007-02-01
Excellent. I've been wondering how to fix this since I installed Ubuntu 4 weeks ago.

Now super-fast. Thanks :D

---

### Post by BulletzBill on 2007-02-22
Sorry to ressurect such an old thread, but I recently tried this fix to alleviate the browsing problems I was having, and it has worked great, however, it seems that after adding the new DNS servers to my resolv.conf file, it is being automatically changed to include the old IPs after a short period of time. I do not even need to reboot for it to happen. Here's a before and after of what the file looks like:

The original file:
> search Belkin
nameserver 192.168.2.1
nameserver 24.29.103.10
nameserver 24.29.103.11

After editing it to use the OpenDNS servers:
> nameserver 208.67.220.220
nameserver 208.67.222.222

After a short period it automatically changes to this and web browsing is slooow again:
> search Belkin
nameserver 192.168.2.1
nameserver 24.29.103.10
nameserver 208.67.222.222

Anyone know why it would be doing this, and how I can prevent it from happening? (FYI I am a Linux newbie :))

---

### Post by Patrick K on 2007-02-22
Take a look here:
[http://www.opendns.com/start/ubuntu.php](http://www.opendns.com/start/ubuntu.php)
I don't know if you followed these direction or not. They look a little different than the page posted above. I've not tried this fix, so can't comment on it.

---

### Post by BulletzBill on 2007-02-23
awesome, seems to be exactly what I need, I will try it now. Thanks :)

---

### Post by Mykatik on 2007-03-03
Excellent tip! Many thanks, that has really improved the situation for me!

---

### Post by rada on 2007-03-03
!!Oh my my... edgy amd64 with firefox64 and attansic atl1 is flying now.... THANK YOU!

It was obvious the delay that had me :mad:   was in DNS resolution... downloads were fast, but couldn't work out why.

---

