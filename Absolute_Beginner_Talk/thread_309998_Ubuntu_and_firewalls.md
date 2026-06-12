---
title: "Ubuntu and firewalls"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by John E on 2006-11-30
Maybe this should really be on the Security forum - but it all seems to be server based, over there....

Having managed to get my internet connection running, what's the situation with firewalls under Ubuntu? I assume they're still necessary because things are still out there pinging me and no doubt trying worse...! I assume that anti-virus software isn't too much of a priority but what's recommended in the way of firewalls?

---

### Post by 56phil on 2006-11-30
Hope this helps.

[http://www.linux.com/article.pl?sid=06/06/26/1556259]("http://www.linux.com/article.pl?sid=06/06/26/1556259")

---

### Post by msak007 on 2006-11-30
> **56phil said:**
> Hope this helps.
 
[http://www.linux.com/article.pl?sid=06/06/26/1556259](http://www.linux.com/article.pl?sid=06/06/26/1556259)
Interesting article...mentions Lokkit (a firewall I had never heard of), then links to Red Hat instructions for installing and configuring it. Then it mentions Guarddog, but doesn't mention Firestarter anywhere in there. Maybe I'm missing something, but if the target of that article was your average home desktop user looking for a firewall, wouldn't you recommend Firestarter before Guarddog? Guarddog, while powerful, is very complex and may leave many users confused (or with broken iptables rules that won't let them access anything). Also, I've always been under the impression that Guarddog is more of a KDE app, which puzzles me even more that Firestarter was not mentioned as it is a GTK / Gnome app.

---

### Post by PurplePenguin on 2006-11-30
I recently made the switch to Ubuntu from another distribution.  I had played with Guarddog before, but had quite a difficult time figuring it out (and I consider myself to be quite handy with computers). :) 

So when I searched the Ubuntu package manager for a firewall, Firestarter was the one that came up.  I installed it and am quite amazed.  It's the closest thing to ZoneAlarm (which I used to use when I was running a system under Windows) that I've found in the linux world.  That is, it's quite easy to block/unblock things, no complex setup, and I'm confident that the firewall will actually do what I'm trying to get it to do!

Firestarter seems to be the most intuitive of all that I have tried, and I do recommend it to any other linux user.

---

