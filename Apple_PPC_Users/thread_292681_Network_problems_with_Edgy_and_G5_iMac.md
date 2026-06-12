---
title: "Network problems with Edgy and G5 iMac"
date: 2006-11-04
forum: Apple PPC Users
---

### Post by mike_hore on 2006-11-04
Hi folks,

Well I've got Edgy installed, applied the fixes so the fans are quiet and the screen resolution is right, but now I'm getting network oddities.

I'm on broadband with an ADSL modem connecting to the Ethernet port.  The network configuration seems OK (automatic DHCP).  Ping  works fine.

But when I run Firefox, it seems to get lost in the weeds.  Usually fhe first site I look up will load with no problems, but when I follow a link, nothing happens.  The status message says "connecting to ...", but the modem lights show no network activity, and everything just sits there till Firefox times out.  However if I ping the site, this works.  Then after pinging, if I manually enter the URL into Firefox, lo and behold it works.  Sometimes.  Pinging in isolation doesn't fix it -- I have to hit stop in Firefox and reload or re-enter the URL.

I do have the Firefox preference "direct internet connection" set.

Everything works fine in OSX, including Firefox.  So I know it's not a hardware problem.  Has anybody else run into this?  It's a standard 17 inch RevA G5 iMac, with Edgy and OSX on different partitions.  Nothing else unusual.

--  Mike.

---

### Post by stream303 on 2006-11-04
Hi Mike - running the same setup as you (although 20").  I don't think this is related to the iMac in particular and probably has more to do with dns resolving timeouts.

What does your **/etc/resolv.conf** look like?  Are your isp's nameservers the first in the list and your routers nameserver last?  I wrote a few posts about how to fix that but lets see if that's even a problem.

I dislike using the removal of ipv6 as a "magic pill" but I don't use it anyway sitting behind a home router:

In Firefox url tab:
1) type about:config
2) In the filter box, search for ipv6
3) double-click the found entry to change the boolean value from false to true
4) Restart Firefox

System-wide ignoral of ipv6:
1) create a "bad_list" file **/etc/modprobe.d/bad_list**
2) the contents should be just one line:

**alias net-pf-10 off**

Reboot / restart system (not very elegant - bad habit) :)
Let see how that goes!

---

### Post by mike_hore on 2006-11-04
> **stream303 said:**
> Hi Mike - running the same setup as you (although 20").  I don't think this is related to the iMac in particular and probably has more to do with dns resolving timeouts.

What does your **/etc/resolv.conf** look like?  Are your isp's nameservers the first in the list and your routers nameserver last?  I wrote a few posts about how to fix that but lets see if that's even a problem.

I dislike using the removal of ipv6 as a "magic pill" but I don't use it anyway sitting behind a home router:

In Firefox url tab:
1) type about:config
2) In the filter box, search for ipv6
3) double-click the found entry to change the boolean value from false to true
4) Restart Firefox

System-wide ignoral of ipv6:
1) create a "bad_list" file **/etc/modprobe.d/bad_list**
2) the contents should be just one line:

**alias net-pf-10 off**

Reboot / restart system (not very elegant - bad habit) :)
Let see how that goes!

Hi, thanks for the advice!  I'm not sure how to get my ISP nameservers but I'll look at my OSX setup which is working.  I'll give you the other information when I have time to get it all.
However ping seems to be resolving names OK, for what that's worth.
-- Mike.

---

### Post by mike_hore on 2006-11-04
Hi again,

Problem solved!!  My resolv.conf just had one line:
nameserver  10.1.1.1
which is my local machine, so I thought that might be the problem, but it wasn't.  ipv6 was.  As soon as I turned that off in Firefox as per your advice, everything started working.

So I'll apply your system-wide solution shortly.

Cheers, and thanks, Mike.

---

### Post by stream303 on 2006-11-05
Glad that worked!

Note that I'm not anti-ipv6, it's just that it's anybody's guess as to how well our windows-centric hardware follows the ipv6 specs.  I suspect that the code in Ubuntu is done properly.

I even disabled it when I ran OSX since it was over the top behind a simple nat-router.

