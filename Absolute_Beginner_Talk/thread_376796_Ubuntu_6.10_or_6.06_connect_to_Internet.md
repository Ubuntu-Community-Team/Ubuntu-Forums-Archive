---
title: "Ubuntu 6.10 or 6.06 connect to Internet"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by IndyBob on 2007-03-05
I downloaded and made discs of Ubuntu 6.10 and 6.06 and checked the discs for errors and both will boot from my desktop.  I still cannot connect to the internet.  I have read several posts from this forum and cannot find the exact problem that I think I have.  I think that Ubuntu does not recognize my ethernet card.  It is an old card and in XP it says it is a NE2000 Compatable ISAPNP Ethernet Adapter Generic.  In XP I connect to the internet with a cable modem and it works fine.  When I have gone through in System - Administrator - Networking it only shows a dial up modem to set up.  So I tried several different commands I read about the the last two I tried were as follows.

Sudo ifconfig - I got the following report:
Link endcap: Local Loopback
Inet addr: 127.0.0.1  Mask: 255.0.0.0
inet6 addr:  ::1/128  Scope: Host
UP LOOPBACK RUNNING MTU 16436 Metric: 1
RX packets: 84 errors: 0 dropped: 0 overruns: 0 frame:0
TX packets: 84 errors: 0 dropped: 0 overruns: 0 carrier:0
collisions: 0 txqueuelen: 0
RX bytes: 6232 (6.8KiB) TX bytes: 6232 (6.0 KiB)

I also tried sudo getit /etc;dchp3/client.conf
and received the message:
sudo getit: command not found

I did go into Firefox and and reset ipv6 to true

What can I do to get Ubuntu to recognize my ethernet card or what other assistance can anyone suggest.

Thanks!

---

### Post by Paerez on 2007-03-05
what does "lspci" spit out?

---

### Post by doobit on 2007-03-05
> **IndyBob said:**
> 
I also tried sudo getit /etc;dchp3/client.conf
and received the message:
sudo getit: command not found

I did go into Firefox and and reset ipv6 to true

What can I do to get Ubuntu to recognize my ethernet card or what other assistance can anyone suggest.

Thanks!

FYI

getit should be gedit

also, did you try ```
sudo modprobe ne
```
to load the ISA driver for that card?
Then type ```
sudo dhclient
```
to restart the DHCP client?

---

### Post by IndyBob on 2007-03-05
For Paerez: I tried Ispci and it reports that it's not found

For Doobit:
I tried modprobe ne and got no response just another command line

