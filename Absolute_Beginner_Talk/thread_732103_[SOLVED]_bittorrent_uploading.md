---
title: "[SOLVED] bittorrent uploading"
date: 2008-03-22
forum: Absolute Beginner Talk
---

### Post by snkiz on 2008-03-22
quick question about bittorrent. I'm downloading an iso using bittorrent as I type but I'm a little confused I thought the whole point of torrent was that you upload what you have at the same time. sharing is caring. frostwire did this for me but bittorrent while faster,  doesn't seem to be uploading anything.. ack I'm a leech I don't really like that I subscribe to the pay it forward philosophy.

---

### Post by kelinu on 2008-03-22
Hi...what bittorrent client are you using?  Most clients upload when the file has finished downloading,  a good recommendation for a bittorrent client is QBittorrent.  It has a lovely, user friendly interface and it uploads while downloading too...also when you finish downloading the file it automatically goes into upload mode, and uploads...so either way you are still sharing and not being a leech! 

Hope this helps,
Michael :wink:

---

### Post by snkiz on 2008-03-22
I was using frostwire but not many had anything nice to say about it and there is alot of overhead. so now I'm tring out the bittorrent that came with ubuntu much faster. still you say there are better clients?

---

### Post by kelinu on 2008-03-22
Hi,
Well Frostwire is based on Limewire...but that was originally made for p2p file sharing, especially music.  You could use the client that came with ubuntu...but I never tried it so I can't give you any info on that.  QBittorrent is very nice, give it a shot.  Just don't mistake it for Qtorrent, cos that's a horrible client!

Michael

---

### Post by snkiz on 2008-03-22
thanks for the info I'll leave bittorrent while go out see if it uploads when finshed. and I'll be sure to try those others you mentioned when I move to hardy. don't see much point in tweeking gutsy any more got the hardy beta now, just need a weekend to fiddle with it

---

### Post by keratos on 2008-03-22
> **kelinu said:**
> Hi...what bittorrent client are you using?  Most clients upload when the file has finished downloading,  a good recommendation for a bittorrent client is QBittorrent.  It has a lovely, user friendly interface and it uploads while downloading too...also when you finish downloading the file it automatically goes into upload mode, and uploads...so either way you are still sharing and not being a leech! 

Hope this helps,
Michael :wink:

**Incorrect!**

If the torrent network decides you have a "piece" (a bit of a file) that another client requires, it will upload that piece.

If the torrent isnt uploading check your port status. There are many sites that can do this but you need to make sure that the port set in the torrent client app is open and available. If not then uploads will be slow (if at all) as will your download speed.

google "bittorrent port nat"

!

---

### Post by snkiz on 2008-03-22
well its maxing out my connection speed if thats an indicator.  I'm downloading knoppix there are lots of seeders so I'm not to worried about it. I don't like to screw with my port settings no experince at all with that stuff and If I lose my net connection wife will kill me lol

update
its uploading now good to see

---

### Post by kelinu on 2008-03-22
whoops sorry thanks for correcting me..I never knew that. But still, we learn from our mistakes!

---

### Post by keratos on 2008-03-22
> **snkiz said:**
> well its maxing out my connection speed if thats an indicator.  I'm downloading knoppix there are lots of seeders so I'm not to worried about it. I don't like to screw with my port settings no experince at all with that stuff and If I lose my net connection wife will kill me lol

update
its uploading now good to see

port setting in bittorrent client DOES NOT affect web.

it is purely a port (a opening if you will) through which bittorrent clients communicate with the torrent network.

there are many torrent apps so im not sure which one your using, but look in the settings area for "Port". The default torrent port is 6881. You need to make sure this port is open. Devices such a routers normally require these to be opened in their settings page, or via UPnP in the router. Sometimes the port can be closed by a software firewall.

Determine what port your client is using and test at...
[http://www.canyouseeme.org/](http://www.canyouseeme.org/)

p.s. always a good idea to change the default port from 6881 because ISPs shut this down to limit traffic on their network !

---

### Post by snkiz on 2008-03-22
I'm using bitorrent that came with gutsy I checked no port options just an option to cap uploaders and speed :(  I plan to try out qtorrent when I do my upgrade

---

### Post by snkiz on 2008-03-22
[QUOTE=keratos;4566175
p.s. always a good idea to change the default port from 6881 because ISPs shut this down to limit traffic on their network ![/QUOTE]

I'm already capped at 123kb/sec damed hi-speed lite they can go you know where

---

