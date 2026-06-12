---
title: "Raspberry Pi Watchdog Setup - Network &quot;ping&quot; multiple IP's"
date: 2014-07-14
forum: Any Other OS
---

### Post by greavette on 2014-07-14
Hello,

I'm hoping this community can give me some direction on the Watchdog Timer and it's setup.

I'm using Debian on the Raspberry Pi and installed the watchdog daemon.  It's working well in that I've setup the Watchdog to check on an IP (my router) and I reboot the router the Pi does reboot as well.  What I'd like to do though is setup Watchdog to watch 2 IP's and not just one.  In this way I can reboot one of the 'watched' devices and not reboot the Pi.  

I know in the Watchdog setup I use Network "ping" and the example on this page seems to say I can use more than one IP - [http://www.sat.dundee.ac.uk/psc/watchdog/watchdog-configure.html](http://www.sat.dundee.ac.uk/psc/watchdog/watchdog-configure.html).  Problem is though if I put in two IP's into my Watchdog config file and I reboot only one of the 'watched' IP's my Pi still reboots which is not what I wanted to happen.

Is this possible to watch two IP's to help ensure my Pi doesn't unnessarily reboot?  

Thank you.

---

### Post by QIII on 2014-07-14
*Moved to **Other OS/Distro Support***


I also modified your title -- hopefully "Raspberry Pi" will catch peoples' attention!

If this doesn't get some response, feel free to bump it (but not too soon, please).

---

### Post by tgalati4 on 2014-07-14
What is the top-level thing that you are trying to accomplish?  What is the Use Case?

There might be a simpler method to accomplish this, than using *watchdog*.  

Why are you rebooting the router?  How often does it need rebooting?

Couple of things you can do in the meantime:  

Set verbosity to yes:

  verbose = yes

```

  grep -h 'watchdog' /var/log/syslog.1 /var/log/syslog
```

Run some tests, take notes and compare the behavior you observe with what is logged in the logfile.

I think multiple IP's use a "OR" condition, so if any IP's in your list go down, watchdog barks.

My dog will bark if there are squirrels in the back yard or if there are cats in the back yard.  He goes crazy if there are both.  I don't think I could train my dog to only bark when there are cats and squirrels in the back yard.

---

### Post by greavette on 2014-07-15
Thank you!  :)

---

### Post by greavette on 2014-07-15
I'm using the Raspberry Pi as a kind of cheap thin client for some workstations in our small office.  I have decent power to the pi (powered by a cirago usb hub).  The setup is quite stable in that our workers don't even know they are using a linux thin client to rdesktop into their VM.  But every once in a while we have a thin client get 'locked' in that the mouse and keyboard don't work.  The only solution is to reset the power switch on the usb hub to reboot the Pi.  I'd rather not do this for corruption purposes.  I'd also like to make this setup as smooth as possible so the thin clients can handle 'lockups' themselves.  I support this small business remotely so anything I can do for myself to make things run more smoothly will help me and the office.

My thought was to use a watchdog timer on the Pi to solve for potential 'lockup' issues.  

We don't reboot our router very often, but in the event we had to reboot it I don't want all our Thin Clients suddenly rebooting on us.  So this is why I thought watching two IP's on our network would allow the reboot of either 'watched' hardware without causing issues to our workstations.

I will take your suggestion and look at my logfile after turning on verbose.  

I had also thought an OR statement would be involved in the watchdog.conf but from my research on setting up the watchdog.conf I don't see any OR statements being used.

---

### Post by greavette on 2014-07-15
Perhaps I should ping a broadcast address instead?

Not sure what to use for that thought (would it be 255.255.255.255)?

---

### Post by tgalati4 on 2014-07-15
Couple of things:

RaspberryPi's are not known for their 24/7 reliability.  Some board manufacturers are better than others.  Do a search in the RP forums and you will see recommendations.

Power seems to be an issue with RP's.  They need a rock-stable power supply capable of 2 amps at 5.000 volts.  Most USB hubs won't provide that.  Any dip in voltage (4.8VDC or so) and your RP locks up.  No mystery here--they just don't have a robust power section.  I would not recommend them for business use or any critical use (like medical monitoring).

Running *watchdog* just gives the RP an additional reason to reboot--over and above the hardware issues.

There are lots of low-cost PC options--RP is just not designed for business use.

Anyone else running RP's 24/7 in a business?

---

### Post by greavette on 2014-07-15
I appreciate your comments and I do understand that the Pi was not designed for business.  We are using our Pi's as thin clients only in situtuations where they are not critical.  But to be honest we've found the Pi's to be very stable for us over the past year we've been using them.  

