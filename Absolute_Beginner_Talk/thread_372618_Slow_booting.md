---
title: "Slow booting"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by Iarwain ben-adar on 2007-02-28
Hi there people,

For some time now my Kubuntu has been starting _pretty_ slow.

I have a bootchart attached, but i don't know where or what to like at :?
Would someone be so kind to tell me what is causing this o-so-slow boot?


Iarwain

---

### Post by Iarwain ben-adar on 2007-03-01
Bump


Iarwain

---

### Post by energiya on 2007-03-01
I could never understand these charts. I can only see a lot of time being waisted (your PC just waits for something). Did you played with the startup scripts or compiled the kernel (or something in connection with it)?

The only solid peace of advice I can give is:
1) Check the logs ans see if you get any errors in the boot process; you could also look at the timings in the log, maybe you could figure it out from there.
(these are faster-booting tips)
2) Read [this]("http://ubuntuforums.org/showthread.php?t=254263").
3) Compile your kernel.

And forgot: what are your system specs?

---

### Post by Iarwain ben-adar on 2007-03-01
Hi, thanks for the reply!

I got a Dell XPS M1710
(a dual core 2 GHz, 2G ram and a 120GB hd)

This should be able to boot Kubuntu in about 20 seconds i reckon..

Btw, what logs should i check?


Iarwain

---

### Post by energiya on 2007-03-01
You could go for the syslog and messages. Don't know where to read the logs in Kubuntu using X, but I think thy should be in /var/log/ (or at least thats where they are on my computer - I'm not using Ubuntu).

---

### Post by maniacmusician on 2007-03-01
> **Iarwain ben-adar said:**
> Hi, thanks for the reply!

I got a Dell XPS M1710
(a dual core 2 GHz, 2G ram and a 120GB hd)

This should be able to boot Kubuntu in about 20 seconds i reckon..

Btw, what logs should i check?


Iarwain
Yeah, that should be really fast.

Do you remember what changes you made before it got slow? that's weird. 

You could try unsetting the usplash and putting it in verbose mode so it shows you the boot process, and maybe you'll get something out of it then. (I dont remember how to do that, just look it up.)

---

### Post by Iarwain ben-adar on 2007-03-01
This is the relevant part of my syslog

