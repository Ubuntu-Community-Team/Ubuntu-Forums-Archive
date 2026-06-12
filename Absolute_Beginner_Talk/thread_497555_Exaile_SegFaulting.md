---
title: "Exaile SegFaulting?"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by Nekiruhs on 2007-07-10
Ahh! All my media players are deserting me! AmaroK wont start anymore. And suddenly Exaile is segfaulting on me at random moments! I ran it through a console and here is the output:
```
nekiruhs@Ubuntu:~$ exaile
Plugins 'AWN' version '0.7.2' loaded successfully
Plugins 'IM Status' version '0.11' loaded successfully
Plugins 'Desktop Cover' version '0.2' loaded successfully
Plugins 'Mini Mode' version '0.4.1' loaded successfully
Plugins 'LibNotify Plugin' version '0.1' loaded successfully
Plugins 'Update Notifier' version '0.2' loaded successfully
Plugins 'Global Hotkeys' version '0.6' loaded successfully
Plugins 'No Taskbar Entry' version '0.1' loaded successfully
Checking in /home/nekiruhs/.exaile/plugins for egg plugins
<pkg_resources.Environment object at 0x8b1bacc>
Created db for thread Thread-1
{'Thread-1': <sqlite3.Connection object at 0x8b236b0>}
Closed db for thread Thread-1
Logging in to audioscrobbler
Using multimedia keys from: gnome
loading tracks...
done loading tracks...
loading songs
Clearing tracks cache
Importing /home/nekiruhs/.exaile/saved/playlist0000.m3u
Last playlist loaded
Loading page 0
Warning: Gstreamer equalizer element not found, please install the latest gst-plugins-bad package
Traceback (most recent call last):
  File "/usr/share/exaile/xl/db.py", line 172, in _execute
    cur.execute(query, args)
OperationalError: database is locked
UPDATE tracks SET last_played=? WHERE path=? ('2007-07-10 10:53:13', u'/home/nekiruhs/My Music/L/Linkin Park/Hybrid Theory/01 - Papercut.mp3')
Traceback (most recent call last):
  File "/usr/share/exaile/xl/db.py", line 172, in _execute
    cur.execute(query, args)
OperationalError: database is locked
UPDATE tracks SET user_rating=? WHERE path=? (6, 193)
Set rating to 6 for track Papercut from Hybrid Theory by Linkin Park
Traceback (most recent call last):
  File "/usr/share/exaile/xl/db.py", line 172, in _execute
    cur.execute(query, args)
OperationalError: database is locked
UPDATE tracks SET rating = rating + 1 , plays = plays + 1 WHERE path=? (193,)
updated plays 1, rating 1
Attempting to submit track Papercut from Hybrid Theory by Linkin Park to last.fm
-AUDIOSCROBBLER- i[0]=2007-07-10%2014%3A54%3A51&b[0]=Hybrid%20Theory&a[0]=Linkin%20Park&u=nekiruhs&m[0]=&t[0]=Papercut&l[0]=185
2007-07-10 14:54:52: Uploaded 1 tracks successfully
next track was reported as  None
Traceback (most recent call last):
  File "/usr/share/exaile/xl/db.py", line 172, in _execute
    cur.execute(query, args)
OperationalError: database is locked
UPDATE tracks SET last_played=? WHERE path=? ('2007-07-10 10:56:18', u'/home/nekiruhs/My Music/L/Linkin Park/Hybrid Theory/01 - Papercut.mp3')
Traceback (most recent call last):
  File "/usr/share/exaile/xl/db.py", line 172, in _execute
    cur.execute(query, args)
OperationalError: database is locked
UPDATE tracks SET last_played=? WHERE path=? ('2007-07-10 10:56:26', u'/home/nekiruhs/My Music/F/F-Ups, The/The F-Ups/01 - Lazy Generation.mp3')
new thread created with The F-Ups The F-Ups
cover thread started
Traceback (most recent call last):
  File "/usr/share/exaile/xl/db.py", line 172, in _execute
    cur.execute(query, args)
OperationalError: database is locked
UPDATE albums SET image=?, amazon_image=1 WHERE id=? ('7e6c99d33ddb23309b0e737eca690872.jpg', 8)
/home/nekiruhs/.exaile/covers/7e6c99d33ddb23309b0e737eca690872.jpg
Traceback (most recent call last):
  File "/usr/share/exaile/xl/db.py", line 172, in _execute
    cur.execute(query, args)
OperationalError: database is locked
UPDATE tracks SET user_rating=? WHERE path=? (7, 30)
Set rating to 7 for track Lazy Generation from The F-Ups by The F-Ups
Traceback (most recent call last):
  File "/usr/share/exaile/xl/db.py", line 172, in _execute
    cur.execute(query, args)
OperationalError: database is locked
UPDATE tracks SET last_played=? WHERE path=? ('2007-07-10 10:56:35', u'/home/nekiruhs/My Music/F/F-Ups, The/The F-Ups/01 - Lazy Generation.mp3')
Aborted cover thread
new thread created with The F-Ups The F-Ups
cover thread started
Traceback (most recent call last):
  File "/usr/share/exaile/xl/db.py", line 172, in _execute
    cur.execute(query, args)
OperationalError: database is locked
UPDATE albums SET image=?, amazon_image=1 WHERE id=? ('7e6c99d33ddb23309b0e737eca690872.jpg', 8)
/home/nekiruhs/.exaile/covers/7e6c99d33ddb23309b0e737eca690872.jpg
Segmentation fault (core dumped)
nekiruhs@Ubuntu:~$ 

```
I noticed it keeps saying something like Database is locked.
Awww. Come on! I was just starting to like Exaile! I may have to use Banshee, sigh.

---

