---
title: "Wow!  The Wireless Works - But Printing Gives me the finger..."
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by margni on 2006-06-30
I can't seem to find what I'm looking for, so I'm asking for a tiny bit of help...

I open the manager for printers...  System >> Administration >> Printers.
Dialog opens.

I click Printer >> Add Printer and now I have 3 steps...

I set up:

Network Printer >> Unix Printer (LPD)
Host:  192.168.1.78
Queue:  L1

>> Forward

Manufacturer:  HP
Model: PSC 500 
Driver: hpijs (recommended)  - I take this as the default

>> Forward

Name:  HP500
Description:  Blah
Location:  Blah

>> Apply

NOTHING HAPPENS!  The printer doesn't show up next to the new printer icon.

What am I not doing?

Any help would be great!

********  On the other hand...

My Older Linksys WPC11 v4 was instantly recognized and I smiled as Ubuntu turned on PCMCIA support and the card lit up.

I Opened up Networking  and only had to add my essid, and a wep key
(But I learned a trick with this distro...)
In other distros if I entered the wep key I had to put a '0x' in front of it because the wep key is usually in Hex.

Here I only had to put the wep key in as it is, and not use '0x'...  Trial and error... got it to work!

My problem is only what I'm doing wrong with the wireless print server as it works in my other distro (and wireless after i had to massage it to work)...

Any suggestions?

Thanks
Margni

---

### Post by richbarna on 2006-06-30
HP printer howto :-
[http://www.ubuntuforums.org/showthread.php?t=184838&highlight=howto+HP+printer]("http://www.ubuntuforums.org/showthread.php?t=184838&highlight=howto+HP+printer")

---

### Post by Kobalt on 2006-06-30
Hello,

I don't know if that might help : 
I had the same problem with my HP Printer, every time I tried to configure it, it was not recognized... Then I turned the printer on BEFORE booting into Ubuntu and then : here it was, detected... Since then it works like a charm. 

I hope it'll be as easy as this for you ! 

Cheers !

---

### Post by margni on 2006-06-30
Kobalt, richbarna,

Thanks for the responses...

I took a look at the links that richbarna sent, and I already have the hpjis, et all loaded in synaptic.

I confess, I'm running the 6.06 live CD.  I don't know if I like a distro til I make it work this way.    I had the printer up and running before I booted the cd.  The problem really is in using the printer setup gui, to set up an lpr printer on a wireless print server...

I've given it a name, IP + queue, etc...  when I click finish, nada!  The newly-created printer doesn't even show up as a choice.  I guess I need to know how to create printers w/ubunto that'll stick...  

Thanks for your help, but if you know something I'm missing here... Please shine a little light on it!

Again, thanks!
margni

---

### Post by margni on 2006-07-06
I've been banging around forums and I'm still having trouble with printing...

I'm running the live CD, since if it won't print from that then whats the bother of switching to this over my current FC4...?

Anyhow,  I'm running the gnome-cups-manager.

I'm selecting network printer  >>  Unix LPD
I give it the dotted address  192.168.1.78
I give it a queue:  L1

I pick out the printer, and the same driver (hpijs) and finish...

The new printer doesn't even show up in the gnome-cups-manager window, and no printing...

Where am I going wrong here?  ](*,)

---

### Post by margni on 2006-07-18
Well... Still beating my head against a wall over the Linksys WPS11 Printserver...  The live CD doesn't seem to like printing...!

I've tried calling the gnome-cups-manager from sudo, then setup with a Networked Unix LPD (the same as my Fedora Core 4 Print setup that works)
Tried <address> then LPR, lpr, L1, L2, Nothing!!!!

I've tried calling the gnome-cups-manager from sudo, then tried IPP as well...  Nothing!

When I was calling the print setup manager from the terminal I got the following:

** (gnome-cups-add:11036): WARNING **: IPP request failed with status 1280

Even when i tried this -setting up the printer as IPP- I get the same thing, AND the printer won't show up at all in the printer setup box as a newly-created printer - regardless of what I set it up as (local user, sudo)

I've been all over the forum here, 

Any help out there?

The reason I'm liking Ubuntu is that it'll run my wireless card(linksys WPC11 v4) - flawlessly - without ndiswrapper, but if it won't print to the rest of the wireless stuff...  Help! Please!

---

### Post by orb9220 on 2006-07-18
Maybe its a limitation of live cd versus installed?

Just a thought.

---

### Post by margni on 2006-07-18
But why would the usually tough stuff i.e. wireless connection work like such a champ, and then the simplest of tasks (at least from my FC4 experiences) of setting up a wireless printer be so <insert your explicative here> difficult?

