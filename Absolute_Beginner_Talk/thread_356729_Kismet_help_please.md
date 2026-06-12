---
title: "Kismet help please"
date: 2007-02-08
forum: Absolute Beginner Talk
---

### Post by clocker on 2007-02-08
I recently bought a Dlink atheros card to work with my centrino laptop.  i have downloaded and compiled and installed recent madwifi drivers as well as the latest kismet build.  

i get this error  from kismet

FATAL: Support for capture source type 'madwifing_ag' was not built.  Check the output from 'configure' for more information about why it might not have been compiled in.

------------------------------------------------------------------------------------------------------------------------

here is my config file

# Kismet config file
# Most of the "static" configs have been moved to here -- the command line
# config was getting way too crowded and cryptic.  We want functionality,
# not continually reading --help!

# Version of Kismet config
version=2005.06.R1

# Name of server (Purely for organizational purposes)
servername=Kismet

# User to setid to (should be your normal user)
suiduser=clocker

# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.No packsources were enabled
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=madwifing_ag,ath0,Atheros

# Comma-separated list of sources to enable.  This is only needed if you defined
# multiple sources and only want to enable some of them.  By default, all defined
# sources are enabled.
# For example:
# enablesources=prismsource,ciscosource

# Do we channelhop?
channelhop=true

# How many channels per second do we hop?  (1-10)
channelvelocity=5

# By setting the dwell time for channel hopping we override the channelvelocity
# setting above and dwell on each channel for the given number of seconds.
#channeldwell=10

# Do we split channels between cards on the same spectrum?  This means if 
# multiple 802.11b capture sources are defined, they will be offset to cover
# the most possible spectrum at a given time.  This also controls splitting
# fine-tuned sourcechannels lines which cover multiple interfaces (see below)
channelsplit=true

# Basic channel hopping control:
# These define the channels the cards hop through for various frequency ranges
# supported by Kismet.   More finegrain control is available via the 
# "sourcechannels" configuration option.
# 
# Don't change the IEEE80211<x> identifiers or channel hopping won't work.

# Users outside the US might want to use this list:
# defaultchannels=IEEE80211b:1,7,13,2,8,3,14,9,4,10,5,11,6,12
defaultchannels=IEEE80211b:1,6,11,2,7,3,8,4,9,5,10

# 802.11g uses the same channels as 802.11b...
defaultchannels=IEEE80211g:1,6,11,2,7,3,8,4,9,5,10

# 802.11a channels are non-overlapping so sequential is fine.  You may want to
# adjust the list depending on the channels your card actually supports.
# defaultchannels=IEEE80211a:36,40,44,48,52,56,60,64,100,104,108,112,116,120,124,128,132,136,140,149,153,157,161,184,188,192,196,200,204,208,212,216 
defaultchannels=IEEE80211a:36,40,44,48,52,56,60,64

# Combo cards like Atheros use both 'a' and 'b/g' channels.  Of course, you
# can also explicitly override a given source.  You can use the script 
# extras/listchan.pl to extract all the channels your card supports.
defaultchannels=IEEE80211ab:1,6,11,2,7,3,8,4,9,5,10,36,40,44,48,52,56,60,64

# Fine-tuning channel hopping control:
# The sourcechannels option can be used to set the channel hopping for 
# specific interfaces, and to control what interfaces share a list of 
# channels for split hopping.  This can also be used to easily lock
# one card on a single channel while hopping with other cards.
# Any card without a sourcechannel definition will use the standard hopping
# list.
# sourcechannels=sourcename[,sourcename]:ch1,ch2,ch3,...chN

# ie, for us channels on the source 'prism2source' (same as normal channel
# hopping behavior):
# sourcechannels=prism2source:1,6,11,2,7,3,8,4,9,5,10

# Given two capture sources, "prism2a" and "prism2b", we want prism2a to stay
# on channel 6 and prism2b to hop normally.  By not setting a sourcechannels 
# line for prism2b, it will use the standard hopping.
# sourcechannels=prism2a:6

# To assign the same custom hop channel to multiple sources, or to split the 
# same custom hop channel over two sources (if splitchannels is true), list
# them all on the same sourcechannels line:
# sourcechannels=prism2a,prism2b,prism2c:1,6,11

