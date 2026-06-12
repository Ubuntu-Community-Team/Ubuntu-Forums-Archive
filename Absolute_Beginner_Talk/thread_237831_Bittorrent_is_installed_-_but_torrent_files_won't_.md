---
title: "Bittorrent is installed - but torrent files won't open!"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by cheway on 2006-08-16
Hi all,

I have bittorrent installed, plus the GUI, but torrent files won't open - I receive the error message "Couldn't display etc etc".

Any ideas why bittorrent isn't working? Thanks in advance.

---

### Post by kb3hkg on 2006-08-18
not sure why but most people use another client, I highly recommend azureus.

---

### Post by cheway on 2006-08-18
It's just that I've had nothing but trouble with Azureus (it's what I always used in Windows and it was fine) - in Linux it the pop-up messages don't dissapear, and never seems to connect.

---

### Post by nickpaton on 2006-08-18
To close the pop up windows in Azureus:

Click on Help>About Azureus.  You will now be able to close the Pop Up window; close About Azureus window afterwards.

A general reminder about using bit torrent download programs - on your router make sure you have your firewall correctly set up:

1. Correct ports opened, say 10550 - 10560, and that this is also mirrored in the bit torrent program you use.

2. That you have the correct IP address specified for your PC.

3. That you are not trying to download too many programs at once.

Doing these should give you a solid download.

Regarding BitTornado, I have just installed it as follows:

First

```
sudo aptitude install bittornado
```

Then went to Synaptic and installed the Bittornado GUI.  This also required a couple of other files (not sure which) but one was python-based.

Maybe worth complete uninstall and retrying as above?

---

### Post by kerry_s on 2006-08-18
there's already a gui for bittorrent, something maybe broke. the stock is> gnome-btdownload < perhaps a reinstall will help.

---

### Post by LadyDoor on 2006-08-18
I'll second the bittornado suggestion. It's good and I haven't had any problems with it. Also, if you want *detailed* help and post an error message, it would be helpful to post the rest of the error as well--etc. etc. doesn't really say a lot as to why something's wrong.

---

### Post by dannyboy79 on 2006-08-18
Azureus is Java based and sucks resources!! I use the Bittornado along with the GUI!! It's awesome. If you pick Bittornado and it's gui it'll pick all the dependence's for ya. Good luck

---

