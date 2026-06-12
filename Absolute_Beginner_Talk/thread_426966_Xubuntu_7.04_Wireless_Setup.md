---
title: "Xubuntu 7.04 Wireless Setup"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by KiwiPete on 2007-04-29
Hi

I need some help setting up my wireless card.
I have installed Xubuntu 7.04 which uses xfce-4 desktop on an old Dell machine (256Mb, 466 Celeron processor).
My wireless card uses Atheros chipset.

Applications > System > Network  (remember this is xfce-4 desktop)
immediately recognised the card and displayed the Wireless Connection.
I set the Essid and DHCP in properties, leaving Network password blank as I have switched off security on my wireless router.
But it does not work - no connection.

I am guessing the problem is omething to do with the Madwifi driver 
- how do I know if it is installed?
- how do I find out what directory path it is in?

Yes, I have enabled linux-restricted-modules.

Here are some terminal results that may help someone diagnose what is wrong...

**sudo iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"linksys"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=44/94  Signal level=-49 dBm  Noise level=-93 dBm
          Rx invalid nwid:7014  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[B]
/etc/network/interfaces file content is as follows:[/B]
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp

iface ath0 inet dhcp
wireless-essid linksys
wireless-key s:




**sudo ifup ath0**
ifup: interface ath0 already configured

Look forward to your help...
KiwiPete

---

### Post by wieman01 on 2007-04-29
Is it possible that you try to establish a connection between a 54M (G) router and a 11M (B) wireless adapter? First guess...

If so you need to enabled "mixed mode" on the router so that it is able to connect with 54M as well as 11M devices.

---

### Post by KiwiPete on 2007-04-29
Thanks for the suggestion wieman.

I enabled mixed on the router - but still no connection through the wireless card.
Any other suggestions or advice?

KiwiPete

---

### Post by wieman01 on 2007-04-30
> Alright then. Please turn off all security (as you may have done already) and replace the contents of "/etc/network/interfaces" with this:
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

[COLOR="Blue"]auto ath0[/COLOR]
iface ath0 inet dhcp
wireless-essid linksys
Does the ESSID match? Then restart the network (and post the results):
> sudo /etc/init.d/networking restart
Also important: Is DHCP enabled on the router?

---

### Post by KiwiPete on 2007-04-30
Hi Wieman01

Security disabled and checked that router has DHCP enabled.
I changed the /etc/network/interfaces file as suggested.
Here is the output from sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:05:1c:19:de:45
Sending on   LPF/eth0/00:05:1c:19:de:45
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:05:1c:19:de:45
Sending on   LPF/eth0/00:05:1c:19:de:45
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:19:e0:83:24:d5
Sending on   LPF/ath0/00:19:e0:83:24:d5
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

What do you suggest next?

KiwiPete

---

### Post by KiwiPete on 2007-04-30
Wieman01

Here is an interesting thing I noticed - not sure if it is related or not...

When system boots to start Xubuntu there is a text message briefly on screen that says something about BIOS 1999 being old and that 2000 is required; then a line that says 
ACP Force is required.

Also when the ubuntu splash screen appears with progress indicator as it boots - it reverts back to text screen after 3 of the 9 progress bars are complete - and the screen has lots of text lines - each with an OK at the end of the line,
except that after the line which says Configuring network interfaces, there is a line saying Setting sensors limits after which it says Fail rather than OK.
It then continues with lots of OK lines and eventually boots into the login screen.

Could this have anything to do with the problems I am having with wireless?

KiwiPete

---

### Post by wieman01 on 2007-04-30
> **KiwiPete said:**
> Wieman01

Here is an interesting thing I noticed - not sure if it is related or not...

When system boots to start Xubuntu there is a text message briefly on screen that says something about BIOS 1999 being old and that 2000 is required; then a line that says 
ACP Force is required.

Also when the ubuntu splash screen appears with progress indicator as it boots - it reverts back to text screen after 3 of the 9 progress bars are complete - and the screen has lots of text lines - each with an OK at the end of the line,
except that after the line which says Configuring network interfaces, there is a line saying Setting sensors limits after which it says Fail rather than OK.
It then continues with lots of OK lines and eventually boots into the login screen.

Could this have anything to do with the problems I am having with wireless?

KiwiPete
Not 100% sure to be frank. However, I have noticed one line that does not look right:
> wifi0: unknown hardware address type 801
It seems to me that the Madwifi driver is incorrect and picks up your device although it shouldn't. So it's a driver issue after all. Have you given "ndiswrapper" a thought yet? "ndiswrapper" lets you deploy the Windows driver for your card, that should resolve your problems. A good tutorial is this one:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

This has worked for me in the past to get my device working, however, I suggest you check out others as well. There should be suitable tutorials around. 

Nevertheless just post here if you need a hand... :-)

---

### Post by KiwiPete on 2007-05-05
Good news...my wireless card is now working fine.

Not sure exactly what fixed it, but here is what I did, which somehow fixed it.

I did not try ndiswrapper...was keen to explore other options first.
I had been using Xubuntu on adual boot system with Win98.
I thought I try to verify the card worked in Win98 at least - so booted into Win98 and as it wasn working thought I uninstall the Windows driver and physically removed the wireless card - and then re-insert card and re-install Windows driver.
I did all of that and was disappointed to find that I still couldn get it working in Win98.

I was quite despondent - having failed to get wireless in both Xubuntu and Win98.
So I left the machine for a couple of days.
Today I re-booted into Xubuntu and wonder of wonders the wireless card was instantly up and running connecion to the network!

All I can guess is that either physically removing and re-inserting the card triggered some kind of plug &#324; play response in Xubuntu - or that the Win98 driver setup was somehow preventing the card from working in Xubuntu.

Regards

KiwiPete

---

### Post by deejay_001 on 2007-05-13
FWIW, this has worked for me in edgy and now in feisty.  What I did was placed ath0 and it's parameters (DHCP, ESSID, Wireless Network) under the Primary interface section and rebooted.  This may be what happened with KiwiPete because before letting it sit for a couple of days, he took the suggestion of someone else who had him place ath0 at the top of the /etc/network/interfaces list then rebooted.  For whatever reason, just doing a /etc/init.d/networking restart does not work.

---

### Post by BinaryBrother on 2008-03-31
I had the EXACT same problem and EXACT same diagnostics messages as 'KiwiPete'. I followed 'wieman01''s advise and found myself with a working Wireless card... The net restart did NOT work for me... I had to change the "/etc/network/interfaces" file to look like  what 'wieman01' said... Added my ESSID as advised... rebooted... and boom... :)

P.S. Big thanks to 'deejay_001' also for advising reboot... :)

---

