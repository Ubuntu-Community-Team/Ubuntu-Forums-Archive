---
title: "msttcorefonts installation problem"
date: 2006-01-31
forum: Absolute Beginner Talk
---

### Post by spime23 on 2006-01-31
Hi,

I am behind a proxy and also configure proxy settings for gnome and synaptic. Now problem is that apt downloads the main package from the repositories, but then it fails to download the various .exe files from the sourceforge mirrors.

```

apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree... Done
msttcorefonts is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up msttcorefonts (1.2ubuntu2) ...
warning: /usr/share/X11/fonts/truetype does not exist or is not a directory
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--11:14:17--  http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving proxy.XXXX.ac.in... 172.31.1.210
Connecting to proxy.XXXX.ac.in|172.31.1.210|:3128... connected.
Proxy request sent, awaiting response... 407 Proxy Authentication Required
11:14:17 ERROR 407: Proxy Authentication Required.

...........
..........
..........

--11:14:18--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving proxy.XXXX.ac.in... 172.31.1.210
Connecting to proxy.XXXX.ac.in|172.31.1.210|:3128... connected.
Proxy request sent, awaiting response... 407 Proxy Authentication Required
11:14:18 ERROR 407: Proxy Authentication Required.

andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

``` 

I have already read the following threads:
[http://ubuntuforums.org/showthread.php?t=75413](http://ubuntuforums.org/showthread.php?t=75413)
[http://ubuntuforums.org/archive/index.php/t-76655.html](http://ubuntuforums.org/archive/index.php/t-76655.html)

so please dont redirect me there.

I want to know some fresh idea.
Please help.

---

### Post by mstlyevil on 2006-01-31
[QUOTE=spime23]Hi,

I am behind a proxy and also configure proxy settings for gnome and synaptic. Now problem is that apt downloads the main package from the repositories, but then it fails to download the various .exe files from the sourceforge mirrors.

```

apt-get install msttcorefonts
Reading package lists... Done
Building dependency tree... Done
msttcorefonts is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up msttcorefonts (1.2ubuntu2) ...
warning: /usr/share/X11/fonts/truetype does not exist or is not a directory
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--11:14:17--  http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving proxy.XXXX.ac.in... 172.31.1.210
Connecting to proxy.XXXX.ac.in|172.31.1.210|:3128... connected.
Proxy request sent, awaiting response... 407 Proxy Authentication Required
11:14:17 ERROR 407: Proxy Authentication Required.

...........
..........
..........

--11:14:18--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving proxy.XXXX.ac.in... 172.31.1.210
Connecting to proxy.XXXX.ac.in|172.31.1.210|:3128... connected.
Proxy request sent, awaiting response... 407 Proxy Authentication Required
11:14:18 ERROR 407: Proxy Authentication Required.

andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

``` 

I have already read the following threads:
[http://ubuntuforums.org/showthread.php?t=75413](http://ubuntuforums.org/showthread.php?t=75413)
[http://ubuntuforums.org/archive/index.php/t-76655.html](http://ubuntuforums.org/archive/index.php/t-76655.html)

so please dont redirect me there.

I want to know some fresh idea.
Please help.[/QUOTE]

Did you try using Automatix to do it for you? If you have no problem with using Automatix, try that and see if it does not fix the issue.

[Automatix]("http://ubuntuforums.org/showthread.php?t=66563")

---

### Post by spime23 on 2006-01-31
I have already tried automatix. But same problem exists. May be i can not set proxy for my username. 

Thankx for your kind advice.

---

### Post by nkayesmith on 2007-01-09
I have repackaged msttcorefonts with a few bugfixes. My package is available at [http://download.formationos.net/](http://download.formationos.net/) - it fixed my problems, so you might want to try it.

---