# Port to serve GUI data
tcpport=2501
# People allowed to connect, comma seperated IP addresses or network/mask
# blocks.  Netmasks can be expressed as dotted quad (/255.255.255.0) or as
# numbers (/24)
allowedhosts=127.0.0.1
# Address to bind to.  Should be an address already configured already on
# this host, reverts to INADDR_ANY if specified incorrectly.
bindaddress=127.0.0.1
# Maximum number of concurrent GUI's
maxclients=5

# Do we have a GPS?
gps=true
# Host:port that GPSD is running on.  This can be localhost OR remote!
gpshost=localhost:2947
# Do we lock the mode?  This overrides coordinates of lock "0", which will
# generate some bad information until you get a GPS lock, but it will 
# fix problems with GPS units with broken NMEA that report lock 0
gpsmodelock=false

# Packet filtering options:
# filter_tracker - Packets filtered from the tracker are not processed or
#                  recorded in any way.
# filter_dump    - Packets filtered at the dump level are tracked, displayed,
#                  and written to the csv/xml/network/etc files, but not 
#                  recorded in the packet dump
# filter_export  - Controls what packets influence the exported CSV, network,
#                  xml, gps, etc files.
# All filtering options take arguments containing the type of address and
# addresses to be filtered.  Valid address types are 'ANY', 'BSSID',
# 'SOURCE', and 'DEST'.  Filtering can be inverted by the use of '!' before
# the address.  For example,
# filter_tracker=ANY(!00:00:DE:AD:BE:EF)
# has the same effect as the previous mac_filter config file option.
# filter_tracker=...
# filter_dump=...
# filter_export=...

# Alerts to be reported and the throttling rates.
# alert=name,throttle/unit,burst/unit
# The throttle/unit describes the number of alerts of this type that are
# sent per time unit.  Valid time units are second, minute, hour, and day.
# Burst rates control the number of packets sent at a time
# For example:
# alert=FOO,10/min,5/sec
# Would allow 5 alerts per second, and 10 alerts total per minute.
# A throttle rate of 0 disables throttling of the alert.
# See the README for a list of alert types.
alert=NETSTUMBLER,10/min,1/sec
alert=WELLENREITER,10/min,1/sec
alert=LUCENTTEST,10/min,1/sec
alert=DEAUTHFLOOD,10/min,2/sec
alert=BCASTDISCON,10/min,2/sec
alert=CHANCHANGE,5/min,1/sec
alert=AIRJACKSSID,5/min,1/sec
alert=PROBENOJOIN,10/min,1/sec
alert=DISASSOCTRAFFIC,10/min,1/sec
alert=NULLPROBERESP,10/min,1/sec
alert=BSSTIMESTAMP,10/min,1/sec
alert=MSFBCOMSSID,10/min,1/sec
alert=LONGSSID,10/min,1/sec
alert=MSFDLINKRATE,10/min,1/sec
alert=MSFNETGEARBEACON,10/min,1/sec
alert=DISCONCODEINVALID,10/min,1/sec
alert=DEAUTHCODEINVALID,10/min,1/sec

# Known WEP keys to decrypt, bssid,hexkey.  This is only for networks where
# the keys are already known, and it may impact throughput on slower hardware.
# Multiple wepkey lines may be used for multiple BSSIDs.
# wepkey=00:DE:AD:C0:DE:00,FEEDFACEDEADBEEF01020304050607080900

# Is transmission of the keys to the client allowed?  This may be a security
# risk for some.  If you disable this, you will not be able to query keys from
# a client.
allowkeytransmit=true

# How often (in seconds) do we write all our data files (0 to disable)
writeinterval=300

# Do we use sound?
# Not to be confused with GUI sound parameter, this controls wether or not the
# server itself will play sound.  Primarily for headless or automated systems.
sound=false
# Path to sound player
soundplay=/usr/bin/play
# Optional parameters to pass to the player
# soundopts=--volume=.3
# New network found
sound_new=${prefix}/share/kismet/wav/new_network.wav
# Wepped new network
# sound_new_wep=${prefix}/com/kismet/wav/new_wep_network.wav
# Network traffic sound
sound_traffic=${prefix}/share/kismet/wav/traffic.wav
# Network junk traffic found
sound_junktraffic=${prefix}/share/kismet/wav/junk_traffic.wav
# GPS lock aquired sound
# sound_gpslock=${prefix}/share/kismet/wav/foo.wav
# GPS lock lost sound
# sound_gpslost=${prefix}/share/kismet/wav/bar.wav
# Alert sound
sound_alert=${prefix}/share/kismet/wav/alert.wav