### Post by msak007 on 2006-11-30
That's exactly why I mentioned Firestarter, as it is the easiest firewall app I'm aware of for Linux (there aren't many apps to begin with). I personally use Firestarter as well. I dabbled with Guarddog and got most of the ports and rules I needed configured, but I had several issues with it:
 
1. Couldn't get the UPnP feature of KTorrent working with the firewall enabled. It must use some odd undocumented port to communicate with the router, because I enabled every single port I set manually in the app and checked off every protocol in the list to test it and it still wouldn't work. Turn it off, boom it works. A minor quibble, I know how to forward ports manually - but the point is the feature should work and it didn't, and I couldn't find any logs to let me know which port was being blocked so I can open it up.
 
2. Creating custom rules. They're easy to create and apply, but if you delete a custom rule / port from the advanced field, the corresponding entry in the list of protocols does not go away. This can get very annoying.
 
3. While not a huge point for me, some people (especially ex-Windows users who are used to using apps such as ZoneAlarm) want a System Tray icon. Firestarter provides this and changes to a red lightning bolt when it detects a possible intrustion or activity that is blocked so you can click on it and check the activity log. I know the GUI is not necessary and the firewall runs in the background, but some people like the re-assurance of a GUI and an icon they can click on to check the status.
 
So overall, I'd recommend Firestarter over Guarddog to someone who is just starting out. If I ever figure out the KTorrent thing though I might consider switching back to Guarddog.

---

### Post by John E on 2006-12-01
Thanks for all the suggestions. I'll see if I can obtain Firestarter, today.

---

### Post by stream303 on 2006-12-01
quick tip:

Once you install and run firestarter just once, your firewall is active from then on, even after a reboot - you just won't *see* it running.  You don't need the firestarter gui running all the time.  It is just a front-end setup program.

If you want additional protection, you can re-run firestarter and set other options.

Ubuntu is very safe since it doesn't run unecessary services out of the box.  If you are behind a nat-router, you are better still.  If that nat-router has an internal firewall active, then you've got even more protection.

I guess what I'm trying to say is that depending on the situation, firestarter shouldn't be considered mandatory and could even be overkill.

If your connection is direct from your computer to a broadband modem, without an intervening router, then I'd run the firestarter gui at least once.  But that's me.  I also run *some* sort of firewall (internal to router etc) just to help keep my system 's eyes closed to the internet "background noise", probes and whatnot :)

---

### Post by zalo on 2006-12-01
> Having managed to get my internet connection running, what's the situation 
> with firewalls under Ubuntu? 

Firestarter (GTK based) is the natural choice for a Gnome desktop. 
I am using it myself.

If you are on Kubuntu, concider Guarddog (QT based).
I use Guarddog on Gentoo. It needs to be set up properly first, and it's easy to mess up if you don't know what you're doing.

Firestarter is the easiest to use IMO, because you can start with the default setup, and then look into the details later. It also lets you see what's happening, which i love. :cool:

---

### Post by zalo on 2006-12-01
> If I ever figure out the KTorrent thing though I might consider switching 
> back to Guarddog.

You can use Firestarter to see what Ktorrent is doing, and then enable the ports in Guarddog.

---

### Post by foofy on 2006-12-01
> Thanks for all the suggestions. I'll see if I can obtain Firestarter, today.

Take a look at automatix2 its simple to install.
There is an option to install Firestarter with a virus scanner.
Its simple, clean and has lots of other goodies too.

---

### Post by msak007 on 2006-12-01
> **foofy said:**
> Take a look at automatix2 its simple to install.
There is an option to install Firestarter with a virus scanner.
Its simple, clean and has lots of other goodies too.
Automatix2 detects your DE and installs a firewall accordingly - in Gnome it installs Firestarter and in KDE it installs Guarddog.

---

### Post by podunk on 2006-12-01
Actually, my understanding is the firewall is iptables and is installed and on by default in K/Ubuntu.

I visited several internet sites that do port scans when I first installed Ubuntu and the only problem is that my *router* for goodness sakes replies to pings. The computer itself is closed and all ports hidden.

The only reason I installed Firestarter is because the firewall is *too* good, I had to create a policy to allow the windows machines to access the Linux machines.

---

### Post by John E on 2006-12-01
I'm a bit confused. I downloaded and installed Automatix2 but....

a) I don't really know what to do with it - and
b) I'm not convinced it's installed FireStarter. Automatix2 seems to be some kind of automatic installer but there's no option to install any firewall. If I search my system for 'Firestarter' it finds a config file, an XML document and a couple of icons but no executable app.

Q-1) How do I find out if Firestarter is installed and working?
Q-2) What exactly is Automatix2 for...? :confused:

---

### Post by drphilngood on 2006-12-01
> **John E said:**
> I'm a bit confused. I downloaded and installed Automatix2 but....

a) I don't really know what to do with it - and
b) I'm not convinced it's installed FireStarter. Automatix2 seems to be some kind of automatic installer but there's no option to install any firewall. If I search my system for 'Firestarter' it finds a config file, an XML document and a couple of icons but no executable app.

Q-1) How do I find out if Firestarter is installed and working?
Q-2) What exactly is Automatix2 for...? :confused:


**Q-1)** 
Enter:

```
gksudo firestarter
```

in terminal.

Alternatively, go to ¨System¨, ¨Administration¨ and select Firstarter.

If you don´t find it, enter:

```
sudo apt-get install firestarter
```

to install it.

From: [¨How to install Firewall (Firestarter)¨]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Firewall_.28Firestarter.29")

**Q-2)**  I don´t use Automatix2 but you can view this thread for more info: [New Automatix2]("http://ubuntuforums.org/showthread.php?t=281520").

---

### Post by John E on 2006-12-01
Thanks - I got it installed but it doesn't seem to recognise my USB broadband modem. The only options I get for intenet devices are 1) **Ethernet Device, 2) IPv6 Tunnel** (whatever that is!) and **3) Dialup Device**.

