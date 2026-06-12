---
title: "Setting up the Linksys WRT54G"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by mockjules on 2006-07-10
Okay now I want to be ambitious but do not know where to begin.

Set up Ubuntu Drake as dual boot went fine. Setting up my hardware, and even my DSL was easy on a old HP Pavilion 800 mh PC. Just took a bit of research. I got a Linksys WRT54G router I would like to set up on the system but I have yet to find any step by step Howto on this model. (I maybe looking in the wrong place.) Anyone out the done it yet? Maybe give me a few pointer on where to start.


Thanks!

---

### Post by Frank Golden on 2006-07-10
Not sure what you mean by setup. I use the WRT54GL model
but setup for all versions of the WRT54G is the same.
I need more info from like what kind of broadband do you
have (cable,dsl etc.). Need to know if you have a dynamic
ip address or a static address. Need to know if this is a brand new router or has it been setup before. Basically you will setup the router which is really a small computer in it's own right to match your connection type. Then your Ubuntu setup should detect
these settings and set itself up to match. I have mine setup through XP
and Ubuntu automagically detected and configured itself.
Placing a router between your cable or dsl modem and your computer is
a great security measure.

---

### Post by FoggyMtn on 2006-07-10
I have run my wrt54g as both a router and a hub.  THere really wasnt much setup to it.  THe only problem I had was my dsl modem is also a router (it will assign dhcp addresses).  I could never get the *&^* thing turned off and functioning as a "dumb" modem.  So, I had it assigning an ip to my linksys.  THe linksys then handled all the lan ips.  It wasn;t the prettiest setup, but it worked.

I just recently added a smoothwall (firewall) box into the loop.  Now i go from the dsl modem, to the smoothwall (which handles dhcp) and the linksys is just a wired and wireless hub. All I had to do for that was to turn off the dhcp setting.

I'm far from proficient at this, actually barely able to act unsupervised, lol, but post back what you actually need to do and I'll help if I can.

Rob

---

### Post by mockjules on 2006-07-10
I see. 

Okay! It is brand new but I never could get it could connect to the net in the final step of the setup disk in Windows XP. I have SBC DSL with Dynamic addresses. So in a sense it has never been set up at all from Windows XP.

So is it possible to do a complete setup right into Dapper Drake? I do not see this possible when all it came with is the Windows setup disk.

One final note, the complete model number is WRT54G v5.

I know it is not faulty because I exchange it before and still have the same problem in XP.

Right now my DSL connection is  is running just fine on its own in Dapper Drake.

:-k

---

### Post by lwf on 2006-07-10
You don&#8217;t need any CDs or setup utilities, just browse to [http://192.168.1.1/](http://192.168.1.1/) and do whatever changes you want to.

---

### Post by FoggyMtn on 2006-07-10
I can't help much with the Xp setup.  Before Ubuntu, I was running mine with a mac osx system.  

I would think you could put it inline, and the dsl would assign an ip to the linksys, which can inturn assign an ip to you linux box.  Can you access it thru a webbrowser?  (mine was 192.168.1.1)

Sorry I can't be much more help, but I sure someone with more knowledge will get ya going...

rob

on edit: I type too slow!  The previous post sums it up! lol

---

### Post by fhqwhgads on 2006-07-10
You'll need to set the modem and router to bridge mode. There will be a web interface on your modem where you set this up. Call your ISP, they should be able to give you the password and talk you through it. 

