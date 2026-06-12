---
title: "localhost:631 not found"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by stevieb on 2007-12-22
hello,

i'm trying to configure a network printer through a web interface, but whenever i type in "http://localhost:631/" i get error 404.

any ideas?

thanks,

steve (running feisty)

---

### Post by SOULRiDER on 2007-12-22
CUPS may not be running. Try
```
sudo /etc/init.d/cups start
```

---

### Post by stevieb on 2007-12-22
```
steve@darwin:~$ sudo /etc/init.d/cups start
Password:
sudo: /etc/init.d/cups: command not found
steve@darwin:~$ sudo /etc/init.d/cupsys start
 * Starting Common Unix Printing System: cupsd                                                                          [ OK ] 
steve@darwin:~$ 

```

still no dice- error 404

---

### Post by stevieb on 2007-12-23
(bump) :-)

---

### Post by p_quarles on 2007-12-23
Sounds like it could be one of a few things: a missing package, a misconfigured network, etc. Anyway, run this:
```
netstat -tunva
```
You should see a line like this:
```
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN 
```
Let us know whether that line is/isn't there.

Next, run these commands and post the output here:
```
cat /etc/network/interfaces
```
and 
```
ifconfig -a
```
These questions are based on my hunch that this has something to do with the loopback network interface (i.e., "localhost").

---

### Post by SOULRiDER on 2007-12-23
You must not have CUPS installed? Try this, its not the same command as before if you look close.
```
sudo /etc/init.d/cupsd start
```
If that doesnt start CUPS check this link out:
[https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)

---

### Post by p_quarles on 2007-12-23
> **SOULRiDER said:**
> You must not have CUPS installed? Try this, its not the same command as before if you look close.
```
sudo /etc/init.d/cupsd start
```
If that doesnt start CUPS check this link out:
[https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)
Err, cupsd isn't the name of the startup script. It's cupsys, and the OP got an "all okay" message when he restarted it.

---

### Post by stevieb on 2007-12-23
```
tcp        0      0 127.0.0.1:631           127.0.0.1:54089         ESTABLISHED

```

```
steve@darwin:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp


#iface eth0 inet dhcp



iface eth0 inet dhcp


```

```
steve@darwin:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:CA:93:82
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0xc000

eth1      Link encap:Ethernet  HWaddr 00:14:A5:9C:78:1D
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14650 errors:0 dropped:3593 overruns:0 frame:0
          TX packets:9266 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:11026402 (10.5 MiB)  TX bytes:1274312 (1.2 MiB)
          Interrupt:23 Base address:0xc000

eth0:avah Link encap:Ethernet  HWaddr 00:0F:B0:CA:93:82
          inet addr:169.254.8.164  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:37445 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37445 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:11803197 (11.2 MiB)  TX bytes:11803197 (11.2 MiB)

```

---

### Post by p_quarles on 2007-12-23
Wow, that's weird: not only is CUPS running, but it's showing that your browser is even connected to it. 

What do you get from this?:
```
lpstat -p
```

---

### Post by stevieb on 2007-12-23
```
steve@darwin:~$ lpstat -p
printer CUPS-PDF disabled since Sun 23 Dec 2007 07:26:23 AM EST -
        Backend /usr/lib/cups/backend/pdf-writer does not exist!
```

---

### Post by p_quarles on 2007-12-23
Hmm. Curiouser and curiouser. Try taking a look at the CUPS error logs:
```
less /var/log/cups/error_log
```

---

