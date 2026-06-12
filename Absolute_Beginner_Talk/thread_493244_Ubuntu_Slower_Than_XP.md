---
title: "Ubuntu Slower Than XP?"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by Yonderknight on 2007-07-05
Hi everyone,

I just installed ubuntu, and I'm starting to get used to it. I'm using fluxbox right now as my window manager, and I thought linux would run much faster than windows XP, but I've noticed that a lot of apps actually run slower.

Firefox, for example, doesn't seem as "snappy". If I run down a list of links in XP, I can clearly see all the links rollover to another color. In ubuntu, only about every other or every third link actually rolls over. Also, sites like this one actually show up a lot slower, and other sites like [customize.org]("http://customize.org/fluxbox/themes/49542") go A LOT slower.

Is this normal? I heard ubuntu itself is a slow OS, and other distros might run faster. Or could there be something wrong with my system?

Thanks!

---

### Post by Raineer on 2007-07-05
If I had to guess it's probably display-driver related.  Just like windows, if the display driver is incorrect it will make the system run like crap.  What card do you use?

---

### Post by stchman on 2007-07-05
> **Yonderknight said:**
> Hi everyone,

I just installed ubuntu, and I'm starting to get used to it. I'm using fluxbox right now as my window manager, and I thought linux would run much faster than windows XP, but I've noticed that a lot of apps actually run slower.

Firefox, for example, doesn't seem as "snappy". If I run down a list of links in XP, I can clearly see all the links rollover to another color. In ubuntu, only about every other or every third link actually rolls over. Also, sites like this one actually show up a lot slower, and other sites like [customize.org]("http://customize.org/fluxbox/themes/49542") go A LOT slower.

Is this normal? I heard ubuntu itself is a slow OS, and other distros might run faster. Or could there be something wrong with my system?

Thanks!

What are your system specs?  On my system apps load a few ticks faster on XP, but nothing to get excited over.  Now Vista Ubuntu loads and works much faster on an average machine.

Ubuntu is pretty quick, there must be something wrong on your end.

---

### Post by Yonderknight on 2007-07-05
My specs are:

Intel Pentium IV 1.8ghz
256mb of RAM

