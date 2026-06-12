---
title: "Need Bittorrent solution"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by seepage87 on 2008-01-02
I'm not sure how to do this.  I just built my first server and I would like it to run a bittorrent client but be controlled by another computer so that when I turn off, e.g. my laptop, the server will keep downloading/seeding.

Is there a way to set up Deluge or something to do this?  I know I could do it with Torrentflux, but I'm not sure what it's like as a client.

Also, I have a problem where my whole network slows to a crawl if I run a torrent client in Linux (only tried Deluge and Azureus so far, trying utorrent/wine tonight).  It doesn't when I run utorrent in windows, even with more connections open than I allow in linux.  utorrent in windows has some 500 connections while even if i allow less than 100 in linux there is much decay (only gets worse if I allow more connections).  Is there a good fix that I haven't read about?

In summary, I need a good remotely controllable bittorrent solution that won't destroy my network.  Thanks.

---

### Post by edward4130 on 2008-01-02
I do something like this with qbittorrent, very stable and full featured.  I suggest using it on the server as a client , then remote access it from the laptop,  qbittorrent is available in the repositories.

edward4130
Kansas city, Ks

---

### Post by AndyCooll on 2008-01-02
> **seepage87 said:**
> I'm not sure how to do this.  I just built my first server and I would like it to run a bittorrent client but be controlled by another computer so that when I turn off, e.g. my laptop, the server will keep downloading/seeding.

Is there a way to set up Deluge or something to do this?  I know I could do it with Torrentflux, but I'm not sure what it's like as a client.

Also, I have a problem where my whole network slows to a crawl if I run a torrent client in Linux (only tried Deluge and Azureus so far, trying utorrent/wine tonight).  It doesn't when I run utorrent in windows, even with more connections open than I allow in linux.  utorrent in windows has some 500 connections while even if i allow less than 100 in linux there is much decay (only gets worse if I allow more connections).  Is there a good fix that I haven't read about?

In summary, I need a good remotely controllable bittorrent solution that won't destroy my network.  Thanks.

You might want to take a look at [TorrentFlux]("http://ubuntuforums.org/showthread.php?t=268985&highlight=howto+torrentflux"). I believe KTorrent also allows remote administration (though I cannot confirm this), and possibly rTorrent.

I was interested in doing this myself awhile back but got side-tracked, so I cannot confirm how well any of these work for the purpose you are wanting.

:cool:

---

### Post by CatKiller on 2008-01-02
I'm personally quite a fan of using one of the command-line BitTorrent clients in combination with SSH and screen for remote control of torrent downloads. That might be something that you hadn't considered.

---

### Post by Seisen on 2008-01-02
If you want to keep your server w/o a gui I would try one of the command line bittorrent clients or you could always install a lightweight window manager like fluxbox or openbox and use Deluge which has a remote administration available which you can access from a  web browser.

---

### Post by seepage87 on 2008-01-02
The idea is to have my server running mythbuntu (uses xfce) since it will be doing recording as well as some other tasks.  Right now it has a regular ubuntu install which I'm more familiar with and used it to build my array (with mdadm) and test out the software I'll eventually be using when I switch over.

Using Deluge's web interface would be nice, but it doesn't have a way I can administer it using a local install of deluge via ssh or something?  I suppose it wouldn't be too much of a hassle.  I'm going to try to have much of my stuff taken care of by RSS, and I'll be using the web interface of mythtv to make recordings, etc.

But about my second problem, is there a reason why every client I try is destroying my network while utorrent in windows isn't?  This is obviously a big deal since a server doesn't do any good if it can't be connected to due to the torrent problems.

---

### Post by yemu on 2008-01-03
maybe try deluge-torrent.org. the client is written in python and has web frontend (you have to enable it with plugins) if you want you can always use vnc to connect to the server add your torrents and disconnect. it has a lot of features like blacklists and control/reductionof download/upload speed. 
i'm using it with the same scenario as you - mythtv with torrent and ssh/vnc for control.
best
y

---

### Post by kpkeerthi on 2008-01-03
As for your bandwidth problem, I suggest you throttle down the torrent client's upload speed to 80% of your network upload speed. See [this]("http://ubuntuforums.org/showthread.php?t=311851") for more information.

I prefer rtorrent as a client suitable for running on servers. Its highly configurable and is ncurses based. Use rtorrent in combination with 'screen' program for unprecedented control.

See:
[How to use rtorrent]("http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/")
[rtorrent and screen]("http://www-cip.physik.uni-bonn.de/~jupp/2007-11-22-using-rtorrent-screen-urxvt-and-xfce-quicklaunch.html")

---

### Post by Borbus on 2008-01-03
rTorrent. I run Debian on all of my headless boxes. Use screen and run rTorrent in screen. If you are not familiar with screen, it basicallt multiplexes your terminal (you can run more than one program in one session, ie. a shell, rtorrent, irssi etc.) and you can also detach the screen session. Everything running in the session keeps running like normal and you can then reattach the screen session from anywhere. screen is one of the best programs ever.

---

### Post by seepage87 on 2008-01-07
I head about screen awhile back, and forgot about it.  I'll definitely check it out.  Should be useful for a lot of processes.  

I think one of my problems with my network was my linksys router, which I've read are notorious for collapsing under bittorrent.  Installing 3rd party firmware and "increasing the maximum ports setting to allow more connections is the usual solution."  Not sure why the windose/linux difference though.  I actually had DD-WRT installed on it, I just didn't know the option to change (found under Administration->Management->Maximum Ports).

EDIT: Increase max ports helps, but also make sure to decrease the timeout for TCP and UDP connections.  The default on DD-WRT is 3600 seconds before idle connections are terminated, making the connections build up, clogging the network.  Turned it down to 90 and everything has been incredible ever since.

---

### Post by cozmicharlie on 2008-01-08
You might try Azureus with the Azsmrc server/client plug in.  There is a tutorial here [http://ubuntuforums.org/showthread.php?t=637160](http://ubuntuforums.org/showthread.php?t=637160)

---

