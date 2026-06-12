---
title: "Is there way to have minimal ver of ubuntu"
date: 2006-07-16
forum: Absolute Beginner Talk
---

### Post by kris2pe on 2006-07-16
I usually dl stuff on the net & I want some way for ubuntu to b minimize all the stuff. I plan to dl bittorrents & I want to just leave it while it downloads. 
Is there way for ubuntu to b minimize in away that it only handles the bittorrent downloads or p2p downloads? 
SHould I try to learn, to use torrentbox & learn how to use server versions of ubuntu?

---

### Post by aysiu on 2006-07-16
Just do a server install and then ```
sudo aptitude update
sudo aptitude install bittorrent
```

---

### Post by kris2pe on 2006-07-16
do I have to download the server version?

---

### Post by aysiu on 2006-07-16
A server install can be done from either the server version or the Alternate CD version of any flavor of Ubuntu (Alternate Ubuntu, Alternate Kubuntu, Alternate Xubuntu).

It cannot be done from the Desktop CD.

Keep in mind, you can have a fully-installed Ubuntu and just use the command-line. You don't have to run the complete graphical environment just because it's installed.

---

### Post by kris2pe on 2006-07-16
how do I go to command line mode then? Can this still open p2p progs?

---

### Post by aysiu on 2006-07-16
Control-Alt-F1

I don't know of any command-line P2P programs, but you can search in Synaptic Package Manager for them.

---

### Post by montun on 2006-10-25
A nice torrent prog for use without Xorg is rtorrent[1].

It uses ncurses to draw the gui in the terminal.

I have used it a lot in combination with screen[2] and it is working very well.
```

$ ssh user@server.myhome
$ screen
(inside screen start rtorrent)
$ rtorrent
#exit screen with Ctrl-A Ctrl-D
$ exit
$ scp ubuntu-6.10-rc-alternate-amd64.iso.torrent user@server.myhome:torrents/
(if rtorrent is configured to it it can look in a directory like ~/torrents) for new torrents files and start the download automatically)

```

You can always log into the  server, resume screen, and monitor your downloads and throttle the up/download speed, start/stop downloads, set priority and so on.

[1] [http://packages.ubuntu.com/dapper/net/rtorrent](http://packages.ubuntu.com/dapper/net/rtorrent)
[2] [http://packages.ubuntu.com/dapper/misc/screen](http://packages.ubuntu.com/dapper/misc/screen)

---

### Post by nickburns on 2006-10-25
If you want a light weight, low resource, minimalist version with a graphical intreface use xubuntu.

---

### Post by n0dl on 2006-10-25
Keep in mind that doing a server install does not come with a GUI by default and you are dumped in a terminal. If you are an experienced (or at least simply comfortable with a terminal) then you should be just fine. If you have no GUI then you will have to use the curses front end to (a) bittorrent client. If you want a minimal system **WITH** a GUI then you may want to look into XFCE or some other lightweight WM.

---

### Post by Ben Sprinkle on 2006-10-25
Xubuntu, bearly uses any memory.

---