# Does the server have speech? (Again, not to be confused with the GUI's speech)
speech=false
# Server's path to Festival
festival=/usr/bin/festival
# Are we using festival lite?  If so, set the above "festival" path to also
# point to the "flite" binary
flite=false
# How do we speak?  Valid options:
# speech    Normal speech
# nato      NATO spellings (alpha, bravo, charlie)
# spell     Spell the letters out (aye, bee, sea)
speech_type=nato
# speech_encrypted and speech_unencrypted - Speech templates
# Similar to the logtemplate option, this lets you customize the speech output.
# speech_encrypted is used for an encrypted network spoken string
# speech_unencrypted is used for an unencrypted network spoken string
#
# %b is replaced by the BSSID (MAC) of the network
# %s is replaced by the SSID (name) of the network
# %c is replaced by the CHANNEL of the network
# %r is replaced by the MAX RATE of the network
speech_encrypted=New network detected, s.s.i.d. %s, channel %c, network encrypted.
speech_unencrypted=New network detected, s.s.i.d. %s, channel %c, network open.

# Where do we get our manufacturer fingerprints from?  Assumed to be in the
# default config directory if an absolute path is not given.
ap_manuf=ap_manuf
client_manuf=client_manuf

# Use metric measurements in the output?
metric=false

# Do we write waypoints for gpsdrive to load?  Note:  This is NOT related to
# recent versions of GPSDrive's native support of Kismet.
waypoints=false
# GPSDrive waypoint file.  This WILL be truncated.
waypointdata=%h/.gpsdrive/way_kismet.txt
# Do we want ESSID or BSSID as the waypoint name ?
waypoint_essid=false

# How many alerts do we backlog for new clients?  Only change this if you have
# a -very- low memory system and need those extra bytes, or if you have a high
# memory system and a huge number of alert conditions.
alertbacklog=50

# File types to log, comma seperated
# dump    - raw packet dump
# network - plaintext detected networks
# csv     - plaintext detected networks in CSV format
# xml     - XML formatted network and cisco log
# weak    - weak packets (in airsnort format)
# cisco   - cisco equipment CDP broadcasts
# gps     - gps coordinates
logtypes=dump,network,csv,xml,weak,cisco,gps

# Do we track probe responses and merge probe networks into their owners?
# This isn't always desireable, depending on the type of monitoring you'reError setting monitor mode on ath0
# trying to do.
trackprobenets=true

# Do we log "noise" packets that we can't decipher?  I tend to not, since 
# they don't have anything interesting at all in them.
noiselog=false

# Do we log corrupt packets?  Corrupt packets have enough header information
# to see what they are, but someting is wrong with them that prevents us from
# completely dissecting them.  Logging these is usually not a bad idea.
corruptlog=true

# Do we log beacon packets or do we filter them out of the dumpfile
beaconlog=true

# Do we log PHY layer packets or do we filter them out of the dumpfile
phylog=true

# Do we mangle packets if we can decrypt them or if they're fuzzy-detected
mangledatalog=true

# Do we do "fuzzy" crypt detection?  (byte-based detection instead of 802.11
# frame headers)
# valid option: Comma seperated list of card types to perform fuzzy detection 
#  on, or 'all'
fuzzycrypt=wtapfile,wlanng,wlanng_legacy,wlanng_avs,hostap,wlanng_wext,ipw2200,ipw2915

# Do we do forgiving fuzzy packet decoding?  This lets us handle borked drivers
# which don't indicate they're including FCS, and then do.
fuzzydecode=wtapfile,radiotap_bsd_a,radiotap_bsd_g,radiotap_bsd_bg,radiotap_bsd_b,pcapfile

