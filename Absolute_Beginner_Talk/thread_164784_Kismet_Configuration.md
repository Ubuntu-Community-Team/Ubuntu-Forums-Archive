---
title: "Kismet Configuration?"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by Syan48306 on 2006-04-23
I've read up on how to install Kismet, and its configuration....yet I can't seem to get it right...](*,) 
I've read this [http://www.ubuntuforums.org/showthread.php?t=23596](http://www.ubuntuforums.org/showthread.php?t=23596) but it talks about orinoco cards and I don't have one of those; can't seem to change the comands to apply to my computer. I have a Dell I9300 which has a 2200bg wireless card. I'm currently running Dapper (constantly updating lol) with ipw2200 drivers. 
[B]
This is what I have in the config file for Kismet:[/B]
# Version of Kismet config
version=2005.06.R1

# Name of server (Purely for organizational purposes)
servername=Kismet

# User to setid to (should be your normal user)
#suiduser=voyager

# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=none,none,addme

# Comma-separated list of sources to enable.  This is only needed if you defined
# multiple sources and only want to enable some of them.  By default, all defined
# sources are enabled.
# For example:
# enablesources=ipw2200,eth1,eth1


# Do we channelhop?
channelhop=true

# How many channels per second do we hop?  (1-10)
channelvelocity=5

# By setting the dwell time for channel hopping we override the channelvelocity
# setting above and dwell on each channel for the given number of seconds.
#channeldwell=10


[B]
When I try to fire up Kismet...I get this error:[/B]
voyager@voyager:~$ sudo kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (addme): Opening none source interface none...
FATAL: Please configure at least one packet source.  Kismet will not function if no packet sources are defined in kismet.conf or on the command line.  Please read the README for more information about configuring Kismet.
Kismet exiting.


If anyone can point me in the correct direction on how to config this I'd be grateful

---

### Post by rhinomite on 2006-04-27
you need to set the capture source (ie the interface to listen on).

see sections 9 and 12 here: [http://www.kismetwireless.net/documentation.shtml#readme](http://www.kismetwireless.net/documentation.shtml#readme)

The line you need to change is 
source=none,none,addme

I have an atheros card, using madwifi_g. Here's my /etc/kismet/kismet.conf


```

# Kismet config file
# Most of the "static" configs have been moved to here -- the command line
# config was getting way too crowded and cryptic.  We want functionality,
# not continually reading --help!

# Version of Kismet config
version=2005.06.R1

# Name of server (Purely for organizational purposes)
servername=Kismet

# User to setid to (should be your normal user)
[COLOR="Red"]#suiduser=<your_username_here>[/COLOR]

# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
s[COLOR="Red"]ource=madwifi_g,ath0,ath0[/COLOR]

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


```

then just sudo kismet.  Should work.

---