> 
Mar  1 16:07:49 iarwain-laptop kernel: [  104.700000] apm: BIOS not found.
Mar  1 16:07:51 iarwain-laptop anacron[11908]: Anacron 2.3 started on 2007-03-01
Mar  1 16:07:51 iarwain-laptop anacron[11908]: Normal exit (0 jobs run)
Mar  1 16:07:55 iarwain-laptop kdm_greet[12111]: Can't open default user face
Mar  1 16:08:00 iarwain-laptop avahi-daemon[12437]: Found user 'avahi' (UID 106) and group 'avahi' (GID 112).
Mar  1 16:08:00 iarwain-laptop avahi-daemon[12437]: Successfully dropped root privileges.
Mar  1 16:08:00 iarwain-laptop avahi-daemon[12437]: avahi-daemon 0.6.16 starting up.
Mar  1 16:08:00 iarwain-laptop avahi-daemon[12437]: Successfully called chroot().
Mar  1 16:08:00 iarwain-laptop avahi-daemon[12437]: Successfully dropped remaining capabilities.
Mar  1 16:08:00 iarwain-laptop avahi-daemon[12437]: No service found in /etc/avahi/services.
Mar  1 16:08:00 iarwain-laptop avahi-daemon[12437]: New relevant interface eth1.IPv4 for mDNS.
Mar  1 16:08:00 iarwain-laptop avahi-daemon[12437]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.2.101.
Mar  1 16:08:00 iarwain-laptop avahi-daemon[12437]: Network interface enumeration completed.
Mar  1 16:08:00 iarwain-laptop avahi-daemon[12437]: Registering new address record for 192.168.2.101 on eth1.
Mar  1 16:08:00 iarwain-laptop avahi-daemon[12437]: Registering HINFO record with values 'I686'/'LINUX'.
Mar  1 16:08:00 iarwain-laptop rpc.statd[12513]: Version 1.0.10 Starting
Mar  1 16:08:00 iarwain-laptop sm-mta[12497]: My unqualified host name (iarwain-laptop) unknown; sleeping for retry
Mar  1 16:08:01 iarwain-laptop avahi-daemon[12437]: Server startup complete. Host name is iarwain-laptop.local. Local service cookie is 957314482.
Mar  1 16:08:02 iarwain-laptop sm-msp-queue[12636]: My unqualified host name (iarwain-laptop) unknown; sleeping for retry
Mar  1 16:08:07 iarwain-laptop sendmail[8539]: unable to qualify my own domain name (iarwain-laptop) -- using short name
Mar  1 16:09:00 iarwain-laptop sm-mta[12497]: unable to qualify my own domain name (iarwain-laptop) -- using short name
Mar  1 16:09:00 iarwain-laptop sm-mta[16058]: starting daemon (8.13.8): SMTP+queueing@00:10:00
Mar  1 16:09:02 iarwain-laptop sm-msp-queue[12636]: unable to qualify my own domain name (iarwain-laptop) -- using short name
Mar  1 16:09:02 iarwain-laptop anacron[16249]: Anacron 2.3 started on 2007-03-01
Mar  1 16:09:02 iarwain-laptop anacron[16249]: Normal exit (0 jobs run)
Mar  1 16:09:02 iarwain-laptop /usr/sbin/cron[16242]: (CRON) INFO (pidfile fd = 3)
Mar  1 16:09:02 iarwain-laptop /usr/sbin/cron[16253]: (CRON) STARTUP (fork ok)
Mar  1 16:09:02 iarwain-laptop /usr/sbin/cron[16253]: (CRON) INFO (Running @reboot jobs)
Mar  1 16:09:03 iarwain-laptop kernel: [  178.120000] /dev/vmmon[16331]: Module vmmon: registered with major=10 minor=165
Mar  1 16:09:03 iarwain-laptop kernel: [  178.120000] /dev/vmmon[16331]: Module vmmon: initialized
Mar  1 16:09:03 iarwain-laptop kernel: [  178.656000] /dev/vmnet: open called by PID 16392 (vmnet-bridge)
Mar  1 16:09:03 iarwain-laptop kernel: [  178.656000] /dev/vmnet: hub 0 does not exist, allocating memory.
Mar  1 16:09:03 iarwain-laptop kernel: [  178.656000] /dev/vmnet: port on hub 0 successfully opened
Mar  1 16:09:03 iarwain-laptop kernel: [  178.656000] bridge-eth0: enabling the bridge
Mar  1 16:09:03 iarwain-laptop kernel: [  178.656000] bridge-eth0: up
Mar  1 16:09:03 iarwain-laptop kernel: [  178.656000] bridge-eth0: already up
Mar  1 16:09:03 iarwain-laptop kernel: [  178.656000] bridge-eth0: attached
Mar  1 16:09:03 iarwain-laptop VMware[init]: Host-only networking disabled because 192.168.2.1
Mar  1 16:09:03 iarwain-laptop VMware[init]: appears to be a real, physical, existing address.
Mar  1 16:09:03 iarwain-laptop VMware[init]: Please run "/usr/bin/vmware-config.pl" to
Mar  1 16:09:03 iarwain-laptop VMware[init]: modify your host-only network configuration.
Mar  1 16:09:03 iarwain-laptop VMware[init]: Host-only networking disabled because 192.168.2.1
Mar  1 16:09:03 iarwain-laptop VMware[init]: appears to be a real, physical, existing address.
Mar  1 16:09:03 iarwain-laptop VMware[init]: Please run "/usr/bin/vmware-config.pl" to
Mar  1 16:09:03 iarwain-laptop VMware[init]: modify your host-only network configuration.
Mar  1 16:09:03 iarwain-laptop kernel: [  178.668000] /dev/vmnet: open called by PID 16406 (vmnet-natd)
Mar  1 16:09:03 iarwain-laptop kernel: [  178.668000] /dev/vmnet: hub 8 does not exist, allocating memory.
Mar  1 16:09:03 iarwain-laptop kernel: [  178.668000] /dev/vmnet: port on hub 8 successfully opened
Mar  1 16:09:12 iarwain-laptop kdm_greet[12111]: Internal error: memory corruption detected
Mar  1 16:09:38 iarwain-laptop kernel: [  213.740000] Bluetooth: Core ver 2.11
Mar  1 16:09:38 iarwain-laptop kernel: [  213.740000] NET: Registered protocol family 31
Mar  1 16:09:38 iarwain-laptop kernel: [  213.740000] Bluetooth: HCI device and connection manager initialized
Mar  1 16:09:38 iarwain-laptop kernel: [  213.740000] Bluetooth: HCI socket layer initialized
Mar  1 16:09:47 iarwain-laptop gconfd (iarwain-16762): starting (version 2.16.1), pid 16762 user 'iarwain'
Mar  1 16:09:47 iarwain-laptop gconfd (iarwain-16762): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Mar  1 16:09:47 iarwain-laptop gconfd (iarwain-16762): Resolved address "xml:readwrite:/home/iarwain/.gconf" to a writable configuration source at position 1
Mar  1 16:09:47 iarwain-laptop gconfd (iarwain-16762): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Mar  1 16:09:47 iarwain-laptop gconfd (iarwain-16762): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Mar  1 16:09:47 iarwain-laptop gconfd (iarwain-16762): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4