# Do we use network-classifier fuzzy-crypt detection?  This means we expect 
# packets that are associated with an encrypted network to be encrypted too, 
# and we process them by the same fuzzy compare. 
# This essentially replaces the fuzzycrypt per-source option.
netfuzzycrypt=true

# What type of dump do we generate? 
# valid option: "wiretap" 
dumptype=wiretap
# Do we limit the size of dump logs?  Sometimes ethereal can't handle big ones.
# 0 = No limit
# Anything else = Max number of packets to log to a single file before closing
# and opening a new one.
dumplimit=0

# Do we write data packets to a FIFO for an external data-IDS (such as Snort)?
# See the docs before enabling this.
#fifo=/tmp/kismet_dump

# Default log title
logdefault=Kismet

# logtemplate - Filename logging template.
# This is, at first glance, really nasty and ugly, but you'll hardly ever
# have to touch it so don't complain too much.
#
# %n is replaced by the logging instance name
# %d is replaced by the current date as Mon-DD-YYYY
# %D is replaced by the current date as YYYYMMDD
# %t is replaced by the starting log time
# %i is replaced by the increment log in the case of multiple logs
# %l is replaced by the log type (dump, status, crypt, etc)
# %h is replaced by the home directory
# ie, "netlogs/%n-%d-%i.dump" called with a logging name of "Pok" could expand
# to something like "netlogs/Pok-Dec-20-01-1.dump" for the first instance and 
# "netlogs/Pok-Dec-20-01-2.%l" for the second logfile generated.
# %h/netlots/%n-%d-%i.dump could expand to
# /home/foo/netlogs/Pok-Dec-20-01-2.dump
#
# Other possibilities:  Sorting by directory
# logtemplate=%l/%n-%d-%i
# Would expand to, for example,
# dump/Pok-Dec-20-01-1
# crypt/Pok-Dec-20-01-1
# and so on.  The "dump", "crypt", etc, dirs must exist before kismet is run
# in this case.
logtemplate=%n-%d-%i.%l

# Where do we store the pid file of the server?
piddir=/var/run/

# Where state info, etc, is stored.  You shouldnt ever need to change this.
# This is a directory.
configdir=%h/.kismet/

# cloaked SSID file.  You shouldn't ever need to change this.
ssidmap=ssid_map

# Group map file.  You shouldn't ever need to change this.
groupmap=group_map

# IP range map file.  You shouldn't ever need to change this.
ipmap=ip_map

---------------------------------------------------------------------------------------------------------

ok i believe i have installed everything correctly my internet works fine with the d link card but i cant get kismet to work properly.

its been a pain

---

### Post by tgalati4 on 2007-03-29
I got kismet to work with an Atheros 5212 chip pcmcia card (netgear wg511U, g and a band dual antenna).

I used the following source line:

source=madwifi_ag,ath0,atheros

---

### Post by colinireland on 2007-04-09
Iv had the exact same problem.
if you have found a solution to this since you posted about the error I'd be grateful if you'd let me know.

---

### Post by athleticbum32 on 2007-04-18
I am running feisty with a AR5006EGS and i have the same problem. When i look at dmesg i see that i correctly installed the latest madwifi-ng driver and still nothing.

root@UpInFlames:/home/bamako# dmesg | grep ath_pci
[   19.864000] ath_pci: 0.9.4.5 (svn r2279)

So i am not sure why kismet is saying i havent compiled it. And also if my wireless wasnt working i couldnt be typing this right now. 

Any advice woould be greatly appriceated.

---

### Post by ttakun on 2007-04-18
First of all, I must say I a complete newby in linux, wireless, ...
I have been two hours tonight trying to get kismet running on my laptop with ipw2200. And in the end I got it working.
Why don't you try to get the latest version (2007.01.R1b) of Kismet from the web, configure, make, ... to see what happens?

#sudo su
#sudo aptitude install build-essential
#wget [http://www.kismetwireless.net/code/kismet-01-R1b.tar.gz](http://www.kismetwireless.net/code/kismet-01-R1b.tar.gz)
#tar xf kismet-2007-01-R1b.tar.gz
#cd kismet-2007-01-R1b
#sudo apt-get install libncurses5-dev
#./configure
#make dep
#make
#make install

