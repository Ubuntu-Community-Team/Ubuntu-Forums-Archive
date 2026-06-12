---
title: "GDesklets installation"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by mohdridha on 2007-01-02
This is my 2nd try to install gdesklets by:
```

sudo aptitude remove gdesklets
sudo aptitude update
sudo aptitude install gdesklets

```


[email]kapla@mrn:~/.gdes[/email]klets/logs$ gdesklets &
[1] 26164
[email]kapla@mrn:~/.gdes[/email]klets/logs$ Starting gdesklets-daemon...
```
Cannot establish connection to daemon: timeout!
The log file might help you solving the problem.

```

[1]+  Exit 1                  gdesklets

[email]kapla@mrn:~/.gdes[/email]klets/logs$ ls
gdesklets%3A0.0.log
[email]kapla@mrn:~/.gdes[/email]klets/logs$ cat gdesklets%3A0.0.log
Log messages of /home/kapla/.gdesklets/logs/gdesklets%3A0.0.log

```

==========================================================[01/03/07-06:33:57]===
=== Unhandled error! Something bad and unexpected happened. ===

[EXC]No module named gtk
in /usr/lib/gdesklets/gdesklets-daemon: line 127 <module>
in /usr/lib/gdesklets/gdesklets-daemon: line 108 _gdesklets_main
in /usr/lib/gdesklets/main/__init__.py: line 114 init
in /usr/lib/gdesklets/utils/ErrorFormatter.py: line 118 _new_imp
[EXC]/usr/lib/gdesklets/utils/ErrorFormatter.py

[---]  113 # give us an absolute path.
[---]  114 #
[---]  115 _old_imp = __import__
[---]  116 def _new_imp(name, globs = {}, locls = {}, fromlist = []):
[---]  117
[ERR]> 118     module = _old_imp(name, globs, locls, fromlist)
[---]  119     # builtin modules have no "__file__" attribute, so we have to check for it
[---]  120     if (module):
[---]  121         if (hasattr(module, "__file__")):
[---]  122             module.__file__ = os.path.abspath(module.__file__)
[---]  123         return module
[---]  124     else:

```

kapla@mrn:~$ gdesklets check
Checking requirements:
 - sys ... found
 - xml.parsers.expat ... found
 - xml.sax ... found
 - gtk ... missing
Version check failed.

GTK python bindings (pygtk2) version >= 2.4.0 and GTK+ version >= 2.4.0 are required.

Please make sure that the required software is installed.
Also try to avoid having multiple versions of a library/binding on your system.
gDesklets won't work if you don't have all necessary dependencies installed
on your system.

THE STARTUP WILL BE CANCELLED NOW!

