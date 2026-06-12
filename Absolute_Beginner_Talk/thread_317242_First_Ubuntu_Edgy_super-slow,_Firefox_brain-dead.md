---
title: "First Ubuntu: Edgy super-slow, Firefox brain-dead"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by warmspell on 2006-12-12
I just got a new Shuttle SB37P2, Intel Core 2 Duo E6400 at 2.13GHz, two 250GB SATA hard disks.

Incidentally I selected Linux for this machine because over the next year or two I want to migrate the home IT setup from Windows to Linux; in the shorter term I want to do some software development on Linux.  I chose Ubuntu specifically because of leading-edge components, reputation, community, single CD installer, GNOME desktop, pre-installed apps, hardware detection.

So, installed Edgy from ubuntu-6.10-desktop-i386.iso image.  Partitioned sda into 100GB, 100GB, 32GB and installed Ubuntu on first partition.  Partitioned sdb into 200GB, 30GB and used last partition as swap.  All installed fine.

Then problems began: (a) Edgy is _very_ slow and (b) Firefox won't browse reliably.

Slowness: takes 10 seconds to launch any application from the desktop.  Even mini-apps like About and screen resolution setting.  Also bigger ones like Firefox, OpenOffice.org take 10-14 seconds.  Much slower than Windows on my previous 3-year-vintage box.  So I'm disappointed ... something must be wrong with my setup because people wouldn't love Ubuntu so much if it was this slow for everyone.

Firefox: it browses some websites ok, but many it doesn't.  Eg news.bbc.co.uk (my standard test site) doesn't load, while on the Windows box it loads in less than a second.  But [www.ubuntu.com](www.ubuntu.com) comes up in about 3 seconds.

I wonder whether there's some network settings problem, that's causing both these issues?

Here's my network setup:

* Netgear DG602 ADSL modem / router at 192.168.0.1 acting as DHCP server and default gateway
* gigabit Ethernet switch
* one Windows XP Home desktop, D8
* one Windows XP Home laptop, L9
* one Buffalo NAS box, NAS2
* occasional presence of Windows 2000 work 
* home machines are in Windows workgroup 123ab (slightly anonymized - anyway not MSHOME)
* work laptop thinks of itself as being in its own domain but anyway co-resides nicely with the home gear
* a wireless bridge for use with the laptops
* all working perfectly together

So I have a slightly random mix of workgroup and NT domain, but no local internet domain in any sense recognized by router, or Windows boxes.

When setting up the new machine under Ubuntu,
* I gave it the host name d11
* gave it domain name 123ab (same as Windows workgroup name)
* told it to use DHCP

A couple of additional comments.

