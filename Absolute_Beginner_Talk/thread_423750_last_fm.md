---
title: "last fm"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by jadie on 2007-04-26
whilst trying to listen to a track from the free downloads section of lastfm,  i got the message
firefox doesn't know how to open this address, because the protocol(lastfm)  isn't associated with any programme.  Can anyone help please.

---

### Post by Iceni on 2007-04-26
Did you download the last.fm software?

---

### Post by galv on 2007-04-26
You can setup in your last.fm profile that you wan't to listen to the tracks on the online flash player they've got (no need to use external player)

---

### Post by jadie on 2007-04-26
thanks for the quick reply, i will try your suggestions.

---

### Post by mcduck on 2007-04-26
There are couple of programs in Ubuntu repositories that can play last.fm, oncluding the official client and last-exit (a GTK2-client). And also at least BMPx can do that as well.

If installing your program of choice doesn't reister the last.fm protocol in Firefox here's how to do it:

1. type about:config into address bar in Firefox
2. right-click and select New/String from the popup menu.
3. set the new key to network.protocol-handler.app.lastfm
4. set the value to path to your program's executable, for example /usr/bin/last-exit
5. restart Firefox

After that lastfm: links will open in your player.

---

### Post by jadie on 2007-04-26
i installed adobe flash player and i can now play the tracks. thanks for your help .

---

