---
title: "Test SSH in local network as if not in local network"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by Enalia on 2006-11-03
Well, I installed Ubuntu 6.10 (first linux distro ever!) all on my own 3 days ago. I absolutely love it! It comes with everything I already use on windows: openoffice, firefox, etc.  I can go on and on about how much I love this OS...  But the main reason I decided to take the plunge into linux was because I was looking forward to using SSH.

I think I've got ssh-server installed... I ran

sudo apt-get install ssh-server

When I get on the windows machine in my home lan, I can use PuTTY to connect to the machine, just fine.  But, when I try connecting from a computer outside of my network, I can't connect at all.

Several questions, I suppose.

1) How can I connect to my machine outside of my home lan

2) Is there a way to test ssh as if I were not in my local network, even though I am? (it's kind of annoying asking my friends to "try it now") Although that's probably not a linux question...

thanks for taking the time to answer!

---

### Post by LotsOfPhil on 2006-11-03
1) Are your computers all hooked up to a router? If so you need to make sure that you are doing the portforwarding correctly. Port 22 needs to be forwarded to the computer you want to SSH into. How to do this will depend on your router.

2) You can SSH into an outside machine and then SSH back in. Something like:
enalia@home$ ssh computer-at-work
enalia@computer-at-work$ ssh home

---

### Post by llamakc on 2006-11-03
If you're using a router, you'll need to use port-forwarding on the router so that connections from OUTSIDE get through to the IP of the server. 

What is your network setup?

---

### Post by Kurt` on 2006-11-03
> **Enalia said:**
> 2) Is there a way to test ssh as if I were not in my local network, even though I am? (it's kind of annoying asking my friends to "try it now") Although that's probably not a linux question...
From a terminal, type: ssh yourusername@localhost

---

### Post by Enalia on 2006-11-03
wow, didn't expect this forum to move so quickly!!

My network setup is...

I've got a linksys wireless router hooked up to my windowsXP machine which is then hooked up to my dsl router.  I've also got my ubuntu desktop, and a windows98 machine hooked up to the linksys router.

I hope that's what was meant by "what's my setup"

I'm not quite sure how to do port forward, could I maybe get some help? Or at least point me in the right direction.


(I just realized how misleading the title of this post is. haha!)

---

### Post by dbott67 on 2006-11-03
Login to your Linksys router (typically 192.168.1.1 or similar) and look for a section on "[port forwarding]("http://www.dpalmi.com/Linksys%20Emulator/Forwarding.htm")".  In this area, you will need to forward port 22 (TCP) to the IP address of your home computer.

A few caveats:

1. You'll need to set your home computer IP address to 'static' (or 'static DHCP' --- basically reserves the same address for your computer).

2. You'll need to know your external IP address of your router (normally provided automatically by your ISP).  There are free '[Dynamic DNS]("http://www.dyndns.com/services/dns/dyndns/")' services that allow you to assign a name to your IP address so that you don't have to worry about ever-changing external IP addresses.

3. Then, in your router go to the [DDNS setting]("http://www.dpalmi.com/Linksys%20Emulator/DDNS.htm") and enter your DynDNS hostname.

4. After that, you can SSH into your computer from anywhere by SSHing to enalia.dyndns.org (or whatever hostname / domain name you've selected at the DynDNS site.

I have a setup very similar to this and have full access from anywhere via my dynamic DNS account.

-Dave

---

### Post by steve.horsley on 2006-11-03
And make sure you hvae a good password. There are bots out there that spend all day every day looking for boxes that accept SSH, and then spend all day every day guessing usenames and passwords. If you are going to leave SSH open, it is worth looking into using the files hosts.allow and hosts.deny to limit which IP addresses can connect to your box.

---