I poked around and found that the kernel is recognizing the two CPUs.  (even if it was only recognizing one, it wouldn't explain why it's _so_ slow, but thought I'd check anyway).

I checked with ifconfig that it's using DHCP correctly.  The address, 192.168.0.4, is one that the router would have allocated.

I installed a SLED 10 distro onto the second partition on sda, and using the same swap partition on sdb.  It worked, and launched apps much more snappily (mostly less than a second, and even OOo and Firefox took only about 2-3 seconds) but its Firefox was equally temperamental - it wouldn't browse anything except the router admin interface at 192.168.0.1.  I conclude from this that my new computer is working ok, but my Linux networking skills are missing something.

Any help _much_ appreciated!

---

### Post by Odisej on 2006-12-12
Well, your problems are well above my knowledge of linux or Ubuntu.  But what I can say is: it is not normal behavior. It should not be or feel sluggish. 

Did you install the correct drivers for your video card (Nvidia, Ati)?

As far as Firefox problem goes: I recently installed Swiftfox which is a variety of Firefox, optimized for different hardware configurations. It works slightly faster and it is compatible with Firefox addons. 

I installed it using Automatix ([http://www.getautomatix.com/wiki/index.php?title=Installation)](http://www.getautomatix.com/wiki/index.php?title=Installation)). I believe automatix may also install the correct video drivers for you.

Odisej

---

### Post by warmspell on 2006-12-12
Odisej,

I'm glad to hear my problems aren't normal :-).

Video driver: I have quite an old card and Ubuntu auto-detected it (MSI PCIe card with GeForce 6200 TurboCache).  Doesn't look like this is the problem.

Swiftfox: thanks for the tip, but my main problem with Firefox isn't speed, it's the fact that it doesn't fetch pages.

---

### Post by kd_pease on 2006-12-12
I had the slow app startup problem too, and solved it by making some changes to the /etc/hosts file. I saw it in another post on the forums but forget which one. If you add your hostname to the line that defines localhost you might see an improvement. e.g.

127.0.0.1 localhost <your_hostname>

Hope that helps...

---

### Post by warmspell on 2006-12-12
Thanks kd_pease - that solved the slow app startup problem!

My /etc/hosts originally read

127.0.0.1 localhost
127.0.1.1 d11.123ab

(and then some IPv6 stuff, and then amazingly it included the fixed addresses of d8 and nas2).

Now I've changed it to read

127.0.0.1 localhost d11 d11.123ab

and deleted the 127.0.1.1 line.

System startup (from login to fully working desktop) is now about 1 second (was more like 30 - I didn't mention that), and app startup is easily less than a second.  Bravo!

**But** Firefox is still problematic.

What I don't understand here is that some websites work, while others don't.  So

* [www.ubuntu.com](www.ubuntu.com), [www.arm.com](www.arm.com), [www.symbian.com](www.symbian.com), [www.warmspell.com](www.warmspell.com) - all work - though they take much longer than my Opera on Windows setup
* my intranet locations (d8, nas2, 192.168.0.1) all work, and work fast
* news.bbc.co.uk, [www.opera.com](www.opera.com) - don't work

I can ping news.bbc.co.uk from a terminal on Ubuntu, and I can surf quickly to both news.bbc.co.uk and [www.opera.com](www.opera.com) from Opera on Windows.

So it looks like I've still got a network setup problem.  Still puzzling.

---

### Post by kd_pease on 2006-12-12
I don't have a fix for that off the top of my head, but as a first port of call I'd check what name servers you've got setup in Ubuntu vs. Windows. You can find out which name servers you're using in Ubuntu by looking at /etc/resolv.conf. 

It might also be worth dumping the output of the "ifconfig" and "route" commands from your Ubuntu setup here to see if anyone can spot anything obvious.

---

### Post by warmspell on 2006-12-12
Aha!  Perhaps we're getting warm now.  

Here's the information:

warmspell@d11:/etc$ cat resolv.conf
domain 123ab
nameserver 192.168.0.1
warmspell@d11:/etc$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         mygateway.ar7   0.0.0.0         UG    0      0        0 eth0

Hmm.  That mygateway.ar7 looks fishy, but I don't quite know what to do about it.  Some googling suggests

sudo route add default gw 192.168.0.1 eth0

which I tried, but I got SIOCADDRT: File exists in response, so still looking for ideas.

---

### Post by Delkster on 2006-12-12
It may be that you're getting closer to the real answer with the name server settings but, just out of curiousity, have you tried any other browsers, such as Opera or Galeon?

---

### Post by kd_pease on 2006-12-12
You could try something along the lines of "sudo route delete default" before trying to add the new route. The syntax might be wrong but it'll be something like that (Not in front of a Linux machine at the moment so I can't test...)

---

### Post by warmspell on 2006-12-12
**Unbelievable!**  I've just found the fix!  What you have to do is turn off IPv6 because, to cut a long story short, it's not working end-to-end in my setup.

I tried what you suggested, ie delete default route and then add a sensible one again, and it came back with mygateway.ar7.

In desperation I googled a bit and found a thread, [http://www.pcguide.com/vb/showthread.php?t=44598](http://www.pcguide.com/vb/showthread.php?t=44598), which shows how to disable IPv6 networking in Firefox.  I did this and I could browse the BBC and Opera sites.

The BBC and Opera sites must be the only ones I tried which actually support IPv6 - the rest don't.  This kind of makes sense given that the BBC and Opera are very interested in mobile phone users (you'd think Symbian would be too ...).

But hold on.  Why am I disabling IPv6 in Firefox?  Shouldn't I be disabling it in Linux instead?  Small quantity of Googling later and I've found out how to do that also: see [http://ubuntuforums.org/archive/index.php/t-6841.html](http://ubuntuforums.org/archive/index.php/t-6841.html) for example.

But hold on!!  Why doesn't Ubuntu come out of the box (I mean, off the CD) with IPv6 disabled, or at least a very prominent installation option giving me the choice?

I suspect that my slow desktop was an IPv6-related thing also.  When I get time I'll do a complete re-install and _only_ disable IPv6 rather than doing the fixes which were suggested earlier, so test that theory.

Well this is my first encounter with Ubuntu and the community.  Many thanks Odisej, kd_pease and Delkster.  Ubuntu was a fast, easy install but not immediately useful - this episode has cost me 8 hours brain time and a few days elapsed time.  I'll see if I can find a way through to the Ubuntu team for the next release - we need the initial experience for Windows emigres to be a bit smoother than this.

---

### Post by Delkster on 2006-12-12
> **warmspell said:**
> But hold on!!  Why doesn't Ubuntu come out of the box (I mean, off the CD) with IPv6 disabled, or at least a very prominent installation option giving me the choice?

Well, I still have IPv6 enabled and have no problems. Your experiences may be valuable, though, particularly since you seem to know your way around, so perhaps taking this up for discussion with the devs is a good idea. It sounds like the real issue may be something else than having IPv6 enabled since, like I said, it works for me (and a lot of other people).

---

### Post by meng on 2006-12-12
Goes to show that persistence pays off. Of course, if you keep playing with it a while longer, you'll find something else that doesn't meet your expectations (if you don't, you're not looking hard enough!) But hopefully that too can be fixed.

---

### Post by Henry Rayker on 2006-12-12
I believe the IPv6 works on some hardware configurations and not on others...and I think they've got it defaulted so as to prepare for it as the standard.

I have IPv6 still enabled with no troubles at all.

---

### Post by ghoster on 2006-12-26
I experienced the exact same problems as the original poster, and the same solution(s) worked for me. 

Some googling leads me to believe that my cheap D-Link Router/Modem is the culprit.

---

### Post by andrewpb on 2006-12-29
> **kd_pease said:**
> I had the slow app startup problem too, and solved it by making some changes to the /etc/hosts file. I saw it in another post on the forums but forget which one. If you add your hostname to the line that defines localhost you might see an improvement. e.g.

127.0.0.1 localhost <your_hostname>

Hope that helps...

i'm running into what seems to be the same problem, i would like to try this suggestion out, however i don't understand how to change that file (i'm very new to linux)

anybody?

---

### Post by Jussi01 on 2006-12-29
> **andrewpb said:**
> i'm running into what seems to be the same problem, i would like to try this suggestion out, however i don't understand how to change that file (i'm very new to linux)

anybody?

go to terminal

then type:

```
sudo gedit /etc/hosts
```


then do the changes as described previously

---

### Post by andrewpb on 2006-12-30
it worked, and the system is running a little more smoothly, thanks

---

### Post by Fungyo on 2007-01-06
excellent work to all posters. No flame wars, just knowledge from others that helped me sort out the same problem that the original poster had within 2 minutes.

Cheers!

---