My graphics card is an NVIDIA GeForce2 MX/MX 400 (I'm not sure, that's what it says under "Display Adapters" in winXP's Device Manager)

I didn't touch any graphics drivers or anything when I installed ubuntu.

---

### Post by mbsullivan on 2007-07-05
I agree with Raineer that it's probably a display driver issue. However, in addition to updating your display drivers, you could also disable IPv6, which is enabled by default under Ubuntu... This will give you a noticeable browsing speed upgrade, as address encapsulation/translation will not be necessary, and IPv6 will not be widely adopted for years to come.

There are many ways to do it, here is one which I think may be easiest:

(1) backup /etc/modprobe.d/aliases:
    (eg: sudo cp /etc/modprobe.d/aliases /etc/modprobe.d/aliases.bak  ) 

(2) edit the file with your favorite editor (and with administrative privileges)
    (eg: sudo gedit /etc/modprobe.d/aliases  )

(3) replace the line "alias net-pf-10 ipv6" with "alias net-pf-10 off"

(4) reboot your machine
    (eg: sudo reboot)

Hope this helps.  As to your second question, there ARE speed differences between different distros.  However, I believe that they are very minor so long as your system is configured properly (statistically insignificant, even).  Fluxbox is a very fast window manager with a small memory footprint, so you should be on your way to having a very speedy system.

Hope this helps!
Mike

---

### Post by stchman on 2007-07-05
> **Yonderknight said:**
> My specs are:

Intel Pentium IV 1.8ghz
256mb of RAM

My graphics card is an NVIDIA GeForce2 MX/MX 400 (I'm not sure, that's what it says under "Display Adapters" in winXP's Device Manager)

I didn't touch any graphics drivers or anything when I installed ubuntu.

That 256MB of RAM is a bare minimum.  I would go with at least 512MB.  Since XP is older than Ubuntu it will run with less RAM.  Upgrade your RAM.

TO get your video card 3D accelerated use teh restricted drivers.

---

### Post by mbsullivan on 2007-07-05
Fluxbox should be good for minimizing memory usage, but 256MB may still not be enough for your memory needs... Firefox is a memory hog, too, though you can configure it to use less if you need to.

Try the following command to see how much memory you're using:

free -M

and/or you can check which applications are consuming the most memory with:

top

You can sort by memory usage by pressing the '>' key until you reach that column.

Hope this helps.
Mike

---

### Post by Yonderknight on 2007-07-05
Hrm,

Currently, I'm using 249mb of my 256mb of RAM, and I'm not using any swap memory at all.

Firefox is using up 20mb, iDesk is using up 7mb, pcmanfm is using up 5mb, and fluxbox is using up2mb of RAM.

I can't tell what's eating up so much of my RAM. Firefox isn't really using up that much, and in WinXP firefox runs very quickly.

When I do something like start up a terminal, it takes a couple of seconds instead of firing up almost instantly like I'm guessing it should.

Will upgrading my video drivers fix things? Does ubuntu really use up more memory than WinXP? I was trying out linux in hopes of getting a faster system with the same amount of RAM.

Thanks!

---

### Post by Yonderknight on 2007-07-06
Okay ,I disabled IPv6, how do I update my video drivers?

Thanks!

---

### Post by randytuggle on 2007-07-06
download and install automatix. you can find the site for the program by doing a google search. automatix has ATI and NVIDIA video drivers to choose from.

---

### Post by logos34 on 2007-07-06
> **mbsullivan said:**
> I agree with Raineer that it's probably a display driver issue. However, in addition to updating your display drivers, you could also disable IPv6, which is enabled by default under Ubuntu... This will give you a noticeable browsing speed upgrade, as address encapsulation/translation will not be necessary, and IPv6 will not be widely adopted for years to come.

There are many ways to do it, here is one which I think may be easiest:

(1) backup /etc/modprobe.d/aliases:
    (eg: sudo cp /etc/modprobe.d/aliases /etc/modprobe.d/aliases.bak  ) 

(2) edit the file with your favorite editor (and with administrative privileges)
    (eg: sudo gedit /etc/modprobe.d/aliases  )

(3) replace the line "alias net-pf-10 ipv6" with "alias net-pf-10 off"

(4) reboot your machine
    (eg: sudo reboot)

Hope this helps.  As to your second question, there ARE speed differences between different distros.  However, I believe that they are very minor so long as your system is configured properly (statistically insignificant, even).  Fluxbox is a very fast window manager with a small memory footprint, so you should be on your way to having a very speedy system.

Hope this helps!
Mike

Easier method:

Type **about:config** in the FF addressbar

type in **ipv6**

toggle the value of **disableipv6** to **true**

restart FF

---

### Post by Raineer on 2007-07-06
> Currently, I'm using 249mb of my 256mb of RAM, and I'm not using any swap memory at all.

Do you have a swap partition set?  Once your RAM fills up it needs to be swapping out to disk.  I agree with the "top" recommendation above, that program will tell us what's burning all that up.

---

### Post by Yonderknight on 2007-07-06
Well, I already followed this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

To install the nVIDIA drivers. I do notice a BIG improvement in the speed of things like transparent things in fluxbox, but firefox is still pretty sluggish. For example, if I go to that page that I linked above, there's a big list of links at the top. If I roll through all the links with my mouse, only one in ten will actually roll-over, and they'll only rollover a second or so after your mouse actually goes over the link.

EDIT:

Yeah, I read a little more about the swap thing, and apparently my swap is only used when it's absolutely necessary (I tested this and the swap does get used).

I also read that in linux, RAM Is used for hard drive caching. Is this feature enabled in ubuntu? Maybe that's eating up all my RAM...

Here's all the memory usages top displays:
henry  23.4   firefox-bin
root    11.6   Xorg
henry    5.4  gnome-terminal
henry     4.7  idesk
haldaemo   2.1   hald
hplip   1.8    python
henry    1.7  fluxbox
henry    1.4  gconfd-2
henry     1.3    bash
henry  1.1  bonobo-activati

and free -m:

 total       used       free     shared    buffers     cached
Mem:           249        243          6          0          8        110
-/+ buffers/cache:        125        124
Swap:          502          0        502

---

### Post by Rabindranath on 2007-07-06
Automatix is great but many say that it messes up the system. Better install NVIDIA drivers seperately.

---

### Post by ericdegen on 2007-07-06
I installed the Nvidia drivers with out automatix, it not very difficult and worked well.  Just be glad you have an Nvidia my friend!  On my ATI based Notebook, it's nothing but trouble; the Desktop is Nvidia and life is great.

Hope that speeds things up for you.

One more question, does disabling IPV6 really speed up a box significantly?  should I bother to do this on my systems?

---

### Post by stchman on 2007-07-06
> **Yonderknight said:**
> Hrm,

Currently, I'm using 249mb of my 256mb of RAM, and I'm not using any swap memory at all.

Firefox is using up 20mb, iDesk is using up 7mb, pcmanfm is using up 5mb, and fluxbox is using up2mb of RAM.

I can't tell what's eating up so much of my RAM. Firefox isn't really using up that much, and in WinXP firefox runs very quickly.

When I do something like start up a terminal, it takes a couple of seconds instead of firing up almost instantly like I'm guessing it should.

Will upgrading my video drivers fix things? Does ubuntu really use up more memory than WinXP? I was trying out linux in hopes of getting a faster system with the same amount of RAM.

Thanks!

Windows XP system requirements are less.  I believe with XP that it needs 128MB recommend 256MB and a 233MHz proc was needed.

Ubuntu requires 256MB recommends 512MB and I believe needs at least a 700MHz proc but 1GHz or better is recommended.

---

### Post by feistyfirsttimer on 2007-07-06
> One more question, does disabling IPV6 really speed up a box significantly? should I bother to do this on my systems?

Well, after reading this thread I gave it a go, and now FF is noticeably snappier.

---

### Post by r4ik on 2007-07-06
Type about:config again and set  "pipe" maxrequest to from 2 to 8

Good luck !

---

### Post by feistyfirsttimer on 2007-07-06
> Type about:config again and set "pipe" maxrequest to from 2 to 8
What will that do?  I mean, I know you're saying it will speed FF up even more, but what does this "pipe" maxrequest *do*?

---

### Post by r4ik on 2007-07-06
Sorry can't find the right info but it is reversable.

---

### Post by r4ik on 2007-07-06
It is part of a bigger story,


If your router is using dhcp:

The best bet would be to put your isp's primary and backup dns server addresses in your router's setup page. That way, when /etc/resolv.conf gets overwritten upon re-lease or reboot by dhclient, your isp's dns addresses will be there. Dhclient sometimes stops detecting anything beyond the dns-forwarder in our low-cost routers - but that is a whole different story - not dhclient's fault!)

i did that, and ubuntu still gets the 192.168.0.1 & 1 dns that's correct

The other option is to manually edit /etc/dhcp3/dhclient.conf and change the PREPEND line to something like this:
Code:
prepend domain-name-servers 123.45.67.89, 345.67.89.10;

i tried to do sudo nano /etc/dhcp3/dhclient.conf & it made a new file...not sure what the original is suppose to look like or how to find it. EDIT! i got this one done. i did gksudo gedit & got the file!! EDIT2: now i see in networking > dns: realaddy1, realladdy2, 192.168.0.1

Note the comma and space between multiple dns addresses and the semicolon at the end. Use real dns addresses of course.

Manually editing addresses in /etc/resolv.conf when you are running dhcp in the router only lasts temporarily as dhclient will overwrite /etc/resolv.conf upon re-lease or reboot. Making resolv.conf read-only doesn't work, and using chattr to make it immutable isn't advisable.

Of course you could run static and resolv.conf will be left the way you edit it, but what fun is that?

I also disable IPV6 globally by running the following as root:
Code:
echo "blacklist ipv6" > /etc/modprobe.d/blacklist

i tried sudo echo "blacklist ipv6" > /etc/modprobe.d/blacklist & it said permission denied. i don't have the root acct turned on

Also try about:config in the adresbar and set the "pipe" maxrequest to 8

then followup by disabling ipv6 in Firefox as well. At this point I just reboot...

if it does not "stick" go to Admin Networking DNS and add the adresses there also.

Still does not tell why but i hope it tells you it not just a stupid remark :)