I'm just trying to save myself a lot of issues by trying this distro out first from a Live CD, rather than going through the pain and suffering of 3 versions of Fedora - which by the way is still the best until Ubuntu proves different.  I hear all this and that about Ubuntu, then when it gets to this I don't know if I want to really pursue this distro...  And if I can't do the simple stuff - print a document - then how much work is it to set up a webserver, or etc...? 

On the other hand, have you tried out the live CD and configured a printer?  Try it, and tell me if I'm wrong here...

Thanks for the response orb9220... Maybe you're right... ???

---

### Post by richbarna on 2006-07-18
Is the pgp encryption set up ok? I found this :-
> [IMG]http://www1.linksys.com/support/images/bullet.gif[/IMG]**Wired Equivalent Privacy (WEP) Troubleshooting**   Configuring WEP encryption can be confusing, especially when using multiple  WLAN products from different vendors. This article will offer some simple  suggestions to aid your WEP configuration. A short description of the methods of  WEP Encryption will help to avoid some of this confusion. Note: your WAP11 will  only support 64-bit WEP. There are two levels of WEP Encryption &#65533; 64 and 128 bit. You may also have  heard the number 40-bit used in conjunction with WEP Encryption.  **4****0-bit WEP and 64-bit WEP are two different names for the same  encryption method. **This level of WEP encryption has been called 40-bit  because it uses a *_**40-bit secret key**_* along with a  **24-bit Initialization Vector (40 + 24 = 64)**.  Because  there has been no official standardization of these terms, wireless vendors may  use either name. For the purposes of this document, the term 64-bit will be used  to refer to this level of encryption.** Now, some simple troubleshooting tips for WEP configuration&#65533; **[LIST=1][LIST=1]
[*]If possible, before attempting to configure WEP, disable encryption and      make sure your wireless network is functioning.
[*]**128-bit WEP will NOT communicate with 64-bit WEP**. 128-bit WEP      also uses a 24-bit Initialization Vector (IV), however, it uses a 104-bit      secret key. Therefore, make sure that all of your wireless devices are using      the same encryption level. All Linksys wireless devices will support 64-bit      WEP, as outlined in the 802.11b standard.
[*]If using a Passphrase to generate your WEP key, make sure you use      EXACTLY the same Passphrase on all wireless devices. These keys are case      sensitive.[/LIST][/LIST] Linksys Instant Wireless products use a Hexadecimal key for WEP. Other  vendors may use an ASCII based key. Encryption using these two different keys  will not communicate with each other. One must be converted. To find out more  about converting from one key based encryption to another, see **Linksys  Knowledge Base Article #136**. 

It was on this site :-
[http://www1.linksys.com/support/support.asp?spid=76](http://www1.linksys.com/support/support.asp?spid=76)

You may have already seen it.

---

### Post by margni on 2006-07-18
Thanks...

I keep harping about the Wireless card - WPC11 V4 - that Ubuntu 'likes' without any ndis funky-ness...  That in itself puts me back on an all -linksys network...

I'll give it a shot though on removing the WEP key and see if it wants to dance or not...  Maybe I'll end up having to cut a partition, and load it...  But I want to give it a full wring-out prior to loading it for more permanent purposes...

More to come !!!

---

### Post by richbarna on 2006-07-18
If you do go for the install, remember you only need the "root" partition, as you've already got Fedora installed, you can use the same "swap", and just direct grub to overwrite your existing bootloader. You would only need 3 Gb for a test run.

---

### Post by richbarna on 2006-07-18
Another tip:-
> **A word of caution: When you install the driver and add a new printer, make sure you select "local printer attached to this computer." Do NOT select "network printer." Another word of advice: If you choose to set the printserver up wirelessly, make sure that your network is set to the factory default (SSID linksys, no WEP encryption, channel 6) or you will waste hours of time on the setup. If you keep recieving an error message when you try to print, try turning the firewall on your computer off. Once the device is set up properly, you should experience no further difficulties.** 
Came from a windows user, but some of his advice may help :-
[http://www.wi-fitechnology.com/Wi-Fi-Products-B00005Y7DP.html](http://www.wi-fitechnology.com/Wi-Fi-Products-B00005Y7DP.html)

And one from a Mac user :-
[http://lowendmac.com/practical/02/0827.html](http://lowendmac.com/practical/02/0827.html)

---

### Post by margni on 2006-07-19
Thanks!  I'm starting to set up and try it out...  Since I've use FC4...  Is the installer Anaconda - or is it some other type?

I want to thank you for the links and advice...  I'm taking this in to consideration before starting anything, or freaking out what I know works to the tee...!

---

### Post by margni on 2006-07-26
I wanted you all to know I got this problem fixed by installing Ubuntu, instead of just running it from a live CD.  

Once Installed, I added a printer, then configured it:
Unix LPD
Dotted Address
L1 for queue
Picked out printer brand/type

Printed a test page over my wireless print server...

Thats it!  Thanks for all your help out there!

---

