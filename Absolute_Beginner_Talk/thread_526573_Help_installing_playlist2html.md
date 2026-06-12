---
title: "Help installing playlist2html"
date: 2007-08-15
forum: Absolute Beginner Talk
---

### Post by Yes on 2007-08-15
I downloaded and extracted playlist2html.  In the terminal, I entered the playlist2html folder, and ran the command 'make', as instructed in the readme file.  I got these errors...

```
g++ -c src/MP3/CFrameHeader.cpp src/MP3/CId3Tag.cpp src/MP3/CVBitRate.cpp src/MP3/CMP3Info.cpp
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/backward/fstream.h:31,
                 from src/MP3/CMP3Info.cpp:1:
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/backward/backward_warning.h:32:2: warning: #warning This file includes at least one deprecated or antiquated header. Please consider using one of the 32 headers found in section 17.4.1.2 of the C++ standard. Examples include substituting the <X> header for the <X.h> header for C++ includes, or <iostream> instead of the deprecated header <iostream.h>. To disable this warning use -Wno-deprecated.
src/MP3/CMP3Info.cpp: In member function ‘int CMP3Info::loadInfo(char*)’:
src/MP3/CMP3Info.cpp:34: error: ‘ios’ has not been declared
src/MP3/CMP3Info.cpp:34: error: ‘ios’ has not been declared
src/MP3/CMP3Info.cpp:34: error: ‘ios’ has not been declared
src/MP3/CMP3Info.cpp:39: error: ‘ios’ has not been declared
src/MP3/CMP3Info.cpp:121: error: ‘ios’ has not been declared
src/MP3/CMP3Info.cpp: In member function ‘int CMP3Info::saveTag(char*, char*, char*, char*, char*, char*, char*)’:
src/MP3/CMP3Info.cpp:157: error: ‘ios’ has not been declared
src/MP3/CMP3Info.cpp:157: error: ‘ios’ has not been declared
src/MP3/CMP3Info.cpp:157: error: ‘ios’ has not been declared
src/MP3/CMP3Info.cpp:165: error: ‘ios’ has not been declared
make: *** [mp3] Error 1
```

Does anyone know what the problem is?  Or, does anyone know of another program that can generate and HTML playlist (Preferably one with a GUI)?

Thanks.

---

### Post by kevinlyfellow on 2007-08-15
It seems like an old program, did you get the gtk1 dependencies resolved?

---

### Post by Yes on 2007-08-15
Sorry, but gtk1 dependencies...?

It is a few years old, but it's the latest release of the program.

---

### Post by petit.padavoine on 2007-08-15
It seems to have old C++ stuff, as in #include <something.h> instead of #include <something> for standard libraries (functions that come with the programming language, kind of :D).

---

### Post by Yes on 2007-08-15
Ok, I'm going to go check all the source files for that, and fix them.

Thanks.

Edit:  I went to the file where the error was occurring, and I removed the .h from all the #include statements, except stdlib and stdio, because I've always ran into errors when I forgot the .h with those files.  When I tried compiling them again, I got these errors:

```
g++ -c src/MP3/CFrameHeader.cpp src/MP3/CId3Tag.cpp src/MP3/CVBitRate.cpp src/MP3/CMP3Info.cpp
src/MP3/CMP3Info.cpp: In member function &#8216;int CMP3Info::loadInfo(char*)&#8217;:
src/MP3/CMP3Info.cpp:34: error: &#8216;ifstream&#8217; was not declared in this scope
src/MP3/CMP3Info.cpp:34: error: &#8216;ifile&#8217; was not declared in this scope
src/MP3/CMP3Info.cpp:34: error: expected type-specifier before &#8216;ifstream&#8217;
src/MP3/CMP3Info.cpp:34: error: expected `;' before &#8216;ifstream&#8217;
src/MP3/CMP3Info.cpp:39: error: &#8216;ios&#8217; has not been declared
src/MP3/CMP3Info.cpp:61: error: type &#8216;<type error>&#8217; argument given to &#8216;delete&#8217;, expected pointer
src/MP3/CMP3Info.cpp:121: error: &#8216;ios&#8217; has not been declared
src/MP3/CMP3Info.cpp:131: error: type &#8216;<type error>&#8217; argument given to &#8216;delete&#8217;, expected pointer
src/MP3/CMP3Info.cpp:136: error: type &#8216;<type error>&#8217; argument given to &#8216;delete&#8217;, expected pointer
src/MP3/CMP3Info.cpp: In member function &#8216;int CMP3Info::saveTag(char*, char*, char*, char*, char*, char*, char*)&#8217;:
src/MP3/CMP3Info.cpp:157: error: &#8216;ofstream&#8217; was not declared in this scope
src/MP3/CMP3Info.cpp:157: error: &#8216;ofile&#8217; was not declared in this scope
src/MP3/CMP3Info.cpp:157: error: expected type-specifier before &#8216;ofstream&#8217;
src/MP3/CMP3Info.cpp:157: error: expected `;' before &#8216;ofstream&#8217;
src/MP3/CMP3Info.cpp:165: error: &#8216;ios&#8217; has not been declared
src/MP3/CMP3Info.cpp:174: error: type &#8216;<type error>&#8217; argument given to &#8216;delete&#8217;, expected pointer
make: *** [mp3] Error 1
```

Since I seemed to get the same errors as before, plus some, I replaced the .h in all the #Include statements.

---

### Post by Yes on 2007-08-15
I think the problem might be in my version of GTK.  I was reading the readme, and it says that I need GTK 1.26 or higher.  I have version 2, but could the program possible need GTK 1.x, and not be able to compile using 2.x, because it's so old?

