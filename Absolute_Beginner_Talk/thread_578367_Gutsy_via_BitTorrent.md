---
title: "Gutsy via BitTorrent ?"
date: 2007-10-17
forum: Absolute Beginner Talk
---

### Post by slink on 2007-10-17
Will it be possible to download Gutsy Gibbon via Bittorrent?

Where from ?

---

### Post by Druke on 2007-10-17
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

at the bottom of that page it says 'complete' list of download locations, click that find your mirror, find 7.10, will be at bottom of page (notice its likely empty right now)

---

### Post by dptxp on 2007-10-17
iso of this size are best downloaded using bittorrent, you get right files.

---

### Post by abhilash82 on 2007-10-17
you can get it here.
[http://releases.ubuntu.com/releases/7.10](http://releases.ubuntu.com/releases/7.10)

---

### Post by Squizzle on 2007-10-17
I might drop a server (100mbit) on the gutsy torrent tomorrow, put a few 100GBs in and help take the pressure off the FTPs a bit. :biggrin:

---

### Post by FredB on 2007-10-17
> **slink said:**
> Will it be possible to download Gutsy Gibbon via Bittorrent?

Of course !

> Where from ?

[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

"
**BitTorrent**

 You can obtain torrent files for each type of Ubuntu installation from the list at the bottom of the [7.04 release page]("http://releases.ubuntu.com/7.04/") or the [6.06 LTS release page]("http://releases.ubuntu.com/6.06/")."



Of course, 7.04 will be replaced by 7.10 tomorrow. And using torrent will be simpler and better for ubuntu servers.

---

### Post by hyper_ch on 2007-10-17
> **Squizzle said:**
> I might drop a server (100mbit) on the gutsy torrent tomorrow, put a few 100GBs in and help take the pressure off the FTPs a bit. :biggrin:

I'll do the same... I have a server that I actually only use for saving my backups also at another place and to stream my music to my workplace (gnump3d).

---

### Post by Squizzle on 2007-10-17
> **hyper_ch said:**
> I'll do the same... I have a server that I actually only use for saving my backups also at another place and to stream my music to my workplace (gnump3d).

Good man, we need to keep that torrent nice and strong, it's going to get raped! :)

---

### Post by slink on 2007-10-17
Thank you all!!

My Azureus is ready!

:guitar:

---

### Post by FredB on 2007-10-17
Azureus ? Just try deluge-torrent, it is far lighter ;)

---

### Post by hyper_ch on 2007-10-17
rtorrent... far lighter than deluge and totally controlable from a ssh-terminal ;)

---

### Post by slink on 2007-10-17
> ust try deluge-torrent, it is far lighter

I'll do!:)

---

### Post by Vadi on 2007-10-17
Could someone please tell me how can I help with the torrent networking also?

I only know that when you're downloading a file, it's helping distribute it. Well once I download the .iso via the torrent, how can I set it to just be sharing (without downloading more stuff)?

---

### Post by hyper_ch on 2007-10-17
Well, once a torrent is completely downloaded the status will change from leecher to seeder... meaning you're offering this data but aren't interested in downloading more :)

---

### Post by Vadi on 2007-10-17
Oh. Alright, I'll give it a try.

---

### Post by Ek0nomik on 2007-10-17
> **Squizzle said:**
> I might drop a server (100mbit) on the gutsy torrent tomorrow, put a few 100GBs in and help take the pressure off the FTPs a bit. :biggrin:

+1

---

### Post by rjmdomingo2003 on 2007-10-17
[FONT="Trebuchet MS"][/FONT]Or rtorrent for that matter.

---

### Post by hyper_ch on 2007-10-17
rtorrent just rules ;)

---

### Post by FredB on 2007-10-17
rtorrent ? A text client ? Well, to have a light seeding client, why not ?

---

### Post by funrider on 2007-10-17
ktorrent!

anyway i think this thread should be done or moved to the community cafe forum...

---

### Post by hyper_ch on 2007-10-17
FredB:

And one you can easily control through a normal ssh connection.

---

### Post by hyper_ch on 2007-10-17
So, I just created a little shell script that will fetch the desired .torrent files from the gutsy folder and download it to your watch-folder (the one which auto-adds torrents in your client)

(1) We need a little text file with the lists of the files we want to fetch (list.txt):
```

http://releases.ubuntu.com/7.10/ubuntu-7.10-alternate-i386.iso.torrent
http://releases.ubuntu.com/7.10/ubuntu-7.10-desktop-i386.iso.torrent

```
Just use the locations and filesnames of your desired files ;)

(2) We need a little shell script (gutsy.sh):
```

#!/bin/bash
# Set the path to your watchlist
cd /home/rtorrent/rtorrent/watchlist
# Set the path to your list file with the torrent locations
wget -N -i /home/rtorrent/list.txt

```

(3) Now add a cron job and run the shell script on a regular base with an entry like:
```

*/5 * * * * sh /home/rtorrent/gusty.sh

```

---

### Post by popey on 2007-10-17
Every minute is somewhat excessive don't you think?

---

### Post by alexj.powell on 2007-10-17
I'll be seeding on [http://demonoid.com](http://demonoid.com) for a couple of 100gbs.

Please seed and take the pressure off the ftps

The FTP download speed will be VERY slow tommorrow. (I remember feisty comeing out! LOL!)

---

### Post by hyper_ch on 2007-10-17
> **popeydc said:**
> Every minute is somewhat excessive don't you think?

Changed it to every 5min... ;)

---

### Post by anemptygun on 2007-10-17
deluge torrent looks pretty cool, thanks for the info!

---

### Post by nealmcb on 2007-10-17
Please don't put a continuous wget of a scarce resource in a cron entry that is scheduled for the indefinite future - folks will forget to disable it after it succeeds and it could go on for days....

Use a solution that will poll slowly and grab it when it shows up and then stop.  A nice little while loop with a sleep 600 should do the trick, and if there is a bug it will still stop eventually, like when you log out or reboot :-)

---

### Post by nealmcb on 2007-10-17
This discussion of clients is useful.  See our bittorrent help 
 [https://help.ubuntu.com/community/BitTorrent](https://help.ubuntu.com/community/BitTorrent)

which will now be pointed to by the release page - see
  [https://bugs.edge.launchpad.net/ubuntu-cdimage/+bug/146514](https://bugs.edge.launchpad.net/ubuntu-cdimage/+bug/146514)

I was updating the help for the default client, but if others could update the information there about better clients that would be great!

---

