---
title: "Program not opening."
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by auraithx on 2007-06-28
So we had a power outage and when I turned my computer on 'Deluge' (BitTorrent Client) won't open - but it doesn't give me any error msgs either. When I click it, it just acts like it's going to open then does nothing.

I've tried reinstalling and restarting.

---

### Post by starcraft.man on 2007-06-28
> **auraithx said:**
> So we had a power outage and when I turned my computer on 'Deluge' (BitTorrent Client) won't open - but it doesn't give me any error msgs either. When I click it, it just acts like it's going to open then does nothing.

I've tried reinstalling and restarting.

Hmmmm, interesting... I think I've seen this before. I'm not exactly sure but I think that it might be because the program is already active and running in the background (even if you didn't start it), check the system monitor (and sessions, kill it if you see it running).  Alternatively if something happened just to that app, try ktorrent and azureus both are great clients.

---

### Post by auraithx on 2007-06-28
How do I get into the systems monitor?

---

### Post by trak87 on 2007-06-28
Run the program from the command line and see if any error messages appear.

---

### Post by Rocket2DMn on 2007-06-28
I'm not in front of my linux computer to test this, but i think you just run
```
gnome-system-monitor
```
It should also be available under System->Admininstration->System Monitor

---

### Post by auraithx on 2007-06-28
Nothing in systems monitor, and it isn't producing an error msg when run though alt+f2 either

Finally! a error msg! - ```
glasgowm@glasgowm-desktop:~$ deluge
no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG value: 1
Applying preferences
Starting DHT...
No DHT file to resume
/var/lib/python-support/python2.5/deluge/core.py:713: DeprecationWarning: integer argument expected, got float
  PREF_FUNCTIONS[pref](self.get_pref(pref))
Traceback (most recent call last):
  File "/usr/bin/deluge", line 83, in <module>
    start_deluge()
  File "/usr/bin/deluge", line 57, in start_deluge
    interface = deluge.interface.DelugeGTK()
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 47, in __init__
    '%s %s'%(common.PROGRAM_NAME, common.PROGRAM_VERSION), common.CONFIG_DIR)
  File "/var/lib/python-support/python2.5/deluge/core.py", line 217, in __init__
    self.sync()
  File "/var/lib/python-support/python2.5/deluge/core.py", line 642, in sync
    avail = self.calc_free_space(torrent.save_dir)
  File "/var/lib/python-support/python2.5/deluge/core.py", line 576, in calc_free_space
    dir_stats = os.statvfs(directory)
OSError: [Errno 2] No such file or directory: '/home/glasgowm/Lisa Lashes'

```

[b] I created a new folder called "Lisa Lashes" and it works fine now! oh my lord what a stupid reason for a program to stop working

THANKS GUYS! :D[/b]

---

### Post by sab0403 on 2007-06-28
*grins*

I had a similar problem recently with VMWare server. Them's the breaks...

---

### Post by caiooiac on 2007-07-07
Hi there
    I'm having the same problem you had, but as I'm a beginner, I just don't know what to do. If I try running from terminal, it shows:

caio@computador:~$ deluge
no existing Deluge session
deluge_core; using libtorrent 0.11.0.0. Compiled with NDEBUG value: 1
Applying preferences
Raising error: 
deluge_core; using libtorrent 0.11.0.0. Compiled with NDEBUG value: 1
terminate called after throwing an instance of 'boost::filesystem::filesystem_error'
  what():  boost::filesystem::default_name_check: default name check already set
Cancelado (core dumped)
caio@computador:~$ 


   If anyone could help I appreciate. And please try to be simple, couse I'm a little stupid.

Thanks

Caio

---

### Post by Jareth on 2007-07-09
Yeah same'ish thing here, its just stopped opening.

I get:

no existing Deluge session
deluge_core; using libtorrent 0.11.0.0. Compiled with NDEBUG value: 1
Applying preferences
Raising error: 
deluge_core; using libtorrent 0.11.0.0. Compiled with NDEBUG value: 1
terminate called after throwing an instance of 'boost::filesystem::filesystem_error'
  what():  boost::filesystem::default_name_check: default name check already set
Aborted (core dumped)

The last I can think of it doing was updating automatix.
Can anyone give any help on this?

---

### Post by Jareth on 2007-07-09
okay, sorry for time wasting, I found another post.

It says remove ~/.config/deluge/persistent.state as a temporary fix

I tried it and worked. Might just want to copy/save the file before deleting it, just a hunch?
Did lose the torrents that weren't finished though!

---

### Post by Anonii on 2007-07-09
> **auraithx said:**
> Nothing in systems monitor, and it isn't producing an error msg when run though alt+f2 either

Finally! a error msg! - ```
glasgowm@glasgowm-desktop:~$ deluge
no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG value: 1
Applying preferences
Starting DHT...
No DHT file to resume
/var/lib/python-support/python2.5/deluge/core.py:713: DeprecationWarning: integer argument expected, got float
  PREF_FUNCTIONS[pref](self.get_pref(pref))
Traceback (most recent call last):
  File "/usr/bin/deluge", line 83, in <module>
    start_deluge()
  File "/usr/bin/deluge", line 57, in start_deluge
    interface = deluge.interface.DelugeGTK()
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 47, in __init__
    '%s %s'%(common.PROGRAM_NAME, common.PROGRAM_VERSION), common.CONFIG_DIR)
  File "/var/lib/python-support/python2.5/deluge/core.py", line 217, in __init__
    self.sync()
  File "/var/lib/python-support/python2.5/deluge/core.py", line 642, in sync
    avail = self.calc_free_space(torrent.save_dir)
  File "/var/lib/python-support/python2.5/deluge/core.py", line 576, in calc_free_space
    dir_stats = os.statvfs(directory)
OSError: [Errno 2] No such file or directory: '/home/glasgowm/Lisa Lashes'

```

[b] I created a new folder called "Lisa Lashes" and it works fine now! oh my lord what a stupid reason for a program to stop working

THANKS GUYS! :D[/b]
I'd suggest you to create a bug report. Since you use Deluge, and like it, why not spend 10 minutes of your time, writing a report for the developers? That will probably fix that "stupid" problem. You can do it here: [http://dev.deluge-torrent.org/newticket](http://dev.deluge-torrent.org/newticket)

If you decide to help, don't forget to mention your Ubuntu version, and your Deluge's version too. Also, how did that happen. The name of the torrent, etc.

Thanks.

---

### Post by Jareth on 2007-07-09
I think I will leave them a ticket for that one, thanks for the link!

I did manage to find the same torrent files, for what I was downloading, and started them up again. They picked up the downloads where they left off.
I didn't think they'd do it, incase I'm pointing out the bleeding obvious!

Thanks again!

---

### Post by Anonii on 2007-07-09
> **Jareth said:**
> I think I will leave them a ticket for that one, thanks for the link!

I did manage to find the same torrent files, for what I was downloading, and started them up again. They picked up the downloads where they left off.
I didn't think they'd do it, incase I'm pointing out the bleeding obvious!

Thanks again!
I am not sure if your problem and the OP's problem are the same. 
Try searching the bug tracker for similar bugs before reporting it, by the way.

---

### Post by Eggnog on 2007-07-11
> **Jareth said:**
> okay, sorry for time wasting, I found another post.

It says remove ~/.config/deluge/persistent.state as a temporary fix

I tried it and worked. Might just want to copy/save the file before deleting it, just a hunch?
Did lose the torrents that weren't finished though!

I downloaded the .deb from getdeb.net and had the same problem.  Removing persistent.state did the trick.

---

### Post by auraithx on 2007-07-17
> **Anonii said:**
> I'd suggest you to create a bug report. Since you use Deluge, and like it, why not spend 10 minutes of your time, writing a report for the developers? That will probably fix that "stupid" problem. You can do it here: [http://dev.deluge-torrent.org/newticket](http://dev.deluge-torrent.org/newticket)

If you decide to help, don't forget to mention your Ubuntu version, and your Deluge's version too. Also, how did that happen. The name of the torrent, etc.

Thanks.

Internal Error

Submission rejected as potential spam (Content contained blacklisted patterns)

It's broken again anyway - I guess I'm just gonna have to get a new torrent client.

---