We use a 7 port cirago USH1070 usb hub.  One of the hubs is a charging port delivering 2 amps and we use this port for powering out pi.  So far it's been working very well for us.  We typically have plugged into the hub at each workstation a mouse, keyboard, barcode scanner and sometimes a weight scale (serial to usb converter cable used).  

The only reason I wanted a watchdog system in place was for 'just in case' scenarios where they pi gets locked up.  Not something that happened very often to us over the past year.  But I do take your point that putting in place a watchdog gives the Pi a reason to reboot when no real reason exists.  And if for some reason the Pi gets stuck in a loop that workstation would be in big trouble.

The employees at our office have instructions on how to reboot the thin client without just turning it off and on.  But in the event they need to force a reboot the usb hub can do that for them, but they have to let me know when they've done it.  Perhaps what I'll put in place as well is an email script to let me know when a thin client has been rebooted (on startup).

If anyone else has suggestions on how I can ping mulitple hardware ip addresses using watchdog it would be good information to have still.

Thanks!

---

### Post by tgalati4 on 2014-07-15
Perhaps some USB hubs are better than others.  If you have all of those devices plugged in, and you have a power dip, do you still get 2 amps out of the charge port?  Perhaps putting the RP's on a separate power supply (at least the ones you have trouble with).  As power supplies age (capacitors get weak) their voltage tends to dip.  A charging port does not provide the stable, clean power that the RP's require.  

As far as multiple pings:

>   In ping mode watchdog tries to  ping  the  given  IP  addresses.  These
       addresses do not have to be a single machine. It is possible to ping to
       a broadcast address instead to see if at least one machine in a  subnet
       is still living.

    [B]   Do not use this broadcast ping unless your MIS person a) knows about it
       and b) has given you explicit permission to use it![/B]

       watchdog will send out three ping packages and wait  up  to  <interval>
       seconds  for  the reply with <interval> being the time it goes to sleep
       between two times triggering the watchdog device.  Thus  a  unreachable
       network will not cause a hard reset but a soft reboot.

So using a subnet (such as 10.10.2.0) should ping all addresses on the "0" subnet.  This might generate a lot of extra network traffic--hence the warning.

How many of these RP's do you have set up?  How many need rebooting on a daily basis?  I would focus on the few that are failing and fix the power problem first, rather than put watchdog timers on all of them, each pinging the network every minute.  That might be chaos.  

RP's are also known to have network card issues.  The chip that controls the USB also controls the ethernet, so if you have a lot of network and USB traffic, the ethernet chip locks up.  In that case, you might consider how you have the RP's hooked up, and perhaps reduce the ethernet speed to 10 MB/sec instead of 100 MB/sec to allow more USB bandwidth.  Again, these were not designed to be robust devices, but cheap learning computers.

---

### Post by greavette on 2014-07-15
All very good points here.  I'm not sure I want to broadcast out to my network from our 5 Pi's to ensure they haven't locked up...especially since we don't get lockups.  I was hoping to be proactive here with my install of watchdog but the more I think about it I don't think I need it now.   It's not like we have a problem with locked up Thin Clients.  And if we did we would not be using them as I do agree they are made for learning and not business enterprise.

Thank you for your insights into my question.  I very much appreciated it.

---

### Post by SeijiSensei on 2014-07-15
You can use nmap to ping all the hosts in a network subnet, e.g.,
```
nmap -v -sP 192.168.1.0/24
```
returns a result like this:
```

Starting Nmap 6.40 ( http://nmap.org ) at 2014-07-15 16:46 EDT
Initiating Ping Scan at 16:46
Scanning 256 hosts [2 ports/host]
Completed Ping Scan at 16:46, 2.38s elapsed (256 total hosts)
Initiating Parallel DNS resolution of 256 hosts. at 16:46
Completed Parallel DNS resolution of 256 hosts. at 16:46, 5.50s elapsed
Nmap scan report for 192.168.1.0 [host down]
Nmap scan report for DD-WRT (192.168.100.1)
Host is up (0.0011s latency).
Nmap scan report for 192.168.1.2 [host down]
Nmap scan report for 192.168.1.3 [host down]
Nmap scan report for 192.168.1.4 [host down]
Nmap scan report for 192.168.1.5 [host down]
[...]
Nmap scan report for 192.168.1.35 [host down]
Nmap scan report for android-something.local (192.168.1.36)
[...]

```
I've used this in scripts to identify hosts that are down.

---