### Post by stevieb on 2007-12-23
```
steve@darwin:~$ cat /var/log/cups/error_log
I [23/Dec/2007:07:26:23 -0500] Saving job cache file "/var/cache/cups/job.cache"...
E [23/Dec/2007:07:26:23 -0500] Will not use User root (UID=0) as specified on line 59 for security reasons.  You must use a non-privileged account instead.
I [23/Dec/2007:07:26:23 -0500] Listening to 0.0.0.0:631 (IPv4)
I [23/Dec/2007:07:26:23 -0500] Listening to :::631 (IPv6)
I [23/Dec/2007:07:26:23 -0500] Loaded configuration file "/etc/cups/cupsd.conf"
I [23/Dec/2007:07:26:23 -0500] Using default TempDir of /var/spool/cups/tmp...
I [23/Dec/2007:07:26:23 -0500] Cleaning out old temporary files in "/var/spool/cups/tmp"...
I [23/Dec/2007:07:26:23 -0500] Configured for up to 100 clients.
I [23/Dec/2007:07:26:23 -0500] Allowing up to 100 client connections per host.
I [23/Dec/2007:07:26:23 -0500] Creating CUPS default administrative policy:
I [23/Dec/2007:07:26:23 -0500] <Policy default>
I [23/Dec/2007:07:26:23 -0500] <Limit Send-Document Send-URI Cancel-Job Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Authenticate-Job>
I [23/Dec/2007:07:26:23 -0500] Order Deny,Allow
I [23/Dec/2007:07:26:23 -0500] Require user @OWNER @SYSTEM
I [23/Dec/2007:07:26:23 -0500] </Limit>
I [23/Dec/2007:07:26:23 -0500] <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
I [23/Dec/2007:07:26:23 -0500] Order Deny,Allow
I [23/Dec/2007:07:26:23 -0500] AuthType Basic
I [23/Dec/2007:07:26:23 -0500] Require user @SYSTEM
I [23/Dec/2007:07:26:23 -0500] </Limit>
I [23/Dec/2007:07:26:23 -0500] <Limit All>
I [23/Dec/2007:07:26:23 -0500] Order Deny,Allow
I [23/Dec/2007:07:26:23 -0500] </Limit>
I [23/Dec/2007:07:26:23 -0500] </Policy>
I [23/Dec/2007:07:26:23 -0500] Full reload is required.
I [23/Dec/2007:07:26:23 -0500] Loaded MIME database from '/usr/share/cups/mime:/etc/cups': 34 types, 39 filters...
I [23/Dec/2007:07:26:23 -0500] Loading job cache file "/var/cache/cups/job.cache"...
I [23/Dec/2007:07:26:23 -0500] Full reload complete.
I [23/Dec/2007:07:26:23 -0500] Listening to 0.0.0.0:631 on fd 2...
E [23/Dec/2007:07:26:23 -0500] Unable to open listen socket for address :::631 - Address family not supported by protocol.

```

---

### Post by p_quarles on 2007-12-23
Well, a couple of things stand out to me there. First, it looks like there's a configuration somewhere that's trying to print a job as root (?). I'm guessing this is either in /var/cache/cups/job.cache or /etc/cups/cupsd.conf. In either case, it's apparently in line 59. ;)

The other thing is that the last line indicates a problem with the IPv6 version of the listening address. Do you know if you've had any other problems with IPv6?

---

### Post by stevieb on 2007-12-23
first, thanks for the help!

can i clear out the job.cache file (i don't have anything waiting to print) and/or regenerate the cupsd.conf?

i did have some issues with IPv6 earlier, but i can't remember what they were (i think it had something to do with running a software midi synthesizer).  in any case, the printing thing is new- since the last kernel update last week or so.  also, i'm running a lowlatency kernel, if that adds any info.

thanks again!
-steve

---

### Post by p_quarles on 2007-12-23
Yeah, you could rename the current job.cache file, and create a new empty one:
```
sudo mv /var/cache/cups/job.cache /var/cache/cups/job.bak
sudo touch /var/cache/cups/job.cache
```
On my system, there is already a backup of the cupsd.conf defaults, which you could restore:
```
sudo cp /etc/cups/cupsd.conf.default /etc/cups/cupsd.conf
```
I don't know how much of a difference either of those steps will make, though. Did you find anything related to the root user in those files?

I am kinda thinking this is a networking issue, so try disabling IPv6. If you already did that, it could have come back with the kernel upgrade depending on the method you used. Anyway, here are the various methods:
[https://answers.launchpad.net/ubuntu/+question/5177](https://answers.launchpad.net/ubuntu/+question/5177)

---

### Post by stevieb on 2007-12-23
i don't know, still no luck.  i don't have a clean cupsd.conf to fall back on; i'll try and find a sample one online somewhere.  i turned off ipv6, both in modprobe and firefox itself (the about:config page).  i also cleaned out the job.cache file.  i don't really know what to look foras far as root jobs that would be the cause here.

localhost:631 is not something i typically pull up on a routine basis, and it just so happens that i haven't printed anything in a couple of weeks, so my only clue as to a cause is the recent kernel update.

i found the problem when i tried to add my network printer to a new laptop.  i couldn't remember the exact ipp://blahblah format and figured, "oh, i'll just pull up the settings that i used on darwin."  that's when i got the 404 error.

thanks again for the help; i'll think about a different way to ask the question and re-post.  i'm also remembering something about "adduser shadow cupsys something", i'll go look that up now.

cheers, 

steve

---

### Post by stevieb on 2007-12-26
problem was solved by "complete" removal (incl. config files) and reinstallation of cupsys.  thanks to all who took the time to help!!

---

