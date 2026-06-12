---
title: "Wireless Wiki Woes..."
date: 2008-10-07
forum: Arch and derivatives
---

### Post by whitefort on 2008-10-07
Apologies in advance for the amount of info I'm dumping here - it's in the hope that somebody will immediately spot a stupid mistake and help me fix it.

I admit I'm clueless about wireless-I've been trying to follow the wiki and I've been reading posts, but after more than a week I've made no progress at all.  I know my card (Netgear) works with linux, because ubuntu and most live CDs I've tried have found and configured it automatically.


First, here's what happens when I try to follow the initial instructions in the Wireless Wiki (the bit to test if you can get it up and running, before you start messing with the rc.conf etc.)

Here's what happens:

=================================

```
[root@Humpty john]# hwdetect --show-net
NET    : e100 eepro100 mii ppp_generic slhc mac80211 ath5k ath_hal ath_pci wlan cfg80211 

[root@Humpty john]# lsmod | grep ath
ath_rate_sample        15872  1 
ath_pci               241848  0 
wlan                  222192  4 wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               250976  3 ath_rate_sample,ath_pci

[root@Humpty john]# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11b  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:0 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

[root@Humpty john]# ifconfig ath0 up
[root@Humpty john]# iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:18:4D:B6:9A:A6
                    ESSID:"ASHTREEHOUSE"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=49/70  Signal level=-46 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

[root@Humpty john]# iwconfig ath0 essid ASHTREEHOUSE key CD384854EA

[root@Humpty john]# ifconfig ath0 192.168.0.11
[root@Humpty john]# route add default gw 192.168.0.1
SIOCADDRT: File exists
```

