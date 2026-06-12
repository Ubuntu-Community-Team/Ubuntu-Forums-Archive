---
title: "Why does eth0 try to start multiple times?"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by movrshakr on 2007-12-22
This is about several problems, but I think they are all resulting from one root cause. It started when I found that ALWAYS after boot, my ntp had no associations with servers to sync to even though good ones were specified in ntp.conf.

I looked in syslog and found that ntpd was starting up when eth0 was not yet active, so of course it could not associate with the servers specified in ntp.conf.

Furthermore, to my surprise, I see that eth0 is trying to start EIGHT TIMES (Stage 1 thru3) before finally succeeding thru Stage 5--fully up on the 9th try. And it appears that the failures of the eight times is because dhcdbd is not yet loaded...there are these lines just after the eight failures

NetworkManager: <WARN> nm_dhcp_manager_begin_transaction(): dhcdbd not running!
Dec 21 08:20:28 maximus NetworkManager: <info> Activation (eth0) failure scheduled...
Dec 21 08:20:28 maximus NetworkManager: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Dec 21 08:20:29 maximus NetworkManager: <info> Activation (eth0) failed.

So,
- is dhcdbd the cause of eth0 not coming up?
- why is it not starting in an acceptable order (early enough)?
- how can I fix this?
- I saw in another thread that wicd should be used instead of NetworkManager. I have no idea how to do that.

Thanks.

---

### Post by blueridgedog on 2007-12-22
How are you starting ntpd?  If through normal or "I don't know" means, what is the output of ls -al /etc/rc5.d ?

---

### Post by movrshakr on 2007-12-23
It is being run as a normal start out of init.d script being called from the "Sxx" runlevel startups.  I just did a routine install of ntp and ntpdate, and things are running however the installs set them up.

I will go see if I can find which S is running it.  I wish the various starts wrote a line in syslog saying when they were beginning...would sure help a lot with troubleshooting.

Will post back in a bit.

---

### Post by movrshakr on 2007-12-23
Here is the requested ls of /etc/rc5.d/ :
lrwxrwxrwx   1 root root    17 2007-12-12 18:11 S05vbesave -> ../init.d/vbesave
lrwxrwxrwx   1 root root    15 2007-12-12 18:11 S10acpid -> ../init.d/acpid
lrwxrwxrwx   1 root root    18 2007-12-12 18:11 S10sysklogd -> ../init.d/sysklogd
lrwxrwxrwx   1 root root    34 2007-12-12 18:11 S10xserver-xorg-input-wacom -> ../init.d/xserver-xorg-input-wacom
lrwxrwxrwx   1 root root    15 2007-12-12 18:11 S11klogd -> ../init.d/klogd
lrwxrwxrwx   1 root root    14 2007-12-12 18:11 S12dbus -> ../init.d/dbus
lrwxrwxrwx   1 root root    13 2007-12-12 18:11 S12hal -> ../init.d/hal
lrwxrwxrwx   1 root root    16 2007-12-12 18:11 S19cupsys -> ../init.d/cupsys
lrwxrwxrwx   1 root root    14 2007-12-12 18:11 S20apmd -> ../init.d/apmd
lrwxrwxrwx   1 root root    16 2007-12-12 18:11 S20apport -> ../init.d/apport
lrwxrwxrwx   1 root root    17 2007-12-13 07:47 S20dirmngr -> ../init.d/dirmngr
lrwxrwxrwx   1 root root    22 2007-12-12 18:11 S20hotkey-setup -> ../init.d/hotkey-setup
lrwxrwxrwx   1 root root    17 2007-12-12 18:11 S20makedev -> ../init.d/makedev
lrwxrwxrwx   1 root root    23 2007-12-12 18:11 S20nvidia-kernel -> ../init.d/nvidia-kernel
lrwxrwxrwx   1 root root    19 2007-12-12 18:11 S20powernowd -> ../init.d/powernowd
lrwxrwxrwx   1 root root    15 2007-12-12 18:11 S20rsync -> ../init.d/rsync
lrwxrwxrwx   1 root root    15 2007-12-14 10:34 S20samba -> ../init.d/samba
lrwxrwxrwx   1 root root    20 2007-12-12 18:11 S22consolekit -> ../init.d/consolekit
lrwxrwxrwx   1 root root    13 2007-12-14 18:30 S23ntp -> ../init.d/ntp
lrwxrwxrwx   1 root root    22 2007-12-12 18:11 S24avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx   1 root root    16 2007-12-12 18:11 S24dhcdbd -> ../init.d/dhcdbd
lrwxrwxrwx   1 root root    19 2007-12-12 18:11 S25bluetooth -> ../init.d/bluetooth
lrwxrwxrwx   1 root root    13 2007-12-12 18:11 S30gdm -> ../init.d/gdm
lrwxrwxrwx   1 root root    17 2007-12-12 18:11 S89anacron -> ../init.d/anacron
lrwxrwxrwx   1 root root    13 2007-12-12 18:11 S89atd -> ../init.d/atd
lrwxrwxrwx   1 root root    14 2007-12-12 18:11 S89cron -> ../init.d/cron
lrwxrwxrwx   1 root root    17 2007-12-12 18:11 S98usplash -> ../init.d/usplash
lrwxrwxrwx   1 root root    22 2007-12-12 18:11 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx   1 root root    21 2007-12-12 18:11 S99laptop-mode -> ../init.d/laptop-mode
lrwxrwxrwx   1 root root    18 2007-12-12 18:11 S99rc.local -> ../init.d/rc.local
lrwxrwxrwx   1 root root    19 2007-12-12 18:11 S99rmnologin -> ../init.d/rmnologin

ntp is at S23, which is where the install put it,

Actually we need to pause here, because in reading many threads to analyze this, I saw some comments about the 'interfaces' file that led me to believe mine was incomplete, as it only referenced the local loopback.  So I added...shoot...gotta go look...
Now it reads as below...the Primary interface 1 lines are what I added:
------- interfaces file ----------
auto lo
iface lo inet loopback

# Primary interface 1
auto eth0
iface eth0 inet dhcp
------ end interfaces file ----------

As a result, I no longer have the repeated attempts to start eth0, but ntpd etc is still not loading.  I will post again in this thread what it is doing after I go look at syslog. ntp now does not even start; before it was running, but had not "locked into"  the specified servers--so was doing nothing.  More to come shortly.

---

### Post by blueridgedog on 2007-12-23
These run in order (01 to 99) so if you simply want to delay the start of ntp, you could rename the symlink in /etc/rc5.d as:

sudo mv /etc/rc5.d/S23ntp /etc/rc5.d/S99ntp

Though this fails to really explain why your Ethernet interface takes so long to come up.

---

### Post by movrshakr on 2007-12-23
OK, here is syslog clip...I've bolded some things that look pertinent...

ntpd is first, and fails.  ntpdate is later, and seems to work...but the proper sequence would be for ntpdate to run, stop, release all ports, and later for ntp to start up.
------- begin syslog clip ---------------
Dec 22 18:18:55 maximus ntpd[5204]: **ntpd** 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Dec 22 18:18:55 maximus ntpd[5205]: precision = 1.000 usec
Dec 22 18:18:55 maximus ntpd[5205]:** unable to bind to wildcard socket address 0.0.0.0 - another process may be running - EXITING**
Dec 22 18:18:55 maximus kernel: [   39.304277] Failure registering capabilities with primary security module.
Dec 22 18:18:55 maximus avahi-daemon[5231]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Dec 22 18:18:55 maximus avahi-daemon[5231]: Successfully dropped root privileges.
Dec 22 18:18:55 maximus avahi-daemon[5231]: avahi-daemon 0.6.20 starting up.
Dec 22 18:18:55 maximus avahi-daemon[5231]: Successfully called chroot().
Dec 22 18:18:55 maximus avahi-daemon[5231]: Successfully dropped remaining capabilities.
Dec 22 18:18:55 maximus avahi-daemon[5231]: No service file found in /etc/avahi/services.
Dec 22 18:18:55 maximus avahi-daemon[5231]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.203.
Dec 22 18:18:55 maximus avahi-daemon[5231]: New relevant interface eth0.IPv4 for mDNS.
Dec 22 18:18:55 maximus avahi-daemon[5231]: Network interface enumeration completed.
Dec 22 18:18:55 maximus avahi-daemon[5231]: Registering new address record for fe80::2e0:4cff:fea0:510a on eth0.*.
Dec 22 18:18:55 maximus avahi-daemon[5231]: **Registering new address record for 192.168.1.203 on eth0.IPv4.**
Dec 22 18:18:55 maximus avahi-daemon[5231]: Registering HINFO record with values 'I686'/'LINUX'.
Dec 22 18:18:55 maximus **[B]dhcdbd:**[/B] Started up.
Dec 22 18:18:55 maximus anacron[5301]: Anacron 2.3 started on 2007-12-22
Dec 22 18:18:55 maximus anacron[5301]: Normal exit (0 jobs run)
Dec 22 18:18:55 maximus /usr/sbin/cron[5332]: (CRON) INFO (pidfile fd = 3)
Dec 22 18:18:55 maximus /usr/sbin/cron[5333]: (CRON) STARTUP (fork ok)
Dec 22 18:18:55 maximus /usr/sbin/cron[5333]: (CRON) INFO (Running @reboot jobs)
Dec 22 18:18:56 maximus kernel: [   40.236110] [drm] Initialized drm 1.1.0 20060810
Dec 22 18:18:56 maximus kernel: [   40.252044] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 22
Dec 22 18:18:56 maximus kernel: [   40.255276] [drm] Initialized radeon 1.27.0 20060524 on minor 0
Dec 22 18:18:56 maximus avahi-daemon[5231]: Server startup complete. Host name is maximus.local. Local service cookie is 3224149468.
Dec 22 18:18:56 maximus **ntpdate[4076]:** adjust time server 209.132.176.4 offset 0.036065 sec
------- end syslog clip ---------------

