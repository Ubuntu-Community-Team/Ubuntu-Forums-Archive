---
title: "Can't connect to MPD"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by infinitejones on 2007-06-21
I've got MPD running smoothly on my server, and the clients (MPC and GMPC) can connect to it fine from that machine. However, no clients can connect from my laptop which is connected via the LAN.

When I run mpc or gmpc (or any client) from the command line on the laptop, I get :

error: problems getting a response from "localhost" on port 6600 : Connection refused

The laptop can ping the server, and everything else (ie. NFS sharing) is absolutely fine between the two machines. Both machines running feisty.

I searched through these forums for a couple of days and dug up just about every post related to mpd with no luck. Weirdly, when I do sudo dpkg-reconfigure mpd on the server, nothing happens - just a pause and the command line appears again.

The only two things I can think of are:

1) Do I need MPD running on the laptop? Surely not - I don't need to run Apache in order to browse the web.
2) Do I need to explicitly open a port on my router? Again, surely not - there's no traffic moving outside the network.

Any ideas? Thanks!

---

### Post by dichtbijzee on 2007-06-21
you need to connect to the servers ip instead of your localhost.

and if that doesnt work disable all firewalls.

---

### Post by infinitejones on 2007-06-21
Thanks for the suggestions... already tried the first one with no luck. And I've exported MPD_HOST and MPD_PORT variables too.

With regards to firewalls - I haven't set one up on either machine, but is there some kind of default firewall or port blocking in Feisty?

---

### Post by dichtbijzee on 2007-06-21
i'm sorry cant help you any further. well maybe.

one thing, what is the output if you try to connect to the server instead of the localhost?

---

### Post by infinitejones on 2007-06-21
MPD is only running on the server, and when I connect via a client installed on the server (using localhost as the server name) everything is fine.

However, when I try to connect gmpc (or any other client I've tried) installed on the laptop to mpd installed on the server machine, I get this error:

error: problems getting a response from "xxxx" on port 6600 : Connection refused

I've put xxxx because I get the same error whether I use the IP address of the server (192.168.0.171), or the resolved name I've given to the server ("server", as it happens).

I'll be honest and say I haven't tried connecting gmpc on the laptop to mpd running on the laptop but my impression is that this is an issue on the server machine, not on the laptop.

Any other ideas, anyone? Thanks!

---

### Post by benlenarts on 2007-06-25
I have exactly the same problem, running ubuntu feisty with gmpd on a laptop and a dapper server with mpd.

I confirmed that the problem is on the server with nmap:
$ sudo nmap -sT -O henk
Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-06-25 21:06 CEST
Interesting ports on henk (192.168.50.150):
Not shown: 1695 closed ports
PORT   STATE SERVICE
22/tcp open  ssh
80/tcp open  http
MAC Address: xxx
Device type: general purpose
Running: Linux 2.6.X
OS details: Linux 2.6.11 - 2.6.15 (Ubuntu or Debian)
Uptime: 0.535 days (since Mon Jun 25 08:15:37 2007)
Network Distance: 1 hop

OS detection performed. Please report any incorrect results at [http://insecure.org/nmap/submit/](http://insecure.org/nmap/submit/) .
Nmap finished: 1 IP address (1 host up) scanned in 2.225 seconds

mpc and jinzora run fine on the server. I thought ubuntu doesn't install a firewall by default, but I'm not sure.

---

### Post by Gus_T_Reer on 2007-07-15
I've got the same problem. Getting "error code 15: problems getting a response from xxxx on port 6600: Connection refused".
Both mpd and gmpc are running on feisty on different machines. The gmpc terminal error shows: "ERROR:   /build/buildd/libmpd-0.12.0/./src/libmpd.c mpd_check_error():#226:    Following error occured: 15: code: 0 msg: problems getting a response from xxxx on port 6600 : Connection refused".

Originally I tried to use Sonata but was getting dbus errors so I switched to gmpc. Sonata does work on the box with mpd on it.

Ubuntu comes with iptables firewall by default. I use firestarter as a gui frontend.
I've opened port 6600 on the mpd box and firestarter is not showing any more events, so it looks like the problem is not the firewall. The same connection error occurs even if mpd is not running so it looks like some kind of configuration/permissions problem within feisty itself as the connection error is not coming from the mpd software.

If anybody has any idea how to resolve this it looks like there'll be a few people who'll be very grateful.

Thanks

---

### Post by Gus_T_Reer on 2007-07-16
Resolved: from another thread and the mpd forum - comment out the bind_to_address "localhost" line in mpd.conf

---

### Post by Badjaccur on 2007-11-09
> **Gus_T_Reer said:**
> Resolved: from another thread and the mpd forum - comment out the bind_to_address "localhost" line in mpd.conf

Thanks for coming back here and posting how you got the connection working. You made my day. Thanks.:KS

---

