---
title: "Gnome PPP w/Earthlink Success"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by bbboB on 2007-02-09
I am a Windows user who is trying out Ubuntu using a dual-boot (actually tri-boot) computer and have never had any experience with Linux before.  I have been searching the boards for information about how to connect using dial-up with Dapper 6.06 for a couple of weeks now and finally got connected today after much trial and error.

I used the Gnome PPP program for my connection and my ISP is Earthlink, so although some things may be different for each of you there may be some information here that you will find helpful (at least, that's how I got it all to work.).

First step was to go into System-->Administration-->Networking and configure the modem there.  Chose the device and clicked properties.  Chose Enable this connection and filled in all the information such as connection number, username and password.  I DID NOT fill in any of the other tabs, including the DNS information.

Next, opened a Terminal.
Did sudo pppconfig
entered my password and this opened the PPP Configuration Utility.  Filled in all the info including the DNS settings I copied from Windows 98.  One change I did make this time around (this is my second install of Ubuntu...couldn't dial out the last time either) was to add ELN\username to the space for usename.  Not sure if it helped, but I read about it in a older document about connections to Earthlink from various systems.  It can be found here
[http://www.expita.com/earthlink.html]("http://www.expita.com/earthlink.html")

Also tried auto-detect, but it failed to find the modem.  I used the default setting of /dev/ttyS1 for the modem com port.  Chose PAP as the authentication method.

Next, opened Gnome PPP-->Setup
On the modem tab, chose the device /dev/modem, since that is the one I wanted to use.

Networking tab, chose dynamic IP Address and used the manual DNS and inserted the numbers from Windows 98.
Options tab-under Connections ticked the following:
Abort Connecting if no dialtone.
Check carrier line
Check default route
Ignore terminal strings (stupid mode)

Saved it all and Gnome connected?!  Re-booted and it was able to connect again.

What I find interesting is that I can't use wvdial to connect...it says that it can't authenticate with the peer, yet Gnome PPP works.  Last time, I had just gotten wvdial to work, but couldn't get Gnome to work.  Go figure...
 
Again, I stress that this is what worked for me, but I have no real working knowledge of Ubuntu, as I am just a novice.

Hope this helps!

boB

---

