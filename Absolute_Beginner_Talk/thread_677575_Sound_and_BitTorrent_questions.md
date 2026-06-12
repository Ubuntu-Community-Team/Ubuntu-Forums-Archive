---
title: "Sound and BitTorrent questions"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by mrphud on 2008-01-24
Hello,

I have a couple of questions. First, I have a game theater xp sound card that seems to work on a hit or miss basis. I have noticed that when it does work the device selection menu for the volume control has it listed as device zero. When it doesn't work the device is listed as device 1 or maybe even 2 but not zero. Finally when I go to system>preference>sound and I try to test ALSA under sound capture for audio conferencing I get an error message that says:

[msg]Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'[/msg]

Any suggestions? 


The second question that I have is I have a large bittorrent file downloading as we speak. I would like to turn off my computer and when I turn it back on I would like to be able to start the torrent file again. I am using the default bittorrent client that is installed in 7.10. Where is the program located? How do I get it to start back up when I want to continue?

Thanks for the help!

---

### Post by jflarm on 2008-01-24
About the second question:
You can try:
which bittorrent
This will tell you the path for the bittorrent program.
Personally, I use azureus. It is WAY better than the default and you can get it through the repositories.

---

### Post by mrphud on 2008-01-24
I have heard that the new azureus is not that good. Personally I used it with windows and I liked the simple version that is now too gaudy for my tastes. How do I get azuresu through the repositories?


I found azureus!!

---

### Post by sloggerkhan on 2008-01-24
The best client, IMO, on Ubuntu, is the latest version of deluge, from [http://www.deluge-torrent.org](http://www.deluge-torrent.org)

However, if you want a simpler one that is better than default, transmission from the repos also works okay.

---

### Post by RomeReactor on 2008-01-25
> **mrphud said:**
> I would like to turn off my computer and when I turn it back on I would like to be able to start the torrent file again. I am using the default bittorrent client that is installed in 7.10. Where is the program located? How do I get it to start back up when I want to continue?

Thanks for the help!

Hi. The default BitTorrent client in Ubuntu doesn't show up on the menus since it only handles one download at a time; to resume the download, double-click on the **.torrent** file you used to start it, and the program will show up asking you if you wish to resume. To download multiple files simultaneously you need to open a client for every download.

If you want a client with more features, such as multiple downloads in the same window, try sloggerkhan's suggestion; Deluge is great.

---

