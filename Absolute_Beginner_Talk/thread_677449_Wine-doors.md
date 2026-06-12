---
title: "Wine-doors"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by webbie180 on 2008-01-24
Anyone using the latest deb version from the wine-doors, it doesnt seem to work on my gutsy....

---

### Post by forenpsych on 2008-01-24
works fine on my Mint :KS

---

### Post by webbie180 on 2008-02-04
I got this error, anyone can help?

ching@ubuntu:~$ wine-doors
Started logging session
Checking wine drive: /home/ching/.wine/
Error: No such file : /home/ching/.wine-doors/packlists/System Base.xml
Traceback (most recent call last):
  File "/usr/bin/wine-doors", line 105, in <module>
    ui.winedoors = ui.WineDoorsGUI()
  File "/usr/share/wine-doors/src/ui.py", line 1032, in __init__
    self.tree = PackTree( self.window['tv_packlist'], self.window )
  File "/usr/share/wine-doors/src/ui.py", line 531, in __init__
    packlist.UpdateAll()
  File "/usr/share/wine-doors/src/packlist.py", line 291, in UpdateAll
    self.Update( ''.join( item[0:1] ) )
  File "/usr/share/wine-doors/src/packlist.py", line 274, in Update
    self.Parse( local_file )
  File "/usr/share/wine-doors/src/packlist.py", line 239, in Parse
    parser.parse( xmlfile )
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/expatreader.py", line 103, in parse
    source = saxutils.prepare_input_source(source)
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/saxutils.py", line 523, in prepare_input_source
    f = urllib2.urlopen(source.getSystemId())
  File "/usr/lib/python2.5/urllib2.py", line 124, in urlopen
    return _opener.open(url, data)
  File "/usr/lib/python2.5/urllib2.py", line 373, in open
    protocol = req.get_type()
  File "/usr/lib/python2.5/urllib2.py", line 244, in get_type
    raise ValueError, "unknown url type: %s" % self.__original
ValueError: unknown url type: /home/ching/.wine-doors/packlists/System Base.xml

---

### Post by jayjaygibbs on 2008-02-21
I'm having the same problem... i tried re-installing wine-doors and i tried re-installing wine and using older versions of wine as well

---

