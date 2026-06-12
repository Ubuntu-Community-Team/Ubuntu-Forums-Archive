---
title: "Applications issue; SoundKonverter install failure;"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by ratbagradio on 2007-04-19
3 weeks new to ubuntu. Now on Edgy with upgrade four days ago. Installed (audio editor) Audacity but could not get it to capture Lame. I then tried to install Mp3 conversion for Jokosher and drew a failure there too despite the massive gstreamer download.

The failure of Audacity to take up Lame seems that  may be a problem with Edgy. Forums suggest use another tool to convert to Mp3. I then downloaded SoundKonverter but could not work out how to install it. It is supposedf to run akin to Amarok which works well on my desk top(and the bes6t audio player I've ever used).

Now after not getting anywhere I cannot open Applications:Add/Remove as it closes during opening with Systems Tools.
I tried to open Konsole and get:> ..error setting up inter -process communications for KDE. The message returned from the system was: Could not network socket. Please check that the "doscserver" program is running!

Why does media on Ubuntu have to be so difficult to set up! It's a killer fault. I had issues with every audio I installed.I recognise copyright problems re Lame but there's a big hole in accessibility there and for the life of me I cannot comprehend the DIY. This issue has occupied me for days and while its been a learning curve I think I've hit a wall.

Anyway. (1) how do I fix my 'system' problem? (2) how can I install SoundKonverter on Edgy.

---

### Post by ratbagradio on 2007-04-19
My iPodder (podcast aggregator) now also suffers from the same failure yo start issue...

---

### Post by ratbagradio on 2007-04-19
My Ipodder readout is> :ratbagradio@Ratbag:~$ sudo ipodder
Password:
[<class 'ipodder.players.XMMSPlayer'>, <class 'ipodder.players.NoPlayer'>]
Traceback (most recent call last):
  File "/usr/share/ipodder/iPodderGui.py", line 3531, in ?
    main()
  File "/usr/share/ipodder/iPodderGui.py", line 3525, in main
    myApp = iPodderGui(ipodder)
  File "/usr/share/ipodder/iPodderGui.py", line 590, in __init__
    wx.App.__init__(self, False, None)
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7700, in __init__
    self._BootstrapApp()
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7352, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
  File "/usr/share/ipodder/iPodderGui.py", line 1460, in OnInit
    self.PopulateDownloadsTab()
  File "/usr/share/ipodder/iPodderGui.py", line 3233, in PopulateDownloadsTab
    self.DownloadTabLog(encinfo,prune=False)
  File "/usr/share/ipodder/iPodderGui.py", line 3143, in DownloadTabLog
    index = self.downloads.InsertStringItem(0,encinfo.item_title)
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_controls.py", line 4809, in InsertStringItem
    return _controls_.ListCtrl_InsertStringItem(*args, **kwargs)
UnicodeDecodeError: 'utf8' codec can't decode bytes in position 1-3: invalid data
ratbagradio@Ratbag:~$ 
ratbagradio@Ratbag:~$ 



---

