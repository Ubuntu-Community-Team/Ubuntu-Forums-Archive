---
title: "Fileserver (smb) Downloader (torrent) and remote from windows"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by poohma on 2007-07-08
Ok, I'm posting here to get some ideas. Hopefully someone else finds this interesting.

I'm going to set up my 6.10 ubuntu-box as this:
*Fileserver -> serving 4 windows-boxes + modified Xbox (using SMB) + 1 ubuntu-box
*Torrentdownloader -> preferably a client with webinterface so I can organize downloads at home from work/other/pda/windows
*remote controlled -> vnc server for linux from my windows-box maybe, or is there another alternative? I prefer graphical interface as much as possible, otherwise I would just use sshd.

Problem is I'm kind of a noob. I would know how to implement this all in windows, but you know...  thats windows... I would prefer to be able to use linux as much as possible. Can't use it for games yet though, but for surfing, servers, mediacenter and so on...

So any Ideas on how this should be done?

Thank you :)

---

### Post by RedG on 2007-07-08
Hi!
For file server look for samba (there are lots of howtos both here on the forum and elsewhere on the net)
([http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605"))

For torrent downloader I use TorrentFlux, and I fits your needs as I can see. ([http://www.torrentflux.com/]("http://www.torrentflux.com/"))
There is a version of Torrentflux in the repositories but I couldn't make it work, I ended up downloading the 2.3 tar.gz-version from SourceForge. Be shore to read the "System Requirements" and the install-guide.

For "remote control" I use FreeNX and NXclient, there is a good howto here if you search for FreeNX on the forum. I am much happier using FreeNX then VNC, its faster and it almost feels like I'm sitting at my ubuntu-server.
([http://ubuntuforums.org/showthread.php?t=97277]("http://ubuntuforums.org/showthread.php?t=97277"))

---

### Post by poohma on 2007-08-01
Thank you. This has been a great help :)
I'm well on my way to trying these now. I had to install ubuntu server edition first though...  or...  it seemed easier at the time :P

---