And later in your kismet.cong in /usr/local/etc/ change the line that says the version:
version=2007.01.R1
Maybe this doesn't affect at all, does it???

---

### Post by athleticbum32 on 2007-04-20
Yes i built the the program the same way with the latest version. And before i put my atheros card in i had a intel 3945 pro which worked fine with no packet injection. So the program works. Now as for the atheros card. ahhhh! The internet works fine, i can even put it into monitor mode with wlanconfig (madwifi tool). The problem lies with the kismet config. For some reason it does not reconize the madwifi driver. Ive tried the lastest madwifi and the lastest madwifi-ng drivers, still nothing. Ive tried numerous sources, but it should be :

source=madwifi_g,wifi0,atheros
source=(source/driver), (dev{wifi0 is the mother dev}), (name in atheros)

Im still trying to solve this. It all worked in backtrack 2 and Ubuntu is 10x better so it has to work. I'm probably just missing something stupid.

---

### Post by tturrisi on 2007-04-21
these are my kismet sources (all working fine):

source=madwifi_ag,wifi0,madwifi
#source=rt8180,wlan1,realtek
#source=acx100,wlan0,acx
#source=orinoco,eth2,hermes1

# OTHER SOURCES
#source=prism54g,eth1,PrismGT
#source=hostap,wlan0,Prism2
#source=wlanng,wlan0,Prism2
#source=ipw2100,eth1,Centrino_b
#source=ipw2200,eth1,Centrino_g
#source=rt2500,ra0,Ralink_g
#source=rt2500,rausb0,Ralink_g
#source=kismet_drone,192.168.2.252:3501,kismet_drone

---

### Post by athleticbum32 on 2007-04-22
I GOT IT! The problem was in the kismet instillation, not the driver like i thought.

Solution: 
install libpcap 0.8 
./configure
make dep
make
make install

I knew it was something stupid. :)

---

### Post by ttakun on 2007-04-23
That's good news, isn't it ¡¡¡
But if you want to try the latest version of libpcap, you can download it from its web. I think last version is 0.9.5 (a little bit newer than the one on the repositories):
[http://www.tcpdump.org/release/libpcap-0.9.5.tar.gz]("http://www.tcpdump.org/release/libpcap-0.9.5.tar.gz")

---

### Post by nex9 on 2007-04-26
I'm having the same problem (atheros based card, net connection works, nada in kismet)... I've downloaded the latest libpcap per your message. I run:

./configure

and I get:

checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables


What am I doing wrong?

Thanks.

---

### Post by zenkaon on 2007-04-26
Hi nex9,

That's a problem with the configure script. 1st of all have you got gcc/g++ installed properly.
sudo apt-get install gcc g++

Next make sure that you have write permissions for the directory. If gcc cant create files it may be because you don't have the right permissions.

My advice would be to unzip the tarball in your home directory
tar zxvf xxx.tar.gz
./configure
make
sudo make install

Good luck getting it working, Kismet is awesome. I would advice ethereal to anaylse what you capture
sudo apt-get install ethereal

and then you should also get aircrack-ng for getting those WEP / WPA keys
sudo apt-get install sircrack-ng

---

### Post by nex9 on 2007-04-26
Thanks, g++ (then flex and bison) did the trick!

---

### Post by athleticbum32 on 2007-04-27
If you thought aircrack-ng was a good WEP cracker try aircrack-ptw. (not related) Anyways it cracked my 64-bit WEP with only 20,000 ivs in 45 sec. I also got a 128-bit in just over 2 min. Check it out for yourself. Google is the answer. Oh and it only cracks WEPs and you still need airodump to capture.

---

### Post by ttakun on 2007-04-27
Thanks for the advice athleticbum32. I'll give aircrack-ptw a try.
nex9, if you don't want to waste your time with the dependencies of kismet, I'll advice you to install the kismet deb package in the repositories through Synaptics (I think it's kismet version 2006-04-R1). That will install all the things you need (libpcap, flex, ... but the older versions)
And later you can start installing the latest version of kismet, libpcap, drivers, ... At least, that's what I did a week ago, and it worked for me. ;-)

---

### Post by Dr.Death on 2007-06-12
I was facing the same problem under fedora 7, i solve it by install libpcap-devel pakage.

;)

---

