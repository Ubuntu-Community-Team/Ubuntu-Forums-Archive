---
title: "Help: Links at www.yahoo.com don't work - can't get to Yahoo email via their site"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Apollo17 on 2007-03-25
Hello.

I just installed Ubuntu 6.10 on Friday night. The install went well. I
was surfing the 'net in about an hour and all was well. On Saturday, I
upgraded Firefox to version 2.0.0.2. Then on Sunday (today) I found I
could visit [www.yahoo.com](www.yahoo.com) just fine, but that none of the links there
would work. At first I thought it was just a yahoo email problem
similar to my Windows XP machine needing the value of MTU changed to a
bigger value.

But now I see that none of the links work. I always get an error
message after a fw minutes saying the site has timed out, I know Yahoo
is working because I can access it from my XP PC, so it is not a Yahoo
problem. In searching the forum I found similar issues with Ebay, but
I'm not sure this is the same problem. On that thread they said it was
related to something called "Personal Security Manager", but I have no
idea of what that is or how to fix it.

On a side note: Google and gmail work just fine. Also, I am sending this from my Windows XP computer after I emailed it to myself using Gmail from my Ubuntu PC. The reason I had to do that was when I clicked on "Submit New Thread" in the forum, using the Ubuntu PC, I got the following error message:

Bad Request

Your browser sent a request that this server could not understand.
Apache/2.0.55 (Ubuntu) PHP/5.1.2 Server at ohiggins.ubuntu.com Port 80

So it may be related. 

I am running an Athlon 900 Mhz PC and have 512 MB of RAM. To be
candid, I'm not sure if I had tried accessing my Yahoo email via their
site before I upgraded to Firefox 2.0.0.2.

Does anyone have any suggestions? As I said, I am a complete newbie on
Ubuntu. I ordered an "Official" book at Amazon, but it hasn't come
yet. Any help and hand holding would be greatly appreciated. 

I am loving Ubuntu so far. I've not tackled trying to share disk drives or printers on my home network yet. If I can get this Yahoo thing fixed, then that may be my project for next weekend.

Thanks,

Ross

---