I tried sudo dhclient and got the following:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium all rights reserved
for info please visit [http://isc.org/sw/dhcp](http://isc.org/sw/dhcp)
Cant create /var/lib/dhcp3/dhclient.leases:Default permission denied
drop-privileges: cold not set group id: operation not permitted

Is there anything else I should try?

I know it needs linix drivers for my video card as I had to switch it to VGA cable and not DVI, but unless I decide to install it, I am not going to download those.

I am surprised since the card is so old that it will not find drivers for the ethernet card and install them automatically.

Any additional assistance would be greatly appreciated as I think it would be a great system to use.

---

### Post by doobit on 2007-03-05
> **IndyBob said:**
> For Paerez: I tried Ispci and it reports that it's not found

For Doobit:
I tried modprobe ne and got no response just another command line

I tried sudo dhclient and got the following:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium all rights reserved
for info please visit [http://isc.org/sw/dhcp](http://isc.org/sw/dhcp)
Cant create /var/lib/dhcp3/dhclient.leases:Default permission denied
drop-privileges: cold not set group id: operation not permitted

Is there anything else I should try?

I know it needs linix drivers for my video card as I had to switch it to VGA cable and not DVI, but unless I decide to install it, I am not going to download those.

I am surprised since the card is so old that it will not find drivers for the ethernet card and install them automatically.

Any additional assistance would be greatly appreciated as I think it would be a great system to use.

When you run modprobe ne and it works, then you may not get an error. Check it by typing lsmod ne, and tellus what it says.
The other error sounds like you didn't get sudoer permission for some reason.

---

### Post by IndyBob on 2007-03-05
I tried Ismod ne and got the following response:

Command Not Found

Then I tried Ispci and got:
Not Found

Do I need to go and get a new ethernet card that Ubuntu may recognize?  My card was put in about 8 years ago when I first went with Cable internet access by Comcast when we lived in Indiana.

Other suggestions are welcomed!

I also retried Modprobe ne and got the following error this time:
WARNING: Error inserting 8390 (/lib/modules/2.6.15-26-386/kernel/drives/net 8390.ko): operation not permitted
FATAL: Error inserting ne (/lib/modules/2.6.15-26-386/kernel/drivers/net/ne.ko):Operation  Not permitted

---

### Post by chaplanger on 2007-03-05
Have you installed either of the operating systems (6.06 or 6.10) or are you simply running them off the live CD at this time?  I didn't have internet access on my system until I actually installed Ubuntu on the hard drive.

---

### Post by IndyBob on 2007-03-05
I have only been running 6.06 and 6.10 just from the disc as I didn't want to install until I saw if it was something I really wanted to go to.  Do any of the live CD Linux programs have access to the internet from the CD?

---

### Post by doobit on 2007-03-06
> **IndyBob said:**
> I tried Ismod ne and got the following response:

Command Not Found

Then I tried Ispci and got:
Not Found

Do I need to go and get a new ethernet card that Ubuntu may recognize?  My card was put in about 8 years ago when I first went with Cable internet access by Comcast when we lived in Indiana.

Other suggestions are welcomed!

I also retried Modprobe ne and got the following error this time:
WARNING: Error inserting 8390 (/lib/modules/2.6.15-26-386/kernel/drives/net 8390.ko): operation not permitted
FATAL: Error inserting ne (/lib/modules/2.6.15-26-386/kernel/drivers/net/ne.ko):Operation  Not permitted

the command is lsmod (little L, not I) and lspci (Little L not I) for list modules and list pci cards.
The error is because you are not running it as root. When you type sudo in front of a set of commands the first thing it should do is ask for your password. The error you got shows me that the module exists, now you just need to type the right string to load it.
```
sudo modprobe ne
password: <insert your password here>
```

Now if you type lsmod (little L) you should get a list of the modules that are loaded. One of them should be the ne.ko or the net8390.ko module.
That is the driver for your card.

If nothing else works, then you should get a plug and play PCI card, if you have a PCI slot to put it in, that is.

---

### Post by IndyBob on 2007-03-06
doobit:

Well, I solved some of the problems:

I downloaded 6.10 again from another site.  Burnt new CD at 6x and checked it for errors and then booted into Ubuntu and viola, can get on internet from desktop, so old files must have been corrupted or burn was not good on first CD.  I have noticed that running on desktop, I can barely see the startup screen (progress bar) so it may be when I checked the first CD that an error was shown and I couldn't see that it was there.   Thanks for all your help.  Now my big decision is do I go ahead and install.  What is the easiest way to take my bookmarks from my XP version of Firefox and import into the Linux version?

---

### Post by doobit on 2007-03-07
> **IndyBob said:**
> doobit:

Well, I solved some of the problems:

I downloaded 6.10 again from another site.  Burnt new CD at 6x and checked it for errors and then booted into Ubuntu and viola, can get on internet from desktop, so old files must have been corrupted or burn was not good on first CD.  I have noticed that running on desktop, I can barely see the startup screen (progress bar) so it may be when I checked the first CD that an error was shown and I couldn't see that it was there.   Thanks for all your help.  Now my big decision is do I go ahead and install.  What is the easiest way to take my bookmarks from my XP version of Firefox and import into the Linux version?

Great! I had suspected a possibility like that, but I'm glad you got it going now. I think Firefox  book marks are just saved as an html file in the firefox folder, so you should be able to copy them to a CD or pendrive or even a floppy.

---

