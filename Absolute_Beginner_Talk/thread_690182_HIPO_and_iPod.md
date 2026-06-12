---
title: "HIPO and iPod"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by deranged on 2008-02-07
Hi, I have some troubles with HIPO. Whenever I plug in my iPod Nano, HIPO will crash. Starting HIPO from the terminal shows this:

```
Unhandled Exception: IPod.DatabaseReadException: Detected unsupported database version 27
  at IPod.DatabaseRecord.Read (IPod.DatabaseRecord db, System.IO.BinaryReader reader) [0x00000] 
  at IPod.TrackDatabase.Reload (Boolean createFresh) [0x00000] 
  at IPod.TrackDatabase..ctor (IPod.Device device, Boolean createFresh) [0x00000] 
  at IPod.Device.LoadTrackDatabase (Boolean createFresh) [0x00000] 
  at IPod.Device.LoadTrackDatabase () [0x00000] 
  at IPod.Device.get_TrackDatabase () [0x00000] 
  at IPod.Device.get_Name () [0x00000] 
  at IPod.DeviceCombo.AddDevice (IPod.Device device) [0x00000] 
  at IPod.DeviceCombo.Refresh () [0x00000] 
  at IPod.DeviceCombo..ctor () [0x00000] 
  at Hipo.HipoMainWindow.CreateWindow (System.String[] args) [0x00000] 
  at Hipo.HipoMain.Main (System.String[] args) [0x00000]
```

Any help is greatly appreciated.

---

### Post by jw5801 on 2008-02-07
I'm not familiar with Hipo, but is this a new generation iPod nano? If it is you might need to update a library, refer to this thread:
[http://ubuntuforums.org/showthread.php?t=611404](http://ubuntuforums.org/showthread.php?t=611404)
There's a bit of reading but I managed to get a mates new iPod nano running through gtkpod with the newer library.

---

