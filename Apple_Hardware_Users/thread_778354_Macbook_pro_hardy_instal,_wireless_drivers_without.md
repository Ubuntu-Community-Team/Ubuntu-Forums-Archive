---
title: "Macbook pro hardy instal, wireless drivers without internet"
date: 2008-05-02
forum: Apple Hardware Users
---

### Post by suchawato on 2008-05-02
so here's a good question,
exactly how are you supossed to download the wireless and oter drivers needed for the macbook pro instalation without internet?
seems a little silly: "go download the drivers _here_ to get your internet working"
seems a little silly.

When I directly conected, it said that the network was "secure"
and wanted all sorts of cryptic info to be able to conect. eos, nework name (we don't have a network), etc.
I don't know any of this information, how am I suposed to install?
How am I supposed to conect?
OS X and Windows will automatically connect if the network is directly through a cord.
Seems a little r-tarded to ask for all sorts of advanced info just to be able to get on directly. Obviously, if I am directly conected, I am physically in front of my router, why do I need all this cryptic info?

So I need to connect.
Any ideas how?
thanks,
-Sara

P.S.
Ubuntu should include drivers needed for macs by default.
I should not have to download them.

---

### Post by PauGNU on 2008-05-02
> **suchawato said:**
> 
P.S.
Ubuntu should include drivers needed for macs by default.
I should not have to download them.

Ubuntu and other GNU/Linux distributions can't do that because of the license driver restrictions. Developers are working on new drivers for this wifi hardware, but drivers are not ready yet.


> When I directly conected, it said that the network was "secure"
and wanted all sorts of cryptic info to be able to conect. eos, nework name (we don't have a network), etc.
I don't know any of this information, how am I suposed to install?
How am I supposed to conect?

But, have you ever been connected or not?. Because first you say "I directly connected" and then you ask how are you supposed to connect".

If you want to connect to your wireless network, you just need to download first wifi drivers (of course, YOU NEED TO DO THAT FROM OTHER COMPUTER OR CONNECTING YOURS BY WIRE).

If you want complete support on GNU/Linux, when you buy a new computer, first try to know if that computer is completely supported by GNU/Linux. Unfortunately, Mac computers aren't completely supported. That sucks.

1. Download this:
[http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz](http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz)

2. Install build-essential (open a terminal and type):
sudo aptitude install build-essential

3. And compile it.

[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

---

### Post by suchawato on 2008-05-02
> **PauGNU said:**
> Ubuntu and other GNU/Linux distributions can't do that because of the license driver restrictions. Developers are working on new drivers for this wifi hardware, but drivers are not ready yet.




But, have you ever been connected or not?. Because first you say "I directly connected" and then you ask how are you supposed to connect".

If you want to connect to your wireless network, you just need to download first wifi drivers (of course, YOU NEED TO DO THAT FROM OTHER COMPUTER OR CONNECTING YOURS BY WIRE).

If you want complete support on GNU/Linux, when you buy a new computer, first try to know if that computer is completely supported by GNU/Linux. Unfortunately, Mac computers aren't completely supported. That sucks.

1. Download this:
[http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz](http://snapshots.madwifi.org/madwifi-trunk-current.tar.gz)

2. Install build-essential (open a terminal and type):
sudo aptitude install build-essential

3. And compile it.

[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

Thanks, but uhh, compile?
I'm not a programmer.
I was connected to the net by wire
I said that.
It wiould not let me on though.
that's what I said.
Just because the wire is conected to the computed doesn't mean I'm on the internet.
Thanks.

---

### Post by cyberdork33 on 2008-05-02
I know that you are probably frustrated, but coming in critcizing Ubuntu and then asking for help is probably not going to get a response. If you think that something is wrong, or should be different, file a bug report in launchpad.net

I don't know why you are getting those interesting messages when connecting by wire. You should have no problem connecting the ethernet cable, and having the dhcp server assign an IP. If there is some strange security feature on the network you have connected to, that is something that should be addressed by the network admin.

Now then, depending on which Macbook Pro you have, you could have a Atheros or a Broadcom wifi card. Atheros cards use the madwifi driver. (Yes, it requires some downloading to get what is needed. Unfortunately, both Atheros and Broadcom do not yet have open drivers, and thus cannot be included with Ubuntu by default) There is support for some atheros cards already in Ubuntu, but the newer Mac cards are not one of them.

To go further, you need to identify what mac version you have. This can be found in the system profiler in OSX and has the form "MacbookPro4,1". You can also determine what card you have by running lspci in Ubuntu in a terminal and looking at the info for your wifi card.

PS and yes, you might be required to compile something... it is really not that difficult. there are full instructions showing each step.

---

### Post by russo.mic on 2008-05-02
> **suchawato said:**
> Thanks, but uhh, compile?
I'm not a programmer.
I was connected to the net by wire
I said that.
It wiould not let me on though.
that's what I said.
Just because the wire is conected to the computed doesn't mean I'm on the internet.
Thanks.

Help me Rhonda.

1. So, put your cdrom into the drive, and type 

sudo apt-cdrom add
sudo apt-get install build-essentials

2. either plug in an RJ45 cable into your MBP or find one of the 1,000 internet connections readily available to you within a 3 mile radius of where your standing and download this:

[http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148](http://sourceforge.net/project/showfiles.php?group_id=93482&package_id=99148)

3. search in the forums for ndiswrapper installation.

4. enjoy your new FREE operating system running on closed hardware!  

I can get my wireless up in about 4 minutes after a reinstall.  I keep the drivers and ndiswrapper on a jumpdrive as I do frequent reinstalls.  May I recommend you write a script to install yours?  that way you could learn a few things and have your internet up.  

I have never had an instance where my wired built-in NIC on my MBP or any other laptop for that matter didn't work upon boot.  If there is a problem with your wired internet connection, I would look elsewhere for the problem.
If you'd like, you could always sell your MBP and my a computer with linux preinstalled.

Russo

---

