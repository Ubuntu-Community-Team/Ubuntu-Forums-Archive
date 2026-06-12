---
title: "DEluge loads then unloads"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by nanogeek on 2007-08-16
When I try to run Deluge it loads and unloads immediately
There are no other instances of Deluge running.
Running Deluge in a terminal window yields:



deluge.py:63: GtkWarning: gtk_scrolled_window_add(): cannot add non scrollable widget use gtk_scrolled_window_add_with_viewport() instead
  self.wTree = gtk.glade.XML(self.gladefile)
python-libtorrent, using libtorrent 0.11.0.0. Compiled with NDEBUG value: 1
Capping download to -1 bytes per second
Capping upload to 20480 bytes per second
Loading DHT state from /home/home/.config/deluge/dht.state
No DHT file to resume
terminate called after throwing an instance of 'asio::error'
  what():  Address already in use
Aborted (core dumped)


What do I do to fix this?

TIA
nanaogeek

---

### Post by Arthur Archnix on 2007-08-16
Is this from the repositories or the deb off of Deluge website? 

If its the former, do:
```
sudo apt-get --purge remove deluge-torrent
```
Then download and install the version from the website.

---

### Post by nanogeek on 2007-08-16
Um.
I think the repositories. It is version 0.4.0 (Does that help?)
How do I download and install it from the web site?

---

### Post by Arthur Archnix on 2007-08-16
Yes, the one in the repo's is quite old. In this case I'd recommend installing the latest version. I'm currently running it quite happily.

Once you remove your old version, using command above, download the latest version from their website. It will put a deb file on your desktop, just rick-click and choose install.

[http://deluge-torrent.org/downloads](http://deluge-torrent.org/downloads)

Make sure you get the right one for your ubuntu version.

---

### Post by nanogeek on 2007-08-16
Thanks for your advice.
The download page only shows a version for Feisty, not for Edgy.
I have been running Ubuntu for all of a week and every step is a big one for me. I am not ready to upgrade yet. Can I just download the Feisty version? 

BTW when I first installed Deluge, it did not have the behavior I mentioned in my original post

---

### Post by Arthur Archnix on 2007-08-16
Hmm.. sorry, thought you were running feisty. Well, if you've done the apt-get purge thing I've recommended it will have removed all config files of deluge. It sounds as if something in the config got screwy. Simply reinstalling it through add/remove should make it work again.

---

### Post by nanogeek on 2007-08-16
running:
 sudo apt-get purge deluge

yeilds:
E: Invalid operation purge
(yes I entered my password. I.m green, but not that green)

Next?

---

### Post by Arthur Archnix on 2007-08-16
My fault. Bad command. I fixed it above. Tested it on my system, and deluge is indeed gone. :)

---

### Post by thexaspect on 2007-08-18
Hey there, I'm having the same problem, and the purge/reinstall from current .deb from the deluge site has failed(doing ther same thing). any other ideas maybe? i'm baffled. tia,
bryan

edit: 
to be more specific, it's giving me this in the terminal:

```
x@tranquility:~$ deluge
no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG.
Applying preferences
Capping download to -1 bytes per second
Capping upload to -1 bytes per second
Raising error: libtorrent reports this is a duplicate torrent
Error: 'libtorrent reports this is a duplicate torrent'
Traceback (most recent call last):
  File "/usr/bin/deluge", line 140, in <module>
    start_deluge()
  File "/usr/bin/deluge", line 127, in start_deluge
    interface = deluge.interface.DelugeGTK()
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 53, in __init__
    '%s %s'%(common.PROGRAM_NAME, common.PROGRAM_VERSION), common.CONFIG_DIR)
  File "/var/lib/python-support/python2.5/deluge/core.py", line 263, in __init__
    self.sync(True)
  File "/var/lib/python-support/python2.5/deluge/core.py", line 837, in sync
    raise e
deluge.core.DuplicateTorrentError: 'libtorrent reports this is a duplicate torrent'

```

---

### Post by Arthur Archnix on 2007-08-19
Do this
```
sudo apt-get --purge remove deluge-torrent
```
then post the output of this:
```
sudo locate deluge
```

---

### Post by thexaspect on 2007-08-19
touche. didn't even think about that, deleted all the config files and it popped right up on reinstall. any idea what i can do to prevent that from happening again?

---

