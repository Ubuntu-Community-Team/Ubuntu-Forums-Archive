---
title: "Problems with the Official BitTorrent client"
date: 2006-10-05
forum: Absolute Beginner Talk
---

### Post by ubuntu27 on 2006-10-05
Hello. I had BitTOrrent 4.X 
and I decided to update this client to 4.20.6, the latest version from BitTorrent.com
I've upgraded it with the same method I've always used:

1) Remove current version of BitTorrent

```
sudo apt-get remove bittorrent
```
2) Download and Install BitTorrent

```
sudo dpkg -i bittorrent_4.20.6_python2.4
``` 

After inserting the last command, I got an error saying that I had some dependencies to take care of.
SO, I installed those dependencies that were on the list. WHich al of those usually started with "python***something"


Now that I took care of the dependencies, I succefully installed BitTOrrent, or so I though. 

After running BitTorrent, I get an error saying: "BitTorrent core initialization failed!"  And it also lost all the *.torrents that I had.


What should I do? I'm lost. 

Click on the thumbnail to see the ScreenShot I took:
[[IMG]http://img183.imageshack.us/img183/9274/bittorrent1mu5.th.png[/IMG]](http://img183.imageshack.us/my.php?image=bittorrent1mu5.png)


PS: I'm running Breezy B.

---

### Post by skymt on 2006-10-05
What errors do you get if you run it from a terminal?

---

### Post by ubuntu27 on 2006-10-09
> **skymt said:**
> What errors do you get if you run it from a terminal?

Sorry I was a little busy.
 
Here it is the result from the terminal:

```
Ghost@Learner:~$ bittorrent
/home/ghost/.themes/Aerials/gtk-2.0/gtkrc:57: error: unexpected identifier `scrollbar_color', expected character `}'
Exception in thread bittorrent:242 in ?: threading.Thread(target=init_core, args=(mainloop,)).start():
Traceback (most recent call last):
  File "/usr/bin/bittorrent", line 242, in ?
    threading.Thread(target=init_core, args=(mainloop,)).start()
  File "/usr/bin/bittorrent", line 230, in init_core
    rawserver.stop()
  File "/usr/lib/python2.4/site-packages/BitTorrent/RawServer_twisted.py", line 899, in stop
    self.doneflag.set()
AttributeError: 'NoneType' object has no attribute 'set'

```


Thank you for the help. :)



EDIT:

THIS Is what I get **after** I close Bittorrent:

```
ghost@Learner:~$ bittorrent
/home/ghost/.themes/Aerials/gtk-2.0/gtkrc:57: error: unexpected identifier `scrollbar_color', expected character `}'
Exception in thread bittorrent:242 in ?: threading.Thread(target=init_core, args=(mainloop,)).start():
Traceback (most recent call last):
  File "/usr/bin/bittorrent", line 242, in ?
    threading.Thread(target=init_core, args=(mainloop,)).start()
  File "/usr/bin/bittorrent", line 230, in init_core
    rawserver.stop()
  File "/usr/lib/python2.4/site-packages/BitTorrent/RawServer_twisted.py", line 899, in stop
    self.doneflag.set()
AttributeError: 'NoneType' object has no attribute 'set'
non-daemon threads not shutting down in a timely fashion:
  <StackThread(disk_thread-1, started)>
  <StackThread(disk_thread-9, started)>
  <StackThread(disk_thread-7, started)>
  <StackThread(disk_thread-6, started)>
  <StackThread(disk_thread-5, started)>
  <StackThread(disk_thread-8, started)>
  <StackThread(disk_thread-4, started)>
  <StackThread(disk_thread-3, started)>
  <StackThread(disk_thread-10, started)>
  <StackThread(disk_thread-2, started)>
You have no chance to survive make your time.
Killed
ghost@learner:~$
```

---

### Post by skymt on 2006-10-10
It looks like a bug in BitTorrent. Either send an email to the developers, or use a different client. rtorrent is what I use.

---