---

### Post by mike_hore on 2006-11-05
Yes, everything's working now.  I also noticed that on the OSX side, Firefox has ipv6 disabled.
But just one thing I'm wondering:  what's ipv6 anyway?  This is all new to me.

Cheers,  Mike.

---

### Post by mike_hore on 2006-11-05
> **mike_hore said:**
> Yes, everything's working now.  I also noticed that on the OSX side, Firefox has ipv6 disabled.
But just one thing I'm wondering:  what's ipv6 anyway?  This is all new to me.

Cheers,  Mike.

I mean by that that I'm a bit of a newbie with networking.  With MacOS, everything usually Just Works.

But I'm still having trouble with Evolution email -- the symptoms are similar -- instead of fetching my mail it just sits there till it times out.  It doesn't even ask for my password.  This is suspiciously similar to the problem I had with Firefox.  But I have  followed the instructions to globally disable ipv6.
-- Mike.

---

### Post by stream303 on 2006-11-05
I'll assume that Firefox is working and you are posting here with it now?  It's just that Evolution is giving you probs right?

You may want to review your mail setting in evolution to doublecheck:
username
password
pop-server address  (inbound mail like pop.myisp.net)
smtp-server (outbound mail like smtp.myisp.net)
These settings may still be on your OSX installation.

I'd also look at /etc/resolv.conf again now that you've disabled IPV6 just to see if it may have picked up anything new.

Did the nameserver you get before in /etc/resolv.conf match what was found in your network settings in OSX?

Note that while I enjoyed Evolution for awhile, I personally prefer Firefox's email-mate: Thunderbird.  You may want to try that as well.

---

### Post by stream303 on 2006-11-05
Just a quick thought until we get this straightened out:

Since these problems are more generic and not apple-specific anymore, we should probably take this to the other setup forums or private email.

Since your browser is working, I'd recommend getting a free web-based email account from the like of [www.gmail.com](www.gmail.com), yahoo, etc.  Always good to have a secondary mail address you can use from anywhere.

You'll get regular email working no doubt, but this would bring your iMac u p to a minimum level of usability right off.  Send me your address in the private mail here and I'll be happy to assist a fellow iMac'er!

---

### Post by mike_hore on 2006-11-06
> **stream303 said:**
> I'll assume that Firefox is working and you are posting here with it now?  It's just that Evolution is giving you probs right?

You may want to review your mail setting in evolution to doublecheck:
username
password
pop-server address  (inbound mail like pop.myisp.net)
smtp-server (outbound mail like smtp.myisp.net)
These settings may still be on your OSX installation.

I'd also look at /etc/resolv.conf again now that you've disabled IPV6 just to see if it may have picked up anything new.

Did the nameserver you get before in /etc/resolv.conf match what was found in your network settings in OSX?

Note that while I enjoyed Evolution for awhile, I personally prefer Firefox's email-mate: Thunderbird.  You may want to try that as well.

Right, it's just Evolution that's giving the problems.  I've now had some success in RECEIVING emails, but I still can't send.  On the Mac side, it shows my ISPs mail server doesn't require authentication for sending, but I'm still getting a password request in Evolution.  It then says the authentication has failed, even though I put in the correct password.  I tried with both "requires authentication" on and off, just to be sure.

Thunderbird?  Sorry, there's no version for PowerPC Linux.  Web-based email?  Can't stand it.  Anyway, I've sent you my email address privately so we can continue there and post again when we get it sorted out.  Thanks for the help.

Cheers,  Mike.

---

### Post by mike_hore on 2006-11-07
For anyone interested, this one's all fixed now.  The final step was to ensure that /etc/resolv.conf has my ISP's DNS IP address as its first line.

resolv.conf gets rewritten at boot time, so the right fix is to edit as root /etc/dhcp3/dhclient.conf.
There's a line

#prepend domain-name-servers 127.0.0.1;

I had to remove the # (uncomment the line), and substitute the right IP address for the DNS (which I got from my OSX Ethernet setup).

Then everything works.  I hope this might help somebody.

Cheers,  Mike.

---

