---
title: "Where Can I find instructions for how to use edubuntu server with one ethernet card?"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by adMOMistrator on 2007-06-22
Please.  Since all my posts go unanswered, and my fingers are bleeding from googling, and even my cries for better documentation get laughed at, can someone please tell me where this stuff is that I can 't find.

My laptop can't autoconfigure the network, so I have to do it manually.  I need to set up static ip, my modem uses pppoe - -whatever that is.  My isp says that most of the static ip configs are 0's ???  I'm so lost.  And I don't even know if my etc/network/interface should  be blank - - but it is.

I'm scared to try anything else without guidance, because I FINALLY have it Almost working, and I don't want it messed up again, because I have no idea what I've done.

I saw somewhere that I may??? need a new ssh key, but that's the first I've heard.

And its not like I'm stupid.  If someone would just give me a clue.  


Danielle

---

### Post by kevinlyfellow on 2007-06-22
I'm a little confused at to what you are trying to do.  Are you trying to connect to your isp through a modem, or are you trying to set up an ssh server, or what?

A blank /etc/network/interfaces is normal for Ubuntu.

---

### Post by Jimmyfj on 2007-06-22
I have an Ubuntu 6.10 server running on a static IP-address next to my Gutsy test-box. Both connect through a Linksys wireless router, though both server and workstation are cabled. I don't understand? Do you want to connect your workstation as a "server" or do you run a dedicated server separately?

---

### Post by adMOMistrator on 2007-06-22
Thanks you guys :-)

I have Edubuntu and I want to run the thin client server off of my pc (so that I can run and control one or two more).  The edubuntu came with the thin client server installed as part of the os (install a server option.  Full desktop just with the added software).

I am trying to connect to my isp through a modem.  Well, expressly, a Westell 2100 adsl modem/router with bridge capabilities (got me?  but that;s what it says).  The ssh thing was another lost attempt of mine to figure this out on my own.  

I thought that probably my network interfaces would/should be blank since most of my pc's use dhcp.  But, because of the static ip, I wasn't sure.  But then it looks like it's assigned dynamically somehow --i dunno what I'm talking about.

The only reason I'm trying the static ip, is coz I have read that edubuntu may be conflicting with my internet and that this is a possible solution.  It's not like I'm in love with it - - i just want this to work.

Thanks again for your time

Danielle

---

### Post by kevinlyfellow on 2007-06-23
I've never done a thin client before, and I'm fairly new to networking, but I think that it'd be best to make sure that its clear what the setup looks like.  You have a usb modem (the Westell) that is used to connect to the ISP, and you have an ethernet card which you have connect to a switch with all of the clients?

Ignoring the internet connect for now, have you got the thin clients setup to work properly?  

Again, I'm new to networking but hopefully someone who is smart about networking will come by!  The internet connection should be able to be assigned an ip address via dns, while the rest of your network can be defined anyway that it needs to be (looks like via a dhcp server).  Your server will have two ip addresses, one for the modem assigned via the isp and one for the ethernet card which is defined by you.

Just in case you haven't come across this, there is a howto for edubuntu thin clients [http://www.edubuntu.org/GettingStarted](http://www.edubuntu.org/GettingStarted)

---

### Post by adMOMistrator on 2007-06-23
Yes, I think you are seeing my net right.  It is a hub, not a switch-for the record.  

The thin clients.  Yes, I think so, pretty much.  My etherboot floppy seems to be doing the right thing, so as soon as I get the file to serve and a few other details worked out, I should be good LOL - yeah, right.  Actually, one of them has edubuntu dapper drake installed (with the thin client server, is that a problem - 2 on one net?, I dunno why, I just picked that one when I installed), I just would like the ability to periodically control it, like during class (home school).  The other has a bad hard disk, so.... I have my fingers crossed.

((Oh, btw, the thin client howto leaves quite a bit to be desired for a newbie.))

