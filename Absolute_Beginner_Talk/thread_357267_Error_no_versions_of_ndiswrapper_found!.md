---
title: "Error: no versions of ndiswrapper found!"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by username132 on 2007-02-09
After installing ndiswrapper using:
```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install ndiswrapper-utils
```

It had said:
```
The following NEW packages will be installed:
  ndiswrapper-utils
```

and finally said:
```
Setting up ndiswrapper-utils (1.8-0ubuntu2) ...
```
before returning me to the command prompt where I type:
```
ndiswrapper
```

and get:
```
Error: no versions of ndiswrapper found!
```

How can this be?

---

### Post by sunexplodes on 2007-02-09
i believe you also need ndiswrapper-common

---

### Post by username132 on 2007-02-09
```
sudo aptitude install ndiswrapper-common
``` didn't work so I installed this manually via the GUI and still got the same error.

---

### Post by Maestro23 on 2007-02-09
> **username132 said:**
> ```
sudo aptitude install ndiswrapper-common
``` didn't work so I installed this manually via the GUI and still got the same error.

Just found it on my system via synaptic.  You need to enable some more repositories in [COLOR="Red"]/etc/apt/sources.list[/COLOR].  Check this link here on how: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by username132 on 2007-02-10
Will that work if my ubuntu has no internet access? I notice the guide includes references to online things.

---

### Post by username132 on 2007-02-25
Does the fact that I'm using a LiveDVD version have any effect on these things or can it be expected to behave in precisely the same way as if it were properly installed?

---

### Post by dowgoldratio7 on 2007-05-07
> **Maestro23 said:**
> Just found it on my system via synaptic.  You need to enable some more repositories in [COLOR="Red"]/etc/apt/sources.list[/COLOR].  Check this link here on how: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

About 6 days into linux now.

I'm running Feisty upgraded from Edgy upgraded from Dapper. I upgraded to Feisty yesterday. When I looked on the psychocats page, I couldn't find any reference to which sources might need to be added to get ndiswrapper-common installed. There was general information on how to add sources, but nothing specific to ndiswrapper that I could see.

I also already apparently have ndiswrapper-common, so I don't know if not having ndiswrapper-common is the issue:

sudo apt-cache search ndiswrapper
linux-image-2.6.20-15-386 - Linux kernel image for version 2.6.20 on i386
linux-image-2.6.20-15-generic - Linux kernel image for version 2.6.20 on x86/x86_64
linux-image-2.6.20-15-server - Linux kernel image for version 2.6.20 on x86/x86_64
linux-image-2.6.20-15-server-bigiron - Linux kernel image for version 2.6.20 on BigIron Server Equipment
ndiswrapper-common - Common scripts required to use the utilities for ndiswrapper
ndiswrapper-utils-1.9 - Userspace utilities for the ndiswrapper linux kernel module
linux-image-2.6.17-11-386 - Linux kernel image for version 2.6.17 on i386
linux-image-2.6.15-23-386 - Linux kernel image for version 2.6.15 on 386.
linux-image-2.6.15-28-386 - Linux kernel image for version 2.6.15 on 386.

but still...

sudo ndiswrapper
Error: no versions of ndiswrapper found!

