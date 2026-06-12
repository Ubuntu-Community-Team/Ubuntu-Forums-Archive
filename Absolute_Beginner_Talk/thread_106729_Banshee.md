---
title: "Banshee"
date: 2005-12-21
forum: Absolute Beginner Talk
---

### Post by jbmalone on 2005-12-21
I just installed Banshee and it won't open for me.  I tried to go to the terminal and open it using sudo but this is the error I got:

jbmalone@Jacob:~$ sudo banshee

Unhandled Exception: DBus.DBusException: No reply within specified time
in [0x0003e] (at /build/buildd/dbus-0.36.2/mono/Bus.cs:46) DBus.Bus:GetBus (BusType busType)
in [0x00001] (at /build/buildd/dbus-0.36.2/mono/Bus.cs:23) DBus.Bus:GetSessionBus ()
in [0x00007] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/DBusIPC.cs:53) Banshee.DBusServer:.ctor ()
in [0x00016] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/Core.cs:135) Banshee.Core:.ctor ()
in [0x0000b] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/Core.cs:73) Banshee.Core:get_Instance ()
in [0x000ef] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/Main.cs:78) Banshee.BansheeEntry:Main (System.String[] args)

What exactly do I need to do differently?  I am desperatly trying anything to get my iPod working.  I was hoping this could fix it.  Thanks.

---

### Post by jbmalone on 2005-12-21
Nevermind, I got this working.

---

### Post by jbmalone on 2005-12-21
I thought I had, but I was wrong.  Help would still be appreciated.

---

### Post by jbmalone on 2005-12-21
Well, after prodding around, I figured out the problem was my iPod and here is the error:

jbmalone@Jacob:~$ banshee
0: Active Player Engine is now 'GStreamer'
1: Loaded PlayerEngine core: GStreamer
2: Loaded AudioCdPlayerEngine core: GStreamer
3: Audio CD Core Initialized

Unhandled Exception: IPod.DatabaseReadException: Detected unsupported database v ersion 16
in <0x001b7> IPod.DatabaseRecord:Read (IPod.DatabaseRecord db, System.IO.BinaryR eader reader)
in <0x0010e> IPod.SongDatabase:Reload ()
in <0x000b2> IPod.SongDatabase:.ctor (IPod.Device device)
in <0x00033> IPod.Device:get_SongDatabase ()
in [0x00023] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src /Library.cs:316) Banshee.IpodSource:Refresh ()
in [0x00039] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src /Library.cs:308) Banshee.IpodSource:.ctor (IPod.Device device)
in [0x000b8] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src /SourceView.cs:204) Banshee.SourceView:RefreshList ()
in [0x00139] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src /SourceView.cs:162) Banshee.SourceView:.ctor ()
in [0x0025d] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src /PlayerInterface.cs:264) Banshee.PlayerUI:BuildWindow ()
in [0x00066] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src /PlayerInterface.cs:133) Banshee.PlayerUI:.ctor ()
in [0x0010d] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src /Main.cs:79) Banshee.BansheeEntry:Main (System.String[] args)


Now, I am really stuck.  If I read the error right it is pretty much saying that it can't read my itunesdb when I know that it is there because I play music on my iPod through Rythmbox all the time.  I had the same problem with gtkpod.  I am so lost.  Any help would be appreciated. 

Sorry for all the posts too, it's just everytime I thought I got close, I didn't.

---

### Post by bscbrit on 2005-12-21
How unusual - a post with 4 entries, all from the same person, and finally resolving the problem.  Congratulations!

---

### Post by fishbroetchn on 2005-12-23
i am having the same problem. Has anybody figured out a way around that??

---