I don't really know what could be the problem..

Except for "sendmail", it takes about 50 seconds..

EDIT:
It hangs quite some time on "Reading files needed to boot" and a hell of a time (around 40sec) on "Starting portmap daemon"

How can i check why portmap is so slow?


Iarwain

---

### Post by Iarwain ben-adar on 2007-03-02
Bump


Iarwain

---

### Post by Iarwain ben-adar on 2007-03-02
No one?


Iarwain

---

### Post by energiya on 2007-03-02
> **Iarwain ben-adar said:**
> This is the relevant part of my syslog



I don't really know what could be the problem..

Except for "sendmail", it takes about 50 seconds..

EDIT:
It hangs quite some time on "Reading files needed to boot" and a hell of a time (around 40sec) on "Starting portmap daemon"

How can i check why portmap is so slow?


Iarwain

As long as some services are not vital (sendmail maybe) you could always block them from starting in the first place. Try installing bum (?) and see what  scripts you don't need.

The best way to manage this problem would be working directly with the init scripts. Unfortunately, as I already mentioned, I'm using another distro that has a different way of dealing with the init process, so I can't help you on this.

---

### Post by dstew on 2007-03-02
It looks like you are having domain-name resolution problems. The processes are waiting to resolve names, and seem to time out. That is what is happening in the gaps.

---

### Post by Iarwain ben-adar on 2007-03-02
Hi,

Thanks! i already deleted sendmail, but it is still as slow :'(


dstew:
and how would i go to change that? It could very well be that i have those problems..


Iarwain

---

### Post by dstew on 2007-03-02
I think sendmail is the owner of the processes that are holding up your boot (sm-mta, for example, as seen in your syslog file). You said you deleted sendmail. I am not familiar with sendmail. How did you delete it? Did you use Synaptic and remove it completely? I saw another forum where a user had similar problems with sendmail, and he was told to put sendmail_enable="NONE" in his /etc/rc.conf file to make sure sendmail didn't come back ([http://lists.freebsd.org/pipermail/freebsd-questions/2006-February/111662.html)](http://lists.freebsd.org/pipermail/freebsd-questions/2006-February/111662.html)).

There is also a significant holdup with the kdm-greet process, as it detected a memory error.

---

### Post by Iarwain ben-adar on 2007-03-02
I removed it with
```
sudo apt-get remove sendmail
```

This should have deleted it, right?

And how can i fix the kdm-greet?


Iarwain

---

### Post by Iarwain ben-adar on 2007-03-03
Bumping to the top!


Iarwain

---

### Post by energiya on 2007-03-03
BTW, are you using Feisty? Because if so, it might be a bug, and you should report it...

---

### Post by Iarwain ben-adar on 2007-03-03
I am,
but the problem was already there when it was still Edgy (but not that slow)

I never really bothered, but now it starts to get on my nerves :D


Iarwain

---