Another page, [http://www.debianhelp.org/node/6752](http://www.debianhelp.org/node/6752), in response to 

      I did install ndiswrapper-common, but when I run sudo ndiswrapper, i get:
      "Error: no versions of ndiswrapper found!"

expert responds (may be for another distribution, but I don't know):

"You did not install the ndiswrapper programs and the ndiswrapper kernel
module. Install ndiswrapper-utils and run

module-assistant auto-install ndiswrapper-source

After that, follow the configuration guidelines in the ndiswrapper Wiki
on ndiswrapper.sf.net. For the future, use apt-cache show $packagename
and apt-cache search $keyword to get more information on the packages
you are about to install.

regards
Andreas Janssen"

When I try

sudo apt-cache show ndiswrapper
W: Unable to locate package ndiswrapper
E: No packages found

And when I try the other suggestion,

sudo module-assistant auto-install ndiswrapper-source
sudo: module-assistant: command not found

which module-assistant produces no output

On the same page, another expert answers...

"
> I did install ndiswrapper-common, but when I run sudo ndiswrapper, i
> get:
> "Error: no versions of ndiswrapper found!"

Another lesson learned! You didn't install everything required.

VT1 root-3-TESTING:~# apt-cache search ndiswrapper
ndiswrapper-common - Common scripts required to use the utilities for ndiswrapper
ndiswrapper-source - Source for the ndiswrapper linux kernel module
ndiswrapper-utils - Userspace utilities for ndiswrapper
ndiswrapper-utils-1.1 - Userspace utilities for ndiswrapper
ndiswrapper-utils-1.9 - Userspace utilities for the ndiswrapper linux kernel module
"

So when I compare the expert's ndiswrapper cache search (which I'm guessing is a working example) to mine, I only see ndiswrapper-source as the difference, I didn't know if having ndiswrapper-source mattered, so I tried

sudo apt-get install ndiswrapper-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ndiswrapper-source is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ndiswrapper-source has no installation candidate

Also here,

[http://www.linuxforums.org/forum/ubuntu-help/81068-ndiswrapper-installed-but-not-found.html](http://www.linuxforums.org/forum/ubuntu-help/81068-ndiswrapper-installed-but-not-found.html)

In response to:

"sudo ndiswrapper -i ~/drivers/BT4501G.inf

and got the reply: Error: no versions of ndiswrapper found."

expert replies:

"ndiswrapper is two things:
1. an executable: try "sudu which ndiswrapper" to see
whether you have it.
2. a loadable kernel module in /lib/modules/`uname -r`/misc
you need both.

the sticky in "wireless internet" is very helpful
suggested further reading"

When I do:

sudo which ndiswrapper 
/usr/sbin/ndiswrapper

I seem to have the executable... And when I do:

uname -r
2.6.20-15-386
ls /lib/modules/2.6.20-15-386 | grep misc

produces no output, so apparently that "kernel module" isn't loaded. Any help out there?

---

### Post by dowgoldratio7 on 2007-05-09
7 days into linux...

When you invoke

which ndiswrapper

and it says:

/usr/sbin/ndiswrapper

Looks like that doesn't mean it's installed. /usr/sbin/ndiswrapper is a script:

 cat ndiswrapper 
#!/bin/sh

set -e

latest_ndiswrapper () {
        for file in /usr/sbin/ndiswrapper-[\.0-9][\.0-9]*; do
                echo $file
        done | sort -n -t - -k 2 | tail -1
}

unset LATEST
LATEST=`latest_ndiswrapper`

if [ -x "$LATEST" ]; then
        $LATEST "$@"
else
        echo "Error: no versions of ndiswrapper found!" 1>&2
        exit 1
fi


So it appears you still need to install ndiswrapper... Will post again if this turns out to help me get ndiswrapper installed...

---

### Post by dowgoldratio7 on 2007-05-10
8 days into linux and I'm wireless. Woohoo!

All the above seems to be true. You don't need ndiswrapper-source. Here are the specific steps/commands collected from a number of other links.

To install ndiswrapper, go to

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)

on the download page and download the most recent stable version of ndiswrapper. I downloaded v1.43 and the commands below worked... A prereq for ndiswrapper is that you have a link to kernel. The way I checked was:

ls -l /lib/modules/`uname -r`/build/kernel

lrwxrwxrwx 1 root root 33 2007-05-06 21:28 /lib/modules/2.6.20-15-386/build/kernel -> ../linux-headers-2.6.20-15/kernel

The first l in the output indicates kernel is a link. Before installing, it suggests you "make uninstall" a few times. It'll let you know when you can stop uninstalling...

make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /sbin/loadndisdriver
/bin/rm: cannot remove `/sbin/loadndisdriver': Permission denied
make: *** [uninstall] Error 1
sudo make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /sbin/loadndisdriver
removing /usr/sbin/ndiswrapper
removing /lib/modules/2.6.20-15-386/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
sudo make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
sudo make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
sudo make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.

sudo make
sudo su
make install
exit

dir
TRANS.TBL  WG511v2.cat  WG511v2.INF  WG511v2.sys
man ndiswrapper

If you have the WG511 v2 made in china netgear card, I hope this works. There are links to the windows drivers files out there, but I forget where I found them you'll need to be in the directory with them for the ndiswrapper call.

sudo ndiswrapper -i WG511v2.INF 
Password:
installing wg511v2 ...
lspci
.
.
.
06:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

ndiswrapper -l
wg511v2 : driver installed
        device (11AB:1FAA) present

Then I followed these instructions...
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29)

sudo modprobe ndiswrapper
sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
gksudo gedit /etc/modules
     (I added ndiswrapper to the last line of this file)

cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
ndiswrapper

sudo iwconfig wlan0 essid "AP" key ababababababababab mode Managed

ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0F:B5:84:B1:70  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:398 (398.0 b)
          Interrupt:11 Memory:2c010000-2c020000 

And last night it didn't work, but the light was flashing, so I knew I'd made some progress, but I figured something wasn't configured right. Today I rebooted and plugged in the card and it talked to my router fine.

---

### Post by dowgoldratio7 on 2007-05-14
> **dowgoldratio7 said:**
> 8 days into linux and I'm wireless. Woohoo!
.
.
.
Today I rebooted and plugged in the card and it talked to my router fine.

Spoke too soon. Doesn't seem to be talking to my router anymore.

---

### Post by dowgoldratio7 on 2007-05-20
> **dowgoldratio7 said:**
> Spoke too soon. Doesn't seem to be talking to my router anymore.

I'd read on a few different places if you have the "Made In China" version of the 54 Mbps Wireless PC Card WG511 v2, you should use ndiswrapper on the "Windows 2000" version of the driver on the netgear cd (the "Windows XP" version apparently works for that card when it's NOT Made In China). I couldn't find my netgear cd, so I downloaded a driver off the internet. That was apparently the Windows XP version. I since found my netgear cd.

So to remove that old driver, I ran:

sudo ndiswrapper -e WG511v2

and then to install the new driver, I got into the "Windows 2000" directory of that cd and ran:

sudo ndiswrapper -i WG511v2.INF

and repeated the steps after that above.

Now when I boot up, the wireless card is consistently detected and connected to my wireless router.

Although most of the time my card wasn't connected (the NetworkTools wlan0 "interface information" was unavailable), sometimes it did connect, and I could surf the net with no problems. Also, the icon that says you have an internet connection never said I was connected before (even when I had an active internet connection) Now that seems to be working, too.

---

