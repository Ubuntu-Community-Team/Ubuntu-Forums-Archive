---
title: "Ubuntu can search mac, but mac cannot search mac???"
date: 2013-05-21
forum: Apple Hardware Users
---

### Post by cbanakis on 2013-05-21
My work is mostly comprised of Apple computers, including our file server, where we archive our entire history of files that build up daily.

Personally, I cannot stand working on Mac's, so I bought my own computer for work, so I could use Ubuntu instead of OSX.

For some reason, no one at work can search for files on the server.
Everyone is using Macs, and if they search the server for a file, it just stops imediately, and says 0 files found.

However, if I search that same Mac server from my Ubuntu machine, it works 100% of the time.

I would like to think this is simply because Ubuntu is better, but it really does not make any sense if Ubuntu can search Mac's better than Mac's can search Mac's.

Does anyone have any ideas that could possible explain this?

---

### Post by rkmugen on 2013-05-21
I don't believe this is an issue related to Ubuntu (ie. it's not an Ubuntu-specific problem that needs to be solved).  Having said that, I believe it's likely either an improper network/file-sharing configuration between the other Macs and the file server, or just the file server or those other Macs needing some driver or system software updates.

What version of OSX are they all using?  Do you know what protocol they're using to connect to the server (Apple Filing Protocol, SAMBA, or something else)?

---

### Post by cbanakis on 2013-05-21
I knew it wasn't an Ubuntu issue, since Ubuntu is the only one that works.

But I just thought I'd throw it out here, since it makes no sense to me why Ubuntu would work better with a mac, than a mac would.

I really don't mind if I find a solution here, or not.
(It works fine for me, the non-mac user) :)

All of the Mac's, including the server are running Mountain Lion, and all updates are current.

The macs communicate using AFP, while Windows machines, and my Ubuntu box connect using "Samba".

Samba is in quotes, because it is actually using Apples sorry excuse for Samba, since they decided to make their own Samba for Lion, and Mountain Lion.
(Which we had to impliment dozens of workarounds in order to get my computer, and the Windows computers to even connect to the Mac server in the beginning)

I guess thats what Samba, and Google Maps have in common.

Both of them were developed over several years, to near perfection, and Apple thought they could start from scratch and do better with both of them.
(They were mistaken on both accounts)

---

### Post by GhettoMrBob on 2013-05-25
If the server is sharing as both AFP and SMB, are you sure that the Macs are connecting with the AFP share and not the SMB share.

Another thing: if the Macs are connected to the AFP share and it isn't working, have you tried to connect to the SMB share? You say that your Ubuntu machine can search the SMB share just fine but have you tried this from the Macs as well?

---

### Post by cbanakis on 2013-05-28
Excellent thought.

It did not occur to me that the macs and ubuntu were not connecting using the same protocal.

---

