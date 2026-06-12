---
title: "XMMS crashes everytime i start it"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by PharaohSD on 2007-10-04
Hey fellow linuxers

first time i used xmms, made it play files from my vista partition, and it played perfectly, was setting up the touch button plugin, and it froze, so i restarted x, and now everytime i try to start xmms it pops up then dissappears  (and yes, i restarted my laptop and it still doesn't work)

when i go into terminal and type 
```

~$ sudo xmms -f

```
i get:
```

Password:
Message: device: default
DBAudioLib ERROR: could not create shared memory for system data.
 Hint: Make sure that dbfsd has been started.
 errno: : No such file or directory
plugin init.c: failed to init dbaudiolib. 
NON FATAL to xmms, but dbmix plugin will not work... 
xmms continuing...  is dbfsd running?
DBAudio ERROR: DBAudiolib initialization failed.
Message: fmt 5, channels: 2
Gdk-ERROR **: BadAccess (attempt to access private resource denied)
  serial 8 error_code 10 request_code 33 minor_code 0
 
```

---

### Post by PharaohSD on 2007-10-04
*doublt post*

anyone?

---

### Post by hotweiss on 2007-10-04
Reinstall it using the Synaptic not terminal.

---

### Post by jimrz on 2007-10-04
Had the same problem, xmms is no longer being developed and does not play nicely with feisty (gnome) on several of my boxes (way different specs on each, so doubt it is a hardware issue). I have switched to "audacious" (this is a fork of "beep" which is a fork of "xmms" but also no longer being developed (although it is still working ok with ubuntu)) which is working nicely for me and is available via Synaptic or apt-get.

---

### Post by hillyu on 2007-10-04
Actrually I suggest u to use xmms2 instead, It could be the best music player that I have found ever, though it's in developing period currently. 
The sound is really awesome.maybe it could be better if it could use mpg123 instead of using mad as the mp3 decoder.
Just apt-get install xmms2 and the xmms2-plugin-all and related packages
and simply use 
```
xmms2d 
```
to start the daemon 
and ```
xmms2 play
``` to start playing after u add your files to the mlib
just use "xmms2 mlib" command to see more information about how to add files to mlib

some cool "client"
gx2osd very cool on screen display
xmms2tray(there is an alternative gnome pannel applet, but sorry to forget the name)
I haven't found a good mlib management tools especailly some thing could add my font cover in the albums directory automatically to mlib.
there is the official web site which maybe helpful:
[http://wiki.xmms2.xmms.se/index.php/Main_Page]("http://wiki.xmms2.xmms.se/index.php/Main_Page")

---

### Post by tgalati4 on 2007-10-04
What is the Touch Button plug-in?  It would seem obvious to remove the plug-in and see if XMMS recovers.  There's nothing like the original.

---