### Post by Schalken on 2007-03-26
Really, truly odd. Yahoo works fine from here (ff2.0.0.2). Go to the yahoo site, click on a link, and when it says "Timed out", grab the domain of the page you were accessing (part after the http:// and before the next /) and go to System>Administration>Network Tools> Ping (tab), paste the domain in the box and try to ping. If you get a respose, then it is likely to be a problem with FF and not the system's network config. Then try openinig Synaptic (Sys>Admin>Synaptic) search for firefox, right click, "completely remove" (this will erase any firefox settings, cache, saved passwords and history), apply, then install firefox again and see if it is still broken.

---

### Post by tatster on 2007-03-26
Hi,

Have you tried pinging any of the links at Yahoo to see if DNS resolution is working correctly?

Eg:
 
```
ping uk.yahoo.com
```

Tat.

---

### Post by AndrewB on 2007-03-26
This happend to my wife a few days ago. However she uses winXP. 

The problem self resolved, was on Yahoo's side not ours.

Ymmv,
Andrew

---

### Post by Apollo17 on 2007-03-26
Hey there - Ross here - still unresolved issue.

I did try pinging the domain as suggested by Schalken and tatster. The
ping worked just fine. In fact, I loaded Epiphony just for the heck of it and tried it, and
the weird thing is that it WORKED - but slowly - then died. I was
actually able to open one email at Yahoo.

Then when I clicked on a back arrow to see if I could open another
one, it too timed out saying "us.f339.mail.yahoo.com dropped the
connection. The server dropped the connection before any data could be
read. The server may be busy or you may have a network connection
problem. Try again later."

Scalken suggested using Synaptic Package Manager to COMPLETELY REMOVE
Firefox. I wanted to try this, however (bear with me I'm a 72 hour
newbie) when I Marked Firefox for complete removal, it told me that
these these other packages would also be removed (which scared me into
not trying it unless I could get more feedback saying that I wasn't about to
screw up my Ubuntu installation. The other packages marked for removal
when I marked Firefox were:

Ekiga
The Epiphany Browser
Firefox-Gnome-Support
Gnome-App-Install
Gxine (which I had found and installed last night to play CSS encrypted 
DVDs)
Ubuntu-Desktop (that one scared me - Would this remove Ubuntu from my
system???? If so, how would I get it back?)
Yelp

So I didn't try it - I was afraid to possibly uninstall Ubuntu.

So, at this point. I still can't access my email at Yahoo. I can get
all the way in, and some links to stories do work, but when I get to
the page with the actual emails and click on one of them, it times
out...But Google and Gmail work just fine. But my Hotmail account acts
the same way as Yahoo. Strange.

Once again, I had a similar problem a couple years ago with my Windows XP PC, but was
able to resolve it by changed the value of a system variable called
MTU. My service provider is Bellsouth if that makes any difference. Is
there a way to change the MTU value in Ubuntu? I did type ifconfig and
found:

eth0      Link encap:Ethernet  HWaddr 00:04:5A:6A:B6:1E
          inet addr:192.168.0.4  Bcast:192.168.0.255  
Mask:255.255.255.0
          inet6 addr: fe80::204:5aff:fe6a:b61e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6839 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:7343 dropped:0 overruns:0 carrier:14668
          collisions:0 txqueuelen:1000
          RX bytes:6512486 (6.2 MiB)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xe000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5304 (5.1 KiB)  TX bytes:5304 (5.1 KiB)

Note the 70 errors. My XP PC has the settings of Tcp Receive Window:
64440 and MTU of 1492 (not 1500) and it works, so my guess would be to
try setting MTU on my Ubuntu PC to be 1492 and see if that helps. Any
possibility that might work? I'm just guessing here. But how can I do
this in Ubuntu?

p.s. Note that clicking on Submit Reply here at the forum also times
out with the error "Bad Request
Your browser sent a request that this server could not understand."

Very strange indeed! I had to send this from my XP PC...

Thank you, especially those that have tried to help,

Ross

---

### Post by Apollo17 on 2007-03-26
Ross here again. Issue is now resolved. I kept suspecting the MTU value as the problem was exactly the same as I'd had with my Win XP PC a couple years ago.

I did some searching using Google for "Setting MTU in Ubuntu" and found a post that had:

sudo ifconfig eth0 mtu 1500

so I changed the value to 1492 and BAM! I visited Yahoo and Hotmail and all the links (and opening of email) works. And since you are reading this, the "Post Reply" button here at the forum works too. I have no idea why this fixed things, It might be something related to BellSouth (I'm on DSL from them).

Now I only have to do some more reading to figure out how to make the change permanent and I'll be clear and free to navigate.

Thanks again to all who helped. This community rocks! I still would like to know if removing Firefox would have also removed Ubuntu (see my previous post in this thread).

Thanks again, I haven't been this excited messing with a PC since I got Windows 3.1 (well, DOS 5.0 wasn't bad - ha!).

Ross (Apollo17)

---

### Post by macogw on 2007-03-26
Is the site churning for quite a while before timing out?&#12288;If so, it maybe be that IPv6 needs to be disabled.  For some people IPv6 makes pages load terribly slow and if its slow that's how time outs happen.  

1. sudo gedit /etc/modprobe.d/aliases (or your preferred text editor)
2. Find the line: alias net-pf-10 ipv6
3. Edit this to: alias net-pf-10 off
4. Save the file and reboot

(instructions nabbed from an ubuntuforums archive)

---

### Post by Apollo17 on 2007-03-28
Hey macogw,

Yeah, it was churning a bit before timing out, but since I've set the MTU value to 1492 instead of 1500 it all works just fine and FAST. Maybe even faster than my Win XP PC.

I still don't fully understand what's up with certain links (especially email) at Yahoo and Hotmail and why they would require me setting MTU to 1492 in order to work, whereas Google and Gmail didn't care - they worked just fine even with MTU at 1500.

BTW, I found the code and a routine for how to make the change permanent when I did a Google search under "Setting MTU in Ubuntu". One of the links that pops up is to a post in this forum that explains how to use the terminal window to fire up you text editor  (either gedit if using Gnome, or kedit if using KDE), and then adding a line for the MTU setting, saving the file, and then brining the network client down and then back up to effect the changes.

Thanks everyone for all the suggestions. I'm one happy new Ubuntu user. At this rate,  depending on my experience with Wine for running Windows programs in Ubuntu, whenever I order a new PC, I may tell Dell to "hold the Windows"...

Ross
Apollo17

---

