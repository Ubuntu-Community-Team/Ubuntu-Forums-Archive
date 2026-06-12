---
title: "[SOLVED] rTorrent Commands/Automation"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by jw5801 on 2007-07-31
Hey guys,

Been using rTorrent for a few weeks now and I really like it! I've got a .rtorrent.rc file set up to automatically load all my torrents and start seeding them when I start rTorrent, but I have a few incomplete torrents that I seed. So my question is, is there a way to tell rTorrent to set the priority of all undownloaded files in a torrent to "off"? Because it's really irritating having to scroll through a few hundred files to find the ones I want to change.

Also while I'm here, is there a way to collapse a directory in the file-list view, I read the man page but couldn't see anything there?

Cheers!

---

### Post by userundefine on 2007-07-31
1) No, I do not think there is.  You could probably code that in with little effort if you can code.

2) Yes!  But if you're using the repo version I don't think so.  At least when I tried the repo version, it was two versions older and didn't include the feature.  The latest version, you just hit / on directories and they collapse.  So much easier.

---

### Post by jw5801 on 2007-07-31
Ok cheers! I didn't think there would be for the first problem, I'll take a look at the code but I think it's a bit out of my depth. And I am using the repo version so that explains a lot, 'cause I remember reading the '/' option somewhere but couldn't find it in the man pages and it didn't work. I'll go get the most recent then!

---

### Post by jw5801 on 2007-08-01
Ok! Well apparently using a session directory stores the state that the torrents were in before rTorrent is closed, so that answered my first question above. I had tried that already but it didn't seem to work correctly the first time around. Perhaps I need to tell it to save the states to this session directory before I close? So far all I have is a command to open it at startup in .rtorrent.rc.

---

### Post by userundefine on 2007-08-01
This is my rtorrent.rc below.  I use scheduling, ratio control, encryption, automatic detection of new torrents in a directory, and auto-loading of torrents in a directory when I start it up (session).  I was answering "no" to your first question in the sense that you cannot auto-start torrents with certain files turned off, UNLESS you already did it manually and you're reloading a session.  If I turn off 2 out of 4 files in a torrent, close rtorrent, when I reopen it (because I use sessions) those 2 will still be 'off'.  I may have misread what you intended before, hope this clears it up.

```
# This is an example resource file for rTorrent. Copy to
# ~/.rtorrent.rc and enable/modify the options as needed. Remember to
# uncomment the options you wish to enable.

# Maximum and minimum number of peers to connect to per torrent.
min_peers = 40
max_peers = 1000

# Same as above but for seeding completed torrents (-1 = same as downloading)
min_peers_seed = 10
max_peers_seed = 50

# Maximum number of simultanious uploads per torrent.
max_uploads = 8

# Global upload and download rate in KiB. "0" for unlimited.
download_rate = 0
upload_rate = 20

# Default directory to save the downloaded torrents.
directory = ~/errata/.torrents/

# Default session directory. Make sure you don't run multiple instance
# of rtorrent using the same session directory. Perhaps using a
# relative path?
session = ~/downloads/.rtorrent-session/

# Watch a directory for new torrents, and stop those that have been
# deleted.
schedule = watch_directory,10,10,load_start=~/downloads/torrentwatch/*.torrent
schedule = tied_directory,10,10,start_tied=
schedule = untied_directory,10,10,close_untied=

# Stop torrents when reaching upload ratio in percent,
# when also reaching total upload in bytes, or when
# reaching final upload ratio in percent.
# example: stop at ratio 2.0 with at least 200 MB uploaded, or else ratio 20.0
schedule = ratio,60,60,stop_on_ratio=100,0

# The ip address reported to the tracker.
#ip = 127.0.0.1
#ip = rakshasa.no

# The ip address the listening socket and outgoing connections is
# bound to.
#bind = 127.0.0.1
#bind = rakshasa.no

# Port range to use for listening.
port_range = 49990-49999

# Start opening ports at a random position within the port range.
port_random = yes

# Check hash for finished torrents. Might be usefull until the bug is
# fixed that causes lack of diskspace not to be properly reported.
#check_hash = no

# Set whetever the client should try to connect to UDP trackers.
use_udp_trackers = yes

# Alternative calls to bind and ip that should handle dynamic ip's.
#schedule = ip_tick,0,1800,ip=rakshasa
#schedule = bind_tick,0,1800,bind=rakshasa

# Encryption options, set to none (default) or any combination of the following:
# allow_incoming, try_outgoing, require, require_RC4, enable_retry, prefer_plaintext
#
# The example value allows incoming encrypted connections, starts unencrypted
# outgoing connections but retries with encryption if they fail, preferring
# plaintext to RC4 encryption after the encrypted handshake
#
encryption = allow_incoming,try_outgoing,enable_retry,prefer_plaintext

#
# Do not modify the following parameters unless you know what you're doing.
#

# Hash read-ahead controls how many MB to request the kernel to read
# ahead. If the value is too low the disk may not be fully utilized,
# while if too high the kernel might not be able to keep the read
# pages in memory thus end up trashing.
#hash_read_ahead = 10

# Interval between attempts to check the hash, in milliseconds.
#hash_interval = 100

# Number of attempts to check the hash while using the mincore status,
# before forcing. Overworked systems might need lower values to get a
# decent hash checking rate.
#hash_max_tries = 10

# Max number of files to keep open simultaniously.
#max_open_files = 128

# Number of sockets to simultaneously keep open.
#max_open_sockets =

# Example of scheduling commands: Switch between two ip's every 5
# seconds.
#schedule = "ip_tick1,5,10,ip=torretta"
#schedule = "ip_tick2,10,10,ip=lampedusa"

# Remove a scheduled event.
#schedule_remove = "ip_tick1"
```

---

### Post by jw5801 on 2007-08-01
Cheers!
I had assumed that the session option would do that but it didn't appear to the first time I closed and opened rTorrent after adding it to .rtorrent.rc. However thinking back this may have been because I changed it whilst rTorrent was still open and then closed it :p But it's defineatly working now!

---

