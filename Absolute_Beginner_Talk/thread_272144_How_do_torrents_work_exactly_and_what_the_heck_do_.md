---
title: "How do torrents work exactly and what the heck do all the terms mean?"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by baylorbear on 2006-10-05
I've never understood the terminology associated with Torrents. For example.. some of the phrases used in KTorrent are completely foreign to me...

Enqueue/Dequeue ?
Manual Announce ?
Sharing Ratio ?
Leechers / Seeders ?
Peers ?
Chunks ?
Trackers ?

What does it all mean?
And something else... the download speed is completely volitile... one minute its good... next minute it sucks. Why?

---

### Post by jd65pl on 2006-10-05
Leechers - Those downloading the file
Seeders - Those providing the file for download
Trackers - Monitoring who is Leeching and Seeding??? Not sure on that
Chunks - Torrents don't download the file in a linear fashion they download lots of parts then put it back together I think this refers to thatdifferent

---

### Post by baylorbear on 2006-10-05
Well that clears up a bit -- but what about some of those other terms?  Sometimes I get around two torrent nuts who go to talking about queue-ing and announcing and whatnot... makes NO sense to me :s

---

### Post by aktiwers on 2006-10-05
Sharing Ratio - should be atleast 1.00 (but more is better)
This is how much of the file you have shared. 

1.00 < Good, the torrent will keep liveing..
1.00 > Bad, now there is a change someone wont be able to complete his download, doe to lag of seeders. 

Always seed your torrents more than 1.00 :)

---

### Post by exer! on 2006-10-05
Terminology

availability
    (also distributed copies) The number of full copies of the file available to the client. Each seed adds 1.0 to this number, as they have one complete copy of the file. A connected peer with a fraction of the file available adds that fraction to the availability, if no other peer has this part of the file. (ie. a peer with 65.3% of the file downloaded increases the availability by 0.653. However, if two peers both have the same portion of the file downloaded - say 50% - and there is only one seeder, the availability is 1.5).

choked
    Describes a peer to whom the client refuses to send file pieces. A client chokes another client in several situations:

        * The second client is a seed, in which case it does not want any pieces (ie. it is completely uninterested)
        * The client is already uploading at its full capacity (ie. the value for max_uploads has been reached)

interested
    Describes a downloader who wishes to obtain pieces of a file the client has. For example, the uploading client would flag a downloading client as 'interested' if that client did not possess a piece that it did, and wished to obtain it.

leech
    A leech is usually a peer who has a negative effect on the swarm by having a very poor share ratio - in other words, downloading much more than they upload. Most leeches are users on asymmetric internet connections and do not leave their BitTorrent client open to seed the file after their download has completed. However, some leeches intentionally avoid uploading by using modified clients or excessively limiting their upload speed. The term leech, however, can be used simply to describe a peer - or any client that does not have 100% of the data.

peer
    A peer is one instance of a BitTorrent client running on a computer on the Internet to which other clients connect and transfer data. Usually a peer does not have the complete file, but only parts of it. However, in the colloquial definition, "peer" can be used to refer to any participant in the swarm (in this case, it's synonymous with "client").

scrape
    This is when a client sends a request to the tracking server for information about the statistics of the torrent, such as with whom to share the file and how well those other users are sharing.

seeder
    A seeder is a peer that has a complete copy of the torrent and still offers it for upload. The more seeders there are, the better the chances are for completion of the file.

snubbed
    An uploading client is flagged as snubbed if the downloading client has not received any data from it in over 60 seconds.

superseed
    When a file is new, much time can be wasted because the seeding client might send the same file piece to many different peers, while other pieces have not yet been downloaded at all. Some clients, like ABC, Azureus, BitTornado, TorrentStorm, and µTorrent have a "superseed" mode, where they try to only send out pieces that have never been sent out before, making the initial propagation of the file much faster. This is generally used only for a new torrent, or one which must be re-seeded because no other seeds are available.

swarm
    Together, all peers (including seeders) sharing a torrent are called a swarm. For example, six ordinary peers and two seeders make a swarm of eight.

torrent
    A torrent can mean either a .torrent metadata file or all files described by it, depending on context. The torrent file contains metadata about all the files it makes downloadable, including their names and sizes and checksums of all pieces in the torrent. It also contains the address of a tracker that coordinates communication between the peers in the swarm.

tracker
    A tracker is a server that keeps track of which seeds and peers are in the swarm. Clients report information to the tracker periodically and in exchange receive information about other clients to which they can connect. The tracker is not directly involved in the data transfer and does not have a copy of the file. 


--------

From Wikipedia.
[http://en.wikipedia.org/wiki/BitTorrent](http://en.wikipedia.org/wiki/BitTorrent)

---

### Post by stoeptegel on 2006-10-06
> **baylorbear said:**
> 

Enqueue/Dequeue ?
Manual Announce ?
Sharing Ratio ?
Leechers / Seeders ?
Peers ?
Chunks ?
Trackers ?


Enqueue/Dequeue
This is a shortcut for changing the way the torrent is controlled by the queue manager. This is either by Queue manager or by user.

Manual announce
This is for doing the communication with the tracker, which is normally done in intervals, by hand, manually. With this "communication/announce", the tracker knows how much you have downloaded/uploaded from the moment you started the torrent and how much you still have left todo. The tracker also gives your client information back on what peers there are in swarm, so your client can find other clients on the torrent.
Normally by spec, this announce will trigger automaticly every 30 minutes, but it can be anything longer if the tracker wants to. KTorrent follows this tracker wish up.
Doing a manual announce will not give you any better speeds per se, nor will tracker usually like it. In general use you won't need it, but if you feel you do i would recommend to use it wisely.

Sharing ratio
Just an indication on how much you have download vs uploaded on a torrent. Keeping this value somewhere around 1.0 before you permently stop the torrent is best.

Leechers/Seeders
Leechers are just computers a.k.a peers that don't have a full copy of the data. Seeders are the peers that do have and share a full copy.
When a client doesn't have all files yet (i.e some files are deselected for download), it should always present itself as leecher towards both the peers in swarm and the tracker.

Peers
Just some weird(but official) naming for other clients that run the same torrent.(both leechers and seeders will catch this title)

Chunks
For purpose of optimal transport, the data representated by the hashes inside the torrent are broken into parts. Those parts are called chunks. Chunks always have a fixed size and can be given sizes from 32KB to normally 4MB in the process of creating a torrent file.
Torrents carrying bigger data generally have bigger chunks, torrents that don't carry so much data are more effective when the chunks are small.

Tracker
Host which track stats and give you information about other peers inside the swarm. The url to the tracker should be in the torrent file.

Hope this was easy to read.

---

### Post by FNDII on 2007-09-18
More on how do torrents work. 

What determines the DL speed of the file?
I started a DL of a file with 200 seeders and 900 leechers.
I assume with that many people With the file that my DL speed would be good.
But as it turns out It the same old 50-110KB/s.
Some torrents have gone even faster/slower at times 
Highly active torrents are sometimes realy slow

---

### Post by FNDII on 2007-09-18
I thought of my torrent questions as I was watching it tick away at  a steady 40KB/s.

I just come back after a snack and the torrent has stopped.
Why does something like this happen on a torrent with 200 seeders and 900 leechers.

I use the default Feisty torrent downloader

---