```


kapla@mrn:~/.gdesklets/logs$ sudo dpkg -l | grep gtk
ii  gtk2-engines-clearlooks                2.7.4.is.2.6.10-0ubuntu1                Clearlooks GTK+ 2.x engine and theme
ii  gtk2-engines-crux                      2.7.4.is.2.6.10-0ubuntu1                the Crux theme engine for GTK+ 2.x
ii  gtk2-engines-highcontrast              2.7.4.is.2.6.10-0ubuntu1                High contrast GTK+ 2.x theme engine
ii  gtk2-engines-industrial                2.7.4.is.2.6.10-0ubuntu1                'industrial' theme for GTK+ 2.x
ii  gtk2-engines-lighthouseblue            2.7.4.is.2.6.10-0ubuntu1                LighthouseBlue theme for GTK+ 2.x
ii  gtk2-engines-mist                      2.7.4.is.2.6.10-0ubuntu1                flat theme for GTK+ 2.x
ii  gtk2-engines-pixbuf                    2.8.20-0ubuntu1                         Pixbuf-based theme for GTK+ 2.x
ii  gtk2-engines-redmond95                 2.7.4.is.2.6.10-0ubuntu1                Windows-like theme for GTK+ 2.x
ii  gtk2-engines-smooth                    2.7.4.is.2.6.10-0ubuntu1                Smooth engine for GTK+ 2.x
ii  gtk2-engines-thinice                   2.7.4.is.2.6.10-0ubuntu1                the ThinIce theme engine for GTK+ 2.x
ii  gtk2-engines-ubuntulooks               0.9.11-1                                'ubuntulooks' theme for GTK+ 2.x
ii  gtkhtml3.8                             3.10.3-0ubuntu1                         HTML rendering/editing library - bonobo comp
ii  gtkorphan                              0.4.1-1                                 A graphical tool to find and remove orphaned
ii  libgdk-pixbuf2                         0.22.0-11                               The GdkPixBuf image library, gtk+ 1.2 versio
ii  libgtk1.2                              1.2.10-18                               The GIMP Toolkit set of widgets for X
ii  libgtk1.2-common                       1.2.10-18                               Common files for the GTK+ library
ii  libgtk2-gladexml-perl                  1.005-1                                 Perl interface to use user interfaces create
ii  libgtk2-perl                           1.102-1ubuntu1                          Perl interface to the 2.x series of the Gimp
ii  libgtk2.0-0                            2.8.20-0ubuntu1                         The GTK+ graphical user interface library
ii  libgtk2.0-bin                          2.8.20-0ubuntu1                         The programs for the GTK+ graphical user int
ii  libgtk2.0-common                       2.8.20-0ubuntu1                         Common files for the GTK+ graphical user int
ii  libgtk2.0-dev                          2.8.20-0ubuntu1                         Development files for the GTK+ library
ii  libgtkhtml2-0                          2.11.0-1                                HTML rendering/editing library - runtime fil
ii  libgtkhtml3.8-15                       3.10.3-0ubuntu1                         HTML rendering/editing library - runtime fil
ii  libgtksourceview-common                1.6.2-0ubuntu1                          common files for the GTK+ syntax highlightin
ii  libgtksourceview1.0-0                  1.6.2-0ubuntu1                          shared libraries for the GTK+ syntax highlig
ii  libgtkspell0                           2.0.10-3                                a spell-checking addon for GTK's TextView wi
ii  libwxgtk2.6-0                          2.6.1.2ubuntu2                          wxWidgets Cross-platform C++ GUI toolkit (GT
ii  openoffice.org-gtk                     2.0.2-2ubuntu12.1                       GTK Integration for OpenOffice.org (Widgets,
ii  python-gtk-1.2                         0.6.12-4ubuntu1                         GTK support module for Python
ii  python-gtk2                            2.8.6-0ubuntu1                          Python bindings for the GTK+ widget set
ii  python-gtk2-dev                        2.8.6-0ubuntu1                          GTK+ bindings: devel files
ii  python2.4-gtk2                         2.8.6-0ubuntu1                          Python bindings for the GTK+ widget set
ii  scim-gtk2-immodule                     1.4.4-1ubuntu12                         GTK+2 input method module with SCIM as backe
kapla@mrn:~/.gdesklets/logs$



kapla@mrn:~$ dpkg -l | grep python
ii  bicyclerepair                          0.9-4ubuntu1                            A refactoring tool for python
ii  diveintopython                         5.4-2ubuntu1                            free Python book for experienced programmers
ii  gimp-python                            2.2.11-1ubuntu3.1                       Python support and plugins for The GIMP
ii  python                                 2.4.2-0ubuntu3                          An interactive high-level object-oriented la
ii  python-adns                            1.0.0-6ubuntu4                          Python bindings to the asynchronous DNS reso
ii  python-apt                             0.6.16.2ubuntu8                         Python interface to libapt-pkg
ii  python-cddb                            1.4-4ubuntu1                            Python interface to CD-IDs and FreeDB
ii  python-clientcookie                    1.1.1-1ubuntu2                          Python module for automating HTTP Cookie man
ii  python-crypto                          2.0.1+dfsg1-1ubuntu1                    cryptographic algorithms and protocols for P
ii  python-dev                             2.4.2-0ubuntu3                          Header files and a static library for Python
ii  python-egenix-mxproxy                  2.0.6ubuntu1-1ubuntu4                   generic proxy wrapper type for Python [dummy
ii  python-egenix-mxstack                  2.0.6ubuntu1-1ubuntu4                   fast and memory-efficient stack for Python [
ii  python-egenix-mxtexttools              2.0.6ubuntu1-1ubuntu4                   fast text manipulation tools for Python [dum
ii  python-egenix-mxtools                  2.0.6ubuntu1-1ubuntu4                   collection of new builtins for Python [dummy
ii  python-epydoc                          2.1-9ubuntu2                            tool for generating Python API documentation
ii  python-eunuchs                         20050320.1ubuntu1                       Missing manly parts of UNIX API for Python
ii  python-examples                        2.4.2-0ubuntu3                          Examples for the Python language (default ve
ii  python-feedparser                      4.1-2ubuntu1                            Universal Feed Parser for Python
ii  python-gadfly                          1.0.0-8ubuntu4                          SQL database and parser generator for Python
ii  python-gd                              0.52.0-0ubuntu2                         Python module wrapper for libgd
ii  python-gdbm                            2.4.2-0ubuntu3                          GNU dbm database support for Python (default
ii  python-genetic                         0.1.1b-3ubuntu1                         genetic algorithms in Python
ii  python-geoip                           1.2.1-1ubuntu2                          python bindings for the GeoIP IP-to-country
ii  python-glade2                          2.8.6-0ubuntu1                          GTK+ bindings: Glade support
ii  python-gmenu                           2.14.3-0ubuntu1                         an implementation of the freedesktop menu sp
ii  python-gnome2                          2.12.4-0ubuntu1                         Python bindings for the GNOME desktop enviro
ii  python-gnome2-desktop                  2.14.0-0ubuntu2                         Python bindings for the GNOME desktop enviro
ii  python-gnome2-desktop-dev              2.14.0-0ubuntu2                         Python bindings for the GNOME desktop enviro
ii  python-gnome2-dev                      2.12.4-0ubuntu1                         Python bindings for the GNOME desktop enviro
ii  python-gnome2-extras                   2.14.0-0ubuntu3                         Python bindings for the GNOME desktop enviro
ii  python-gnupginterface                  0.3.2-7                                 Python interface to GnuPG (GPG)
ii  python-gobject-dev                     2.10.1-0ubuntu1                         GObject bindings: devel files
ii  python-gst0.10                         0.10.4-0ubuntu1                         generic media-playing framework (Python bind
ii  python-gtk-1.2                         0.6.12-4ubuntu1                         GTK support module for Python
ii  python-gtk2                            2.8.6-0ubuntu1                          Python bindings for the GTK+ widget set
ii  python-gtk2-dev                        2.8.6-0ubuntu1                          GTK+ bindings: devel files
ii  python-htmlgen                         2.2.2-10ubuntu3                         Python library for the generation of HTML
ii  python-htmltmpl                        1.22-5ubuntu3                           Templating engine for separation of code and
ii  python-id3lib                          0.5.1-6ubuntu2                          id3lib wrapper for Python - dummy package
ii  python-imaging                         1.1.5-4ubuntu1                          Python Imaging Library
ii  python-imaging-sane                    1.1.5-4ubuntu1                          Python Imaging Library SANE interface
ii  python-jabber                          0.5.0-1ubuntu3                          Python module for the Jabber instant messagi
ii  python-kjbuckets                       1.0.0-8ubuntu4                          Set and graph data types for Python [dummy p
ii  python-launchpad-integration           0.1.3                                   library for launchpad integration
ii  python-ldap                            2.0.4-1ubuntu4                          A LDAP interface module for Python. [dummy p
ii  python-libxml2                         2.6.24.dfsg-1ubuntu1                    Python bindings for the GNOME XML library
ii  python-minimal                         2.4.2-0ubuntu3                          A minimal subset of the Python language (def
ii  python-mysqldb                         1.2.1c3-4ubuntu4                        A Python interface to MySQL
ii  python-netcdf                          2.4.9-3ubuntu2                          A netCDF interface for Python
ii  python-newt                            0.51.6-31ubuntu1                        A NEWT module for Python
ii  python-numeric                         24.2-1ubuntu2                           Numerical (matrix-oriented) Mathematics for
ii  python-orbit                           0.3.1-12ubuntu1                         Python bindings for ORBit
ii  python-pam                             0.4.2-10.1ubuntu4                       A Python interface to the PAM library
ii  python-parted                          0.11.2ubuntu4                           Python bindings for GNU Parted
ii  python-pexpect                         0.999-5ubuntu2                          Python module for automating interactive app
ii  python-pgsql                           2.4.0-6ubuntu3                          A Python DB-API 2.0 interface to PostgreSQL
ii  python-pisock                          0.11.8-17                               Python module to communicate with PalmOS PDA
ii  python-pqueue                          0.2-6ubuntu1                            a priority queue extension for Python
ii  python-pyao                            0.82-1ubuntu1                           A Python interface to the Audio Output libra
ii  python-pylibacl                        0.2.1-2ubuntu4                          module for manipulating POSIX.1e ACLs
ii  python-pyogg                           1.3-1ubuntu1                            A Python interface to the Ogg library
ii  python-pyopenssl                       0.6-2ubuntu3                            Python wrapper around the OpenSSL library (d
ii  python-pyorbit                         2.14.1-0ubuntu1                         A Python language binding for the ORBit2 COR
ii  python-pyorbit-dev                     2.14.1-0ubuntu1                         PyORBit: development files
ii  python-pyvorbis                        1.3-1ubuntu1                            A Python interface to the Ogg Vorbis library
ii  python-pyxattr                         0.2-2ubuntu4                            module for manipulating filesystem extended
ii  python-reportlab                       1.20debian-3ubuntu1                     ReportLab library to create PDF documents us
ii  python-simpletal                       4.1-2ubuntu1                            Simple TAL, TALES and METAL implementation
ii  python-soappy                          0.11.3-1.4ubuntu3                       SOAP Support for Python (SOAP.py)
ii  python-sqlite                          1.0.1-4ubuntu1                          python interface to SQLite 2
ii  python-stats                           0.6-5ubuntu1                            A collection of statistical functions for Py
ii  python-syck                            0.55-3ubuntu3                           YAML parser kit -- python bindings (default
ii  python-tk                              2.4.2-0ubuntu3                          Tkinter - Writing Tk applications with Pytho
ii  python-unit                            1.4.1-9ubuntu4                          unit test framework for Python (default vers
ii  python-uno                             2.0.2-2ubuntu12.1                       Python interface for OpenOffice.org
ii  python-vte                             0.12.2-0ubuntu1                         Python bindings for the VTE widget set
ii  python-xdg                             0.15-1ubuntu5                           A python library to access freedesktop.org s
ii  python-xml                             0.8.4-1ubuntu3                          XML tools for Python [dummy package]
ii  python-xmms                            2.06-3ubuntu1                           Python interface to XMMS
ii  python-xmpp                            0.2-rc3-1ubuntu1                        Python library for communication with XMPP (
ii  python2.4                              2.4.3-0ubuntu6                          An interactive high-level object-oriented la
ii  python2.4-adns                         1.0.0-6ubuntu4                          A Python 2.4 interface to the asynchronous D
ii  python2.4-apt                          0.6.16.2ubuntu8                         Python interface to libapt-pkg
ii  python2.4-cairo                        1.0.2-1ubuntu1                          Python 2.4 language bindings for the Cairo v
ii  python2.4-clientcookie                 1.1.1-1ubuntu2                          Python 2.4.x module for automating HTTP cook
ii  python2.4-crypto                       2.0.1+dfsg1-1ubuntu1                    cryptographic algorithms and protocols for P
ii  python2.4-dbus                         0.60-6ubuntu8                           simple interprocess messaging system (Python
ii  python2.4-dev                          2.4.3-0ubuntu6                          Header files and a static library for Python
ii  python2.4-dictclient                   1.0.2ubuntu1                            Python client library for DICT (RFC2229) pro
ii  python2.4-egenix-mxdatetime            2.0.6ubuntu1-1ubuntu4                   date and time handling routines for Python 2
ii  python2.4-egenix-mxproxy               2.0.6ubuntu1-1ubuntu4                   generic proxy wrapper type for Python 2.4
ii  python2.4-egenix-mxstack               2.0.6ubuntu1-1ubuntu4                   fast and memory-efficient stack for Python 2
ii  python2.4-egenix-mxtexttools           2.0.6ubuntu1-1ubuntu4                   fast text manipulation tools for Python 2.4
ii  python2.4-egenix-mxtools               2.0.6ubuntu1-1ubuntu4                   collection of new builtins for Python 2.4
ii  python2.4-epydoc                       2.1-9ubuntu2                            tool for generating Python API documentation
ii  python2.4-eunuchs                      20050320.1ubuntu1                       Missing manly parts of UNIX API for Python
ii  python2.4-examples                     2.4.3-0ubuntu6                          Examples for the Python language (v2.4)
ii  python2.4-gadfly                       1.0.0-8ubuntu4                          SQL database and parser generator for Python
ii  python2.4-gd                           0.52.0-0ubuntu2                         Python module wrapper for libgd
ii  python2.4-gdbm                         2.4.3-0ubuntu6                          GNU dbm database support for Python (v2.4)
ii  python2.4-geoip                        1.2.1-1ubuntu2                          python bindings for the GeoIP IP-to-country
ii  python2.4-glade2                       2.8.6-0ubuntu1                          GTK+ bindings: Glade support
ii  python2.4-gnome2                       2.12.4-0ubuntu1                         Python bindings for the GNOME desktop enviro
ii  python2.4-gnome2-desktop               2.14.0-0ubuntu2                         Python bindings for the GNOME desktop enviro
ii  python2.4-gnome2-extras                2.14.0-0ubuntu3                         Python bindings for the GNOME desktop enviro
ii  python2.4-gobject                      2.10.1-0ubuntu1                         Python bindings for the GObject
ii  python2.4-gtk2                         2.8.6-0ubuntu1                          Python bindings for the GTK+ widget set
ii  python2.4-htmlgen                      2.2.2-10ubuntu3                         Generation of HTML documents with Python scr
ii  python2.4-htmltmpl                     1.22-5ubuntu3                           Templating engine for separation of code and
ii  python2.4-id3lib                       0.5.1-6ubuntu2                          id3lib wrapper for Python - library
ii  python2.4-imaging                      1.1.5-4ubuntu1                          Python Imaging Library
ii  python2.4-imaging-sane                 1.1.5-4ubuntu1                          Python Imaging Library SANE interface
ii  python2.4-jabber                       0.5.0-1ubuntu3                          Python module for the Jabber instant messagi
ii  python2.4-kjbuckets                    1.0.0-8ubuntu4                          Set and graph data types for Python 2.4
ii  python2.4-ldap                         2.0.4-1ubuntu4                          A LDAP interface module for Python 2.4
ii  python2.4-librdf                       1.0.2.1-1ubuntu5                        Python 2.4 language bindings for the Redland
ii  python2.4-libxml2                      2.6.24.dfsg-1ubuntu1                    Python 2.4 bindings for the GNOME XML librar
ii  python2.4-libxslt1                     1.1.15-1ubuntu1                         Python 2.4 bindings for libxslt1
ii  python2.4-minimal                      2.4.3-0ubuntu6                          A minimal subset of the Python language (ver
ii  python2.4-mysqldb                      1.2.1c3-4ubuntu4                        A Python interface to MySQL
ii  python2.4-numeric                      24.2-1ubuntu2                           Numerical (matrix-oriented) Mathematics for
ii  python2.4-pam                          0.4.2-10.1ubuntu4                       A Python interface to the PAM library
ii  python2.4-pexpect                      0.999-5ubuntu2                          Python 2.4.x module for automating interacti
ii  python2.4-pgsql                        2.4.0-6ubuntu3                          A Python DB-API 2.0 interface to PostgreSQL
ii  python2.4-pycurl                       7.15.0-1ubuntu1                         Python bindings to libcurl
ii  python2.4-pylibacl                     0.2.1-2ubuntu4                          module for manipulating POSIX.1e ACLs
ii  python2.4-pyopenssl                    0.6-2ubuntu3                            Python wrapper around the OpenSSL library, e
ii  python2.4-pyorbit                      2.14.1-0ubuntu1                         A Python language binding for the ORBit2 COR
ii  python2.4-pyxattr                      0.2-2ubuntu4                            module for manipulating filesystem extended
ii  python2.4-reportlab                    1.20debian-3ubuntu1                     ReportLab library to create PDF documents us
ii  python2.4-simpletal                    4.1-2ubuntu1                            Simple TAL, TALES and METAL implementation,
ii  python2.4-soappy                       0.11.3-1.4ubuntu3                       SOAP Support for Python (SOAP.py)
ii  python2.4-sqlite                       1.0.1-4ubuntu1                          python interface to SQLite 2
ii  python2.4-syck                         0.55-3ubuntu3                           YAML parser kit -- Python 2.4 bindings
ii  python2.4-tk                           2.4.3-0ubuntu6                          Tkinter - Writing Tk applications with Pytho
ii  python2.4-unit                         1.4.1-9ubuntu4                          PyUnit -- Unit test framework for Python (2.
ii  python2.4-xml                          0.8.4-1ubuntu3                          XML tools for Python (2.4.x)
ii  python2.4-xmms                         2.06-3ubuntu1                           Python interface to XMMS (Python 2.4 version
ii  python2.4-xmpp                         0.2-rc3-1ubuntu1                        Python library for communication with XMPP (


```

So much things i have installed during the first tries, including compiling a whole package of Python from source (in which i dunno how to uninstall them)..

---

