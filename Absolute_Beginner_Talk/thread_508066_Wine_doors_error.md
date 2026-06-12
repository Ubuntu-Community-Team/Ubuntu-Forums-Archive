---
title: "Wine doors error"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-07-23
ive installed wine doors from a deb but its not working.

after entering wine-doors in terminal i got this as a result

```

scott@scott-desktop:~$ wine-doors
Started logging session
Checking wine drive: /home/scott/.wine/
/home/scott/.themes/Darker theme/gtk-2.0/gtkrc:50: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/scott/.themes/Darker theme/gtk-2.0/gtkrc:51: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/scott/.themes/Darker theme/gtk-2.0/gtkrc:52: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Error: No such file : /tmp/System Global.xml
Traceback (most recent call last):
  File "/home/scott/bin/wine-doors", line 99, in <module>
    ui.winedoors = ui.WineDoorsGUI()
  File "/home/scott/.local/share/wine-doors/src/ui.py", line 920, in __init__
    self.tree = PackTree( self.window['tv_packlist'], self.window )
  File "/home/scott/.local/share/wine-doors/src/ui.py", line 460, in __init__
    packlist.UpdateAll()
  File "/home/scott/.local/share/wine-doors/src/packlist.py", line 284, in UpdateAll
    self.Update( ''.join( item[0:1] ) )
  File "/home/scott/.local/share/wine-doors/src/packlist.py", line 266, in Update
    self.Parse( local_file )
  File "/home/scott/.local/share/wine-doors/src/packlist.py", line 231, in Parse
    parser.parse( xmlfile )
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/expatreader.py", line 103, in parse
    source = saxutils.prepare_input_source(source)
  File "/usr/lib/python2.5/site-packages/_xmlplus/sax/saxutils.py", line 523, in prepare_input_source
    f = urllib2.urlopen(source.getSystemId())
  File "/usr/lib/python2.5/urllib2.py", line 121, in urlopen
    return _opener.open(url, data)
  File "/usr/lib/python2.5/urllib2.py", line 366, in open
    protocol = req.get_type()
  File "/usr/lib/python2.5/urllib2.py", line 241, in get_type
    raise ValueError, "unknown url type: %s" % self.__original
ValueError: unknown url type: /tmp/System Global.xml
scott@scott-desktop:~$ 

```

anyone know what this is?

---

### Post by eiskalt on 2007-07-23
I"ve never used this, but after looking at the web page your probably missing some things.

[http://www.wine-doors.org/wordpress/?page_id=3](http://www.wine-doors.org/wordpress/?page_id=3)

check the list of dependencies with your synaptic package manager.  I also recommend compiling wine from source first, seems that its just more likely to work if you do it that way.  Once you do that your probably better off compilling doors from source too.

---

### Post by dark_harmonics on 2008-01-24
I have also experienced this same issue. I have done the following:

Reinstalled wine from the repositories
Installed Wine-doors from the Deb
Purged both wine and wine-doors
Reinstalled wine from the repositories
Compiled and installed  wine-doors from source.

I still get the same issue. Any suggestions?

---

