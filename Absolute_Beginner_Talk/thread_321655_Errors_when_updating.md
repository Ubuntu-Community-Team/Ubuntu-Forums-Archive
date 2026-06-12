---
title: "Errors when updating"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by meniscus on 2006-12-19
I was trying to download cedega a while ago in order to play games.  The website i used is here

[http://doc.gwos.org/index.php/CedegaCVSInstallation](http://doc.gwos.org/index.php/CedegaCVSInstallation)

I only got to step 2 in the end. Now everytime i go

```
sudo apt-get update 
```

I get the foillowing errors.

> Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
Ack!  Something bad happened while installing packages.  Trying to recover:
Setting up msttcorefonts (1.2ubuntu2) ...
warning: /usr/share/X11/fonts/truetype does not exist or is not a directory
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--14:43:56--  [http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.ex](http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.ex) e
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... 193.190.198.97
Connecting to belnet.dl.sourceforge.net|193.190.198.97|:80... connected.
HTTP request sent, awaiting response... Read error (Connection reset by peer) in  headers.
Giving up.

--14:47:05--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32](http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32). exe
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... 69.16.168.245
Connecting to easynews.dl.sourceforge.net|69.16.168.245|:80... connected.
HTTP request sent, awaiting response... Read error (Connection reset by peer) in  headers.
Giving up.

--14:50:15--  [http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32](http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32) .exe
           => `./andale32.exe'
Resolving twtelecom.dl.sourceforge.net... 207.250.4.12
Connecting to twtelecom.dl.sourceforge.net|207.250.4.12|:80... connected.
HTTP request sent, awaiting response... Read error (Connection reset by peer) in  headers.
Giving up.

--14:53:24--  [http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.ex](http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.ex) e
           => `./andale32.exe'
Resolving aleron.dl.sourceforge.net... 204.157.3.229
Connecting to aleron.dl.sourceforge.net|204.157.3.229|:80... connected.
HTTP request sent, awaiting response... Read error (Connection reset by peer) in headers.
Giving up.

















Can anything be done here?

---

### Post by bapoumba on 2006-12-19
hi,
you probably have to install msttcorefonts (multiverse repositories).

---

### Post by meniscus on 2006-12-19
When i type 

```
sudo apt-get install msttcorefonts
```

or go through synaptic manager 


i get the same error?

---

### Post by JShadow on 2006-12-19
It sounds like the package has a script to download the actual fonts from another site, maybe the files moved. I would suggest removing the package and trying to reinstall it.

---

### Post by meniscus on 2006-12-20
I tried reinstalling them but when i open synaptic it says 

dpkg was interupted. you must manually run 'dpkg --configure -a' to correct the problem.


Whats that about?

---

### Post by bapoumba on 2006-12-20
Then try **sudo dpkg --configure -a**, this will have dpkg try to configure the packages left unconfigured after installation :
[QUOTE=man dpkg] dpkg --configure package ... | -a | --pending
              Reconfigure an unpacked package. If -a  or  --pending  is  given
              instead  of  package, all unpacked but unconfigured packages are
              configured.

              Configuring consists of the following steps:

              1. Unpack the configuration files, and at the same time back  up
              the  old  configuration  files,  so that they can be restored if
              something goes wrong.

              2. Run postinst script, if provided by the package.
[/QUOTE]

---

### Post by meniscus on 2006-12-20
I did and got this message.





```
meniscus@meniscot:~$ sudo dpkg --configure -a
Password:
Setting up msttcorefonts (1.2ubuntu2) ...
warning: /usr/share/X11/fonts/truetype does not exist or is not a directory
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--12:02:47--  http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... 193.190.198.97
Connecting to belnet.dl.sourceforge.net|193.190.198.97|:80... connected.
HTTP request sent, awaiting response... Read error (Connection reset by peer) in headers.
Giving up.

--12:05:56--  http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... 69.16.168.245
Connecting to easynews.dl.sourceforge.net|69.16.168.245|:80... connected.
HTTP request sent, awaiting response... Read error (Connection reset by peer) in headers.
Giving up.

--12:09:06--  http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving twtelecom.dl.sourceforge.net... 207.250.4.12
Connecting to twtelecom.dl.sourceforge.net|207.250.4.12|:80... connected.
HTTP request sent, awaiting response... Read error (Connection reset by peer) in headers.
Giving up.

--12:12:15--  http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving aleron.dl.sourceforge.net... 204.157.3.229
Connecting to aleron.dl.sourceforge.net|204.157.3.229|:80... connected.
HTTP request sent, awaiting response... Read error (Connection reset by peer) in headers.
Giving up.

--12:15:24--  http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving cesnet.dl.sourceforge.net... 195.113.161.88
Connecting to cesnet.dl.sourceforge.net|195.113.161.88|:80... connected.
HTTP request sent, awaiting response... Read error (Connection reset by peer) in headers.
Giving up.

--12:18:34--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... 130.59.138.20, 2001:620:0:1b::20
Connecting to switch.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... Read error (Connection reset by peer) in headers.
Giving up.

andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
meniscus@meniscot:~$


```

What can i do?

---

### Post by bapoumba on 2006-12-20
Please post the output to **cat /etc/apt/sources.list**.

---

### Post by meniscus on 2007-01-10
Sorry for so long in replying. Im just back from holidays. 

Here is the output.


```
#deb cdrom:[Ubuntu 5.10 _dapper Badger_ - Release i386 (20051012)]/ dapper main restricted


## Uncomment the following two lines to fetch updated software from the network
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.# deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted

# deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

---

### Post by meniscus on 2007-01-11
Everythings sorted!

I downloaded a copy of msttcorefonts and placed it in the /usr/share/fonts/truetype folder and it fixed everything. Thanks for all your help

---

### Post by bapoumba on 2007-01-11
Well, I did not helped you that much. Nice to know you got it working, thanks :)

---

