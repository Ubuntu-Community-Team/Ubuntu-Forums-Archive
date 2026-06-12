---
title: "Firestarter help"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2008-03-05
How do setup firestarter so that it exempts ktorrent from the firewalling? Is there a simple way like I remember there was with Zone Alarm on Windows? The reason I want to exempt Ktorrent is that I believe that it is limiting my speeds. I get dozens of "hits" in only a couple of minutes that are either TCP and UDP.

---

### Post by the.phantom on 2008-03-05
this is not a "program firewall"( like on windows that uses a lot of resources)
deals with addresses and such 
on the hits, are they the same ip address?
you can use "policy" and wire a rule to block

---

### Post by intense.ego on 2008-03-05
all the hits are from different ip addresses. i want to be able to let them through

---

### Post by intense.ego on 2008-03-06
bump. anyone?

---

### Post by hyper_ch on 2008-03-06
by default the firewall installed (iptables) does not block ktorrent at all....

however in ktorrent go to the plugins and enable UPnP.

---

### Post by Archmage on 2008-03-06
For incoming ports you need to open the port in Firestartet.

Simply add the port to the Firststarter rule.

---

### Post by hyper_ch on 2008-03-06
Archmage:

No ports need to be opened as no ports are closed by default.

---

### Post by intense.ego on 2008-03-06
I checked and it turns out UPnP is already enabled, yet I still get the triangle with the exclamation mark in the bottom left corner. I tried rescanning, but nothing happened. Could it be that the wrong ports are being forwarded?

---

### Post by hyper_ch on 2008-03-06
then it's your router that is not UPnP enabled

---

### Post by intense.ego on 2008-03-06
I will try playing around with it and see what happens. Just curious, if it is a router problem, why would it show up in Firestarter?

---

### Post by hyper_ch on 2008-03-07
what does show up in firestarter?

---

### Post by Archmage on 2008-03-07
> **hyper_ch said:**
> Archmage:

No ports need to be opened as no ports are closed by default.

If we are taliking about Firestarter: This is a firewall that CLOSE all incomming ports. To use ktorrent effectivly you need to open some ports.

---

### Post by hyper_ch on 2008-03-07
Archmage

(1) Firestarter is no firewall

(2) The firewall is called iptables

(3) By default iptables has no closed ports at all - as there are no services listening to it

---

### Post by Archmage on 2008-03-07
> **hyper_ch said:**
> Archmage

(1) Firestarter is no firewall

(2) The firewall is called iptables

(3) By default iptables has no closed ports at all - as there are no services listening to it

When you install Firestarter it will automatical close all ports. Therefore you either need to uninstall firestarter or to open the ports in Firestarter.

---

### Post by hyper_ch on 2008-03-07
If that is really true, that upon installation of firestarter the ports get closed, I doubt that the will be opened again when you remove it.

---

### Post by crjackson on 2008-03-07
> **hyper_ch said:**
> If that is really true, that upon installation of firestarter the ports get closed, I doubt that the will be opened again when you remove it.

You are correct.  Uninstalling Firestarter won't reopen the ports to the previous state as before.  They now need to be reconfigured.  Firestarter is a configuration tool for ip tables.  If the port he needs is closed, he can simply add it to the incoming rules using the firestarter interface.

Installing Firestarter on my system didn't bolck the default bit-torrent tool on this machine.  I have tried my others.

---