This looks OK, up to the point where it says 'File exists' (Presumably because the gateway is already set up in rc.conf as part of my wired setup?  But would that block the connection?

Also, by now my little gnome panel applets are all showing signal strength etc and telling me I'm connected to ASHTREEHOUSE.  But I can't ping the router, www, or any other PC on the network.

Finally, just for completeness, here's my current rc.conf.  If anyone can point me in the right direction, I'd be really grateful.

I'm enjoying arch so much that I'm tempted to just forget about wireless and buy a long cable... but that feels a bit defeatist and un-Arch, somehow...

```
#
# /etc/rc.conf - Main Configuration for Arch Linux
#

# -----------------------------------------------------------------------
# LOCALIZATION
# -----------------------------------------------------------------------
#
# LOCALE: available languages can be listed with the 'locale -a' command
# HARDWARECLOCK: set to "UTC" or "localtime"
# USEDIRECTISA: use direct I/O requests instead of /dev/rtc for hwclock
# TIMEZONE: timezones are found in /usr/share/zoneinfo
# KEYMAP: keymaps are found in /usr/share/kbd/keymaps
# CONSOLEFONT: found in /usr/share/kbd/consolefonts (only needed for non-US)
# CONSOLEMAP: found in /usr/share/kbd/consoletrans
# USECOLOR: use ANSI color sequences in startup messages
#
LOCALE="en_GB.utf8"
HARDWARECLOCK="localtime"
USEDIRECTISA="no"
TIMEZONE="GB"
KEYMAP="uk"
CONSOLEFONT=
CONSOLEMAP=
USECOLOR="yes"

# -----------------------------------------------------------------------
# HARDWARE
# -----------------------------------------------------------------------
#
# MOD_AUTOLOAD: Allow autoloading of modules at boot and when needed
# MOD_BLACKLIST: Prevent udev from loading these modules
# MODULES: Modules to load at boot-up. Prefix with a ! to blacklist.
#
# NOTE: Use of 'MOD_BLACKLIST' is deprecated. Please use ! in the MODULES array.
#
MOD_AUTOLOAD="yes"
#MOD_BLACKLIST=() #deprecated
MODULES=(e100 eepro100 mii slhc !ath5k ath_hal ath_pci wlan ac97_bus snd-mixer-oss snd-pcm-oss snd-page-alloc snd-pcm snd-timer snd snd-ac97-codec snd-intel8x0 soundcore)

# Scan for LVM volume groups at startup, required if you use LVM
USELVM="no"

# -----------------------------------------------------------------------
# NETWORKING
# -----------------------------------------------------------------------
#
# HOSTNAME: Hostname of machine. Should also be put in /etc/hosts
#
HOSTNAME="Humpty"

# Use 'ifconfig -a' or 'ls /sys/class/net/' to see all available interfaces.
#
# Interfaces to start at boot-up (in this order)
# Declare each interface then list in INTERFACES
#   - prefix an entry in INTERFACES with a ! to disable it
#   - no hyphens in your interface names - Bash doesn't like it
# 
# DHCP:     Set your interface to "dhcp" (eth0="dhcp")
# Wireless: See network profiles below
#
eth0="eth0 192.168.0.11 netmask 255.255.255.0 broadcast 192.168.0.255"
INTERFACES=(eth0 ath0 wlan0)

# Routes to start at boot-up (in this order)
# Declare each route then list in ROUTES
#   - prefix an entry in ROUTES with a ! to disable it
#
gateway="default gw 192.168.0.1"
ROUTES=(gateway)
 
# Enable these network profiles at boot-up.  These are only useful
# if you happen to need multiple network configurations (ie, laptop users)
#   - set to 'menu' to present a menu during boot-up (dialog package required)
#   - prefix an entry with a ! to disable it
#
# Network profiles are found in /etc/network.d
#
# This now requires the netcfg package
#
#NETWORKS=(main)

# -----------------------------------------------------------------------
# DAEMONS
# -----------------------------------------------------------------------
#
# Daemons to start at boot-up (in this order)
#   - prefix a daemon with a ! to disable it
#   - prefix a daemon with a @ to start it up in the background
#
DAEMONS=(syslog-ng network netfs crond @alsa @hal @fam @fuse @sshd)
```

---

### Post by Rumor on 2008-10-08
Whitefort, I would ***highly*** recommend you post this in the Arch networking forums. You'll get more expertise there, I think.

I am no wireless guru. The only time I've used wireless in Arch I did so using [wicd]("http://wiki.archlinux.org/index.php/Wicd").

Looking at what you've posted, i'd think you need to set the lines in your rc.conf file for ath0 and wlan0
ath0="dhcp"
wlan0="dhcp"

But, like I said, I am no wireless guru :confused:

---

### Post by whitefort on 2008-10-08
Thanks for the reply, Rumor.

I probably WILL post it in the Arch forum.  The dchp thing won't work for me, because the computer has to fit into an existing network with a static IP assigned to it.

I've been lurking in the Arch forum, and I don't think it's as newbie-unfriendly as I thought at first.

(In bygone years, I've found some Linux groups to be especially nasty to newbies - This is largely why I didn't switch to Linux a long time ago.  The general friendliness of people in the Ubuntu forums was what got me through my initial Linux/Hardware problems.  It was just so nice to get questions answered without being told 'you're probably too stupid for linux'!!!)

Yeah, I'll see if I can get any help over there - I just wanted to double check first that there was nothing *obviously* stupid with what I've been trying.

---

### Post by MisfitI38 on 2008-10-08
One observation: It looks like udev is only loading ath_pci and not ath5k, but I have had instances in which ath5k interfered with madwifi, and required blacklisting.

If ath_pci is the right driver, try blacklisting ath5k or vice-versa.
[http://wiki.archlinux.org/index.php/Wireless#madwifi](http://wiki.archlinux.org/index.php/Wireless#madwifi)

---

### Post by crimesaucer on 2008-10-08
> **whitefort said:**
> ".....Also, by now my little gnome panel applets are all showing signal strength etc and telling me I'm connected to ASHTREEHOUSE.  But I can't ping the router, www, or any other PC on the network...."


Are you using NetworkManager? [http://wiki.archlinux.org/index.php/NetworkManager](http://wiki.archlinux.org/index.php/NetworkManager)


..... if you are, then it looks like your daemons line of you rc.conf is wrong. You said "gnome panel applets" so I assumed you went with the gnome networkmanager.


from the wiki:

> You must also "disable" the default network daemon, and add the hal, dhcdbd and networkmanager daemons in this order:

```
DAEMONS=( ... !network hal dhcdbd networkmanager ... )

```


I'm sure that you've read all of these and chose at least one of them: [http://wiki.archlinux.org/index.php/Wireless#Part_II:_Wireless_Management](http://wiki.archlinux.org/index.php/Wireless#Part_II:_Wireless_Management)

---

### Post by whitefort on 2008-10-10
Crimesaucer,

Miraculously, I'm posting this message with the network cable on my Arch machine UNplugged!

MANY THANKS.

I ***wasn't*** actually using networkmanager - when I referred to the applet, I meant that little one that comes as an option in the gnome panel menu.

But I decided to give networkmanager a shot.

It wasn't entirely painless, and I failed miserably the first few times.  But then I noticed that one of the changes had done something dramatic - for the first time, when I followed the Wireless Wiki instructions, THEY WORKED.

Anyway, now it's all working.  Sorry for such a wordy reply, but I'm excited - this is the one thing I needed to make Arch my main distro.

Thanks again!

---

### Post by crimesaucer on 2008-10-11
> **whitefort said:**
> Crimesaucer,

Miraculously, I'm posting this message with the network cable on my Arch machine UNplugged!

MANY THANKS.

I ***wasn't*** actually using networkmanager - when I referred to the applet, I meant that little one that comes as an option in the gnome panel menu.

But I decided to give networkmanager a shot.

It wasn't entirely painless, and I failed miserably the first few times.  But then I noticed that one of the changes had done something dramatic - for the first time, when I followed the Wireless Wiki instructions, THEY WORKED.

Anyway, now it's all working.  Sorry for such a wordy reply, but I'm excited - this is the one thing I needed to make Arch my main distro.

Thanks again!

I'm gladded it worked out for you, it's a good feeling of accomplishment when you build and configure all of your apps from scratch like you do in Arch. It's also nice to get something working after it feels like there is no way to do it.


The really cool thing about Arch is that after you go through all the effort of getting your computer working correctly..... you've ended up learning all about your hardware, the apps you've installed, and the conf files that are needed to make everything work..... I like that a lot better than just installing a system from a click of a button and not knowing anything about what I installed and how to configure/customize it to my liking.

---

