---
title: "Installing a non synaptic program"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by keheikev on 2006-05-25
Hi all,
I want to install gpodder. I downloaded the gpodder_0.7-1ubuntu1_all.deb file from [http://perli.net/projekte/gpodder/downloads.html](http://perli.net/projekte/gpodder/downloads.html) . I was looking at this how to site 
[http://www.psychocats.net/ubuntu/installingsoftware.php](http://www.psychocats.net/ubuntu/installingsoftware.php) but I want to make sure I install the file to this directory /opt will this code do what I want

[HTML] code
cd Desktop
sudo dpkg -i gpodder_0.7-1ubuntu1_all.deb[/HTML]

Which I clipped from the web page.
TIA
Keheikev
:KS I wont give up if you dont!

---

### Post by aysiu on 2006-05-25
If you install a .deb, the application usually lives in the /usr directory somewhere, not /opt.

Any reason in particular you want it in /opt?

---

### Post by keheikev on 2006-05-25
Yes,
I thought thats where programs are supposed to be installed...
Keheikev
a how come your online lite is always out aysiu?

---

### Post by Sef on 2006-05-25
> how come your online lite is always out aysiu?

How come your on all the time aysiu? Is that what you mean?

If it is, the answer is simple: clones.  There is a clone for 8-4, another for 4-12, and another one for 12-8, thus 24 hour coverage. :lol:

---

### Post by aysiu on 2006-05-25
[QUOTE=Sef]How come your on all the time aysiu? Is that what you mean?

If it is, the answer is simple: clones.  There is a clone for 8-4, another for 4-12, and another one for 12-8, thus 24 hour coverage. :lol:[/QUOTE] I have Ubuntu elves...

---

### Post by keheikev on 2006-05-25
Cute anyway  I was wrong after reading a bit more I see that the install needs to go to /usr/local for stuff not in the official distrubution. My source is 

 [http://linuxcommand.org/lts0040.php](http://linuxcommand.org/lts0040.php) what exactly in my above command installs it to that /usr/local directory? Is that just the default install path for sudo dpkg -i ?
Keheikev
:KS I wont give up if you dont!

---

### Post by aysiu on 2006-05-25
[QUOTE=keheikev]Cute anyway  I was wrong after reading a bit more I see that the install needs to go to /usr/local for stuff not in the official distrubution. My source is 

 [http://linuxcommand.org/lts0040.php](http://linuxcommand.org/lts0040.php) what exactly in my above command installs it to that /usr/local directory? Is that just the default install path for sudo dpkg -i ?
Keheikev
:KS I wont give up if you dont![/QUOTE] I'm just not understanding what your preoccupation is with *where* the program gets installed. If you type ```
sudo dpkg -i *programname*.deb
``` it installs the same way as a program installed through Synaptic Package Manager does--the only difference is that you needed to download the .deb manually, and the dependencies do not get resolved automatically.

---

### Post by keheikev on 2006-05-25
[QUOTE=aysiu]I'm just not understanding what your preoccupation is with *where* the program gets installed. If you type ```
sudo dpkg -i *programname*.deb
``` it installs the same way as a program installed through Synaptic Package Manager does--the only difference is that you needed to download the .deb manually, and the dependencies do not get resolved automatically.[/QUOTE]
I guess my  caution comes from relying on different sources of information. I wanted to make sure I was installing correctly. Anyway the application is installed but now I need to get rid of it as when I put in a channel [http://twit.tv.net](http://twit.tv.net) it errored out and will not not come up with the gui...this after reinstalling. gpodder_0.7-1ubuntu1_all.deb

raceback (most recent call last):
  File "/usr/bin/gpodder", line 141, in ?
    sys.exit(main())
  File "/usr/bin/gpodder", line 137, in main
    gpodder.main( __version__)
  File "/usr/lib/python2.4/site-packages/gpodder/gpodder.py", line 979, in main
    g_podder = Gpodder()
  File "/usr/lib/python2.4/site-packages/gpodder/gpodder.py", line 108, in __init__
    SimpleGladeApp.__init__(self, path, root, domain, **kwargs)
  File "/usr/lib/python2.4/site-packages/gpodder/SimpleGladeApp.py", line 108, in __init__
    self.new()
  File "/usr/lib/python2.4/site-packages/gpodder/gpodder.py", line 169, in new
    self.channels = reader.read( False)
  File "/usr/lib/python2.4/site-packages/gpodder/libgpodder.py", line 315, in read
    parser.parse( gPodderLib().getChannelsFilename())
  File "/usr/lib/python2.4/site-packages/_xmlplus/sax/expatreader.py", line 109, in parse
    xmlreader.IncrementalParser.parse(self, source)
  File "/usr/lib/python2.4/site-packages/_xmlplus/sax/xmlreader.py", line 125, in parse
    self.close()
  File "/usr/lib/python2.4/site-packages/_xmlplus/sax/expatreader.py", line 226, in close
    self.feed("", isFinal = 1)
  File "/usr/lib/python2.4/site-packages/_xmlplus/sax/expatreader.py", line 220, in feed
    self._err_handler.fatalError(exc)
  File "/usr/lib/python2.4/site-packages/_xmlplus/sax/handler.py", line 38, in fatalError
    raise exception
xml.sax._exceptions.SAXParseException: /home/kevin/.config/gpodder/channels.xml:3:0: no element found
Thats what comes up in terminal when I type in gpodder now.
Keheikev

---

### Post by Sef on 2006-05-25
Are you using Breezy or Dapper?

---

### Post by keheikev on 2006-05-25
breezy

---

### Post by keheikev on 2006-05-26
Well  removed the install with
> code
sudo apt-get remove gpodder
I guess I could remove the configuration files with sudo apt-get remove --purge gpodder and then attempt the reinstall. I think what I gave the program as input broke it...I could use the check-install  to see if there is something missing 
Keheikev
:KS si tiempo para gustual (and the time to enjoy them)

---