---

### Post by Yonderknight on 2007-07-06
Okay, so the problem is with ubuntu then...I never noticed the 512mb recommended RAM thing =\.

Has anybody used another distro that doesn't require so much memory? I think I'd be better off asking this question in a forum not dedicated to one distro =p.

---

### Post by Super TWiT on 2007-07-06
I have gotten Ubuntu to work very smoothly on a laptop that had 192 MB of ram.  It's running Gnome.  I did however have to use the alternate install CD to install it though.

---

### Post by R3linquish3r on 2007-07-06
> **Yonderknight said:**
> Okay, so the problem is with ubuntu then...I never noticed the 512mb recommended RAM thing =\.

Has anybody used another distro that doesn't require so much memory? I think I'd be better off asking this question in a forum not dedicated to one distro =p.

ArchLinux. I'm using it on my Dell Latitude C600. It boots faster than my Ubuntu dekstop :)

[http://www.archlinux.org](http://www.archlinux.org)

---

### Post by r4ik on 2007-07-06
Ubuntu is available for PC, 64-Bit and Mac architectures. CDs require at least 256 MB of RAM. Install requires at least 4 GB of disk space.

---

### Post by mbsullivan on 2007-07-17
> 
I also read that in linux, RAM Is used for hard drive caching. Is this feature enabled in ubuntu? Maybe that's eating up all my RAM...

That is a very good point which seems to have been discounted.  Linux does use space for file system buffers, etc.  This space, although technically "allocated", should not be counted as program memory, as such.  Look at your report from free:

> and free -m:

total used free shared buffers cached
Mem: 249 243 6 0 8 110
-/+ buffers/cache: 125 124
Swap: 502 0 502

This means that your programs take 125 / 256 MB of RAM (less than would be used by Win XP, undoubtedly). Assuming that Firefox is taking quite a bit of that (it's a memory hog), I wouldn't say that your memory usage is half bad.  The rest is used by the system for things like buffers and caches... they will usually fill just about all of your available memory.

If I were you, I'd try some Firefox tweaks (both those from r4ik and some you can find on the Internet). If that doesn't make things better, you could try Swiftfox (some people think it's faster... I'm skeptical and it's not as updated) or an alternative browser -- maybe Opera.

Mike

---

