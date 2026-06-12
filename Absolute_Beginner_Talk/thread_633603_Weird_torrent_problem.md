---
title: "Weird torrent problem"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by aparigraha on 2007-12-06
**Never mind, I just made a complete uninstall and removed the .mozilla folder in my home catalog, Everything works better now.**

I just got a really strange torrent problem, which I can't seem to figure out how to solve.

First my torrent file association in Firefox disappeared, and the popup dialog window, which asks you what you want to do with the file you click, disappeared with it. When I clicked on a torrent file, ANY torrent file, nothing happened... absolutely nothing.

I had to start Firefox in Safe Mode: firefox --safe-mode
The dialog window appeared when clicking a torrent file and I solved that. The dialog window now appears.

But now I have another issue. It seems a link diectly to a .torrent file works fine, and the client starts. For instance this open source torrent works perfectly: [http://ostorr.org/uploads/OpenCD-07.04.iso.torrent]("http://ostorr.org/uploads/OpenCD-07.04.iso.torrent")

The problem is with torrents which are not in a direct link to the torrent file. It just doesn't work in Firefox. Here are some examples:

Any torrent on the Ubuntu torrent page: [http://torrent.ubuntu.com:6969/]("http://torrent.ubuntu.com:6969/")
the top torrent "breezy-live-i386.iso" gives me the link [http://torrent.ubuntu.com:6969/file?info_hash=%FE%2B%D0%826%BC%E9%E2%123%AC%0CP%F9%E1%9E%86%BC%86%A5]("http://torrent.ubuntu.com:6969/file?info_hash=%FE%2B%D0%826%BC%E9%E2%123%AC%0CP%F9%E1%9E%86%BC%86%A5")
and when I click it nothing happens.

any closed member tracker with download links like this:
[http://blablabla.net/download.php?id=6719](http://blablabla.net/download.php?id=6719)   (not a real adress but you get my meaning)
again, when I click those nothing happens.

When I try the same in Opera or Firefox Safe Mode, it all works fine.

I have tried disabling all AddOns and reinstalling Firefox but still no good. The strange thing is that it just happened all of the sudden while I was surfing the web, and Taadaaa, it didn't work. And for the above links I don't even get a popup dialog window asking me what to do with the torrent files. (Save File to..., Run with App...) So I can't even save the file and run it from the Desktop.

If anyone got any input on this it would be sweet. 
THX

---

### Post by vikramsharma on 2007-12-06
You can try installing bittornado-gui or bittorrent for handling torrent files.  Use Synaptic Package Manager to install these clients.  You can also try installing Azureus.

---

### Post by D_Murdock on 2007-12-11
I'm weirded out because BitTorrent keeps trying to start a connection with my PC unsolicited. Of course Firestarter blocks it, but I have no BitTorrent client installed or even BitTorrent. Why would I be getting a connection from it? Any suggestions?

---