It won't let me select Ethernet Device (because that one's also used for my LAN connection (even though this is a stand-alone PC). And if I try to select either of the other 2 options, neither of tham can be started. :(

---

### Post by Rodneyck on 2006-12-01
> **msak007 said:**
> Automatix2 detects your DE and installs a firewall accordingly - in Gnome it installs Firestarter and in KDE it installs Guarddog.

Automatrix2 does not automatically install a firewall. You have to select it for download and installation. Mine displays the Gnome Security Suite which includes a Firestarter firewall for download.

If you are behind a router, most routers come with a firewall so you can activate it and you should be good to go, none needed on ubuntu.

---

### Post by drphilngood on 2006-12-01
This guide will help you start the Firestarter firewall wizard and configure it the way you want: [Firestarter firewall wizard]("http://www.fs-security.com/docs/wizard.php").

---

### Post by John E on 2006-12-01
Thanks - but I seem to have fallen at the first hurdle here. I ran the wizard and selected my ethernet device (eth0) as the internet connection device. I also disabled internet connection sharing. However, when I try to start the firewall it says "Failed to start the firewall. The device eth0 is not ready. Please check your network device settings and make sure your internet connection is active"


It is active, because I'm using it at the moment... :confused:

---

### Post by msak007 on 2006-12-01
> **Rodneyck said:**
> Automatrix2 does not automatically install a firewall. You have to select it for download and installation. Mine displays the Gnome Security Suite which includes a Firestarter firewall for download.
 
If you are behind a router, most routers come with a firewall so you can activate it and you should be good to go, none needed on ubuntu.
I wasn't implying that it installs it automatically. I was simply stating that if you* do* opt to intall the "Security Suite" option, it detects your DE and installs Firestarter or Guarddog depending on whether you're running Gnome or KDE, respectively.

---

### Post by Rodneyck on 2006-12-01
> **msak007 said:**
> I wasn't implying that it installs it automatically. I was simply stating that if you* do* opt to intall the "Security Suite" option, it detects your DE and installs Firestarter or Guarddog depending on whether you're running Gnome or KDE, respectively.

No problems... it's all good.  ;)

---

### Post by macme on 2006-12-02
Question.
How to set ubuntu server firewall back to default, so i can have the access with webmin...
everything has to be on [COLOR="Red"]accept[/COLOR] so i can start over again

Please i need the root code

---

### Post by John E on 2006-12-04
Couldn't get Firestarter to work -so I uninstalled it and installed Lokkit. I ran the Lokkit configuration wizard and it reached the stage where it said it was about to apply my configuration settings. I pressed 'OK' and the wizard dialog just disappeared from my screen.

I don't seem to have any indication that Lokkit is now running. Is there any way to tell?

---

### Post by John E on 2006-12-04
I found something called System Monitor which gives me a list of running apps. However, Lokkit doesn't appear in the list. Should I assume it's not working?

---

### Post by Tomosaur on 2006-12-04
Yes, you should, unless Lokkit is just a one-time iptables configurator (which many linux firewalls are). I would recommend sticking at firestarter. I rarely use it unless I'm messing around with servers etc (easy way to open up ports and suchlike :P), and it sticks around, which is always good. Did firestarter give you any errors?

---

### Post by John E on 2006-12-04
Yes - every time I try to start it, it says - "Failed to start the firewall. The device eth0 is not ready."

I'm assuming that **eth0** is my PC's onboard LAN. But if that's the case, then Firestarter never even recognised that my internet connection was actually via a USB modem.

---

### Post by Tomosaur on 2006-12-04
Load up firestarter, click Edit > Preferences, then go to Network Settings. There, you can change which device Firestart watches :)

---

### Post by John E on 2006-12-04
Tomosaur - I've already tried that. It only gave me these 3 options for my internet connection device:-

1) Ethernet Device (eth0)
2) IPv6 Tunnel (sit0) -whatever that is!
3) Dialup Device (ppp0).

No matter which one of those I select, I get the error "Failed to start the firewall. The device [WHICHEVER] is not ready."

---

### Post by Tomosaur on 2006-12-04
Strange, that definately shouldn't be happening. What's the output of 'lsusb' in the terminal?

---

### Post by John E on 2006-12-04
I'm not sure what you mean by this. Do you mean "what happens if you open a terminal window and type **isusb**"?

If so, I just get the response "command not found"

---

### Post by bodhi.zazen on 2006-12-04
> **John E said:**
> I'm not sure what you mean by this. Do you mean "what happens if you open a terminal window and type **isusb**"?

If so, I just get the response "command not found"

Yes John E, it is a command to be typed in a terminal...

Typo, it should be **lsusb** with a small "L" 

[color=red] not isusb[/color] with an i

HTH

---

### Post by John E on 2006-12-04
Ah, sorry.... in that case, the relevant output is:-

```
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 005: ID 06b9:4061 Alcatel Telecom SpeedTouch ISDN or ADSL Modem
Bus 001 Device 004: ID 045e:0024 Microsoft Corp. Trackball Explorer
Bus 001 Device 003: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
```

---