I think that the easiest resolution would be just to use a different program.  Unfortunately, I still can't find any.  But if anyone knows of a program that will take a .m3u playlist and make an HTML page listing all the songs, then please let me know.

Edit:  It appears that the program Amarok has a playlist2html tool.  The only problem, is it's for KDE, and I use Gnome.  Is there a Gnome equiviland of Amarok that has a playlist2html tool?

Edit2:  I've found it!  quodlibet with the quodelibet plugins, both of which are in Synaptic.  Included in the plugins is a "Playlist to HTML" tool.

---

### Post by Yes on 2007-08-16
Never mind, I haven't found it.  The quodelibet playlist to HTML tool makes a playlist that uses tables, which is not preferable.  So I'd still like to try playlist2HTML, meaning that I still need help.

---

### Post by kevinlyfellow on 2007-08-16
Hmmm, I'm looking around but its not looking so bright.  Have you tried amaroK?  Just because you use gnome doesn't mean a qt app won't run.  It will look weird (but so won't a gtk1 app), but that can be fixed so that its not completely out of place.

---

### Post by kevinlyfellow on 2007-08-16
Don't uninstall quodlibet just yet

if you look at the file /usr/share/quodlibet/plugins/songsmenu/html.py you may be able to play with the plugin enough to get it to do what you want, assuming you know html.  I'd be willing to help you out on it, provided you let me know what your looking for in the html.

---

### Post by Yes on 2007-08-16
Well, I tried editing the file.  I would be able to edit it if I only needed to know HTML, but it appears that I also need to know Python (I think that's the language it's in).

Here's the code for the file:

```
# Copyright 2005 Eduardo Gonzalez
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License version 2 as
# published by the Free Software Foundation
#
# $Id$

import os
import re
import gtk
import config

from util import tag, escape
from plugins.songsmenu import SongsMenuPlugin

HTML = '''<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" />
<title>Zybez Radio Playlist</title>
<link href="style.css" rel="stylesheet" type="text/css" />
</head>

<body>
<h1 align="center">Zybez Radio</h1>
<center><img src="/img/community/radio/banner.png" alt="' /></center>
<hr align="center" width="500" />


<h2>Playlist: DJ 3-M</h2>

  <br />

<ol>
 <li>%(songs)s </li>
</ol>
 
</body>
</html>
'''

class ExportToHTML(SongsMenuPlugin):
    PLUGIN_ID = "Export to HTML"
    PLUGIN_NAME = _("Export to HTML")
    PLUGIN_DESC = _("Export the selected song list to HTML.")
    PLUGIN_ICON = gtk.STOCK_CONVERT
    PLUGIN_VERSION = "0.17"

    def plugin_songs(self, songs):
        if not songs: return

        chooser = gtk.FileChooserDialog(
            title="Export to HTML",
            action=gtk.FILE_CHOOSER_ACTION_SAVE,
            buttons=(gtk.STOCK_CANCEL, gtk.RESPONSE_REJECT,
                     gtk.STOCK_OK, gtk.RESPONSE_ACCEPT))
        chooser.set_default_response(gtk.RESPONSE_ACCEPT)
        resp = chooser.run()
        if resp != gtk.RESPONSE_ACCEPT:
            chooser.destroy()
            return

        fn = chooser.get_filename()
        chooser.destroy()

        cols = config.get("settings", "headers").split()

        cols_s = ""
        for col in cols:
            cols_s += '<th>%s</th>' % tag(col)

        songs_s = ""
        for song in songs:
            s = '<tr>'
            for col in cols:
                col = {"~#rating":"~rating", "~#length":"~length"}.get(
                    col, col)
                s += '\n<td>%s</td>' % (
                    escape(unicode(song.comma(col))) or '&nbsp;')
            s += '</tr>'
            songs_s += s

        f = open(fn, 'w')
        f.write((HTML % {'headers': cols_s, 'songs': songs_s}).encode('utf-8'))
        f.close()
```

I edited the HTML, but I need to edit the Python too to keep from putting the data in a table format.  I really just need it to look like this:

```
SongNumber    ArtistName   SongName
```

Also, after I change a Python file, do I have to compie it or something? 

Thanks.

---

### Post by kevinlyfellow on 2007-08-16
> **Yes said:**
> Well, I tried editing the file.  I would be able to edit it if I only needed to know HTML, but it appears that I also need to know Python (I think that's the language it's in).

Here's the code for the file:

I edited the HTML, but I need to edit the Python too to keep from putting the data in a table format.  I really just need it to look like this:

```
SongNumber    ArtistName   SongName
```

Also, after I change a Python file, do I have to compie it or something? 

Thanks.

Yeah, it looked easier than it has been so far.  I know a bit of python (I should know more) and I've been playing with it a bit.  A few things are still a bit mysterious for me though.  I still think I'll be able to hack this to just have line breaks instead of tables.

These files do not need to be compiled.  Python is mostly a scripting language.

---

### Post by kevinlyfellow on 2007-08-16
Here is the list strictly without tables, no information in the list was modified.  If you save it on your desktop
```
sudo chown root:root ~/Desktop/html_no_table.py
sudo chmod 644 ~/Desktop/html_no_table.py
sudo mv ~/Desktop/html_no_table.py /usr/share/quodlibet/plugins/songsmenu/html_no_table.py

```

---

### Post by Yes on 2007-08-16
It worked perfectly!  Thank you so much =D .

---

### Post by kevinlyfellow on 2007-08-17
No prob, it was fun :-)

---

