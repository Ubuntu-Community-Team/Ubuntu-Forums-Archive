---
title: "[SOLVED] Am I doing Torrents wrong?!! Very SLOW...."
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by qprfact on 2007-03-22
I've been running Ubuntu as dual boot with Win XP for a few weeks now, and am quickly getting into the habit of booting into Ubuntu rather than Windows!

However, I still am unsure that I've fully got to grips with torrents in Linux. On Windows I use an app called Bit Torrent (Shad0w experimental) and get pretty good speeds (I'm on 1MB DSL via a Belkin router)

In Linux, I have kTorrent, Bit Tornado and Bit Torrent, and am unsure if one of these should be my method of choice (also tried Opera)

However, I do find that torrents which open in Windows often return error messages in 'nux ("Bad File", for example) and download speeds seem a **lot** slower.

This may be due to the way I have ports set up. This is all a bit of a mystery to me, and I've not tinkered with my settings, but maybe I need to optimise them?

Also, I tried to install Azureus, but it gets to the "language" screen on set up and then just exits! I've tried uninstalling and reinstalling to no effect. Are there tmp files or set up files that I need to delete as they may have duff info in them?

Thanks in advance!!!

---

### Post by graigsmith on 2007-03-22
can you launch 2 torrents at once? or does it give an error?

---

### Post by HereInOz on 2007-03-22
Firstly you will need to find what port, or range of ports, the BitTorrent client uses.  BitTornado, for example, is set by default to use random ports, but this will not work with a firewall and a router.

You need to go in to prefs in BitTornado and set the port (or ports) so that they are always the same, (disable randomize) and then you need to open those ports in both your Ubuntu firewall, and your gateway router, if you have one.

The easiest way to open ports in your Ubuntu IPTables firewall is to install Firestarter, available through Synaptic, provided you have the right repositories selected.  Once you have Firestarter installed, you should be able to work out how to open the inbound ports which you have set up in "prefs" as your BitTorrent ports.

You then need to go in to your router, and forward those same ports to the IP address of your Ubuntu machine.  For this reason, it may be worth while going in to Networking, and setting up a static IP, gateway, and DNS addresses.  This makes sure that the IP address of the Ubuntu machine is always the same, so the port forwarding works.

I cannot give you any clues as to how you do that with your router/modem, as they are all different.

I hope this helps a little.

---

### Post by InQuieto on 2007-03-22
> **qprfact said:**
> 

Also, I tried to install Azureus, but it gets to the "language" screen on set up and then just exits! I've tried uninstalling and reinstalling to no effect. Are there tmp files or set up files that I need to delete as they may have duff info in them?

Thanks in advance!!!

For this, try a look at [https://launchpad.net/ubuntu/+source/azureus/+bug/57875](https://launchpad.net/ubuntu/+source/azureus/+bug/57875) and [https://launchpad.net/ubuntu/+source/azureus/+bug/57875](https://launchpad.net/ubuntu/+source/azureus/+bug/57875).
If you install azureus from repo, there's a bug. I suggest use the Jar ver. from sourceforge.

Bye

---

### Post by shavenlunatic on 2007-03-22
i use BitComet in Windows, purely because it uses good encryption.  Many ISP's now limit the transfer speeds on suspected P2P transactions.

I have not used torrents so much in Linux but I expect it is a similar situation (although I am very often wrong!, bit of a linux noob at the minute)..   I would just advise to look for a client whcih uses encryption.  In windows with encryption I run at pretty much max speed (150-200k/s on a 2meg cable), without encryption turned on it drops to about 30k/s

---

### Post by qprfact on 2007-03-22
Thanks for some really helpful responses.

I was indeed getting an error when trying two at once.

I already have Firestarter installed (that cautious Windows mentality coming in there!), and interestingly it was showing a red logo in the Ubuntu equivalent of the system tray (not sure what that's called!) showing hits on my machine - should I be worried about that?!!

I installed Azureus from Synaptic Package Manager - so that would suggest I need to try the alternative approach?

I will try the other things out tonight.

Thanks again!

---

### Post by InQuieto on 2007-03-22
Here you can download Azureus: [http://azureus.sourceforge.net/](http://azureus.sourceforge.net/)
If you use synpatic you get a bugged vers. of Azureus. Here you can find an alternate method to install Azureus [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_P2P_BitTorrent_Client_.28Azureus.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_P2P_BitTorrent_Client_.28Azureus.29)
You may also use Automatix2 ([http://www.getautomatix.com/)](http://www.getautomatix.com/)).

Azureus supports a good encryption system, so in my experience it is more more rapid than Deluge, KTorrent or BitTorrent.

Bye

---

### Post by Efros on 2007-03-22
The best response from the myriad torrent clients I've tried in ubuntu has been with utorrent under wine. Ironic!

---

### Post by qprfact on 2007-03-29
Well, I thought I would give it a quick go last night.

I put the static IP address bit to one side, as Belkin said:
> 
It is not neccessary to assign static IP adddress if you want enter the port number to access P2P application through router, please follow the below steps to enter the port number on the router setup page:

-Please open the Internet Explorer and in the address bar type in "192.168.2.1" and Enter.
-Leave the password blank and click on "submit”.
-Click on "Virtual server" under the "Firewall".
-Enter the port numbers under "LAN Port" & "public port".
-Enter the IP address of this computer under the "LAN IP Address".
-Check the "Enable" box and click on "Set".

So, I won't, I thought! Went into the setup, and working on the basis that 192.xxx.2.1 was the router, then my two PCs would be 192.xxx.2.2 and .3 respectively. Put the uTorrent port in those, tried the test and it worked! Port open!

Being paranoid, I then ran a check on Shields Up! [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

All tests passed satisfactorily!

So, then tried a random download (a book, that I subsequently deleted) - soon was d'l ing at 95kB/s - much faster than I'd ever achieved before!!!

Now all I need to do is get the Web UI up and running.....!

---

### Post by Soarer on 2007-03-29
Excellent!

This MAY stop working one day though, if your PCs get different IP addresses from the router at some stage.

That's why static IPs are used in a case like this, so the port destination PCs always have the same IPs.

---

### Post by qprfact on 2007-03-29
Yep, someone else mentioned this to me, so I may still have to delve further.

For the time being, though, all is well!!!

---

### Post by Chemist on 2007-03-29
i have no end of trouble trying to obtain a decent speed on linux box. I've tried azerues, deluge and ktorrent, the most I seem able to download is about 20kbs and it fluctuates wildly. On my Windoze laptop i can get 200kbs + through azerues with the same tracker.

---

### Post by Hallvor on 2007-03-29
Sounds like a firewall issue - or that your ISP is throttling your connection. The differences between Windows and Ubuntu may be caused if you use a client with encryption in Windows and one without in Ubuntu. Can`t remember what clients have encryption enabled by default, however.

In general, bittorrent under Ubuntu has been much faster for me.

---

### Post by qprfact on 2007-03-29
I ticked the encrypted box in uTorrent - though whether that makes much difference I don't know!

Of course, I could have been very lucky with that first download I did!

---

