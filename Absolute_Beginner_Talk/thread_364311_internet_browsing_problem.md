---
title: "internet browsing problem"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by tim1970 on 2007-02-18
I am having problems with Firefox.  I am able to browse most sites, but there are a few that I can't get to.  For instance [www.downloads.com](www.downloads.com).  I can get to it just fine with my windows machine, but everytime I try with my ubuntu machine, I get the generic problem loading page error.  Also, I tried to download some drivers, and then some desktop themes from gnome-look.org, and when I try to download with my ubuntu machine, I get site not found, but I am able to download just fine from my windows machine.

Any ideas why I would be able to get to some websites, and download files from some places but not all places?

Thanks

---

### Post by Spike-X on 2007-02-18
No idea, sorry. That link works fine for me.

---

### Post by jonathan.lees on 2007-02-18
Try pointing Firefox to Gnome-looks' IP address:  [http://80.190.240.90/](http://80.190.240.90/) if it works, you shoudl check your dns configuration, maybe compare it with XP's.

---

### Post by tim1970 on 2007-02-18
I am not sure what I am checking in my DNS configuration.  My windows machine has everything set to automatically detect.

My configuration is that I am hard-wired to a router (same as my windows machine).  I am not able to get to about 1/4 of the web-sites I normally visit from m windows machine.  I have the two machines side-by-side and I can get there from windows, so I know it is not a problem with the web site.  I have a belkin router if that makes a difference.

any instructions on setup would be greatly appreciated.

Thanks

---

### Post by bulldog on 2007-02-18
Do you have the flash-player installed?

---

### Post by tim1970 on 2007-02-18
I do not believe I have flash player installed.  Can this make a difference even getting to the website?

Also here is some more info.  My isp requires a static IP address.  This is all set up correctly on my router.  My windows machine then is set to obtain everything automatically.

Something is working, because I am able to see some of the websites I visit with my ubuntu machine.

Here is the output from ifconfg if that helps..

eth0      Link encap:Ethernet  HWaddr 00:B0:D0:C9:24:F0  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2b0:d0ff:fec9:24f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25613 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17632 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27328717 (26.0 MiB)  TX bytes:2058632 (1.9 MiB)
          Interrupt:5 Base address:0x6c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13728 (13.4 KiB)  TX bytes:13728 (13.4 KiB)

---

### Post by bulldog on 2007-02-18
If you have the possibillity to use the DHCP option in your router,use DHCP in ubuntu too.
So everything should be the same as in windows.

If you don't have the flash-player plugin,it's possible you cant access site's with alot of flash within.
Search in synaptic for the flashplugin-nonfree and install it.

---

### Post by paydaydaddy on 2007-02-18
I had a similar problem and it turned out to be a setting related to Ipv6. I will do a search and see if I can find the thread that provided my solution and post a link to it here. Feel free to search yourself in the meantime. I will warn you that you will find a lot of info about Ipv6, but there is one very simple and effective way to disable it in the firefox config options. I will look for the link.

---

### Post by tim1970 on 2007-02-18
I installed Flash.  That did not help.  I tried to do a traceroute on a couple of the sites that I could not get to.  [www.downloads.com](www.downloads.com) and [www.dfw.com](www.dfw.com) (Fort Worth Star Telegram)

I got a message saying address could not be found.  When I tried to enter just the ip address in my browser, I got the message invalid url.

---

### Post by paydaydaddy on 2007-02-18
It worked for me in 6.06LTS. Try this: 

Additional: Disabling ipv6 in Firefox

   1. Type about:config in your address entry bar (in firefox)
   2. Type "ipv6" in the filter
   3. Change the value of "network.dns.disableIPv6" to true

---

### Post by tim1970 on 2007-02-18
> **paydaydaddy said:**
> It worked for me in 6.06LTS. Try this: 

Additional: Disabling ipv6 in Firefox

   1. Type about:config in your address entry bar (in firefox)
   2. Type "ipv6" in the filter
   3. Change the value of "network.dns.disableIPv6" to true

I tried this restarted firefox, and still no go.  Now that I think about it, I don't think it would be a problem with Firefox, because I can't even ping these sites.  Also under network settings
I am set up for DHCP.  ON the DNS serves tab is 192.168.2.1 and under search domains the name Belkin is there.  (The type of router I have).  Under the hosts tab I have several entries.  Here is the screenshot

---

### Post by paydaydaddy on 2007-02-18
First off I want you to know that I am pretty new to Ubuntu myself, but I just did (yesterday) go through a similar situation. I compared your posted network info to mine and did see some minor differences, but I'm not in a position to say that those differences are the cause of your problem. While working on another problem yesterday (trying to get my Ubuntu box to see my printer connected to another computer) I botched my network settings. The method I used to get them back was to boot frome the live cd. As soon as I was running off the live cd I could connect to the internet. I carefully made note of the settings that were automatically detected, ejected the disc and rebooted. Then I entered the values I had copied and was once again back on my network and able to connect to the internet. YMMV.

As a side note, try pinging each of the components and machines in your LAN. Also use traceroute (I believe it is  under system.admin.networking tools) and see how far out you get towards a site you cannot access before it stops. That may contain some clues.

---

### Post by tim1970 on 2007-02-18
On the sites that I can't get to when I do a traceroute I get nowhere.  As soon as I start the trace I get the message the address could not be found.

---

### Post by paydaydaddy on 2007-02-18
That would lead me to think that the problem is in the LAN. The confusing part is that you can get to some sites. Carefully check/configure settings on all components.

---

### Post by tim1970 on 2007-02-19
I agree that it is very confusing and very frustrating.  To make things even more weird, one of the sites that I can't get to is [www.downloads.com](www.downloads.com)  I can't even ping that site, I get "unknown host".  However I can go to [www.download.com](www.download.com) (without the 'S') just fine.  both names point to the same site, but I can not get there through the first method. :confused:

---

### Post by Threbus5 on 2007-02-19
Hi,
You mentioned that your ISP requires a fixed IP.
Do your windows and ubuntu machines each possess the same IP?
Are they active simultaneously on the LAN?
Just a thought.

---

### Post by daspooky on 2007-03-07
Hello all!

I'm new to ubuntu 6.10 (installed it a few weeks ago) and today I started experiencing the exact same problem as tim1970 :(

Some websites work, some don't:

[www.downloads.com](www.downloads.com) -> doesn't work on ubuntu, works in windows
[www.download.com](www.download.com) works fine

[www.google.com](www.google.com) and gmail.google.com work fine in ubuntu, [www.microsoft.com](www.microsoft.com) doesn't work. These are only a few examples.

Has anyone found a clue about this problem yet?

---