As for the dynamic IP address, your (and my) router has a dyndns client built in. Just sign up for service at [http://www.dyndns.com/](http://www.dyndns.com/) enter your username and password in the tab in the router's web admin page and enjoy your free static-like network access.

---

### Post by RRS on 2006-07-10
Even in windows you don't need (or want) to run the Linksys cd.

I also have SBCYahoo with a 2wire modem. My particular modem is also a router and that's what created problems for me. Which modem do you have?

I also set up my Linksys as a "switch" similar to what Foggymtn did.

I'll try to get my configuration for you in a bit.

---

### Post by FoggyMtn on 2006-07-10
FWIW they are right saying that it will simplify things if you set up the modem as a bridge.  But, I have a speedstream modem, and when I would set it to bridge, I had issues with the linksys (which was now handling my pppoe connections) dropping the connection. So I went back to having everything assign ips.  It was far from convenient or pretty, but it worked.  As long as you can have everything following a logical path, you can still muddle thru it like I did and make it work.  



rob

---

### Post by RRS on 2006-07-10
OK, here's a basic rundown of my setup:
My modem/router has DHCP enabled and acts as the DHCP and DNS server.
In my Linksys WRT54G I have DHCP dissabled and connected the modem to a LAN port rather then the WAN port.

To access the router plug it into your computer's ethernet port and open Firefox. Enter 192.168.1.1 in the add. bar and "go" Leave user name blank and "admin" or "administrator" for the password. You can and should change this later.

To access your modem;
System>Administration>Networking>DNS
The IP of your DNS server is the modems address. It should also have a web based interface you can access from Firefox. Try your username and password for SBCYahoo or call them and they'll provide it if you can't remember setting one when you first installed the service.

I was never successful setting the modem to bridge mode but this has been working fine for me, both computers have internet access and I can share files, etc. between them.

Here's some screenshots of the setup pages from my router. Hope this helps you out.

---

### Post by fhqwhgads on 2006-07-10
I have a speedstream 5100 and a wrt54g v5. I need to reboot 'em about once a month, i think this is mainly due to bittorrent, which is a problem with the linksys firmware. It just locks up after a while. I kinda wish I didn't get this model because it's hard to load the linux firmware onto it, unlike older models with more RAM.

Bridge mode is the way to go if you want stuff to work the way its supposed to. It's a bad plan to have 2 DHCP servers running. Call SBC tech support, you'll be sorted in 20 minutes if you can escalate the call to a tech who understands.

The way RRS describes will work too, but you're using the linksys as an access point more than a router. My way will make port forwarding and VPN and such much easier for you to deal with.

---

### Post by mockjules on 2006-07-10
I like to thank everyone to the helpful feedback everyone has given me. From all these helpful replies. I think I have enough to start setting it up. (Nice thing about Linux is that it is fun to tinket with it.)

As to RRS reply, yes I do have a 2Wire Modem. A simple 1070-B Gateway model. They given me an admin password to access the settings when I hook it up on my laptop with XP. I get internet access on it but I was never able to send out any e-mail on Outlook. I can recieve but not send. It is only when I hook up to an outside connection like my office network it sends out e-mail fine.

But I can now recieve and send e-mail just fine with the modem going through the Ubuntu system. Which give me a great respect to the distro.

THe only settings I did in Ubuntu is after installing the OS is to choose "set up the ethernet card manually" during setup. Then I enable the ethernet card with DHCP setting. Then I went over to the DSN tab and added the DSN server adress given to me by 2wire which added the search domain setting as "gateway.2wire.net and BAM! My DSL was up. I did not do anything else.

---

### Post by mockjules on 2006-07-10
Okay! I the off chance it might work, I just plugged in the router and type in 192.168.1.1. Nothing worked. Although all the LEDs on the router and modem showed I am coneected. Therefre I have DSL but my router is not internally configured.

So according to Frank Golden suggestion, I should get the router configured first before Ubuntu can detect it. So maybe I should set the router up at my office network with the matching settings for my home system and then bring it home and try it out.

---

### Post by Frank Golden on 2006-07-11
> **mockjules said:**
> Okay! I the off chance it might work, I just plugged in the router and type in 192.168.1.1. Nothing worked. Although all the LEDs on the router and modem showed I am coneected. Therefre I have DSL but my router is not internally configured.

So according to Frank Golden suggestion, I should get the router configured first before Ubuntu can detect it. So maybe I should set the router up at my office network with the matching settings for my home system and then bring it home and try it out. 
That should work. There is something you should know about your
version of the WRT54G. There are several versions of this same model. Everything up to v.5-v.6 used a variation of linux for 
it's firmware. A router is really a complete mini computer, the
firmware being the OS. As a matter of fact you can turn an
old windows box into a good router with the right programs
and some inexpensive hardware. The earlier versions had 4 to 8
MB of flash for the firmware and up to 16MB of ram. The v.5 and v.6 versions only have 2 MB flash and 8 MB ram plus Linksys
replaced the Linux (open source) firmware with an inferior
closed source VxWorks. This firmware is not hackable. There
is lots of third party firmwares available for the earlier
versions. The factory firmware worked great on those earlier versions but there is a large community of folks using the various free "hacked firmwares". As a matter of fact my router a
WRT54GL, the last version with 4/16 flash/memory and Linux firmware has a "hacked firmware" on it. Makes it more stable and
versatile than factory. Only factory firmware is available
for v.5-v.6 and earlier versions of this was unstable and unreliable. So in summary he v.5 and v.6 versions have 
smaller flash and ram and at least earlier firmwares were
unstable, unreliable.
   Do a google search for the WRT54G v.5 and you will see lots 
of stuff about this.
   In was going to suggest you go to Linksys download site after
getting setup and online and update the firmware but I just 
checked and they don't list a firmware update for this version.
They don't even list the v.5 router or my version, they only go up to
v.3. Strange and perplexing. Linksys used to be a pretty good company.
Good thing I downloaded the latest factory firmware and saved it.
Maybe they are just updating their website.
Will check the "WRT54G" forums for more info.

Update: Checked around forums the latest firmware for v.5 is v1.00.9 
but the UK and Australian Linksys sites only list v1.00.6 ??
If your firmware version is v1.00.9 you have the latest. At least one person reported problems with v1.00.9 and reinstalled the earlier version. As reported earlier US site doesn't even list anything past version v.3. ??
Wish I could be of more help.
If you get set up copy settings from status page in router and save them if you need to use them in Ubuntu. If you are sucessful in Windows your Ubuntu
install should configure automagically.

---

### Post by hasimir44 on 2006-07-27
Has anyone been able to connect to this router (Linksys WRT54G) using wpa_supplicant with TKIP? I've followed several howtos and such, but it's still not working. This router is running linux, so I must be able to connect to it with linux.. What I'm concerned about is the "one touch easy setup".. There's a button on the router that you hit to add dhcp clients. The web setup page then says "now accepting clients" but wpa_supplicant won't connect even through nm-applet. 

I can connect fine without WPA, so it isn't drivers, etc.. 

If anyone has connected to this particular router using WPA TKIP, then please let me know. 

Thanks

---

