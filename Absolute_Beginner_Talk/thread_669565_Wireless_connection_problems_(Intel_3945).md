---
title: "Wireless connection problems (Intel 3945)"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by falseidol on 2008-01-16
Hey, all,

I'm having trouble getting my wireless connection up and running, My ethernet connection works fine, I'm on a new install of the most recent Kubuntu distribution. I've read up on the massive problems the Intel(R) PRO/Wireless 3945 seems to have and tried out some general fixes as well as the beginnings of getting [linux-specific drivers]("http://www.intellinuxwireless.org/?p=mac80211&n=HOWTO-mac80211") going, but I'm extremely green and I'd appreciate some help.

First off, I'm not sure if I even need the drivers I linked, because my system appears to know they're there, (eth1 Enabled Wireless Device shows up in Network Settings) but KNetworkManager finds no enabled device. Here are the results of iwconfig:

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"NETGEAR"
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:13 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1398   Missed beacon:0


```

Anyways, I'm trying to apply the prerequisite mac80211 system package that once installed should let me install their drivers, but partway through the process it comes up with:

```
$ sudo make patch_kernel

WARNING: $SHELL not set to bash.

If you experience build errors, try 'make SHELL=/bin/bash'.

Kernel Makefile not found at '/lib/modules/2.6.22-14-generic/source/'
If patch or script failed, check pre/ and post/ for current stage.
make: *** [compatible/modified] Error 1
```

Tried setting it to bash (again, green, only a vague idea of what I'm doing there) and reapplying, no effect. There is no source directory there, so on the chance that it was the headpalm problem of looking in the wrong dir, I created that source dir and copied makefile from /lib/modules/2.6.22-14-generic/build to it. No dice. Please let me know if that was a terribly perilous route to take, but I figured as long as I wasn't moving/deleting/editing files in /lib..., I'd be fine.


Ok, any help would be much appreciated - am I on the right track? got a solution to makefile missing? I'm happy to answer any diagnostic questions you have, and thanks in advance for anything you can give me a hand with!

---

### Post by randcoop on 2008-01-16
I'm not sure what's wrong, but I can tell you that my Kubuntu system has comfortably recognized the 3945 through Feisty and Gutsy.  That's using Knetworkmanager.

So you don't need any NDIS wrapper or drivers.  

Getting yours to work may be a problem, though.  Knetworkmanager is often one of those things that either works or it doesn't.  It's not very configurable.  Having said that, the first thing I'd suggest is to see what Knetworkmanager sees.  When you left click on the Knetworkmanaer icon in the task bar, it will tell you what device it's working with.  Does it do that correctly?

If it does, then the next step (IMHO) would be to right click on the Knetworkmanager icon and select manual configuration.  See if you can enable your wireless.

If that doesn't work, I'd suggest using a different wifi program.  For example, you can use Wifi Radar (but that's not the only one).

---

