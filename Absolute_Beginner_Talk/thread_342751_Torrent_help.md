---
title: "Torrent help"
date: 2007-01-20
forum: Absolute Beginner Talk
---

### Post by kbsuperstar on 2007-01-20
What's the best torrent downloading program and how can i get it?

I tried bittorrent, bittornado, and azureus, but they've all sucked + download at 0 kb/s


My friend uses Transmission in FC, but I don't know if I can get that on ubuntu. What do you guys like to use?

---

### Post by halitech on 2007-01-20
Personally I'm using bittornado and it works fine for me. I've downloaded at up to 300KBs when I've gotten a good connection. is your router set up properly and do you have any firewalls set up?

---

### Post by Phixion on 2007-01-20
rtorrent is the best client out there, it's used on seedboxes alot too due to it being stable and fast. It is CLI based.

sudo apt-get install rtorrent

Then you need to make an rtorrent config file called '.rtorrent.rc'

Heres the config file I use:

```

# Maximum and minimum number of peers to connect to per torrent.
#min_peers = 40
#max_peers = 130

# Same as above but for seeding completed torrents (-1 = same as downloading)
#min_peers_seed = 10
#max_peers_seed = 50

# Maximum number of simultanious uploads per torrent.
#max_uploads = 17

# Global upload and download rate in KiB. "0" for unlimited.
#download_rate = 590
#upload_rate = 100

# Default directory to save the downloaded torrents.
directory = /home/mark/downloads

# Default session directory.
#session = /home/mark/torrents/sessions

# Watch a directory for new torrents, and stop those that have been deleted.
#schedule = watch_directory,5,5,load_start=/home/homedir/torrents/torrentfiles/*.torrent
#schedule = untied_directory,5,5,stop_untied=

# Close torrents when diskspace is low.
#schedule = low_diskspace,5,60,close_low_diskspace=100M

# Stop torrents when reaching upload ratio in percent,
# when also reaching total upload in bytes, or when
# reaching final upload ratio in percent.
# example: stop at ratio 2.0 with at least 200 MB uploaded, or else ratio 20.0
#schedule = ratio,60,60,stop_on_ratio=200,200M,2000

# Port range to use for listening.
port_range = 61407-61607

# Start opening ports at a random position within the port range.
# port_random = yes

# Set whetever the client should try to connect to UDP trackers.
use_udp_trackers = yes

```

as you can see, alot of the options are commented out, the only ones that I use in the file are the port_range and directory options. Obviously you will need to change the ports you want to use and your torrent save directory.

usage: download the .torrent and type 'rtorrent torrentname.torrent'

'man rtorrent' will show all other info.

---

### Post by dorcssa on 2007-01-20
I prefer using utorrent+wine. It's just working out of the box. :)

---

### Post by jimmygza on 2007-02-05
rtorrent works also out of the box, the config file is just for adjustments. The great advantage is that it uses very few resources because is console based and you can use it remote with ssh. Also it's way more efficient than any other torrent software I have ever used.

rtorrent is absolutly the best torrent software there is.

Best Regards,

---