(I don't know what is starting ntpdate)

---

### Post by blueridgedog on 2007-12-23
If you type "man ntpdate" it will give you an eyeful.  It is not related to our issue, but may be running at boot due to some other tinkering that has gone on.

It may be useful if we stop and start ntpd and then see what the logs tell us.  Just to be certain that it will stop and start cleanly post boot.

sudo /etc/init.d/ntpd stop
sudo /etc/init.d/ntpd start
tail /var/log/messages

---

### Post by movrshakr on 2007-12-23
Have done much more reading (and yes, I've man'ed ntpd, ntpdate etc)...

It has become clear there is an issue with the implementation.  It appears in posts allaround the net, and there have been bug reports about similar issues--many of which are closed with 'corrections' but problems remain.  See 

[http://packages.debian.org/changelogs/pool/main/n/ntp/ntp_4.2.2.p4+dfsg-2/changelog](http://packages.debian.org/changelogs/pool/main/n/ntp/ntp_4.2.2.p4+dfsg-2/changelog)

ntpdate is actually started out of 'if-up.d' and is started by ntpdate-debian.  The file /etc/network/ntpdate is involved.  There are so many things called from so many places, it has gotten impossible for me to sort out.  

The bottom line is that the sequencing is all messed up.  It needs to be:

 - ethernet connection is up FOR GOOD (not to be stopped, or changed, or restarted subsequently during the boot)

 - ntpdate runs, sets the time, completely exits, and releases all ports or other resources.  It would be nice to have the option also of having it run 'hwclock --systohc' afterwards to write the time into the hw clock.

 - ntpd is started

I really don't know what to do at this point.  The syslog is not giving me enough clues as to exactly what the problem is, and I am definitely not sufficiently knowledgeable to write scripts to brute force it.

---

### Post by blueridgedog on 2007-12-23
Did you try delaying the start by renaming S23ntp? 

However, you seem to have learned a great deal on this an perhaps it was not such a bad idea.

Me?  I would put /etc/init.d/ntpd start in rc.local and move on.  But I am sort of a get it done guy.

---

### Post by movrshakr on 2007-12-23
Yes, I tried moving it to S97, but that did not solve the problem.  The error messages were different, but end result the same...ntpd not running properly.

And I may end up "brute forcing" it, but I hate creating very non-standard set-ups.  That has bitten me too many times.  I may have to though...I plan to beat on this ffor a day or two longer, then give up.

---

### Post by blueridgedog on 2007-12-23
Well, you seem to have a good handle on the debugging.  I wish everyone was as eager as you.  I have been telling people how to mount drives for two days now.  I decided that I would put in some time in the groups this weekend.

Send me a note if you get it.

---

### Post by heindsight on 2007-12-23
Hi,
I saw movrshakr's [post]("http://ubuntuforums.org/showthread.php?t=647404") in the networking forum and discovered that I have the same problem. I've been digging around in the init scripts and I think I know the cause of the problem and how to solve it.

The problem is that the boot sequence goes something like this:[LIST]
[*]**S12dbus**: Starts dbus
[LIST]
[*]NetworkManager is started and starts trying to bring up network interfaces 
Initially, it fails for interfaces using dhcp, since dhcdbd is not yet running.
[/LIST]
[*]**S23ntp**:Starts ntpd
ntpd tries to associate with servers, but fails because network interfaces are not yet up.
[*]**S24dhcdbd**: Starts dhcdbd
NetworkManager can finally bring up interfaces that use dhcp
[*]**S40networking**: Runs scripts in /etc/network/if-up.d
[LIST]
[*]ntpdate tries to set the time, but fails because ntpd is already running.
[/LIST]
[/LIST]

The solution would be to do the following:
[LIST=1]
[*]Move S23ntp to S45ntp
[*]Move S24dhcdbd to S13dhcdbd
[/LIST]

I haven't actually made these changes yet myself, so I can't guarantee that it will work, but I don't see why it shouldn't.

EDIT:
btw, ubuntu uses runlevel 2 by default (not 5 although by default runlevels 2-5 are all more or less the same), 
so these changes need to be made in /etc/rc2.d (but it won't hurt to do the same for rc[345].d as well).

---

### Post by blueridgedog on 2007-12-23
> **heindsight said:**
> ubuntu uses runlevel 2 by default (not 5 although by default runlevels 2-5 are all more or less the same), 
so these changes need to be made in /etc/rc2.d (but it won't hurt to do the same for rc[345].d as well).

I did not know that.  Why?  The OS surely thinks it is at run level 5 with gdm?

That means our earlier trial of moving it was moot because we moved it in rd5.d.

---

### Post by heindsight on 2007-12-24
I discovered it by accident about a year ago (just after I started using Ubuntu) 
when I was trying to tweak my boot sequence the way I was used to doing on other distros.
I was rather surprised when I found that changing scripts in rc5.d had no effect and that 
switching to rc3.d did not kill gdm. 

There's nothing (other than tradition) that says that runlevel 2 must be multiuser without networking,
3 must be multiuser without gui and runlevel 5 must be full multiuser with gui. As long as you're
consistent you can set up the runlevels any way you like. I believe Ubuntu inherited this runlevel
setup from Debian.

I'm not exactly sure what the philosophy behind doing things this way is, but I suppose one reason
is to make life as easy as possible for windows users switching to ubuntu (and to shield them from 
actually having to learn something new). I suppose someone who's never used anything other than
windows (or MacOS for that matter) would be thrown into a panic if they accidentally added say a
3 to their kernel parameters and suddenly found themselves without a nice fluffy gui login screen.
Although I can't imagine why someone like that would be fooling around with kernel parameters in the 
first place.

BTW: I've implemented the changes I suggested in my previous post, and while moving
S23dhcdbd to S13dhcdbd does help (NetworkManager now succeeds in brining up dhcp
configured interfaces on the first attempt), ntpd is still being started too early (before 
the network interfaces are completely up and still before ntpdate has been run). I suppose
the parallelisation of the boot sequence has something to do with it. I'll have to experiment
some more to see if I can find a way to force ntpd to start after the interfaces are completely
up and ntpdate has been run.

---

### Post by movrshakr on 2007-12-24
heindsight, this is wonderful.  You clearly have a skill set that is letting you get a better handle on it than I was with my muddling through it.

One comment on the initial analysis.  In my case, ntpdate was usually succeeding.  ntpd preceding it was failing--obviously due to the network not being up. 

Of course, ntpdate should run **BEFORE **ntpd...and it would be wonderful to have it also do a 'hwclock --systohc' after ntpdate just in case this is a startup with a dead CMOS battery, meaning the clock is very wrong and meaning that ntpd will not run due to 'more than 1000sec difference' and you won't know it unless you read the syslog.

BTW, how do we get this issue to the ubuntu team to REALLY fix it.  I note that there have been MANY bugs on things about the ntpd and ntpdate  in the past and I think all are closed, but it certainly isn't right yet.

---

### Post by heindsight on 2007-12-24
> **movrshakr said:**
> heindsight, this is wonderful.  You clearly have a skill set that is letting you get a better handle on it than I was with my muddling through it.
hahaha, it's just a combination of a bit of experience, insomnia and a severe case of Thesis Avoidance Syndrome.
It turns out I got it wrong though, so perhaps my skillz aren't that great after all. ;)

I was wrong about the order in which the init scripts run. S40networking is in /etc/rcS.d
so it runs before anything in rc2.d, but it only brings up interfaces that are marked as 'auto' in
/etc/network/interfaces. All other interfaces are managed by NetworkManager, and 
NetworkManager runs the /etc/network/if-up.d/* scripts for each interface it brings up.
Also, I assumed that the init scripts are executed in parallel by default, it turns out this is not
the case, so that's not part of the problem either.

The real problem lies in the manner in which NetworkManager manages the network interfaces 
and in how that differs from "the traditional" method of bringing up interfaces. Traditionally,
all network interfaces were brought up by the networking init script and any services 
(such as ntpd) that required network interfaces to be up before starting, would simply have 
been started after the networking script. Network manager on the other hand, runs as a
daemon and brings up a network interface as soon as it can. The problem is that there is no way
of knowing when an interface will definitely be up. So any service (including ntpd) which 
requires a fully configured network interface before it can start, should not be started by
a script in /etc/rc?.d or even from rc.local, but rather by a script in /etc/network/if-up.d/
(presumably it should then also be stopped by a script in /etc/network/if-down.d/).

So, the solution is to remove S23ntp from rc[2345].d (the correct way of doing it would be
to rename the links to rc[2345].d/K77ntp) and putting a script in /etc/network/if-up.d/ to start
ntpd (and a script in /etc/network/if-down.d/ to stop it) and to ensure that this script runs
*after* the ntpdate script.

An alternative solution might be to just eliminate NetworkManager from the equation by
putting all your network interfaces in /etc/network/interfaces.

> **movrshakr said:**
> One comment on the initial analysis.  In my case, ntpdate was usually succeeding.  ntpd preceding it was failing--obviously due to the network not being up. 
Interesting, in my case ntpdate complains that the ntp socket is already in use and then exits
without doing anything. Does your ntpd exit when it fails to contact any other servers?

> **movrshakr said:**
> and it would be wonderful to have it also do a 'hwclock --systohc' after ntpdate just in case this is a startup with a dead CMOS battery
You could achieve this by adding 'hwclock --systohc' to /etc/network/if-up.d/ntpdate

> **movrshakr said:**
> BTW, how do we get this issue to the ubuntu team to REALLY fix it.  I note that there have been MANY bugs on things about the ntpd and ntpdate  in the past and I think all are closed, but it certainly isn't right yet.
The answer is to file yet another bug report about this. Now that we know exactly what the
cause of the problem is (at least I think we do), the devs should be able to fix it quite easily.
I'm not quite sure what package it should be filed against, because as I said, this does not just
affect ntpd and ntpdate but also all services that require the network to be up before they start.

---

### Post by movrshakr on 2007-12-24
> **heindsight said:**
> 
An alternative solution might be to just eliminate NetworkManager from the equation by
putting all your network interfaces in /etc/network/interfaces.My interfaces file originally had only local in it.  I added the last three lines...
------- interfaces file ----------
auto lo
iface lo inet loopback

# Primary interface 1
auto eth0
iface eth0 inet dhcp
------ end interfaces file ----------
and that was what stopped boot from failing 8 times to get eth0 up.  So with this file can I eliminate NetworkManager?  Smart?  How do?

> **heindsight said:**
> ... Does your ntpd exit when it fails to contact any other servers? Alas, I have made many changes trying to solve this and getting slightly different responses.  Foolishly, I've lost track.  But I do know that at first, when there were 8 tries at starting eth0, when ntpd tried to run, it did stay loaded but had no associations to any servers--so was not doing anything.  With the config I have now, it ends up not staying loaded after running.  I have about ten clips of syslogs on my desktop, but stupidly don't know what the change I did was before the boot producing that log.
> **heindsight said:**
> You could achieve this by adding 'hwclock --systohc' to /etc/network/if-up.d/ntpdate
I would think there would need to be some tests before that to be sure ntdate (ntpdate-debian) had run successfully and actually gotten a good time.  I am not capable of writing 'if' tests.
> **heindsight said:**
> The answer is to file yet another bug report about this. Now that we know exactly what the cause of the problem is (at least I think we do), the devs should be able to fix it quite easily. I'm not quite sure what package it should be filed against, because as I said, this does not just
affect ntpd and ntpdate but also all services that require the network to be up before they start.I truly hope this can be done though.

---

### Post by movrshakr on 2007-12-24
I have to leave the board for the rest of the evening...Christmas Eve service at church and birthday dinner for my son.

I hope we can go one more step and end this with a **specific **set of changes that will enable ntpd and ntpdate to run reliably.

I think this will help many people and perhaps be a starting point for the debian/ubuntu dev gurus to publish an official change that works.

And yes I am thanking you profusely for the amazing insight you have already brought to this and begging you for that last step.  :)

---

### Post by blueridgedog on 2007-12-24
Have a great Christmas and birthday party.

I am off to family as well.

---

### Post by movrshakr on 2007-12-25
There is a BUG #114505 on this.  See [https://bugs.launchpad.net/ntp/+bug/114505](https://bugs.launchpad.net/ntp/+bug/114505)

I added an input there about a little of what we have said here.

Also, there are some proffered ideas there about how to fix it that are quite different than what we have seen here.

There is a line there that it is "declined" for Gutsy.  I don't know what that means.

I still don't know how to make mine work.

---

### Post by heindsight on 2007-12-25
> **movrshakr said:**
> My interfaces file originally had only local in it.  I added the last three lines...
------- interfaces file ----------
auto lo
iface lo inet loopback

# Primary interface 1
auto eth0
iface eth0 inet dhcp
------ end interfaces file ----------
and that was what stopped boot from failing 8 times to get eth0 up.  So with this file can I eliminate NetworkManager?  Smart?  How do?

Well, NetworkManager only manages interfaces that aren't listed in /etc/network/interfaces, 
so if all your interfaces are listed there, then NetworkManager will start up, but it won't actually 
do much. If you want, you can completely disable it (stop it from running) by deactivating
(removing all executable permissions from) the NetworkManager scripts in /etc/dbus-1/event.d/
Whether this is a smart thing to do is a decision you'll have to make for yourself.

To get back to the ntp issue, I've been doing some experiments (poor ceridwen has never been
rebooted so many times within 48 hours before) and I think I have a solution that works for me
regardless of whether NetworkManager manages my interfaces. The only problem I have with
this solution at the moment is that it may lead to misleading log entries about ntpd (especially if
NetworkManager is not managing your interfaces).

Solution:
[LIST]
[*]deactivate the ntpdate script in /etc/network/if-up.d/ (by removing its executable permissions)
[*]Copy the script attached with this post to /etc/network/if-up.d/ntpd
[*]Set ownership of /etc/network/if-up.d/ntpd to root.root and give it full executable permission
[*]Leave the symlinks to /etc/init.d/ntp in /etc/rc?d/ at the installation defaults (my script won't run ntpd unless it's configured to start in the current runlevel)
[/LIST]

The script I wrote is basically a modification of the original ntpdate script from /etc/network/if-up.d
For every interface that is brought up (except the loopback interface), it first stops ntpd (if it was
running) then, while ntpd is not stopped, it runs /usr/sbin/ntpdate-debian and also runs 
hwclock --systohc if ntpdate successfully updated the clock. Finally it starts ntpd up again, but
only if ntpd is configured to start in the current runlevel.

I'm also going to be uploading this script with some more comments to that thread on launchpad,
so feel free to post any comments/thoughts either here or there.

---

### Post by movrshakr on 2007-12-26
Great!  That sounds like (from a sequence standpoint) what needs to be done...I'm not knowledgeable enough to comment on the technical approach.

I will try it this afternoon.

Gosh, I hope the devs fix it, cause when you have to do things like this, when something is updated (or you decide to install the next release), it can overwrite a file you had changed and mess everything up.  But there's no other choice if we want it to work now.

And I truly appreciate your willingness to hammer on this.  Thanks ever so much.

---

### Post by heindsight on 2007-12-26
> **movrshakr said:**
> Great!  That sounds like (from a sequence standpoint) what needs to be done...I'm not knowledgeable enough to comment on the technical approach.

I will try it this afternoon.

Gosh, I hope the devs fix it, cause when you have to do things like this, when something is updated (or you decide to install the next release), it can overwrite a file you had changed and mess everything up.  But there's no other choice if we want it to work now.

And I truly appreciate your willingness to hammer on this.  Thanks ever so much.

Actually. I should be the one thanking you. I might never even have realised that I was having ntp problems, if it wasn't for you. 
Besides, tinkering with this was a lot more fun than working on my thesis would have been.

---

### Post by movrshakr on 2007-12-26
OK, I implemented heindsight's recommended solution, and ntpd is running!!!
Hooray!

I don't know if the ntpdate-debian part worked because I don't see any way to tell.  There are no comments about ntpdate in syslog.

Are there a lines of code we could put into the script so that it would write to syslog that ntpdate is starting, then do a test for "good" exit code, then write that it succeeded, or write that it did not?

---

### Post by movrshakr on 2007-12-26
Oops, but there may be a problem, Houston.

While it is a huge advance that ntpd is starting, I can find no evidence that ntpdate (from /etc/network.if-up.d/ntpd) is running.  I put statements in the script like:

    logger -s -t "ntpdate starting"

and there was nothing in syslog to that effect.

I changed it to

    echo "ntpdate starting">>/home/myname/ntpdate.log

and there was nothing written to that file.

How can I verify that the code in the script is running and that ntpdate/hwclock are executing?  Do scripts in /.../if-up.d automatically get run?

---

### Post by heindsight on 2007-12-27
Well, the script does pass the -s option to ntpdate, which causes it to send output to syslog. 

The problem is that if your network connection is being brought up by /etc/rcS.d/S40networking, 
then ntpdate runs before syslogd is started by /etc/rc2.d/S10sysklogd. This doesn't explain why
the echo command you put in there doesn't work though. I've done some more testing and it 
seems that in my case when rcS.d/S40networking starts up the interface; /usr is not yet mounted
(my /usr lives on its own partition) -- I don't quite understand this, because local filesystems are
supposed to be mounted before S40networking runs, the complete lack of logs during that phase
of the boot sequence is rather frustrating. 

Anyway, what this means, is that if when an interface is brought up by rcS.d/S40networking,
```
[ -x /usr/sbin/ntpdate-debian ]
```
returns false, so ntpdate doesn't get executed. Letting NetworkManager manage your interface
should solve this, because when NetworkManager starts the interface, all local filesystems are
already mounted. If you let NetworkManager manage the interface you should also get some output
from ntpdate in your syslog.

If /usr is mounted from nfs, then the interface over which /usr is mounted can't be managed by NetworkManager
(obviously, since NetworkManager lives under /usr), but nfs filesystems are mounted by an if-up.d script
which runs before the ntpd script. So with such a setup /usr will be mounted before the ntpd script tries to
run ntpdate.

---

### Post by movrshakr on 2007-12-27
So, I should remove the last three lines (ones I put in) from interfaces, and then NetworkManager will start it?  It seems that back at the very first when I was looking at this, it was putting these lines into interfaces that ended the problem of eth0 trying to start eight times before succeeding.

------- interfaces file ----------
auto lo
iface lo inet loopback

# Primary interface 1
auto eth0
iface eth0 inet dhcp
------ end interfaces file ----------

I'll go try it.

---

### Post by movrshakr on 2007-12-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/ntp/+bug/114505](https://bugs.launchpad.net/ubuntu/+source/ntp/+bug/114505) [br].[/br] ---------------------------- [br].[/br]
				Oh gosh--and we were so close.

Sure enough, putting 'interfaces' back to the way it originally was (two lines for 'lo' only) has resulted in going back to basically where I started from.  eth0 tries to start multiple times (10 in this run), ntpd started after the 7th try of eth0--and ended up staying running but with no associations.  No entries for ntpdate in syslog either.

Summary of this config that doesn't work: ntpd is at S23 in runlevels 2-5, and heindsights's changes are incorporated (the ntpd script put into .../if-up.d/ntpd, made executable, owned by root.root, and ntpdate script made unexecutable) .

I have a thought:  how about putting a 'post-up' command into interfaces to run ntpdate?

---

### Post by heindsight on 2007-12-27
> **movrshakr said:**
>  it was putting these lines into interfaces that ended the problem of eth0 trying to start eight times before succeeding.


Yes, NetworkManager might fail to bring up eth0 on the first try again, but at least this time that shouldn't cause problems for ntpd. Like I said before, if you force dhcdbd to start earlier then 
NetworkManager should be able to get eth0 up on the first try.

---

### Post by heindsight on 2007-12-27
> **movrshakr said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/ntp/+bug/114505](https://bugs.launchpad.net/ubuntu/+source/ntp/+bug/114505) [br].[/br] ---------------------------- [br].[/br]
				Oh gosh--and we were so close.

Sure enough, putting 'interfaces' back to the way it originally was (two lines for 'lo' only) has resulted in going back to basically where I started from.  eth0 tries to start multiple times (10 in this run), ntpd started after the 7th try of eth0--and ended up staying running but with no associations.  No entries for ntpdate in syslog either.

Summary of this config that doesn't work: ntpd is at S23 in runlevels 2-5, and heindsights's changes are incorporated (the ntpd script put into .../if-up.d/ntpd, made executable, owned by root.root, and ntpdate script made unexecutable) .

Oh no! It works perfectly for me. My guess is that for some reason /etc/if-up.d/ntpd isn't running
when NetworkManager brings up your eth0. Try running the script manually
```
METHOD=dhcp MODE=start sudo /etc/network/if-up.d/ntpd
```
and post the output here, hopefully that will give us an indication of what's going wrong.

---

### Post by movrshakr on 2007-12-27
The result is:

... !/bin/sh:  not found

---

### Post by heindsight on 2007-12-27
What?! That really shouldn't be happening.
 It looks like you accidentally removed the # from the beginning of the first line.
Try it with the original script I uploaded and see if that works.

---

### Post by movrshakr on 2007-12-27
Exactly..such a dummy; somehow I had deleted the leading pound sign.

Unfortunately, adding it back in and rebooting results in the same thing...multiple eth0 starts, ntpd ending running with no associations

Here is what I have in the /.../if-up.d/ntpd script (most comments deleted):
--------------------------
# !/bin/sh

if [ "$METHOD" = "loopback" ]; then
    exit 0
fi

if [ "$METHOD" = "static" ]; then
	NTPDATEOPTS="-b"
fi

if [ "$MODE" = "start" ]; then

    /etc/init.d/ntp stop
    if [ -x /usr/sbin/ntpdate-debian ]; then
        echo "/etc/network/if-up.d/ntpd to start ntpdate-debian">>/home/bob/ntpdate.log
        /usr/sbin/ntpdate-debian -s $NTPDATEOPTS 2>/dev/null && hwclock --systohc
        echo "/etc/network/if-up.d/ntpd completed ntpdate-debian, hwclock --systohc">>/home/bob/ntpdate.log
    fi

    if which invoke-rc.d >/dev/null 2>&1; then
        invoke-rc.d ntp start
    else
	/etc/init.d/ntp start
    fi
fi
------------------------------------------------------------------------------------------------------
DOES ntpdate-debian NEED A START PARAMETER?
DOES ntpdate-debian CALL NTPDATE SCRIPT, WHICH WE HAVE MADE NON-EXECUTABLE?

---

### Post by heindsight on 2007-12-27
That's very strange. I see no reason why your version of the script wouldn't work (I've tried it,
and it works for me). I really don't know what the problem could be.

Perhaps we should have a look at your syslog again, can you post everything from your syslog, 
starting at the point where NetworkManager first tries to bring up eth0 until the machine is completely
booted up?

---

### Post by heindsight on 2007-12-27
> **movrshakr said:**
> 
DOES ntpdate-debian NEED A START PARAMETER?
DOES ntpdate-debian CALL NTPDATE SCRIPT, WHICH WE HAVE MADE NON-EXECUTABLE?

No on both of those. ntpdate-debian calls /usr/sbin/ntpdate. It doesn't really need any parameters.
It just passes any aruments you give it (plus ntpdate options specified in /etc/default/ntpdate and
a list of ntp servers) on to /usr/sbin/ntpdate. ntpdate-debian is a shell script, so you can easily 
have a look to see exactly what it does.

---

### Post by movrshakr on 2007-12-27
Certainly...wish this site had a post attachment facility.

I will do a reboot and get a clean syslog.  Coming soon to a forum near you!

---

### Post by movrshakr on 2007-12-27
I apologize to all for the length of this post;  I am so desperate to get this issue solved and hope the final result benefits all.

I did deleted some lines judged to be not associated with this problem to shorten the post.

----------- begin syslog -------------
Dec 27 13:44:18 maximus syslogd 1.4.1#21ubuntu3: restart.
Dec 27 13:44:18 maximus kernel: Inspecting /boot/System.map-2.6.22-14-generic
Dec 27 13:44:18 maximus kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Dec 27 13:44:18 maximus kernel: Symbols match kernel version 2.6.22.
Dec 27 13:44:18 maximus kernel: No module symbols loaded - kernel modules not enabled. 
Dec 27 13:44:18 maximus kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Dec 18 08:02:57 UTC 2007 (Ubuntu 2.6.22-14.47-generic)
[deleted bios lines]
Dec 27 13:44:18 maximus kernel: [    0.000000] 127MB HIGHMEM available.
Dec 27 13:44:18 maximus kernel: [    0.000000] 896MB LOWMEM available.
Dec 27 13:44:18 maximus kernel: [    0.000000] found SMP MP-table at 000f5620
Dec 27 13:44:18 maximus kernel: [    0.000000] Entering add_active_range(0, 0, 262128) 0 entries of 256 used
Dec 27 13:44:18 maximus kernel: [    0.000000] Zone PFN ranges:
Dec 27 13:44:18 maximus kernel: [    0.000000]   DMA             0 ->     4096
Dec 27 13:44:18 maximus kernel: [    0.000000]   Normal       4096 ->   229376
Dec 27 13:44:18 maximus kernel: [    0.000000]   HighMem    229376 ->   262128
Dec 27 13:44:18 maximus kernel: [    0.000000] early_node_map[1] active PFN ranges
Dec 27 13:44:18 maximus kernel: [    0.000000]     0:        0 ->   262128
Dec 27 13:44:18 maximus kernel: [    0.000000] On node 0 totalpages: 262128
Dec 27 13:44:18 maximus kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Dec 27 13:44:18 maximus kernel: [    0.000000]   DMA zone: 0 pages reserved
Dec 27 13:44:18 maximus kernel: [    0.000000]   DMA zone: 4064 pages, LIFO batch:0
Dec 27 13:44:18 maximus kernel: [    0.000000]   Normal zone: 1760 pages used for memmap
Dec 27 13:44:18 maximus kernel: [    0.000000]   Normal zone: 223520 pages, LIFO batch:31
Dec 27 13:44:18 maximus kernel: [    0.000000]   HighMem zone: 255 pages used for memmap
Dec 27 13:44:18 maximus kernel: [    0.000000]   HighMem zone: 32497 pages, LIFO batch:7
Dec 27 13:44:18 maximus kernel: [    0.000000] DMI 2.2 present.
[deleted acpi lines]
Dec 27 13:44:18 maximus kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Dec 27 13:44:18 maximus kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 27 13:44:18 maximus kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
Dec 27 13:44:18 maximus kernel: [    0.000000] Built 1 zonelists.  Total pages: 260081
Dec 27 13:44:18 maximus kernel: [    0.000000] Kernel command line: root=UUID=bebd331b-d7a8-4a5e-b15f-337ad9c517d6 ro
Dec 27 13:44:18 maximus kernel: [    0.000000] mapped APIC to ffffd000 (fee00000)
Dec 27 13:44:18 maximus kernel: [    0.000000] mapped IOAPIC to ffffc000 (fec00000)
Dec 27 13:44:18 maximus kernel: [    0.000000] Enabling fast FPU save and restore... done.
Dec 27 13:44:18 maximus kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Dec 27 13:44:18 maximus kernel: [    0.000000] Initializing CPU#0
Dec 27 13:44:18 maximus kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Dec 27 13:44:18 maximus kernel: [    0.000000] Detected 2075.194 MHz processor.
Dec 27 13:44:18 maximus kernel: [   13.190393] Console: colour VGA+ 80x25
Dec 27 13:44:18 maximus kernel: [   13.192971] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Dec 27 13:44:18 maximus kernel: [   13.194356] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec 27 13:44:18 maximus kernel: [   13.229164] Memory: 1027880k/1048512k available (2015k kernel code, 19932k reserved, 916k data, 364k init, 131008k highmem)
Dec 27 13:44:18 maximus kernel: [   13.229228] virtual kernel memory layout:
Dec 27 13:44:18 maximus kernel: [   13.229229]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
Dec 27 13:44:18 maximus kernel: [   13.229230]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Dec 27 13:44:18 maximus kernel: [   13.229231]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Dec 27 13:44:18 maximus kernel: [   13.229233]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Dec 27 13:44:18 maximus kernel: [   13.229234]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
Dec 27 13:44:18 maximus kernel: [   13.229235]       .data : 0xc02f7de6 - 0xc03dce84   ( 916 kB)
Dec 27 13:44:18 maximus kernel: [   13.229236]       .text : 0xc0100000 - 0xc02f7de6   (2015 kB)
Dec 27 13:44:18 maximus kernel: [   13.229554] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Dec 27 13:44:18 maximus kernel: [   13.229681] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Dec 27 13:44:18 maximus kernel: [   13.309680] Calibrating delay using timer specific routine.. 4154.19 BogoMIPS (lpj=8308384)
Dec 27 13:44:18 maximus kernel: [   13.309798] Security Framework v1.0.0 initialized
Dec 27 13:44:18 maximus kernel: [   13.309847] SELinux:  Disabled at boot.
Dec 27 13:44:18 maximus kernel: [   13.309904] Mount-cache hash table entries: 512
Dec 27 13:44:18 maximus kernel: [   13.310121] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
Dec 27 13:44:18 maximus kernel: [   13.310131] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Dec 27 13:44:18 maximus kernel: [   13.310176] CPU: L2 Cache: 256K (64 bytes/line)
Dec 27 13:44:18 maximus kernel: [   13.310217] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
Dec 27 13:44:18 maximus kernel: [   13.310231] Compat vDSO mapped to ffffe000.
Dec 27 13:44:18 maximus kernel: [   13.310285] Checking 'hlt' instruction... OK.
Dec 27 13:44:18 maximus kernel: [   13.325882] SMP alternatives: switching to UP code
Dec 27 13:44:18 maximus kernel: [   13.326242] Freeing SMP alternatives: 11k freed
Dec 27 13:44:18 maximus kernel: [   13.326675] Early unpacking initramfs... done
Dec 27 13:44:18 maximus kernel: [   13.631175] ACPI: Core revision 20070126
Dec 27 13:44:18 maximus kernel: [   13.631316] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Dec 27 13:44:18 maximus kernel: [   13.634917] CPU0: AMD Athlon(tm) XP 2600+ stepping 01
Dec 27 13:44:18 maximus kernel: [   13.635045] Total of 1 processors activated (4154.19 BogoMIPS).
Dec 27 13:44:18 maximus kernel: [   13.635831] ENABLING IO-APIC IRQs
Dec 27 13:44:18 maximus kernel: [   13.636180] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 27 13:44:18 maximus kernel: [   13.781306] Brought up 1 CPUs
Dec 27 13:44:18 maximus kernel: [   13.781519] Booting paravirtualized kernel on bare hardware
Dec 27 13:44:18 maximus kernel: [   13.781644] Time: 18:43:56  Date: 11/27/107
Dec 27 13:44:18 maximus kernel: [   13.781716] NET: Registered protocol family 16
Dec 27 13:44:18 maximus kernel: [   13.781864] EISA bus registered
Dec 27 13:44:18 maximus kernel: [   13.781917] ACPI: bus type pci registered
Dec 27 13:44:18 maximus kernel: [   13.789321] PCI: PCI BIOS revision 2.10 entry at 0xfb400, last bus=1
Dec 27 13:44:18 maximus kernel: [   13.789364] PCI: Using configuration type 1
Dec 27 13:44:18 maximus kernel: [   13.789404] Setting up standard PCI resources
[deleted acpi lines]
Dec 27 13:44:18 maximus kernel: [   13.821066] Linux Plug and Play Support v0.97 (c) Adam Belay
Dec 27 13:44:18 maximus kernel: [   13.821120] pnp: PnP ACPI init
Dec 27 13:44:18 maximus kernel: [   13.821173] ACPI: bus type pnp registered
Dec 27 13:44:18 maximus kernel: [   13.824452] pnp: PnP ACPI: found 16 devices
Dec 27 13:44:18 maximus kernel: [   13.824497] ACPI: ACPI bus type pnp unregistered
Dec 27 13:44:18 maximus kernel: [   13.824539] PnPBIOS: Disabled by ACPI PNP
Dec 27 13:44:18 maximus kernel: [   13.824641] PCI: Using ACPI for IRQ routing
Dec 27 13:44:18 maximus kernel: [   13.824684] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Dec 27 13:44:18 maximus kernel: [   13.845240] NET: Registered protocol family 8
Dec 27 13:44:18 maximus kernel: [   13.845280] NET: Registered protocol family 20
Dec 27 13:44:18 maximus kernel: [   13.845400] pnp: 00:02: ioport range 0x4000-0x407f has been reserved
Dec 27 13:44:18 maximus kernel: [   13.845445] pnp: 00:02: ioport range 0x5000-0x500f has been reserved
Dec 27 13:44:18 maximus kernel: [   13.849196] Time: tsc clocksource has been installed.
Dec 27 13:44:18 maximus kernel: [   13.875796] PCI: Bridge: 0000:00:01.0
Dec 27 13:44:18 maximus kernel: [   13.875836]   IO window: 9000-9fff
Dec 27 13:44:18 maximus kernel: [   13.875878]   MEM window: e0000000-e00fffff
Dec 27 13:44:18 maximus kernel: [   13.875920]   PREFETCH window: d8000000-dfffffff
Dec 27 13:44:18 maximus kernel: [   13.875974] PCI: Setting latency timer of device 0000:00:01.0 to 64
Dec 27 13:44:18 maximus kernel: [   13.875987] NET: Registered protocol family 2
Dec 27 13:44:18 maximus kernel: [   13.913200] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec 27 13:44:18 maximus kernel: [   13.913458] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
Dec 27 13:44:18 maximus kernel: [   13.916259] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Dec 27 13:44:18 maximus kernel: [   13.917293] TCP: Hash tables configured (established 131072 bind 65536)
Dec 27 13:44:18 maximus kernel: [   13.917340] TCP reno registered
Dec 27 13:44:18 maximus kernel: [   13.929291] checking if image is initramfs... it is
Dec 27 13:44:18 maximus kernel: [   14.376730] Switched to high resolution mode on CPU 0
Dec 27 13:44:18 maximus kernel: [   14.504286] Freeing initrd memory: 7067k freed
Dec 27 13:44:18 maximus kernel: [   14.504824] audit: initializing netlink socket (disabled)
Dec 27 13:44:18 maximus kernel: [   14.504881] audit(1198781037.016:1): initialized
Dec 27 13:44:18 maximus kernel: [   14.504996] highmem bounce pool size: 64 pages
Dec 27 13:44:18 maximus kernel: [   14.506921] VFS: Disk quotas dquot_6.5.1
Dec 27 13:44:18 maximus kernel: [   14.507026] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec 27 13:44:18 maximus kernel: [   14.507177] io scheduler noop registered
Dec 27 13:44:18 maximus kernel: [   14.507218] io scheduler anticipatory registered
Dec 27 13:44:18 maximus kernel: [   14.507259] io scheduler deadline registered
Dec 27 13:44:18 maximus kernel: [   14.507310] io scheduler cfq registered (default)
Dec 27 13:44:18 maximus kernel: [   14.507363] PCI: VIA PCI bridge detected. Disabling DAC.
Dec 27 13:44:18 maximus kernel: [   14.507458] Boot video device is 0000:01:00.0
Dec 27 13:44:18 maximus kernel: [   14.507636] isapnp: Scanning for PnP cards...
Dec 27 13:44:18 maximus kernel: [   14.861202] isapnp: No Plug & Play device found
Dec 27 13:44:18 maximus kernel: [   14.892520] Real Time Clock Driver v1.12ac
Dec 27 13:44:18 maximus kernel: [   14.892673] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Dec 27 13:44:18 maximus kernel: [   14.892814] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec 27 13:44:18 maximus kernel: [   14.893156] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Dec 27 13:44:18 maximus kernel: [   14.894014] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Dec 27 13:44:18 maximus kernel: [   14.894462] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Dec 27 13:44:18 maximus kernel: [   14.894810] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 16
Dec 27 13:44:18 maximus kernel: [   14.897919] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Dec 27 13:44:18 maximus kernel: [   14.898219] input: Macintosh mouse button emulation as /class/input/input0
Dec 27 13:44:18 maximus kernel: [   14.898350] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Dec 27 13:44:18 maximus kernel: [   14.898753] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 27 13:44:18 maximus kernel: [   14.898798] serio: i8042 AUX port at 0x60,0x64 irq 12
Dec 27 13:44:18 maximus kernel: [   14.899007] mice: PS/2 mouse device common for all mice
Dec 27 13:44:18 maximus kernel: [   14.899162] EISA: Probing bus 0 at eisa.0
Dec 27 13:44:18 maximus kernel: [   14.899222] Cannot allocate resource for EISA slot 4
Dec 27 13:44:18 maximus kernel: [   14.899263] Cannot allocate resource for EISA slot 5
Dec 27 13:44:18 maximus kernel: [   14.899315] EISA: Detected 0 cards.
Dec 27 13:44:18 maximus kernel: [   14.899549] TCP cubic registered
Dec 27 13:44:18 maximus kernel: [   14.899597] NET: Registered protocol family 1
Dec 27 13:44:18 maximus kernel: [   14.899657] Using IPI No-Shortcut mode
Dec 27 13:44:18 maximus kernel: [   14.899889]   Magic number: 3:660:747
Dec 27 13:44:18 maximus kernel: [   14.900682] Freeing unused kernel memory: 364k freed
Dec 27 13:44:18 maximus kernel: [   14.936263] input: AT Translated Set 2 keyboard as /class/input/input1
Dec 27 13:44:18 maximus kernel: [   15.100744] AppArmor: AppArmor initialized<5>audit(1198781037.516:2):  type=1505 info="AppArmor initialized" pid=1186
Dec 27 13:44:18 maximus kernel: [   15.107694] fuse init (API version 7.8)
Dec 27 13:44:18 maximus kernel: [   15.112842] Failure registering capabilities with primary security module.
Dec 27 13:44:18 maximus kernel: [   15.124578] ACPI: Fan [FAN] (on)
Dec 27 13:44:18 maximus kernel: [   15.129899] ACPI: Processor [CPU0] (supports 2 throttling states)
Dec 27 13:44:18 maximus kernel: [   15.131528] ACPI: Thermal Zone [THRM] (54 C)
Dec 27 13:44:18 maximus kernel: [   15.737108] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 17
Dec 27 13:44:18 maximus kernel: [   15.790063] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[17]  MMIO=[e0100000-e01007ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
Dec 27 13:44:18 maximus kernel: [   15.807530] usbcore: registered new interface driver usbfs
Dec 27 13:44:18 maximus kernel: [   15.807606] usbcore: registered new interface driver hub
Dec 27 13:44:18 maximus kernel: [   15.807672] usbcore: registered new device driver usb
Dec 27 13:44:18 maximus kernel: [   15.808659] USB Universal Host Controller Interface driver v3.0
Dec 27 13:44:18 maximus kernel: [   15.809061] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
Dec 27 13:44:18 maximus kernel: [   15.809106] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
Dec 27 13:44:18 maximus kernel: [   15.809156] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
Dec 27 13:44:18 maximus kernel: [   15.809280] uhci_hcd 0000:00:10.0: UHCI Host Controller
Dec 27 13:44:18 maximus kernel: [   15.809510] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Dec 27 13:44:18 maximus kernel: [   15.809591] uhci_hcd 0000:00:10.0: irq 18, io base 0x0000a800
Dec 27 13:44:18 maximus kernel: [   15.809783] usb usb1: configuration #1 chosen from 1 choice
Dec 27 13:44:18 maximus kernel: [   15.809852] hub 1-0:1.0: USB hub found
Dec 27 13:44:18 maximus kernel: [   15.809901] hub 1-0:1.0: 2 ports detected
Dec 27 13:44:18 maximus kernel: [   15.894437] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Dec 27 13:44:18 maximus kernel: [   15.894493] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Dec 27 13:44:18 maximus kernel: [   15.911368] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
Dec 27 13:44:18 maximus kernel: [   15.911495] uhci_hcd 0000:00:10.1: UHCI Host Controller
Dec 27 13:44:18 maximus kernel: [   15.911561] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Dec 27 13:44:18 maximus kernel: [   15.911634] uhci_hcd 0000:00:10.1: irq 18, io base 0x0000ac00
Dec 27 13:44:18 maximus kernel: [   15.911792] usb usb2: configuration #1 chosen from 1 choice
Dec 27 13:44:18 maximus kernel: [   15.911859] hub 2-0:1.0: USB hub found
Dec 27 13:44:18 maximus kernel: [   15.911907] hub 2-0:1.0: 2 ports detected
Dec 27 13:44:18 maximus kernel: [   15.916756] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
Dec 27 13:44:18 maximus kernel: [   15.916810] via-rhine: Broken BIOS detected, avoid_D3 enabled.
Dec 27 13:44:18 maximus kernel: [   16.015291] ACPI: PCI Interrupt 0000:00:10.2[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
Dec 27 13:44:18 maximus kernel: [   16.015419] uhci_hcd 0000:00:10.2: UHCI Host Controller
Dec 27 13:44:18 maximus kernel: [   16.015495] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Dec 27 13:44:18 maximus kernel: [   16.015565] uhci_hcd 0000:00:10.2: irq 18, io base 0x0000b000
Dec 27 13:44:18 maximus kernel: [   16.015731] usb usb3: configuration #1 chosen from 1 choice
Dec 27 13:44:18 maximus kernel: [   16.015799] hub 3-0:1.0: USB hub found
Dec 27 13:44:18 maximus kernel: [   16.015848] hub 3-0:1.0: 2 ports detected
Dec 27 13:44:18 maximus kernel: [   16.019253] Floppy drive(s): fd0 is 1.44M
Dec 27 13:44:18 maximus kernel: [   16.064085] FDC 0 is a post-1991 82077
Dec 27 13:44:18 maximus kernel: [   16.120425] ACPI: PCI Interrupt 0000:00:10.3[D] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 18
Dec 27 13:44:18 maximus kernel: [   16.120557] ehci_hcd 0000:00:10.3: EHCI Host Controller
Dec 27 13:44:18 maximus kernel: [   16.120646] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Dec 27 13:44:18 maximus kernel: [   16.120752] ehci_hcd 0000:00:10.3: irq 18, io mem 0xe0101000
Dec 27 13:44:18 maximus kernel: [   16.120798] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Dec 27 13:44:18 maximus kernel: [   16.120957] usb usb4: configuration #1 chosen from 1 choice
Dec 27 13:44:18 maximus kernel: [   16.121026] hub 4-0:1.0: USB hub found
Dec 27 13:44:18 maximus kernel: [   16.121075] hub 4-0:1.0: 6 ports detected
Dec 27 13:44:18 maximus kernel: [   16.223458] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 23
Dec 27 13:44:18 maximus kernel: [   16.223510] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
Dec 27 13:44:18 maximus kernel: [   16.223560] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 19
Dec 27 13:44:18 maximus kernel: [   16.227692] eth0: VIA Rhine II at 0x1c000, 00:e0:4c:a0:51:0a, IRQ 19.
Dec 27 13:44:18 maximus kernel: [   16.228621] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 41e1.
Dec 27 13:44:18 maximus kernel: [   16.230346] VP_IDE: IDE controller at PCI slot 0000:00:11.1
Dec 27 13:44:18 maximus kernel: [   16.230680] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
Dec 27 13:44:18 maximus kernel: [   16.230725] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
Dec 27 13:44:18 maximus kernel: [   16.230776] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 20
Dec 27 13:44:18 maximus kernel: [   16.230922] VP_IDE: chipset revision 6
Dec 27 13:44:18 maximus kernel: [   16.230962] VP_IDE: not 100%% native mode: will probe irqs later
Dec 27 13:44:18 maximus kernel: [   16.231029] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
Dec 27 13:44:18 maximus kernel: [   16.231085]     ide0: BM-DMA at 0xb400-0xb407, BIOS settings: hda:DMA, hdb:pio
Dec 27 13:44:18 maximus kernel: [   16.231202]     ide1: BM-DMA at 0xb408-0xb40f, BIOS settings: hdc:DMA, hdd:DMA
Dec 27 13:44:18 maximus kernel: [   16.231315] Probing IDE interface ide0...
Dec 27 13:44:18 maximus kernel: [   16.646583] hda: WDC WD1200BB-16DAA0, ATA DISK drive
Dec 27 13:44:18 maximus kernel: [   17.066211] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001106000099b6c5]
Dec 27 13:44:18 maximus kernel: [   17.319921] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Dec 27 13:44:18 maximus kernel: [   17.332281] Probing IDE interface ide1...
Dec 27 13:44:18 maximus kernel: [   18.193091] hdc: SONY DVD RW DRU-510A, ATAPI CD/DVD-ROM drive
Dec 27 13:44:18 maximus kernel: [   18.976333] hdd: ATAPI CD-ROM 52XMax, ATAPI CD/DVD-ROM drive
Dec 27 13:44:18 maximus kernel: [   19.032914] ide1 at 0x170-0x177,0x376 on irq 15
Dec 27 13:44:18 maximus kernel: [   19.044276] SCSI subsystem initialized
Dec 27 13:44:18 maximus kernel: [   19.050656] libata version 2.21 loaded.
Dec 27 13:44:18 maximus kernel: [   19.060399] hda: max request size: 512KiB
Dec 27 13:44:18 maximus kernel: [   19.073098] hda: 234441648 sectors (120034 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
Dec 27 13:44:18 maximus kernel: [   19.074918] hda: cache flushes supported
Dec 27 13:44:18 maximus kernel: [   19.075031]  hda: hda1 hda2 < hda5 >
Dec 27 13:44:18 maximus kernel: [   19.130937] hdc: ATAPI 32X DVD-ROM DVD-R CD-R/RW drive, 8192kB Cache, UDMA(33)
Dec 27 13:44:18 maximus kernel: [   19.131227] Uniform CD-ROM driver Revision: 3.20
Dec 27 13:44:18 maximus kernel: [   19.144336] hdd: ATAPI 52X CD-ROM drive, 0kB Cache, UDMA(33)
Dec 27 13:44:18 maximus kernel: [   19.504373] Attempting manual resume
Dec 27 13:44:18 maximus kernel: [   19.504416] swsusp: Resume From Partition 3:5
Dec 27 13:44:18 maximus kernel: [   19.504418] PM: Checking swsusp image.
Dec 27 13:44:18 maximus kernel: [   19.527982] PM: Resume from disk failed.
Dec 27 13:44:18 maximus kernel: [   19.582023] kjournald starting.  Commit interval 5 seconds
Dec 27 13:44:18 maximus kernel: [   19.582084] EXT3-fs: mounted filesystem with ordered data mode.
Dec 27 13:44:18 maximus kernel: [   29.101295] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 27 13:44:18 maximus kernel: [   29.120504] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Dec 27 13:44:18 maximus kernel: [   29.133192] Linux agpgart interface v0.102 (c) Dave Jones
Dec 27 13:44:18 maximus kernel: [   29.136141] agpgart: Detected VIA KT400/KT400A/KT600 chipset
Dec 27 13:44:18 maximus kernel: [   29.143764] agpgart: AGP aperture is 128M @ 0xd0000000
Dec 27 13:44:18 maximus kernel: [   29.466883] irda_init()
Dec 27 13:44:18 maximus kernel: [   29.466917] NET: Registered protocol family 23
Dec 27 13:44:18 maximus kernel: [   30.074098] input: PC Speaker as /class/input/input2
Dec 27 13:44:18 maximus kernel: [   30.575499] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
Dec 27 13:44:18 maximus kernel: [   30.575551] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
Dec 27 13:44:18 maximus kernel: [   30.575601] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 21
Dec 27 13:44:18 maximus kernel: [   30.575854] PCI: Setting latency timer of device 0000:00:11.5 to 64
Dec 27 13:44:18 maximus kernel: [   30.686747] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
Dec 27 13:44:18 maximus kernel: [   30.689133] parport_pc 00:0b: reported by Plug and Play ACPI
Dec 27 13:44:18 maximus kernel: [   30.689230] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Dec 27 13:44:18 maximus kernel: [   32.101185] lp0: using parport0 (interrupt-driven).
Dec 27 13:44:18 maximus kernel: [   32.177376] Adding 3028212k swap on /dev/hda5.  Priority:-1 extents:1 across:3028212k
Dec 27 13:44:18 maximus kernel: [   32.571815] EXT3 FS on hda1, internal journal
Dec 27 13:44:18 maximus kernel: [   34.426755] input: Power Button (FF) as /class/input/input4
Dec 27 13:44:18 maximus kernel: [   34.431769] ACPI: Power Button (FF) [PWRF]
Dec 27 13:44:18 maximus kernel: [   34.470694] input: Power Button (CM) as /class/input/input5
Dec 27 13:44:18 maximus kernel: [   34.475681] ACPI: Power Button (CM) [PWRB]
Dec 27 13:44:18 maximus kernel: [   34.509287] input: Sleep Button (CM) as /class/input/input6
Dec 27 13:44:18 maximus kernel: [   34.509617] ACPI: Sleep Button (CM) [SLPB]
Dec 27 13:44:18 maximus kernel: [   34.563605] No dock devices found.
Dec 27 13:44:18 maximus NetworkManager: <info>  starting... 
[deleted hal-device lines]
Dec 27 13:44:19 maximus kernel: [   36.339367] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
Dec 27 13:44:19 maximus NetworkManager: <info>  eth0: Device is fully-supported using driver 'via-rhine'. 
Dec 27 13:44:19 maximus NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Dec 27 13:44:19 maximus NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Dec 27 13:44:19 maximus NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Dec 27 13:44:19 maximus NetworkManager: <info>  Deactivating device eth0. 
Dec 27 13:44:19 maximus NetworkManager: <debug> [1198781059.428268] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1106_3059_oss_pcm_1'). 
Dec 27 13:44:19 maximus NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
[deleted hal device lines]
Dec 27 13:44:19 maximus NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Dec 27 13:44:19 maximus NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Dec 27 13:44:19 maximus NetworkManager: <info>  Will activate connection 'eth0'. 
Dec 27 13:44:19 maximus NetworkManager: <info>  Device eth0 activation scheduled... 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) started... 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Dec 27 13:44:19 maximus NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) failure scheduled... 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
[deleted hal device lines]
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) failed. 
Dec 27 13:44:19 maximus NetworkManager: <info>  Deactivating device eth0. 
Dec 27 13:44:19 maximus NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Dec 27 13:44:19 maximus NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Dec 27 13:44:19 maximus NetworkManager: <info>  Will activate connection 'eth0'. 
Dec 27 13:44:19 maximus NetworkManager: <info>  Device eth0 activation scheduled... 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) started... 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Dec 27 13:44:19 maximus NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) failure scheduled... 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Dec 27 13:44:19 maximus cupsd[4892]: *** WARNING *** The programme 'cupsd' uses the Apple Bonjour compatiblity layer of Avahi.
Dec 27 13:44:19 maximus cupsd[4892]: *** WARNING *** Please fix your application to use the native API of Avahi!
Dec 27 13:44:19 maximus cupsd[4892]: *** WARNING *** For more information see <http://0pointer.de/avahi-compat?s=libdns_sd&e=cupsd>
Dec 27 13:44:19 maximus kernel: [   36.763589] audit(1198781059.356:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4892 profile="/usr/sbin/cupsd"
Dec 27 13:44:19 maximus kernel: [   36.829357] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Dec 27 13:44:19 maximus kernel: [   36.829364] apm: overridden by ACPI.
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) failed. 
Dec 27 13:44:19 maximus NetworkManager: <info>  Deactivating device eth0. 
Dec 27 13:44:19 maximus NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Dec 27 13:44:19 maximus NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Dec 27 13:44:19 maximus NetworkManager: <info>  Will activate connection 'eth0'. 
Dec 27 13:44:19 maximus NetworkManager: <info>  Device eth0 activation scheduled... 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) started... 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Dec 27 13:44:19 maximus NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) failure scheduled... 
Dec 27 13:44:19 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) failed. 
Dec 27 13:44:20 maximus NetworkManager: <info>  Deactivating device eth0. 
Dec 27 13:44:20 maximus NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Dec 27 13:44:20 maximus NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Dec 27 13:44:20 maximus NetworkManager: <info>  Will activate connection 'eth0'. 
Dec 27 13:44:20 maximus NetworkManager: <info>  Device eth0 activation scheduled... 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) started... 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Dec 27 13:44:20 maximus NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) failure scheduled... 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) failed. 
Dec 27 13:44:20 maximus NetworkManager: <info>  Deactivating device eth0. 
Dec 27 13:44:20 maximus NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Dec 27 13:44:20 maximus NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Dec 27 13:44:20 maximus NetworkManager: <info>  Will activate connection 'eth0'. 
Dec 27 13:44:20 maximus NetworkManager: <info>  Device eth0 activation scheduled... 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) started... 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Dec 27 13:44:20 maximus NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) failure scheduled... 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) failed. 
Dec 27 13:44:20 maximus NetworkManager: <info>  Deactivating device eth0. 
Dec 27 13:44:20 maximus NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Dec 27 13:44:20 maximus NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Dec 27 13:44:20 maximus NetworkManager: <info>  Will activate connection 'eth0'. 
Dec 27 13:44:20 maximus NetworkManager: <info>  Device eth0 activation scheduled... 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) started... 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Dec 27 13:44:20 maximus NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) failure scheduled... 
Dec 27 13:44:20 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Dec 27 13:44:21 maximus NetworkManager: <info>  Activation (eth0) failed. 
Dec 27 13:44:21 maximus NetworkManager: <info>  Deactivating device eth0. 
Dec 27 13:44:21 maximus NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Dec 27 13:44:21 maximus NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Dec 27 13:44:21 maximus NetworkManager: <info>  Will activate connection 'eth0'. 
Dec 27 13:44:21 maximus NetworkManager: <info>  Device eth0 activation scheduled... 
Dec 27 13:44:21 maximus NetworkManager: <info>  Activation (eth0) started... 
Dec 27 13:44:21 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 27 13:44:21 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Dec 27 13:44:21 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Dec 27 13:44:21 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Dec 27 13:44:21 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Dec 27 13:44:21 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Dec 27 13:44:21 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Dec 27 13:44:21 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Dec 27 13:44:21 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Dec 27 13:44:21 maximus NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Dec 27 13:44:21 maximus NetworkManager: <info>  Activation (eth0) failure scheduled... 
Dec 27 13:44:21 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Dec 27 13:44:21 maximus ntpd[5211]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Dec 27 13:44:21 maximus ntpd[5228]: precision = 1.000 usec
Dec 27 13:44:21 maximus ntpd[5228]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Dec 27 13:44:21 maximus ntpd[5228]: Listening on interface #1 wildcard, ::#123 Disabled
Dec 27 13:44:21 maximus ntpd[5228]: Listening on interface #2 lo, ::1#123 Enabled
Dec 27 13:44:21 maximus ntpd[5228]: Listening on interface #3 lo, 127.0.0.1#123 Enabled
Dec 27 13:44:21 maximus ntpd[5228]: kernel time sync status 0040
Dec 27 13:44:21 maximus ntpd[5228]: frequency initialized 104.296 PPM from /var/lib/ntp/ntp.drift
Dec 27 13:44:21 maximus NetworkManager: <info>  Activation (eth0) failed. 
Dec 27 13:44:21 maximus NetworkManager: <info>  Deactivating device eth0. 
Dec 27 13:44:21 maximus NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Dec 27 13:44:21 maximus NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running! 
Dec 27 13:44:21 maximus NetworkManager: <info>  Will activate connection 'eth0'. 
Dec 27 13:44:21 maximus NetworkManager: <info>  Device eth0 activation scheduled... 
Dec 27 13:44:21 maximus NetworkManager: <info>  Activation (eth0) started... 
Dec 27 13:44:21 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 27 13:44:21 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Dec 27 13:44:21 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Dec 27 13:44:21 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Dec 27 13:44:21 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Dec 27 13:44:21 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Dec 27 13:44:21 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Dec 27 13:44:21 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Dec 27 13:44:21 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Dec 27 13:44:21 maximus NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running! 
Dec 27 13:44:21 maximus NetworkManager: <info>  Activation (eth0) failure scheduled... 
Dec 27 13:44:21 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Dec 27 13:44:21 maximus kernel: [   38.285146] Failure registering capabilities with primary security module.
Dec 27 13:44:21 maximus avahi-daemon[5272]: Found user 'avahi' (UID 106) and group 'avahi' (GID 114).
Dec 27 13:44:21 maximus avahi-daemon[5272]: Successfully dropped root privileges.
Dec 27 13:44:21 maximus avahi-daemon[5272]: avahi-daemon 0.6.20 starting up.
Dec 27 13:44:21 maximus avahi-daemon[5272]: Successfully called chroot().
Dec 27 13:44:21 maximus avahi-daemon[5272]: Successfully dropped remaining capabilities.
Dec 27 13:44:21 maximus avahi-daemon[5272]: No service file found in /etc/avahi/services.
Dec 27 13:44:21 maximus avahi-daemon[5272]: Network interface enumeration completed.
Dec 27 13:44:21 maximus avahi-daemon[5272]: Registering HINFO record with values 'I686'/'LINUX'.
Dec 27 13:44:21 maximus avahi-daemon[5272]: Server startup complete. Host name is maximus.local. Local service cookie is 881830352.
Dec 27 13:44:21 maximus dhcdbd: Started up.
Dec 27 13:44:21 maximus NetworkManager: <info>  Activation (eth0) failed. 
Dec 27 13:44:21 maximus NetworkManager: <info>  Deactivating device eth0. 
Dec 27 13:44:21 maximus NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Dec 27 13:44:21 maximus anacron[5341]: Anacron 2.3 started on 2007-12-27
Dec 27 13:44:21 maximus anacron[5341]: Normal exit (0 jobs run)
Dec 27 13:44:21 maximus /usr/sbin/cron[5375]: (CRON) INFO (pidfile fd = 3)
Dec 27 13:44:21 maximus /usr/sbin/cron[5376]: (CRON) STARTUP (fork ok)
Dec 27 13:44:21 maximus /usr/sbin/cron[5376]: (CRON) INFO (Running @reboot jobs)
Dec 27 13:44:22 maximus kernel: [   39.299678] [drm] Initialized drm 1.1.0 20060810
Dec 27 13:44:22 maximus kernel: [   39.315707] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 22
Dec 27 13:44:22 maximus kernel: [   39.318887] [drm] Initialized radeon 1.27.0 20060524 on minor 0
Dec 27 13:44:23 maximus ntpd_initres[5247]: host name not found: 0.pool.ntp.org
Dec 27 13:44:23 maximus ntpd_initres[5247]: couldn't resolve `0.pool.ntp.org', giving up on it
Dec 27 13:44:23 maximus ntpd_initres[5247]: host name not found: 1.pool.ntp.org
Dec 27 13:44:23 maximus ntpd_initres[5247]: couldn't resolve `1.pool.ntp.org', giving up on it
Dec 27 13:44:23 maximus ntpd_initres[5247]: host name not found: 2.pool.ntp.org
Dec 27 13:44:23 maximus ntpd_initres[5247]: couldn't resolve `2.pool.ntp.org', giving up on it
Dec 27 13:44:23 maximus ntpd_initres[5247]: host name not found: pool.ntp.org
Dec 27 13:44:23 maximus ntpd_initres[5247]: couldn't resolve `pool.ntp.org', giving up on it
Dec 27 13:44:23 maximus kernel: [   40.433589] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Dec 27 13:44:23 maximus kernel: [   40.433878] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Dec 27 13:44:23 maximus kernel: [   40.434083] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Dec 27 13:44:23 maximus dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Dec 27 13:44:23 maximus NetworkManager: <info>  Will activate connection 'eth0'. 
Dec 27 13:44:23 maximus NetworkManager: <info>  Device eth0 activation scheduled... 
Dec 27 13:44:23 maximus NetworkManager: <info>  Activation (eth0) started... 
Dec 27 13:44:23 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 27 13:44:23 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Dec 27 13:44:23 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Dec 27 13:44:23 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Dec 27 13:44:23 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Dec 27 13:44:23 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Dec 27 13:44:23 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Dec 27 13:44:23 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Dec 27 13:44:23 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Dec 27 13:44:23 maximus kernel: [   40.789706] [drm] Setting GART location based on new memory map
Dec 27 13:44:23 maximus kernel: [   40.789753] [drm] writeback test succeeded in 1 usecs
Dec 27 13:44:24 maximus NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Dec 27 13:44:24 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Dec 27 13:44:24 maximus NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Dec 27 13:44:25 maximus NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Dec 27 13:44:25 maximus kernel: [   42.810989] NET: Registered protocol family 17
Dec 27 13:44:29 maximus dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Dec 27 13:44:30 maximus dhclient: DHCPACK from 192.168.1.1
Dec 27 13:44:30 maximus avahi-daemon[5272]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.203.
Dec 27 13:44:30 maximus avahi-daemon[5272]: New relevant interface eth0.IPv4 for mDNS.
Dec 27 13:44:30 maximus avahi-daemon[5272]: Registering new address record for 192.168.1.203 on eth0.IPv4.
Dec 27 13:44:30 maximus NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface eth0 
Dec 27 13:44:30 maximus NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Dec 27 13:44:30 maximus NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Dec 27 13:44:30 maximus dhclient: bound to 192.168.1.203 -- renewal in 33663 seconds.
Dec 27 13:44:30 maximus dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Dec 27 13:44:30 maximus dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Dec 27 13:44:30 maximus dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Dec 27 13:44:30 maximus dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Dec 27 13:44:30 maximus NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Dec 27 13:44:30 maximus NetworkManager: <info>    address 192.168.1.203 
Dec 27 13:44:30 maximus NetworkManager: <info>    netmask 255.255.255.0 
Dec 27 13:44:30 maximus NetworkManager: <info>    broadcast 192.168.1.255 
Dec 27 13:44:30 maximus NetworkManager: <info>    gateway 192.168.1.1 
Dec 27 13:44:30 maximus NetworkManager: <info>    nameserver 192.168.1.1 
Dec 27 13:44:30 maximus NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Dec 27 13:44:30 maximus NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Dec 27 13:44:30 maximus NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Dec 27 13:44:30 maximus avahi-daemon[5272]: Withdrawing address record for 192.168.1.203 on eth0.
Dec 27 13:44:30 maximus avahi-daemon[5272]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.203.
Dec 27 13:44:30 maximus avahi-daemon[5272]: Interface eth0.IPv4 no longer relevant for mDNS.
Dec 27 13:44:30 maximus avahi-daemon[5272]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.203.
Dec 27 13:44:30 maximus avahi-daemon[5272]: New relevant interface eth0.IPv4 for mDNS.
Dec 27 13:44:30 maximus avahi-daemon[5272]: Registering new address record for 192.168.1.203 on eth0.IPv4.
Dec 27 13:44:31 maximus NetworkManager: <info>  Clearing nscd hosts cache. 
Dec 27 13:44:31 maximus NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Dec 27 13:44:31 maximus NetworkManager: <info>  Activation (eth0) successful, device activated. 
Dec 27 13:44:31 maximus NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Dec 27 13:44:31 maximus NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Dec 27 13:44:33 maximus avahi-daemon[5272]: Registering new address record for fe80::2e0:4cff:fea0:510a on eth0.*.
Dec 27 13:44:42 maximus kernel: [   59.570860] eth0: no IPv6 routers present
Dec 27 13:44:48 maximus NetworkManager: <info>  Updating allowed wireless network lists. 
Dec 27 13:44:48 maximus NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..

---

### Post by heindsight on 2007-12-27
Well, it seems the ntpd script isn't running when NetworkManager brings up eth0.

Somewhere just after these lines in your log
> **movrshakr said:**
> 
Dec 27 13:44:31 maximus NetworkManager: <info>  Activation (eth0) successful, device activated. 
Dec 27 13:44:31 maximus NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Dec 27 13:44:31 maximus NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 

you should be seeing something like this:
```
Dec 27 17:53:25 localhost ntpd[5470]: ntpd exiting on signal 15
Dec 27 17:53:29 localhost ntpdate[5895]: adjust time server 131.211.84.189 offset 0.005943 sec
Dec 27 17:53:29 localhost ntpd[5973]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 22:22:31 UTC 2007 (1)

```
Followed by several more lines from ntpd as it starts up and associates with other servers.

Everything else seems OK, except that our ntpd script is not running when it should be. 

I know it seems silly, but are you VERY sure that you have the correct ntpd script in 
/etc/network/if-up.d and that it is executable? I'm afraid I really can't think of any other reason
why it doesn't run.

---

### Post by movrshakr on 2007-12-27
OK, As you saw, I edited your original script some, so I will go get the original and install it with NO edits at all.

Hold on a few minutes.

While I am doing that, consider these:
DOES ntpdate-debian NEED A START PARAMETER?
DOES ntpdate-debian CALL NTPDATE SCRIPT, WHICH WE HAVE MADE NON-EXECUTABLE?

---

### Post by heindsight on 2007-12-27
> **movrshakr said:**
> OK, As you saw, I edited your original script some, so I will go get the original and install it with NO edits at all.

Hold on a few minutes.

While I am doing that, consider these:
DOES ntpdate-debian NEED A START PARAMETER?
DOES ntpdate-debian CALL NTPDATE SCRIPT, WHICH WE HAVE MADE NON-EXECUTABLE?

[http://ubuntuforums.org/showpost.php?p=4023660&postcount=35](http://ubuntuforums.org/showpost.php?p=4023660&postcount=35)

---

### Post by movrshakr on 2007-12-27
OK, on the two questions--I missed that.

And, here's the deal with using EXACTLY your script
(I don't know why it is different with my little mods, but clearly there is a difference)...

a. There were still multiple eth0 starts, stage 1 to 3
b. After eth0 #6 (or 7?) there is this:
Dec 27 14:38:54 maximus ntpd[5217]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Dec 27 14:38:55 maximus NetworkManager: <info>  Activation (eth0) failed. 
Dec 27 14:38:55 maximus NetworkManager: <info>  Deactivating device eth0. 

c.deleted

d. ...and just about 10 lines after that is: 
Dec 27 14:38:55 maximus **ntpd[5218]: frequency initialized **104.296 PPM from /var/lib/ntp/ntp.drift
Dec 27 14:38:55 maximus NetworkManager: <info>  Activation (eth0) failed. 
Dec 27 14:38:55 maximus NetworkManager: <info>  Deactivating device eth0. 

e. then another eth0 through stage 3 and 
Dec 27 14:38:57 maximus ntpd_initres[5278]: **host name not found: 0.pool.ntp.org**
Dec 27 14:38:57 maximus ntpd_initres[5278]: couldn't resolve `0.pool.ntp.org', giving up on it
Dec 27 14:38:57 maximus ntpd_initres[5278]: host name not found: 1.pool.ntp.org
Dec 27 14:38:57 maximus ntpd_initres[5278]: couldn't resolve `1.pool.ntp.org', giving up on it
Dec 27 14:38:57 maximus ntpd_initres[5278]: host name not found: 2.pool.ntp.org
Dec 27 14:38:57 maximus ntpd_initres[5278]: couldn't resolve `2.pool.ntp.org', giving up on it
Dec 27 14:38:57 maximus ntpd_initres[5278]: host name not found: pool.ntp.org
Dec 27 14:38:57 maximus ntpd_initres[5278]: couldn't resolve `pool.ntp.org', giving up on it

f. then success with eth0 after LOTS of effort...1-3, then stuff, then 4-5 PLUS **ntpdate** and  **ntpd** AGAIN (I think this may be where the script is running and the above stuff is from who knows why)....
Dec 27 14:38:57 maximus dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Dec 27 14:38:57 maximus NetworkManager: <info>  Will activate connection 'eth0'. 
Dec 27 14:38:57 maximus NetworkManager: <info>  Device eth0 activation scheduled... 
Dec 27 14:38:57 maximus NetworkManager: <info>  Activation (eth0) started... 
Dec 27 14:38:57 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 27 14:38:57 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Dec 27 14:38:57 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Dec 27 14:38:57 maximus NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Dec 27 14:38:57 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Dec 27 14:38:57 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Dec 27 14:38:57 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Dec 27 14:38:57 maximus NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Dec 27 14:38:57 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Dec 27 14:38:57 maximus kernel: [   41.446424] [drm] Setting GART location based on new memory map
Dec 27 14:38:57 maximus kernel: [   41.446471] [drm] writeback test succeeded in 1 usecs
Dec 27 14:38:58 maximus NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Dec 27 14:38:58 maximus NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Dec 27 14:38:58 maximus NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Dec 27 14:38:59 maximus NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Dec 27 14:38:59 maximus kernel: [   43.725435] NET: Registered protocol family 17
Dec 27 14:39:03 maximus dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Dec 27 14:39:05 maximus dhclient: DHCPACK from 192.168.1.1
Dec 27 14:39:05 maximus avahi-daemon[5260]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.203.
Dec 27 14:39:05 maximus avahi-daemon[5260]: New relevant interface eth0.IPv4 for mDNS.
Dec 27 14:39:05 maximus avahi-daemon[5260]: Registering new address record for 192.168.1.203 on eth0.IPv4.
Dec 27 14:39:05 maximus NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface eth0 
Dec 27 14:39:05 maximus NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Dec 27 14:39:05 maximus NetworkManager: <info>  Activation **(eth0) Stage 4 of 5 (IP Configure Get) started...** 
Dec 27 14:39:05 maximus dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Dec 27 14:39:05 maximus dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Dec 27 14:39:05 maximus dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Dec 27 14:39:05 maximus dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Dec 27 14:39:05 maximus NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Dec 27 14:39:05 maximus NetworkManager: <info>    address 192.168.1.203 
Dec 27 14:39:05 maximus NetworkManager: <info>    netmask 255.255.255.0 
Dec 27 14:39:05 maximus NetworkManager: <info>    broadcast 192.168.1.255 
Dec 27 14:39:05 maximus NetworkManager: <info>    gateway 192.168.1.1 
Dec 27 14:39:05 maximus NetworkManager: <info>    nameserver 192.168.1.1 
Dec 27 14:39:05 maximus NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Dec 27 14:39:05 maximus NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Dec 27 14:39:05 maximus NetworkManager: <info>  Activation **(eth0) Stage 5 of 5 (IP Configure Commit) started... **
Dec 27 14:39:05 maximus avahi-daemon[5260]: Withdrawing address record for 192.168.1.203 on eth0.
Dec 27 14:39:05 maximus avahi-daemon[5260]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.203.
Dec 27 14:39:05 maximus avahi-daemon[5260]: Interface eth0.IPv4 no longer relevant for mDNS.
Dec 27 14:39:05 maximus avahi-daemon[5260]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.203.
Dec 27 14:39:05 maximus avahi-daemon[5260]: New relevant interface eth0.IPv4 for mDNS.
Dec 27 14:39:05 maximus avahi-daemon[5260]: Registering new address record for 192.168.1.203 on eth0.IPv4.
Dec 27 14:39:05 maximus dhclient: bound to 192.168.1.203 -- renewal in 27955 seconds.
Dec 27 14:39:06 maximus NetworkManager: <info>  Clearing nscd hosts cache. 
Dec 27 14:39:06 maximus NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Dec 27 14:39:06 maximus NetworkManager: <info>  Activation (eth0) successful, device activated. 
Dec 27 14:39:06 maximus NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Dec 27 14:39:06 maximus NetworkManager: <info>  **Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.**
Dec 27 14:39:06 maximus ntpd[5218]: ntpd exiting on signal 15
Dec 27 14:39:07 maximus avahi-daemon[5260]: Registering new address record for fe80::2e0:4cff:fea0:510a on eth0.*.
Dec 27 14:39:14 maximus **ntpdate**[5593]: adjust time server 64.202.112.75 offset -0.018117 sec
Dec 27 14:39:15 maximus **ntpd[5830]: ntpd **4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Dec 27 14:39:15 maximus ntpd[5831]: precision = 1.000 usec
Dec 27 14:39:15 maximus ntpd[5831]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Dec 27 14:39:15 maximus ntpd[5831]: Listening on interface #1 wildcard, ::#123 Disabled
Dec 27 14:39:15 maximus ntpd[5831]: Listening on interface #2 eth0, fe80::2e0:4cff:fea0:510a#123 Enabled
Dec 27 14:39:15 maximus ntpd[5831]: Listening on interface #3 lo, ::1#123 Enabled
Dec 27 14:39:15 maximus ntpd[5831]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Dec 27 14:39:15 maximus ntpd[5831]: Listening on interface #5 eth0, 192.168.1.203#123 Enabled
Dec 27 14:39:15 maximus ntpd[5831]: kernel time sync status 0040
Dec 27 14:39:15 maximus ntpd[5831]: frequency initialized 104.296 PPM from /var/lib/ntp/ntp.drift
ONLY 4 MORE LINES FOLLOWED--END OF LOG

ntpd was running and associated.  So it looks like we ended with the desired result (ntpdate first, then ntpd associated) but with a lot of thrashing around before that.

---

### Post by heindsight on 2007-12-27
Congratulations! That looks right to me anyway. ntpd gets started twice,
the first time from the initscript in rc2.d:
> Dec 27 14:38:55 maximus ntpd[5218]: frequency initialized 104.296 PPM from /var/lib/ntp/ntp.drift

but it fails to associate:
> Dec 27 14:38:57 maximus ntpd_initres[5278]: host name not found: 0.pool.ntp.org
Dec 27 14:38:57 maximus ntpd_initres[5278]: couldn't resolve `0.pool.ntp.org', giving up on it

Then eventually NetworkManager gets eth0 up
> Dec 27 14:39:06 maximus NetworkManager: <info> Activation (eth0) successful, device activated. 

and runs our script which stops ntpd 
> Dec 27 14:39:06 maximus ntpd[5218]: ntpd exiting on signal 15

runs ntpdate 
> Dec 27 14:39:14 maximus ntpdate[5593]: adjust time server 64.202.112.75 offset -0.018117 sec


and starts ntpd again. 
> Dec 27 14:39:15 maximus ntpd[5830]: ntpd 4.2.4p0@1.1472-o Thu Oct 4 20:58:45 UTC 2007 (1)

Excellent! Of course now that you've got it working you can start tinkering with that script again
and see if you can figure out why the changes you made broke it. ;)

Like I said before, if you move S24dhcdbd to S13dhcdbd in /etc/rc2.d then NetworkManager
should get eth0 up faster.

---

### Post by movrshakr on 2007-12-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/ntp/+bug/114505](https://bugs.launchpad.net/ubuntu/+source/ntp/+bug/114505) [br].[/br] ---------------------------- [br].[/br] 
				OK, I will try that.  We have a working arrangement here, but there is this "thing" inside me that says all those repeated eth0 startup attempts are just "wrong."  I don't like dirty, inelegant (thus 'wrong') things.

I'll move the priority and see what that does.  I still worry that deviating from the "standard" will create problems later (and I won't remember the details of what was changed!...a problem of being born too long ago)

You might want to post a summary of this over on the bugs =  launchpad.net site since it is your fundamental fantastic work.

Thanks again.

---

### Post by heindsight on 2007-12-27
> **movrshakr said:**
> 
I'll move the priority and see what that does.  I still worry that deviating from the "standard" will create problems later
As far as I'm concerned, 99% of the reason for using a free operating system (as in religion, not
beer -- although free beer can be a religion) is having the freedom to do things the way you want it,
not having to trust that some code monkey you've never met knows what's best for you. So change
it with a smile on your face and a song in your heart and as you do it, say "Thank you, Richard Stallman!"

And if you're worried about not being able to fix it again later, if necessary, then bookmark this thread or something :)

---

### Post by movrshakr on 2007-12-27
Hmmm, as I started this, I see...

dhcdbd is S24 in 2-5, but K16 in 0,1,6.  What do I change the Kill priority to?

Also, avahi-xxxx is also S24/K16.  How can they both be the same?

---

### Post by movrshakr on 2007-12-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/ntp/+bug/114505](https://bugs.launchpad.net/ubuntu/+source/ntp/+bug/114505) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				As they say in the South, "Well gol-darned."

I reset (using "sysv-rc-conf -p ' by the way) S24dhcdbd to S13dhcdbd in /etc/rc[2-5].d.  And, lo and behold, 

a. ntpd tries to start but fails to get associations due to eth0 not being configured yet (as before)...BUT...

b. eth0 no longer tried 7 to 10 times to come up; it goes through the five stages only once!

c. ntpdate runs--apparently successfully--from the new script:.. 
(Dec 27 18:57:48 maximus ntpdate[5454]: adjust time server 209.132.176.4 offset 0.009138 sec)

d. ntpd starts again, successfully--from the new script, as a post boot 'ntpq -p' shows associations to the servers configured in ntp.conf.

In other words, all works as it should, after the modifications so kindly suggested by heindsight.

Summary: on my machine, the problem is completely solved by 
doing the changes he suggested (read previous posts) and 
using the script file he provided, and 
changing dhcdbd to priority S13 (BTW, I left the Kill ones unchanged at K16 in 0,1,6)

Thanks, heindsight.  You have my sincere gratitude.  And I hope the devs use this to fix this BUG in the next release.

---

### Post by blueridgedog on 2007-12-27
> **heindsight said:**
>  I've been doing some experiments (poor ceridwen has never been
rebooted so many times within 48 hours before) and I think I have a solution

Not that it is relevant to the thread, but why not use telinit?

sudo telinit 1

Then to test:

sudo telinit 5

---

### Post by heindsight on 2007-12-27
> **movrshakr said:**
> (BTW, I left the Kill ones unchanged at K16 in 0,1,6)
Was going to suggest that yes. As long as you're not having trouble with shutdown, there's no
real reason to change them.

> **blueridgedog said:**
> Not that it is relevant to the thread, but why not use telinit?

sudo telinit 1

Then to test:

sudo telinit 5

Because that doesn't quite reproduce what happens when the system boots. In runlevel 1 a few
services may be running and some network interfaces (loopback, interfaces with static addresses)
may be up. Also  the scripts in rcS.d are run before entering runlevel 1, and not when switching 
from runlevel 1 to 2 (or 5). So the only way to accurately reproduce what happens when the system
boots, is to boot the system.

I suppose I could have set up a virtual machine and done all the experimentation and testing on 
that, but I didn't think of that until now, and even if I had, I would probably have decided that it
would be too much effort to set up a virtual machine just for this.

---

### Post by movrshakr on 2008-01-29
A note to all:

updates released sometime shortly before 1-27-08, when I installed them, **REVERTED **the change of S24dhcdbd to S13dhcdbd start priority **in rc5.d** back to S24 !!   
(I used  "sysv-rc-conf -p ' tool to make the previous changes by the way) 

This reversion caused the previous behavior of multiple attempts to start eth0 to return.  If you installed these updates, you should check your system and ensure none of the changes you previously made to correct this bug were not undone like mine were.

---

### Post by dave_atl on 2008-02-02
I had  the exact same issue come up on my server. I got round it by a simple edit of the /etc/network/if-up.d/ntpdate script. In order to stop ntpdate running in the backgroud and conflicting with the ntpd startup, I removed the "&" from the line shown below:

/usr/sbin/ntpdate-debian -s $OPTS 2>/dev/null &

Now it shows:

/usr/sbin/ntpdate-debian -s $OPTS 2>/dev/null

and a simple reboot has ntpdate running to completion and then starting ntpd without errors.

Hope this helps others.

---

### Post by movrshakr on 2008-02-02
dave_atl, which "exact same issue" are you referring to...the whole of this thread, or just the last part about recent updates interfering with the workaround (and according to other threads, with networking in general)?

In short, exactly what symptom did removing the background & solve?

Also, did you implement the whole of this workarond bug fix...the heindsight script and start order changes, etc?

---

### Post by dave_atl on 2008-02-03
It was really the first issue mentioned in the thread I was experiencing. NTPD would not start on bootup even though it was configured to since NTPDATE was still running. I tracked down where NTPDATE was being called and saw that it was being sent to background and NTPD would then try to start up but could not. 

By removing the "&" the boot process waits for NTPDATE to complete before starting up NTPD. 

I actually came across this post and the other "fixes" after I changed the ip.up script. I didn't need the other workarounds to fix my problem so I literally only removed the "&" and it was fixed.

---

### Post by movrshakr on 2008-02-03
OK, thanks for the clarification.

It is interesting to wonder what the logic was of the creators of the standard script in putting the & (run as background) in there in the first place.  

I can speculate but do not really know...the ntpdate functioning requires some time to complete (contacting the time servers etc).  So, would I be correct that, without the &, the boot process will hold at that point until ntpdate closes with a completion code?

---

### Post by dave_atl on 2008-02-03
I believe that is the exact reason - I found some info in the ntpdate change log that shows that the "&" was added to reduce boot time.

Here's the link: [https://lists.ubuntu.com/archives/ubuntu-patches/2006-November/004045.html]("https://lists.ubuntu.com/archives/ubuntu-patches/2006-November/004045.html")

Search for the word "background" and it shows the bug report numbers for the slow boot issue.

Since I reboot on a weekly cron job in the middle of the night, I can afford the boot process running a few minutes longer.

---

