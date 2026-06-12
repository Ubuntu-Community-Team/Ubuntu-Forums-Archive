---
title: "Using Deluge BitTorrent Client"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by barrack on 2007-12-24
So I don't like the default bt client. I couldn't get the official BitTorrent going. Azureus was great, but the only version I get working is the new version 3 which is an awful interface. So it was recommended that I try Deluge. I have what seems to be a very simple problem... so simple that I have no idea what to do:

Normally when I am getting torrents, I'm using a site such as mininova. There I wold click on a link that says "download this torrent!" and the client takes over from there.

Now when I click on a torrent, I have the choice to select "Open with Deluge Torrent Client" and Deluge will open, but nothing happens. How do I actually get Deluge to start a download?

So far, the only way that I can get a download going is if I search for a torrent using the built-in browser, which is annoying.

Thoughts? Thanks in advance!

---

### Post by diatribe on 2007-12-24
> **barrack said:**
> So I don't like the default bt client. I couldn't get the official BitTorrent going. Azureus was great, but the only version I get working is the new version 3 which is an awful interface. So it was recommended that I try Deluge. I have what seems to be a very simple problem... so simple that I have no idea what to do:

Normally when I am getting torrents, I'm using a site such as mininova. There I wold click on a link that says "download this torrent!" and the client takes over from there.

Now when I click on a torrent, I have the choice to select "Open with Deluge Torrent Client" and Deluge will open, but nothing happens. How do I actually get Deluge to start a download?

So far, the only way that I can get a download going is if I search for a torrent using the built-in browser, which is annoying.

Thoughts? Thanks in advance!

you just click add at the top, or go to file add torrent

---

### Post by barrack on 2007-12-24
> **diatribe said:**
> you just click add at the top, or go to file add torrent

So I have to save the torrent file locally first and then open up Deluge separately and then use Deluge to add the torrent file?

Is there no simpler way?

---

### Post by diatribe on 2007-12-24
> **barrack said:**
> So I have to save the torrent file locally first and then open up Deluge separately and then use Deluge to add the torrent file?

Is there no simpler way?

you would have to go into your web browsers settings to have them open with deluge

---

### Post by barrack on 2007-12-24
I set that up and it didn't work. Click on a torrent-link gets as far as opening Deluge, but once open, nothing happens.

---

### Post by kvizz on 2007-12-24
it might be some problem with deluge, try to start it from terminal by typing "deluge" and hitting enter.

---

### Post by diatribe on 2007-12-24
> **barrack said:**
> I set that up and it didn't work. Click on a torrent-link gets as far as opening Deluge, but once open, nothing happens.

when you set it to use deluge you need to make sure the command is deluge filename, I think you would use deluge %f as the launcher, otherwise it will just open deluge and nothing will happen

---

### Post by barrack on 2007-12-24
When i go to my firefox preferences, there's no option for me to use a command. I can only select either the default (Deluge BitTorrent Client) or browse or save the file to my computer.

Thanks for the tip though, I bet it would work if I could use a command.

---

### Post by onero on 2007-12-24
I use the "Open with this application" setting in FIrefox. Click Browse, then select /usr/bin/deluge. This works for me, and when I open torrent files they are automatically added to Deluge. 

If this doesn't work for you, there's probably something wrong with deluge itself, probably in the configuration or installation. Try running it from the command line as was previously suggested.

(side note: I just started using Deluge recently, and I love it :D)

---

### Post by Lord DarkPat on 2007-12-24
Not trying to start a flame war or s'thing, but Deluge STINKS!! I hate the interface. Use Ktorrent. Better interface, somewhat same/better speed.

---

### Post by barrack on 2007-12-24
Thanks everyone for the help. I tried all the suggestions mentioned, but nothing worked. I hate to say it, but I'm back to Azureus. I found out how to avoid the Vuze Interface, so now I like it again.

---

### Post by k9dev on 2008-05-17
I know this is a while after the fact, but in Deluge there is an option in edit > preferences to set an autoload directory.  If you save your torrents to this defined directory (e.g. home > torrents, or whatever you like) Deluge will automatically start those torrents, then once you're done with the downloads, you can simply delete the torrents from within the program.

---

### Post by Ux64 on 2008-05-19
Dunno, latest Deluge version installation fails.

[http://forum.deluge-torrent.org/viewtopic.php?f=7&t=5905&start=10&st=0&sk=t&sd=a#p27305](http://forum.deluge-torrent.org/viewtopic.php?f=7&t=5905&start=10&st=0&sk=t&sd=a#p27305)

---

