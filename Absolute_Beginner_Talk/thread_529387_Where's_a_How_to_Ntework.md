---
title: "Where's a How to Ntework?"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by ZootNerper on 2007-08-19
Hi,

Could some one point me in the direction of a "How to..." for networking Linux computers. Specifically I have 2 computers running Ubuntu 7.04. I'd like to share files. (Can't seem to figure it out myself!)

Thanks

-- Zoot

---

### Post by mikeyphi on 2007-08-19
> **ZootNerper said:**
> Hi,

Could some one point me in the direction of a "How to..." for networking Linux computers. Specifically I have 2 computers running Ubuntu 7.04. I'd like to share files. (Can't seem to figure it out myself!)

Thanks

-- Zoot

I can suggest a few steps for you to try!!!
Make sure 'Folder sharing service' is enabled - samba and/or nfs-kernel
Make sure computers are connected - check Network/network tools
Make sure you Add folders you want to share under System/Administration/Shared Folders

it should be as simple as that - unless I've missed something!!

---

### Post by ZootNerper on 2007-08-19
Thanks MikePhi,

I've checked nfs. I think it's running on both machines (one asked to install it when I was making a folder sharable ad the other did not.)

I can ping from both machines to the other.

I have used the "shared folders" to make a folder sharable on both machines.

But no luck - When I go "places->networks", I get a Windows Network icon and there is nothing beyond that". This may be because one machine used to access an XP machine up till last week. Now the XP machine is the Ubuntu machine it wants to share with (I don't run Windows anymore). But I get it on both machines.

I noticed on both machines that the Domain name which I set to "ZootWired" gets forgotten in both the network window and shared folders. Is this important?

Any further ideas?

-- Zoot

---

### Post by RomeReactor on 2007-08-19
Hi. I have no experience with networking, but the [Ubuntu community documentation]("https://help.ubuntu.com/community/") page is a great resource; perhaps [this page]("https://help.ubuntu.com/community/InternetAndNetworking#head-121a173dae16b9a1bb0a3e8116f907ade85e648c") is what you're looking for.

---

### Post by ZootNerper on 2007-08-19
Thanks RomeReactor,

I had a look at the page you suggested but the setting up an nfs client page is not written yet! So, no luck there.

I just made sure that samba is not running on the machine that used to talk to XP. I did an "apt-get remove" and it said that samba was not installed.

-- Zoot

---

### Post by mikeyphi on 2007-08-19
> **ZootNerper said:**
> Thanks MikePhi,

I noticed on both machines that the Domain name which I set to "ZootWired" gets forgotten in both the network window and shared folders. Is this important?

Any further ideas?

-- Zoot

Yes - I think it is.  I've just checked my system - one of the computers has the "this computer is a Wins Server" box checked, that's under general properties in the Shared Folders window. (probably one has to act as a server for both to communicate?)

Under the hosts tab in Network settings you should find that, under the alias column, the second line reads "hostname".domain-name (obviously the domain-name will be the same on both computers but the hostname will be different-whatever you set)

---

### Post by dpar on 2007-08-19
I know nothing about networking, but these may help.

[http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

[http://nfs.sourceforge.net/nfs-howto/](http://nfs.sourceforge.net/nfs-howto/)

---

### Post by ZootNerper on 2007-08-19
Hi MikePhi,

I set one machine to WinS server and the other to look to the server (I enter the hostname of the server). Still no luck.

The non-server does not remember the domainname after a reboot. The server may not either (didn't before) but I'm typing this on it at the mo.

I just thought I have different usernames and passwords on both machines. Could this be a problem? I am never asked for any when I am using the file browser to look for the network.

I have done a port scan on both machines and they both have an nfs port open - 2049.

Thanks dpar for the documentation source. I will read it next.

-- Zoot

---

### Post by mikeyphi on 2007-08-19
> **ZootNerper said:**
> Hi MikePhi,

I just thought I have different usernames and passwords on both machines. Could this be a problem? 

-- Zoot

No - that's fine
Are you using static DNS? 
If your coupled system worked previously with windows - it should still be working with the same settings now......
Have you set up all network DNS settings as they were with windows?

Try also using samba on both machines - leave the nfs as it is.

---

### Post by xpod on 2007-08-19
nfs is great and really easy to set up...

I actually used this guide at the time
[http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+howto](http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+howto)

---

### Post by ZootNerper on 2007-08-19
Hi,

I'm not using static DNS. My router is the DNS server in my "network". I've not had much luck setting my network up with static DNS in the past - everything seems to stop working (can't get to the internet, ping other nodes). I only have two machines and the IP addresses seem to stay the same.

After a reboot, neither machine will remember the Domain name in the "Network Settings" window General tab, but do have Hostname.Domanname in the Hosts tab. They both remember in the "Shared Folders" window "General Properties" tab.

I started looking at the nfs documentation and I do need a designated server and one or more clients. But I'm not sure now that WinS is an nfs server. If I follow the doc, I will have some editing to do, but it doesn't look too bad. Though I think I will need static DNS working.

Ho-hum. It's getting late here so I won't do more tonight. Tomorrow is a public holiday so I'll have lots of time to try some more.

Thanks to all.

-- Pat

---