I found this info (at dsl reports.com) on bellsouth, now at&t,  dsl with any westell modem which could be useful for me (there are about 6 other ways it'll work depending on your physical config):

**Standard Default Mode Connection (separate hub or switch present)**
[COLOR=red]Highly recommended setup for networking. Detailed instructions and information is available **here**[/COLOR]. 
  Modem's built in PPPoE client used.
  Username and Password required on modem (accessed through **Easy Login** page).
  NIC(s) should be set to "Obtain IP Address Automatically".
  WAN IP address will be on modem and PC NIC(s) will have a 192.168.1.xxx IP address.
  Requires no changes in configuration to the modem. When you reset the modem (either through the software interface or the reset button on the back of modem) this configuration is set.

**Bridged Ethernet Mode (no separate router present)**
  Must use a PPPoE client on the PC.  Clients such as the **BellSouth Connection Agent**, RasPPPoE, and the native PPPoE client on Windows XP are available. 
  Username and Password required on PC through the PPPoE client interface. Username and password on the modem will be disabled when you select "bridged ethernet" connection and save the settings.
  NIC should be set to "Obtain IP Address Automatically".
  WAN IP address will be on the PC NIC. This is one of two ways to assign the WAN IP directly to the NIC; with the other method being "IP Passthrough" without a router.
Requires changes to the modem configuration. Must enter Expert Mode, click on the Configuration button and then click on the Connections button. Enable "bridged ethernet" mode from the Protocol pulldown. **Connection Screen Shot**.  

**IP Passthrough Mode (no separate router present)**
  Instructions for enabling IP Passthrough are available **here**.
  Modem's built in PPPoE client used.
  Username and Password required on modem (accessed through **Easy Login** page).
  NIC should be set to "Obtain IP Address Automatically".
  WAN IP address will be on modem and PC NIC. Some VPNs, servers, and games require the WAN IP directly on the PC. This is one of two ways to assign the WAN IP directly to the NIC; with the other method being "bridge ethernet" without a router.
  Requires changes to the modem configuration. Must enter Expert Mode, click on the Configuration button and then click on the IP Passthrough button. Select "User Configured PC" or the IP address shown and click on the Enable button. **IP Passthrough Screen Shot**. 
  Requires you to release and renew your IP before the changes will take effect. You can do this through a DOS prompt or by restarting your PC.


Some things that seem mysterious to me about MY stuff are (this is stuff I have seen over the course of a year, not all at once),
 1.  I tried copying the hosts table from my 6.06 and that wouldn't get close.
 2.  Even if I clear it all out, my hosts table ends up with tons of entries, like         30--according to my modem, there are 2.
3.  Should my host table mostly match the one on my modem?
4.  I see no eth1 on my feisty pc, just eth0.  But i ran pppoe conf and it says all is good.  But maybe i did wrong there. (and, i saw no way to put in my username and password-do I need it)

Last night I tried going to network manager and I:  set eth0 for static ip and filled in my ip, then i changed it back to dhcp (but the ip is still filled in that blank-I left the rest of that blank).  Restarted this morning and.....looking for google forever, then waiting forever. Never loaded.  I can ping localhost, but nothing else.

Fun.

Thanks so very much

Danielle

---

### Post by adMOMistrator on 2007-06-23
To let you know, I decided to try a fresh install of the edubuntu feisty.  This time, the static ip was set up on the modem (thanks to one day when I had stuff pretty close, and the modem grabbed it) - - as long as it gets the same ip. 

I don't know what's going on, its still installing, but I did get to a point where I was at manual network configuration (all others failed), and put strings of 0's for each requested #, except for dns, I think.  That time it went on with the install, without saying it would try later, or giving me a red screen. We'll see how bad I screwed it up.

Bye :-)

Danielle

---

### Post by kevinlyfellow on 2007-06-23
> **adMOMistrator said:**
> 

3.  Should my host table mostly match the one on my modem?
4.  I see no eth1 on my feisty pc, just eth0.  But i ran pppoe conf and it says all is good.  But maybe i did wrong there. (and, i saw no way to put in my username and password-do I need it)


3. When you say "host table" do you mean /etc/hosts?  That should be filled up with the ip-addresses of your thin-clients and a few other things.  As far as I know the modem shouldn't be creating entries there.

4.  Your modem will be called something like ppp0 Your ethernet cards will be called something like eth0

> Actually, one of them has edubuntu dapper drake installed (with the thin client server, is that a problem - 2 on one net?, I dunno why, I just picked that one when I installed), I just would like the ability to periodically control it, like during class (home school).

Are you saying you have two dhcp servers on one subnet?  That doesn't sound workable (or necessary).  It can be on the subnet running an os from the disk, I can't imagine that that would be a problem, but I wouldn't run dhcpd.  Maybe I completely misunderstood.  

I hope your install goes well.  Keep me posted on how that goes.

---

### Post by Jose Catre-Vandis on 2007-06-23
I have two dhcp servers running on one subnet, but in separate number ranges, one from my router, and one from the LTSP server (edubuntu), and yes, all with a single NC.
(It does get in a muddle sometimes when I connect a new machine, but I usually move it to a static IP if it is going to stay on the LAN / or reboot to pick up the correct range) Thin clients always find the right range due to the PXE boot process)

I am still trying to understand exactly what you want to do. If your LTSP and thin clients are working fine on your LAN, then are you having trouble connecting the LTSP server box to the net, and subsequently the thin clients? Or do you want to access your LTSP server from outside the LAN?

Set up the main Edubuntu on your router first (login as primary login you gave on install). Give it a static IP on the router (within the router range!). LTSP should then bridge your thin clients across to give net access.

You won't be able to get thin client access from outside the LAN, but you should be able to get remote access, as long as you give your router the instructions (e.g. port 80 (http) or port 5901 (vnc)) to point at your edubuntu box.

Its been a while since I set up my edubuntu server and LTSP so I think this is how it goes...

---

### Post by adMOMistrator on 2007-06-24
Hi,

> I am still trying to understand exactly what you want to do. If your LTSP and thin clients are working fine on your LAN, then are you having trouble connecting the LTSP server box to the net, and subsequently the thin clients? Or do you want to access your LTSP server from outside the LAN?

I am having trouble connecting my LTSP server box to the net, and subsequently the thin clients.  Oh and maybe even eventually the windows pc LOL.  And I am only assuming that the LTSP server is working right.  The 6.06 pc with it seems to work ok, however;  I don't have it figured out just yet either (but this pc is on the modem and internet just fine, it autoconfigured). 

As for all the other info, thanks so much.  Unfortunately it is a good way over my head at the moment (maybe too many cups of coffee this morning - -I think I'm on #6 RRR!!LOL)

Speaking of too much coffee, I'm about to smash this laptop into the stone floor  !!

I had no luck with my fresh install - -  worse thann I had it.  I tried again with the server - no luck, and as a workstation-  still no luck.  I guess that, yet again, I don't have time to mess with this piece of ^%&*

Unless someone has another suggestion, I guess there's no sense having anyone waste anymore time on this one.  Thanks again, tho.

Danielle

---

