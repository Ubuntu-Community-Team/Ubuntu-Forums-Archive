---
title: "How Secure is UBUNTU???!"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by Hellofriends on 2007-07-14
I recently installed Firestarter and saw that a lot of connections were trying to be made to
my computer! Someone even try to use SSH! So I was wondering, how likely is it with or without
something like Firestarter that Ubuntu is secure from attacks?

---

### Post by UltimaDude on 2007-07-14
Ubuntu is secure, You could remove Firestarter though and it would probably fix the problem.

Ubuntu is secure, Many bugs are reported during version beta releases etc.

Please reply if you still have the problem after Firestarter.

---

### Post by insane_alien on 2007-07-14
well, its blocking them isn't it. the firewall is iptables. the GUI is firestarter. iptables was doing its job before you installed firestarter and it'll continue doing its job if you remove it.

of course, there is no easy way to remain connected and be secure from the most advanced crackers out there. but they won't be interested in some averaje joes computer. iptables will eep out the idiots and script kiddies that will bother trying to access your computer.

ubuntu is secure. 

even if they get in they'll likely not be able to do much. they'd need the root password for that.

---

### Post by Wim Sturkenboom on 2007-07-14
[A recent thread](http://ubuntuforums.org/showthread.php?t=497979)

[shields up](https://www.grc.com/x/ne.dll?bh0bkyd2)
click proceed in middle of page
click all service ports
preferably you want to see green blocks only showing that your PC is non existing; that is the situation with firestarter
blue is also fine as they don't accept requests; you will see a lot of them if you stop firestarter
you don't want to see red blocks

---

### Post by PriceChild on 2007-07-14
Ubuntu ships with _NO_ open ports by default.

This means that it is basically impossible for someone to gain remote access unless you start installing things like openssh-server etc. without understanding the full implications of your actions.

Pricey

---

### Post by Hendrixski on 2007-07-14
> **UltimaDude said:**
> You could remove Firestarter though and it would probably fix the problem.
.

ummm... firestarter is not the firewall, it's just a GUI for managing the firewall.. Linux has one built in at the Kernel level.  Why is that good? Because if you block someone at a high level then they can just dig a little lower and break your system.  but the kernel is the lowest level.

So tell them good luck breaking into your machine, you have a firewall that they can't dig under, or climb over.  :-)

---

### Post by nelamvr6 on 2007-07-14
> **Wim Sturkenboom said:**
> [A recent thread](http://ubuntuforums.org/showthread.php?t=497979)

[shields up](https://www.grc.com/x/ne.dll?bh0bkyd2)
click proceed in middle of page
click all service ports
preferably you want to see green blocks only showing that your PC is non existing; that is the situation with firestarter
blue is also fine as they don't accept requests; you will see a lot of them if you stop firestarter
you don't want to see red blocks

I did find out that my system is responding to pings.  Is there any way to stop this, or at least modify this behavior?

When I run the same test on my window$ box I don't receive this warning.

TIA

---

### Post by earobinson on 2007-07-14
Ill make you a deal, Ill answer this question when you tell me how secure windows is? This is something really really hard to measure and a completely fair metric will never be found.

---

### Post by xpod on 2007-07-14
> I did find out that my system is responding to pings. Is there any way to stop this, or at least modify this behavior?

You can use the ICMP filtering in firestarters preferences

EDIToops

---

### Post by Nussbaum on 2007-07-14
> **insane_alien said:**
> well, its blocking them isn't it. the firewall is iptables. the GUI is firestarter. iptables was doing its job before you installed firestarter and it'll continue doing its job if you remove it.

of course, there is no easy way to remain connected and be secure from the most advanced crackers out there. but they won't be interested in some averaje joes computer. iptables will eep out the idiots and script kiddies that will bother trying to access your computer.

ubuntu is secure. 

even if they get in they'll likely not be able to do much. they'd need the root password for that.

Afaik without firestarter daemon running iptables won't have any entries (unless you set them manually), so then it could just as well run not at all. (its not just a gui)

---

### Post by Malibu Illusion on 2007-07-14
There is absolutely no reason to block ICMP ping requests.

---

### Post by jrlii on 2007-07-14
As I understand it, there are a few Linux-specific viruses & worms. Most are not particularly virulent, 'cause they can't get root privileges, but. . .

Sometimes I wonder about how many of the malware definitions F-prot checks for are ones which could even possibly run on Ubuntu.

F-prot is a proprietary antivirus product which is available for free for home Linux workstations. (As well as paid versions for Windows.)

The user interface for the Linux workstation edition is nearly identical to the interface for the DOS version back in the'80s when floppy disks were the usual medium of transmission, and 1200 bps modems were really fast. . .

In Windows, security was an afterthought. In Linux security was built in from the get-go, as has been the case with all the multi-user OSes I'm aware of. Unfortunately multiple users were an afterthought for Windows too. . .

---

### Post by nelamvr6 on 2007-07-14
> **xpod said:**
> You can use the ICMP filtering in firestarters preferences

EDIToops

How is this done?  I checked "Enable ICMP Filtering" and nothing is being allowed, but I still get a "Failed" grade because I'm responding to pings.

Is there something else I have to do?

---

### Post by macogw on 2007-07-14
> **jrlii said:**
> As I understand it, there are a few Linux-specific viruses & worms. Most are not particularly virulent, 'cause they can't get root privileges, but. . .

Yeah, if you're still using software versions from 1997.  They've been patched out of existence, mostly.  There's one in the wild.  I think it's the one that has an uninstaller built in. 

And by default iptables shows no rules because nothing is listening on any ports as Pricey said.  Removing Firestarter won't erase whatever iptables rules you set with it.  Iptables is ALWAYS RUNNING though...well, as long as Linux is running, so if the computer's off, the firewall's off, but then you don't need one anyway

---

### Post by Nussbaum on 2007-07-14
> **macogw said:**
> 
And by default iptables shows no rules because nothing is listening on any ports as Pricey said.  Removing Firestarter won't erase whatever iptables rules you set with it.  Iptables is ALWAYS RUNNING though...well, as long as Linux is running, so if the computer's off, the firewall's off, but then you don't need one anyway

When I had a fresh install of Ubuntu whenver I started the computer and not manually start the firestarter gui, the firestarter daemon didnt load and the entries in iptables remained empty. Furthermore if the firestarter program is removed entirely their is no firestarter daemon to begin with so iptables will be empty unless you've set it yourself manually.If I do 'sudo /etc/init.d/firestarter stop' now, followed by 'sudo iptables -L', I have no entries, so even if iptables is running it doesnt block anything.

Also you don't have a firewall just to prevent unwanted incoming but also outgoing traffic.

---

### Post by ityro on 2007-07-14
Hello All,

I ran the GRC Shieldsup! and it found two ports open: 1) port 22 ssh remote login protocol and 2) port 443 https http protocol over tls/ssl.  All other ports were blue. No green.

Can someone tell me how to close the two ports?  Did I understand correctly that I could just remove Firestarter? If so how?  Remove it with the Package Manager or just stop it?

I am running Feisty on a dual boot (XP) HP/Compaq 9010 notebook.

Thanks for your time.

---

### Post by iAlta on 2007-07-14
Are you using a router ?

it should block most of the background noise...

---

### Post by MRiGnS on 2007-07-14
> **Nussbaum said:**
> When I had a fresh install of Ubuntu whenver I started the computer and not manually start the firestarter gui, the firestarter daemon didnt load and the entries in iptables remained empty. Furthermore if the firestarter program is removed entirely their is no firestarter daemon to begin with so iptables will be empty unless you've set it yourself manually.If I do 'sudo /etc/init.d/firestarter stop' now, followed by 'sudo iptables -L', I have no entries, so even if iptables is running it doesnt block anything.

Also you don't have a firewall just to prevent unwanted incoming but also outgoing traffic.

the ports are simply not open by default. you will have to open them with iptables. it's not the other way around.

---

### Post by p_quarles on 2007-07-14
> **MRiGnS said:**
> the ports are simply not open by default. you will have to open them with iptables. it's not the other way around.
Exactly. I really think we need a sticky post in this forum which points this out:

No IPtables rules = no outside access whatsoever. 

The reason for this is that those ports are not providing any services. So, even if Evil Hacker sends a request for a certain connection, your OS doesn't even notice it. If Evil Hacker is really good, then sure, he/she can break in. But IPtables rules woudn't really help you in that situation anyway.

---

### Post by ityro on 2007-07-14
Thanks for the response. to iAlta, no I do not have a router and I use a CATV connection to the internet.

MRiGnS, I'm lost but it looks like you are telling me not to stop Firestarter. So, case closed on that idea. But I still don't know how to close ports 22 and 443. Is it done using Preferences in Firestarter?

Thanks for your time!

---

### Post by MRiGnS on 2007-07-14
> **ityro said:**
> Thanks for the response. to iAlta, no I do not have a router and I use a CATV connection to the internet.

MRiGnS, I'm lost but it looks like you are telling me not to stop Firestarter. So, case closed on that idea. But I still don't know how to close ports 22 and 443. Is it done using Preferences in Firestarter?

Thanks for your time!

they should not be open by default but if you want to set up a rule type:


```
sudo iptables -A INPUT -p tcp --destination-port 22 -j REJECT
```

```
sudo iptables -A INPUT -p tcp --destination-port 443 -j REJECT
```

---

### Post by ityro on 2007-07-14
MRiGnS,  I can't thank you enough. I don't understand how the firewall tables and Firestarter work but, you have given me a tool to start learning. It appears the instructions you gave me will put the tables back to default and Firestarter should pick up the ball and keep it straight. I will stop Firestarter, perform the two changes and then start Firestarter.  Then I will use ShieldsUp to monitor the changes.

Thanks Again.

---

### Post by ramjet_1953 on 2007-07-14
Basically, Ubuntu is as secure as you are.

If you leave iptables alone and don't run applications in root mode on your desktop while connected to the Internet, you will not have any problems.

The only reason you should need to run Firestarter would be to set-up port forwarding for a particular application.

Otherwise, don't try to fix something that isn't broken.

Regards,
Roger :cool:

---

### Post by Nekiruhs on 2007-07-14
> **Nussbaum said:**
> Afaik without firestarter daemon running iptables won't have any entries (unless you set them manually), so then it could just as well run not at all. (its not just a gui)
It is. just a GUI. If you install it, configure IpTables with it, then remove it. IpTables functions as normal.

---

### Post by ityro on 2007-07-14
Roger that!  Message received 5X5.  I will stop Firetsarter, type the two commands and NOT start Firestarter.
If ShieldsUp says all is OK  I will leave it alone but check it once in awhile.

Thanks again to all. I really had no idea what to do.

---

### Post by Hellofriends on 2007-07-15
Thanks for all the information! Much appreciated and good to know!

---

