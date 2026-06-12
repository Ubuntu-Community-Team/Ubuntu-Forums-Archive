---
title: "I'm new - problem with Azureus"
date: 2007-10-02
forum: Absolute Beginner Talk
---

### Post by mft on 2007-10-02
Hi all

I'm trying to make the switch to Ubuntu 7.04 from XP, and have run into a problem with Azureus.

I've set Azureus up as I believe it should be, and my router is set up fine for torrent access via a chosen port.  It has worked fine for years with uTorrent in XP, and the NAT light in Azureus is green.


When I start a torrent, all works fine, and the download starts.  However, after a few minutes the download rate on all torrents drops to 0k / sec, despite being connected to lots of 'fully established' peers.  I don't think it's an ISP issue, as uTorrent behaves fine on XP.


Any thoughts? :)

---

### Post by baysl on 2007-10-02
You can use uTorrent in Ubuntu. It works fine with me.
Just install uTorrent with Wine.

---

### Post by Perfect Storm on 2007-10-02
Try and see if the same happen with deluge: [http://deluge-torrent.org/](http://deluge-torrent.org/) if it does it's some configuration problem. (there's Ubuntu packages for easy install).

---

### Post by Louis Cypher on 2007-10-02
> **Artificial Intelligence said:**
> Try and see if the same happen with deluge: [http://deluge-torrent.org/](http://deluge-torrent.org/) if it does it's some configuration problem. (there's Ubuntu packages for easy install).

I had the same issue with azureus.  When I switched to Deluge the problem vanished.  Checkout Deluge.

---

### Post by nemesis7 on 2007-10-02
Hi,

You should try to install azureus with Automatix [http://www.getautomatix.com/]("http://www.getautomatix.com/") 

I have installed azureus on my feisty x64 and it is working fine (up to 300ko sometimes).

---

### Post by mft on 2007-10-02
Great!  Deluge is working nicely, thanks - 83k/sec and counting... :)




And now for my second trick... to eradicate Totem, and ensure that VLC is the default player for video files... :-k

---

### Post by Perfect Storm on 2007-10-02
> **mft said:**
> Great!  Deluge is working nicely, thanks - 83k/sec and counting... :)




And now for my second trick... to eradicate Totem, and ensure that VLC is the default player for video files... :-k

```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude --purge remove totem totem-gstreamer totem-mozilla
sudo aptitude install vlc mozilla-plugin-vlc libdvdcss2
```

Right click on example an .avi file and choose properties. Go to "Open with" tab. And select VLC.

---

### Post by Perfect Storm on 2007-10-02
> **nemesis7 said:**
> Hi,

You should try to install azureus with Automatix [http://www.getautomatix.com/]("http://www.getautomatix.com/") 

I have installed azureus on my feisty x64 and it is working fine (up to 300ko sometimes).

Automatix is not the solution. It's a security risk and can break your system (mainly when you want to upgrade your system to a new version of Ubuntu).
Also Ubuntu does not support automatix.

---

### Post by fivesmellydragons on 2007-10-02
> **Louis Cypher said:**
> I had the same issue with azureus.  When I switched to Deluge the problem vanished.  Checkout Deluge.

I also had the same issue with Azureus and got fed up with it after awhile, tried Deluge and am lovin it!

---

### Post by tlink on 2007-10-02
> **mft said:**
> 
When I start a torrent, all works fine, and the download starts.  However, after a few minutes the download rate on all torrents drops to 0k / sec, despite being connected to lots of 'fully established' peers )

I had the exact same problem and installed uTorrent, problem solved.

---

### Post by break1979 on 2007-10-03
Hi,

I also had the problem with Azureus 2.5.0.0 and the download/upload speed dropping to zero after a couple of minutes of activity

I got Azureus working with Feisty by

1. getting the latest JRE from
[http://java.com/en/download/index.jsp](http://java.com/en/download/index.jsp)

(download the self-exctracting .bin file -> copy it to /usr/java -> execute the .bin as root --- from here azureus can locate the JRE files)

2. getting the latest Azureus from (I am currently running the 3.0.3.0 release)
[http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php)

(get the tarball and unpack it with "tar xvf <filename>" to your home directory. you can start azureus with the "azureus" executable from the ~/azureus directory)


currently downloading a torrent with 380 KB/s, hope this keeps up!

- Olli

---

### Post by Stoff on 2007-10-24
I also have the same problem. So I will give the proposed solution above a try.

However, one of the nice things about azureus is that it automatically switches to another torrent if one is running slowly. Do the other recommended clients support this feature as well?

Christoph

---