### Post by tad1073 on 2008-03-07
[http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers](http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)
[http://www.howtoforge.com/linux_iptables_sarge](http://www.howtoforge.com/linux_iptables_sarge)
Firestarter hase two rules when first installed, which are to allow traffic for port 80 all other ports are closed which is why you need to add services/ports for email, networking, torrents, etc. If you choose to uninstall firestarter it will sudo iptables -F to remove all the rules set by the user and the inteface, but you still need to sudo iptables -L then sudo iptables -F from the terminal to make sure all rules have been flushed.

---

### Post by intense.ego on 2008-03-07
Wait, so firestarter is **NOT** a firewall? Can someone recommend me a good firewall, then? 

If I decide to stick with firestarter, all I have to do is go to Firestarter and then to Policy and then add the port number I want unblocked into the space where it says, "IP, host, or network"?

---

### Post by bodhi.zazen on 2008-03-07
> **intense.ego said:**
> Wait, so firestarter is **NOT** a firewall? Can someone recommend me a good firewall, then? 

If I decide to stick with firestarter, all I have to do is go to Firestarter and then to Policy and then add the port number I want unblocked into the space where it says, "IP, host, or network"?

The firewall in Linux is now called iptables. You can manually configure it if you learn the terminology or you can use any number of gui front ends. The gui front ends configure iptables.

There are a number of on ling guides , of varying length :

[http://www.google.com/search?q=how+to+iptables&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=how+to+iptables&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

Or this thread :

[http://ubuntuforums.org/showthread.php?&t=159661](http://ubuntuforums.org/showthread.php?&t=159661)

===================

For information on how to use firestarter :

Guide: [http://doc.gwos.org/index.php/Firestarter_Guide](http://doc.gwos.org/index.php/Firestarter_Guide)

	wiki: [https://help.ubuntu.com/community/Firestarter](https://help.ubuntu.com/community/Firestarter)

===================

If you would like to try another, I suggest guard dog.

[http://www.simonzone.com/software/guarddog/](http://www.simonzone.com/software/guarddog/)

	[http://www.tuxmagazine.com/node/1000267](http://www.tuxmagazine.com/node/1000267)

---

### Post by R@inm@n on 2008-03-07
I run KTorrent  with Firestarter.

My understanding of it is limited, but this is what i've got so far.

Firestarter is a front - end for your IP tables. 

IP tables are ports and addresses on the 'net you want to block or allow.

Firestarter can br programmed to block or allow specific ports on your computer.

I installed Firestarter and KTorrent works fine with it. KTorrent is the fastest torrent downloader I have tried.

It works very well with 'buntu, as long as you don't let it "grow" or become larger and take over your desktop :(

As far as configuring Firestarter goes....

 I simply ticked [in Preferences] "Enable ICMP Filtering"  "Enable ToS Filtering"

Under advanced Firewall Options I have packet Rejection set to "Drop Silently" and "Block broadcasts from external network" ticked. 

  I start Firestarter, check to see that all is ok and nothing has changed, then turn it off...exit from it.

I run KTorrent and my download speeds are excellent, usually...but that depends on how you have KTorrent set up, too.

 It also depends on what you are trying to 'down, whether there are a lot of Peers and Seeders.

Firestarter is only the front end, or GUI for the IP Tables that control your ports. You don't need to have it running all the time, Once you set it up, let the IP tables take care of the port access.

KTorrent runs fast and well once you configure it. The Firestarter doesn't seem to limit my speeds at all.



    R.

---

### Post by intense.ego on 2008-03-07
> **R@inm@n said:**
> I run KTorrent  with Firestarter.

My understanding of it is limited, but this is what i've got so far.

Firestarter is a front - end for your IP tables. 

IP tables are ports and addresses on the 'net you want to block or allow.

Firestarter can br programmed to block or allow specific ports on your computer.

I installed Firestarter and KTorrent works fine with it. KTorrent is the fastest torrent downloader I have tried.

It works very well with 'buntu, as long as you don't let it "grow" or become larger and take over your desktop :(

As far as configuring Firestarter goes....

 I simply ticked [in Preferences] "Enable ICMP Filtering"  "Enable ToS Filtering"

Under advanced Firewall Options I have packet Rejection set to "Drop Silently" and "Block broadcasts from external network" ticked. 

  I start Firestarter, check to see that all is ok and nothing has changed, then turn it off...exit from it.

I run KTorrent and my download speeds are excellent, usually...but that depends on how you have KTorrent set up, too.

 It also depends on what you are trying to 'down, whether there are a lot of Peers and Seeders.

Firestarter is only the front end, or GUI for the IP Tables that control your ports. You don't need to have it running all the time, Once you set it up, let the IP tables take care of the port access.

KTorrent runs fast and well once you configure it. The Firestarter doesn't seem to limit my speeds at all.



    R.

Sorry for being such a noob, but where are these "Preferences" or "Firewall" menus? In my Ktorrent (3.5.8), I cannot find them. Or are you talking about something else?

---

### Post by intense.ego on 2008-03-08
bump. anyone?

---

### Post by Mud.Knee.Havoc on 2008-03-08
He was referring to the menus in Firestarter.

It's actually very easy.  You've got a torrent program and firestarter installed.  Go into the torrent program and pick a good port for it to use (don't use the default - try something high like 40000).  Open up firestarter and create/apply a rule that allows traffic on port 40000 or whatever you pick.  That's it. :D  

Some people get confused because they think that firestarter is like Zone Alarm.  If you close Zone Alarm, you have no firewall running.  When you close firestarter, you have only closed the configuration gui (which is called firestarter).

EDIT: If you're running your computer behind a hardware firewall (like a router), you'll need to go in and forward the proper port (in this case 40000) to your computer (192.168.1.1 or whatever).  If you need help with this, go to portforward.com (it has instructions for hundreds of routers).

---

### Post by hyper_ch on 2008-03-09
don't install firestarter and you won't have a problem at all...

---

### Post by Mud.Knee.Havoc on 2008-03-09
If he's behind a hardware firewall already, I'd agree with that.  If not, firestarter is probably the easiest way I've seen to manage a firewall.

---

### Post by intense.ego on 2008-03-09
When I go to firestarter and click on add rule, do i put the port number in the area that says "IP host or network"?

---

### Post by bodhi.zazen on 2008-03-09
Start firestarter

go to the "Policy" tab

Right click in the "Allow service" window -> "Add rule"

A dialog comes up asking for service and port ...

Select one of the default services or add your own, change the default port if needed.

Allow anyone or by IP 

click the "Add button"

---

### Post by hyper_ch on 2008-03-10
> **Mud.Knee.Havoc said:**
> If he's behind a hardware firewall already, I'd agree with that.  If not, firestarter is probably the easiest way I've seen to manage a firewall.

If no services are running a firewall is pointless...

---

