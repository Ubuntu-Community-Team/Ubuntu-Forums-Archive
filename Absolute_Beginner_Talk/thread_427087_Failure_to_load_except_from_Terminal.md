---
title: "Failure to load except from Terminal"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by ratbagradio on 2007-04-29
Newbie:I was on iPodder/Juice/Lemon as my podcatcher program (to download podcasts) but when I upgraded to Feisty I lost iPodder completely and had to replace it. I installed IcePodder which worked for for a time then suddenly it refused to load at all -- it would begin to load then collapse,

See post here:
[http://ubuntuforums.org/showthread.p...64#post2544564](http://ubuntuforums.org/showthread.p...64#post2544564)

I had been 'loading it' via Terminal using>  sudo icepodder. But even that failed.

So I went looking for alternative...and the best option I've found for the way I use podcasts is PenguinTV. It works fine and is an excellent interface with easy syncing. It is unfortunate that it archives via date and not "show" but nonetheless it's pretty good and bookmarked it works well for me inside Amarok.

However to use it I have to open it via > sudo PenguinTV in Terminal and I have to keep Terminal open otherwise PenguinTV closes. So I have to open Terminal to load PenguinTV and closing Terminal will cause PenguinTv to exit.

Surely there's a work around? I can switch to Democracy TV or Songbird but really these (and I prefer Democracy TV as I ran it on WinXP) are too busy and too loaded with stuff for my simple needs.

It follows that a question mark has to be placed over Linux podcatchers iof these issues are encountered.

---

### Post by Najand on 2007-04-29
Can you copy/paste the ERROR messages you recieve in the terminal?

---

### Post by ratbagradio on 2007-04-29
For *sudo icepodder *I get:

> [<class 'ipodder.players.XMMSPlayer'>, <class 'ipodder.players.NoPlayer'>]
Beep-Media-Player couldn't be imported
Traceback (most recent call last):
  File "CastPodderGui.py", line 3623, in <module>
    main()
  File "CastPodderGui.py", line 3617, in main
    myApp = iPodderGui(ipodder)
  File "CastPodderGui.py", line 685, in __init__
    wx.App.__init__(self, False, None)
  File "/usr/lib/python2.5/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7700, in __init__
    self._BootstrapApp()
  File "/usr/lib/python2.5/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7352, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
  File "CastPodderGui.py", line 1533, in OnInit
    self.PopulateDownloadsTab()
  File "CastPodderGui.py", line 3359, in PopulateDownloadsTab
    self.DownloadTabLog(encinfo,prune=False)
  File "CastPodderGui.py", line 3254, in DownloadTabLog
    index = self.downloads.InsertStringItem(0,encinfo.item_title)
  File "/usr/lib/python2.5/site-packages/wx-2.6-gtk2-unicode/wx/_controls.py", line 4809, in InsertStringItem
    return _controls_.ListCtrl_InsertStringItem(*args, **kwargs)
  File "encodings/utf_8.py", line 16, in decode
UnicodeDecodeError: 'utf8' codec can't decode bytes in position 1-3: invalid data
ratbagradio@Ratbag:~$ 


---

### Post by ratbagradio on 2007-04-29
For *sudo PenguinTV *I get:

> using pynotify notifications
libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory

There's more but the forum won't let mne post it all because of urls and images....

---

### Post by drdf on 2007-05-09
I had the same problem using IcePodder on Dapper.  To get around it I edited the file CastPodderGui.py at the offending line.  I replaced line 3254, that read like:
```

                index = self.downloads.InsertStringItem(0,encinfo.item_title)

```
with
```

                try:
                    index = self.downloads.InsertStringItem(0,encinfo.item_title)
                except UnicodeDecodeError:
                    index = self.downloads.InsertStringItem(0,"read_error")

```
Note that the spacing matters so get the indentation right, and you might want to backup the original incase things go wrong.  I guess editing the source is a bit ugly, but it worked for me.  As far as I can tell, the only consequence of this is that in the page that displays the downloaded files the name of the offending file is shown as "read_error" instead of whatever is was supposed to be.  For me, this was only one file.

---

### Post by LinuxVictim on 2007-05-09
Just as a remark on the problem with the terminal you couldn't close without
closing the app, too.
When you start an app from the terminal, it is tied to that terminal.

It's the same with all GUI apps and the desktop manager. 
*sudo killall gdm* will kill not only x, but all other GUI apps.

I guess there's a way to start an app independently, but I don't know it.

Greetz,

LinuxVictim

---

