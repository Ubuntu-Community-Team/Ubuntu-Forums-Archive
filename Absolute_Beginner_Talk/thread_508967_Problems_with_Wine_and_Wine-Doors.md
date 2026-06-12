---
title: "Problems with Wine and Wine-Doors"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by macher on 2007-07-24
Hi

I installed WINE and then tried to get Office 2003 to work but the installer crashed. I then changed compability mode to windows 98. After that, the Office installer wanted to do a system upgrade and crashed, and every time i restart the installer (independent of compability mode) it wants to continue the system upgrade. Whether i choose yes or no, it crashes. After that i tested wine-doors and wanted to try to install office through that. But, when wine-doors was setting itself up at the first start, it crashed. And after that, it wouldn't run anymore. I've tried to reinstall wine and wine-doors but nothing happens. When i try to launch wine-doors from the terminal i get this: ```
wmattias@HPn:~$ wine-doors
Started logging session
Traceback (most recent call last):
  File "/usr/bin/wine-doors", line 22, in <module>
    from queue import queue
  File "/usr/share/wine-doors/src/queue.py", line 6, in <module>
    from application import ApplicationPack
  File "/usr/share/wine-doors/src/application.py", line 7, in <module>
    from packlist import packlist
  File "/usr/share/wine-doors/src/packlist.py", line 597, in <module>
    packlist = PackList()  
  File "/usr/share/wine-doors/src/packlist.py", line 165, in __init__
    self.GetInstalledPacks()
  File "/usr/share/wine-doors/src/packlist.py", line 177, in GetInstalledPacks
    self.Parse( self.installed_list )
  File "/usr/share/wine-doors/src/packlist.py", line 231, in Parse
    parser.parse( xmlfile )
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/expatreader.py", line 109, in parse
    xmlreader.IncrementalParser.parse(self, source)
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/xmlreader.py", line 125, in parse
    self.close()
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/expatreader.py", line 226, in close
    self.feed("", isFinal = 1)
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/expatreader.py", line 220, in feed
    self._err_handler.fatalError(exc)
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/handler.py", line 38, in fatalError
    raise exception
xml.sax._exceptions.SAXParseException: /home/mattias/.wine/wine-doors/installed.packlist.xml:1:0: no element found
mattias@HPn:~$ 

```

Anyone who knows what is wrong or maybe a possible solution?

---

### Post by Al3xK3aton on 2007-07-24
I believe Office 2003 requires Windows 2003, thus the same year in their name.

---

### Post by macher on 2007-07-24
I also tried using windows xp compability mode... and that didnt work either. But I'll try with win 2003! 

I've also tried using CrossOver, and that didn't work. Could my copy of Office be damaged? maybe i should try using another one...

Thanks for the quick answer! Ill try with win 2003 compability

---

### Post by macher on 2007-07-25
No luck with windows 2003 compability mode either.... Got Wine-doors to work by choosing another account and start it from that. But it didn't help...

any other ideas?

---

### Post by dorath on 2007-07-26
Office 2003 will run on Win2k(SP3+), XP, Server 2003, and Vista ([sys reqs]("http://support.microsoft.com/kb/822129")).  

The WINE application database ratings for Office 2003 aren't especially good ([http://appdb.winehq.org/appview.php?iVersionId=3214](http://appdb.winehq.org/appview.php?iVersionId=3214)).  However, there are a number of installation tips listed in the appdb and a number of people seem to have had good success with it.

---

