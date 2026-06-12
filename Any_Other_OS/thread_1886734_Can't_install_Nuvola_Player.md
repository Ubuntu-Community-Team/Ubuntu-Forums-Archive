---
title: "Can't install Nuvola Player"
date: 2011-11-25
forum: Any Other OS
---

### Post by doppel.ganger on 2011-11-25
I downloaded the tar.gz file from their Launchpad site ([https://launchpad.net/nuvola-player]("https://launchpad.net/nuvola-player")) and followed the instructions in the README.Fedora file. It worked fine until I got here:
```
[kathryn@Kathryn-Fedora google-music-frame-0.3.2]$ ./waf install
Waf: Entering directory `/home/kathryn/Downloads/google-music-frame-0.3.2/build'
>>> vala defines: ['GLIB_DBUS', 'LIBSOUP_CACHE', 'HAVE_WEBKIT', 'HAVE_GDK', 'HAVE_XLIB', 'HAVE_SOUP', 'HAVE_GTK', 'HAVE_GOBJECT', 'HAVE_LOCALE_H', 'HAVE_GEE', 'HAVE_GLIB', 'HAVE_UNIQUE', 'HAVE_GTHREAD', 'HAVE_NOTIFY', 'HAVE_GIO', 'VALAC_0_13']
+ install /usr/local/share/applications/googlemusicframe.desktop (from data/applications/googlemusicframe.desktop)
Waf: Leaving directory `/home/kathryn/Downloads/google-music-frame-0.3.2/build'
Build failed
Traceback (most recent call last):
  File "/home/kathryn/Downloads/google-music-frame-0.3.2/.waf-1.6.4-37059750328bf24b869521d97d29c0c1/waflib/Task.py", line 125, in process
    ret=self.run()
  File "/home/kathryn/Downloads/google-music-frame-0.3.2/.waf-1.6.4-37059750328bf24b869521d97d29c0c1/waflib/Task.py", line 49, in run
    return m1(self)
  File "/home/kathryn/Downloads/google-music-frame-0.3.2/.waf-1.6.4-37059750328bf24b869521d97d29c0c1/waflib/Build.py", line 444, in run
    return self.generator.exec_task()
  File "/home/kathryn/Downloads/google-music-frame-0.3.2/.waf-1.6.4-37059750328bf24b869521d97d29c0c1/waflib/Build.py", line 461, in exec_install_files
    self.generator.bld.do_install(y.abspath(),destfile,self.chmod)
  File "/home/kathryn/Downloads/google-music-frame-0.3.2/.waf-1.6.4-37059750328bf24b869521d97d29c0c1/waflib/Build.py", line 506, in do_install
    raise Errors.WafError('Could not install the file %r'%tgt)
WafError: Could not install the file '/usr/local/share/applications/googlemusicframe.desktop'

[kathryn@Kathryn-Fedora google-music-frame-0.3.2]$ 

```
Any suggestions? Any help would be greatly appreciated. By the way, I'm running Fedora 16 Gnome.

---

### Post by wolfen69 on 2011-11-25
You could download the .debs from [here]("https://launchpad.net/~nuvola-player-builders/+archive/unstable/+build/2952005") and use alien to convert to rpm. Just a thought.

---

### Post by doppel.ganger on 2011-11-25
I mean the program previously named Google Music Frame. ;) Easy mistake to make.

---

### Post by azmyth on 2011-11-25
since it's trying to write a file to a directory that is owned by root, I believe you will need to run the install as root.

[kathryn@Kathryn-Fedora google-music-frame-0.3.2]$ sudo ./waf install

---

### Post by doppel.ganger on 2011-11-25
Thanks! I'll try that!

---

### Post by doppel.ganger on 2011-11-25
It worked! Thanks so much, azmyth!

---

