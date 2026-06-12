---
title: "Cannot install/uninstall msttcorefonts"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by danteman on 2007-10-21
Hi,
I miserably fail this simple task...
What could be wrong. Please help!
/D

sudo aptitude purge msttcorefonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages will be REMOVED:
  msttcorefonts{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 193kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 90466 files and directories currently installed.)
Removing msttcorefonts ...
W: /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Andale_Mono.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Webdings.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Black.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Impact.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Italic.ttf: not registered.
dpkg: error processing msttcorefonts (--purge):
 subprocess pre-removal script returned error exit status 1

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--10:03:01--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving surfnet.dl.sourceforge.net... failed: Connection timed out.
--10:03:11--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving internap.dl.sourceforge.net... failed: Connection timed out.
--10:03:21--  [http://puzzle.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://puzzle.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving puzzle.dl.sourceforge.net... failed: Connection timed out.
--10:03:31--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving heanet.dl.sourceforge.net... failed: Connection timed out.
--10:03:41--  [http://superb-west.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://superb-west.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving superb-west.dl.sourceforge.net... failed: Connection timed out.
--10:03:51--  [http://superb-east.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://superb-east.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving superb-east.dl.sourceforge.net... failed: Connection timed out.
--10:04:01--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Connection timed out.
--10:04:11--  [http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving jaist.dl.sourceforge.net... failed: Connection timed out.
--10:04:21--  [http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving mesh.dl.sourceforge.net... failed: Connection timed out.
--10:04:31--  [http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving nchc.dl.sourceforge.net... failed: Connection timed out.
--10:04:41--  [http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving kent.dl.sourceforge.net... failed: Connection timed out.
--10:04:51--  [http://umn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://umn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving umn.dl.sourceforge.net... failed: Connection timed out.
--10:05:01--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Connection timed out.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done

---

### Post by mikeyphi on 2007-10-21
What happens when you try to remove or reinstall using Synaptic?

---

### Post by danteman on 2007-10-21
Same thing happens. BTW: I'm running Gutsy. I've tried to remove, reinstall with and without synaptic. /D

---

### Post by LanDan on 2007-10-21
you can always do it manually

cd /usr/share/fonts/truetype/

sudo rm -r msttcorefonts

---

### Post by mikeyphi on 2007-10-21
See if 'sudo dpkg --configure -a' clears the problem

---

### Post by danteman on 2007-10-21
Same problem I'm afraid.

---

### Post by mikeyphi on 2007-10-21
any joy with #4?

---

### Post by danteman on 2007-10-21
Nope. It says: rm: cannot remove `msttcorefonts': No such file or directory

The content of above dir is 
arphic    openoffice    ttf-bitstream-vera  ttf-indic-fonts-core  ttf-mgopen
freefont  thai          ttf-dejavu          ttf-lao               unfonts
kochi     ttf-arabeyes  ttf-gentium         ttf-malayalam-fonts

---

### Post by LanDan on 2007-10-21
????

the directory msttcorefonts is there but you can not remove it?

---

### Post by danteman on 2007-10-21
It's not there.

---

### Post by LanDan on 2007-10-21
then why are you trying to remove it? :confused:

---

### Post by danteman on 2007-10-21
The problem is that I was trying to install something else (don't rember what now...) but msttcorefonts was needed. I tried to install msttcorefonts but got error message:

--10:03:01-- [http://surfnet.dl.sourceforge.net/so...s/andale32.exe](http://surfnet.dl.sourceforge.net/so...s/andale32.exe)
=> `./andale32.exe'
Resolving surfnet.dl.sourceforge.net... failed: Connection timed out.
--10:03:11-- [http://internap.dl.sourceforge.net/s...s/andale32.exe](http://internap.dl.sourceforge.net/s...s/andale32.exe)
=> `./andale32.exe'
Resolving internap.dl.sourceforge.net... failed: Connection timed out.
--10:03:21-- [http://puzzle.dl.sourceforge.net/sou...s/andale32.exe](http://puzzle.dl.sourceforge.net/sou...s/andale32.exe)
=> `./andale32.exe'
Resolving puzzle.dl.sourceforge.net... failed: Connection timed out.
--10:03:31-- [http://heanet.dl.sourceforge.net/sou...s/andale32.exe](http://heanet.dl.sourceforge.net/sou...s/andale32.exe)
=> `./andale32.exe'

... and so on
I've tried to install, reinstall using both synaptic and commandline, but I get stuck with the same problem: Connection time out 
/D

---

### Post by LanDan on 2007-10-21
mmmm

it simply seems that somehow you could't connect to these servers, i have just tried now and it works perfectly


can you give it another try?

---

### Post by mikeyphi on 2007-10-21
I might see a light!!!

Open Software sources - make sure third party repos are all deselected
then use Synaptic to install msttcorefonts

---

### Post by danteman on 2007-10-21
LanDan: I've given this alot of tries.
mikeyphi: Tried what you suggested, but same problem.

---

### Post by LanDan on 2007-10-21
the links you posted above are not the complete path so i can't check but they should be ok

it stoppes when trying to resolve the sourceforge site so this could also be a dns problem somehow, although it would be strange if it only could not find the sourceforge site.


when happens when you open the link from the terminal in firefox?

---

### Post by ed_d on 2007-10-21
Ive run ito the same problem while installing those fonts on almost all distros of Ubuntu. What eventually will happen is that it will finally find that server and install. be patient and it will load.

---

### Post by danteman on 2007-10-21
If I do that I can download the file. Is it possible to use this locally stored file instead?

---

### Post by danteman on 2007-10-21
Here are some of the other things I've tried so far:

sudo dpkg-reconfigure fontconfig
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoclean

/D

---

### Post by mikeyphi on 2007-10-21
> **danteman said:**
> If I do that I can download the file. Is it possible to use this locally stored file instead?

What's the full name of this file?

---

### Post by danteman on 2007-10-21
> **mikeyphi said:**
> What's the full name of this file?

[http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)

---

### Post by mikeyphi on 2007-10-21
> **danteman said:**
> [http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)

As far as I know - it is not possible to directly use an *.exe program in Ubuntu.
However that still doesn't get round the basic problem of not being to install through Synaptic!!
More thought required!

---

### Post by danteman on 2007-10-21
> **mikeyphi said:**
> As far as I know - it is not possible to directly use an *.exe program in Ubuntu.
However that still doesn't get round the basic problem of not being to install through Synaptic!!
More thought required!

Indeed. I'm very greatful for everything that might help! /D

---

### Post by mikeyphi on 2007-10-21
Could you post the content of /etc/apt/sources.list

---

### Post by danteman on 2007-10-21
> **mikeyphi said:**
> Could you post the content of /etc/apt/sources.list

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [ftp://ftp.tudelft.nl/pub/Linux/archive.ubuntu.com/](ftp://ftp.tudelft.nl/pub/Linux/archive.ubuntu.com/) gutsy main universe restricted multiverse
deb-src [ftp://ftp.tudelft.nl/pub/Linux/archive.ubuntu.com/](ftp://ftp.tudelft.nl/pub/Linux/archive.ubuntu.com/) gutsy universe main multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb-src [ftp://ftp.tudelft.nl/pub/Linux/archive.ubuntu.com/](ftp://ftp.tudelft.nl/pub/Linux/archive.ubuntu.com/) gutsy-security universe main multiverse restricted
deb [ftp://ftp.tudelft.nl/pub/Linux/archive.ubuntu.com/](ftp://ftp.tudelft.nl/pub/Linux/archive.ubuntu.com/) gutsy-updates universe main multiverse restricted
deb-src [ftp://ftp.tudelft.nl/pub/Linux/archive.ubuntu.com/](ftp://ftp.tudelft.nl/pub/Linux/archive.ubuntu.com/) gutsy-updates universe main multiverse restricted
deb [ftp://ftp.tudelft.nl/pub/Linux/archive.ubuntu.com/](ftp://ftp.tudelft.nl/pub/Linux/archive.ubuntu.com/) gutsy-backports universe main multiverse restricted
deb-src [ftp://ftp.tudelft.nl/pub/Linux/archive.ubuntu.com/](ftp://ftp.tudelft.nl/pub/Linux/archive.ubuntu.com/) gutsy-backports universe main multiverse restricted
deb [ftp://ftp.tudelft.nl/pub/Linux/archive.ubuntu.com/](ftp://ftp.tudelft.nl/pub/Linux/archive.ubuntu.com/) gutsy-proposed universe main multiverse restricted
deb-src [ftp://ftp.tudelft.nl/pub/Linux/archive.ubuntu.com/](ftp://ftp.tudelft.nl/pub/Linux/archive.ubuntu.com/) gutsy-proposed universe main multiverse restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by LanDan on 2007-10-21
well,

i was born next to the university where those repo's are, but its not a sources problem.

the problem is your connection to the sourceforge server where the fonts are located

---

### Post by danteman on 2007-10-21
> **LanDan said:**
> well,

i was born next to the university where those repo's are, but its not a sources problem.

the problem is your connection to the sourceforge server where the fonts are located

So, any suggestions of how to proceed?

---

### Post by LanDan on 2007-10-21
lets try to find out where to problem may be.

the msttcorefonts package downloaded from the ubuntu repo is basically a script that will automatically downloads the .exe files with the fonts from the various servers.

it seems to stop while resolving sourceforge.net

what happens if you do this?
ping nchc.dl.sourceforge.net

---

### Post by danteman on 2007-10-21
> **LanDan said:**
> well,

i was born next to the university where those repo's are, but its not a sources problem.

the problem is your connection to the sourceforge server where the fonts are located

I actually have some trouble with the network. After each boot I have to run the commands:
sudo /etc/init.d/networking restart
sudo ifdown ath0
sudo ifup ath0

and after disabling ivp6 the speed is improved. I have a static IP (and wifi) and I read somewhere that  network manager is unable to handle this? how should I go about checking the network? Maybe thats a newbie question, but hey! that's what I am! 
Just for a few minutes ago the network went down and I had to run 
sudo ifup ath0 

to get it running.
Any thoughts?

---

### Post by LanDan on 2007-10-21
wich dns server do you use?

---

### Post by danteman on 2007-10-21
> **LanDan said:**
> lets try to find out where to problem may be.

the msttcorefonts package downloaded from the ubuntu repo is basically a script that will automatically downloads the .exe files with the fonts from the various servers.

it seems to stop while resolving sourceforge.net

what happens if you do this?
ping nchc.dl.sourceforge.net

ping nchc.dl.sourceforge.net
PING nchc.dl.sourceforge.net (211.79.61.10) 56(84) bytes of data.
64 bytes from sourceforge.nchc.org.tw (211.79.61.10): icmp_seq=1 ttl=35 time=338 ms
64 bytes from sourceforge.nchc.org.tw (211.79.61.10): icmp_seq=2 ttl=35 time=337 ms
64 bytes from sourceforge.nchc.org.tw (211.79.61.10): icmp_seq=3 ttl=35 time=336 ms
64 bytes from sourceforge.nchc.org.tw (211.79.61.10): icmp_seq=4 ttl=35 time=340 ms
64 bytes from sourceforge.nchc.org.tw (211.79.61.10): icmp_seq=5 ttl=35 time=337 ms
64 bytes from sourceforge.nchc.org.tw (211.79.61.10): icmp_seq=6 ttl=35 time=338 ms
64 bytes from sourceforge.nchc.org.tw (211.79.61.10): icmp_seq=7 ttl=35 time=338 ms
64 bytes from sourceforge.nchc.org.tw (211.79.61.10): icmp_seq=8 ttl=35 time=337 ms
64 bytes from sourceforge.nchc.org.tw (211.79.61.10): icmp_seq=9 ttl=35 time=337 ms
...
that seems like slow respones right?

---

### Post by danteman on 2007-10-21
> **LanDan said:**
> wich dns server do you use?

From /etc/resolve.conf

nameserver 195.54.122.201
nameserver 195.54.122.204

---

### Post by LanDan on 2007-10-21
the connection seems OK to me

what happens if you do this
wget [http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)

---

### Post by danteman on 2007-10-21
> **LanDan said:**
> the connection seems OK to me

what happens if you do this
wget [http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)

 wget [http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
--18:17:17--  [http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `andale32.exe'
Resolving nchc.dl.sourceforge.net... 211.79.61.10, 2001:e10:5c00:1::10
Connecting to nchc.dl.sourceforge.net|211.79.61.10|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 198,384 (194K) [application/octet-stream]

100%[======================================================================================>] 198,384       93.42K/s             

18:17:30 (93.30 KB/s) - `andale32.exe' saved [198384/198384]

---

### Post by LanDan on 2007-10-21
mmmm now it is annoying ;)

i don't get it

---

### Post by danteman on 2007-10-21
> **LanDan said:**
> mmmm now it is annoying ;)

i don't get it

I second that! Maybe I'm better off running Opensuse, which I did some time ago. Never had this kind of problem.

---

### Post by LanDan on 2007-10-21
well..

i did, but that was many years ago, you could select the corefonts during install in YAST and it always used to hang on me.

if i were you i would give it a day and try another time tomorrow, it might as well be that a lot of people are hitting that mirror cause of the new gutsy release ;)

---

### Post by danteman on 2007-10-21
> **LanDan said:**
> well..

i did, but that was many years ago, you could select the corefonts during install in YAST and it always used to hang on me.

if i were you i would give it a day and try another time tomorrow, it might as well be that a lot of people are hitting that mirror cause of the new gutsy release ;)

Maybe you're right. In the mean time I gonna try to resolve the problem with the network going down. I just had to run

sudo ifup ath0

again. This is possibly even more annoying...

---

### Post by mikeyphi on 2007-10-21
During #34 you managed to download the exe file you also need the cabextract file.
If your connection is now working try using Synaptic again.
I just downloaded and installed msttcorefonts using Synaptic - only difference to your setup is that I use the GB mirror (http) rather than your (ftp) - but that shouldn't be an issue.

---

### Post by danteman on 2007-10-21
> **mikeyphi said:**
> During #34 you managed to download the exe file you also need the cabextract file.
If your connection is now working try using Synaptic again.
I just downloaded and installed msttcorefonts using Synaptic - only difference to your setup is that I use the GB mirror (http) rather than your (ftp) - but that shouldn't be an issue.

Still not working...

---

### Post by danteman on 2007-10-21
Problem solved!!!!!!! 
I changed the nameservers to opendns.
Thanks alot everyone who tried to solve my problem!

/D

---

### Post by ader10 on 2007-10-21
I'm having the same problem, and I don't have a /etc/resolve.conf. I did a sudo vim /etc/resolve.conf and put in "opendns 195.54.122.201" and :wq

Nothing changes... Help?

---

### Post by LanDan on 2007-10-21
in /etc/resolv.conf you have to write it like this

nameserver 195.54.122.201

---

### Post by danteman on 2007-10-21
> **ader10 said:**
> I'm having the same problem, and I don't have a /etc/resolve.conf. I did a sudo vim /etc/resolve.conf and put in "opendns 195.54.122.201" and :wq

Nothing changes... Help?

The openDNS should be:

nameserver 208.67.220.220
nameserver 208.67.222.222

---

### Post by LanDan on 2007-10-21
also watch the spelling /etc/resolv.conf

it is RESOLV.CONF

---

### Post by ader10 on 2007-10-21
It still fails. Help?

---

### Post by Nick Fedchik on 2007-10-22
Peoples!!!!
It's not an .exe problem (actually it's self-extracted CAB)
It's not a DNS problem.

The problem is in wget here: (see the /var/lib/dpkg/info/msttcorefonts.postinst file)

```
if ! wget --continue --tries=1 --dns-timeout=10 --connect-timeout=5 --read-timeout=300 $QUIET_ARG --directory-prefix . --no-directories --no-background $URLROOT$ff ; then
```

I guess than it's a kind of changes in new wget that unable to work with lots of pre-defined params.
Hope than msttcorefonts package maintainer solve the problem ASAP.
I solve it by change that big line by short 
```
wget $URLROOT$ff
```

---

### Post by ader10 on 2007-10-22
Thank you very much, Nick!

To clarify what he said, you replace the code
```
wget --continue --tries=1 --dns-timeout=10 --connect-timeout=5 --read-timeout=300 $QUIET_ARG --directory-prefix . --no-directories --no-background $URLROOT$ff
```
with
```
wget $URLROOT$ff
```
instead of the entire line of code.

---

### Post by danteman on 2007-10-22
> **Nick Fedchik said:**
> Peoples!!!!
It's not an .exe problem (actually it's self-extracted CAB)
It's not a DNS problem.

The problem is in wget here: (see the /var/lib/dpkg/info/msttcorefonts.postinst file)

```
if ! wget --continue --tries=1 --dns-timeout=10 --connect-timeout=5 --read-timeout=300 $QUIET_ARG --directory-prefix . --no-directories --no-background $URLROOT$ff ; then
```

I guess than it's a kind of changes in new wget that unable to work with lots of pre-defined params.
Hope than msttcorefonts package maintainer solve the problem ASAP.
I solve it by change that big line by short 
```
wget $URLROOT$ff
```

Well, changing DNS solved my problem with slow and occasionally dropping network.

---

### Post by Nick Fedchik on 2007-10-23
> **danteman said:**
> Well, changing DNS solved my problem with slow and occasionally dropping network.
I had no changes to my /etc/resolv.conf
The download of msttf files works fine if wget had no any parameters except of URL.
Also if You try to google for "Ubuntu 7.10 andale32.exe", so You can see than lots of peoples have the same problem. So if the problem reproduced on a lots of hosts around the world, it's not a DNS problem, it's a wget parameters problem.
Yep, my workaround isn't so easy compare with DNS changes, but I guess it's not always possible to change DNS addresses.
Of course I happy if workaround with DNS changes also solve the problem. ;)

---

### Post by Nick Fedchik on 2007-10-23
Package Maintainer: Tollef Fog Heen <tfheen / debian.org>  answered me:
> sorry, I no longer maintain msttcorefonts.  Also, you might want to
contact whoever uploaded it into Ubuntu, not me.

---

### Post by damonlab on 2007-10-26
> **ader10 said:**
> Thank you very much, Nick!

To clarify what he said, you replace the code
```
wget --continue --tries=1 --dns-timeout=10 --connect-timeout=5 --read-timeout=300 $QUIET_ARG --directory-prefix . --no-directories --no-background $URLROOT$ff
```
with
```
wget $URLROOT$ff
```
instead of the entire line of code.

I had the same problem and this solution worked for me.

---

### Post by spur on 2007-10-26
This should be a sticky somewhere as the script needs updating and plenty of people will need to know how to fix it . I had the same problem with Feisty and Gutsy and this fix is the only one that works.

---

### Post by stefanuswiely on 2007-10-30
I have same problems here, this think happened when I try install ubuntu-restricted-extras package. I don't have internet connection at my home, so do you think can I solve this problem by downloading "andale32.exe" then put it on my home directory and do installation again?

Thank you.

---

### Post by spur on 2007-10-30
No, just downloading the andale.exe is not enough as it's only one of the font and other packages are needed. If you don't have an internet connection you can  get the fonts. Copy them from someone's windows installation.( Preferably your own as they are copyright.)Put them in your fonts folder.(system -> preferences ->appearance -> fonts -> details ->go to fonts folder)

---

### Post by stefanuswiely on 2007-10-31
Thank you for the respond. I will try it later :)

---

### Post by jimmux on 2007-11-03
I've been trying to modify the script as described but it doesn't seem to be working - probably doing it wrong. Could some one provide more detailed instructions, including the location of the script to be altered? Or even better, a fixed deb. Thanks.

And if anyone is interested, as a last resort I removed the entry for msttcorefonts from /var/lib/dpkg/status. This prevents it from trying to configure all the time, but it won't give you a successful install and is a bit messy.

---

### Post by spur on 2007-11-03
The location is /etc/resolve.conf you will need to sudo to change it. Be care full when you do change it as you need the ';' at the end to stay put.

---

### Post by lenB on 2007-11-04
> No, just downloading the andale.exe is not enough as it's only one of the font and other packages are needed. If you don't have an internet connection you can get the fonts. Copy them from someone's windows installation.( Preferably your own as they are copyright.)Put them in your fonts folder.(system -> preferences ->appearance -> fonts -> details ->go to fonts folder)


All the windows fonts??

---

### Post by spur on 2007-11-04
All the ones you want.

---

### Post by Gweeper64 on 2007-12-05
The problem is the string setting for the proxy somewhere in the package config files. The proxy string is set to "http://:8080/" which is of course bogus.

I ran "sudo dpkg-reconfigure --force msttcorefonts" in a shell window and made sure to make the proxy string blank when it asked, and that seemed to cure the problem.

I don't know the "dpkg" system well enough to know where that default proxy string is set, so I have not found that yet.

---

### Post by beow on 2007-12-06
I edited the /var/lib/dpkg/info/msttcorefonts.postinst file (as root) according to this:

--- snip ---
db_get msttcorefonts/http_proxy
http_proxy=$RET

# own "fix":
unset http_proxy
#---------------

if [ -e /usr/share/fonts/truetype/ms-fonts ] ; then
--- snip ---

It cured the problem with the bogus proxy. (of course you have to have a direct connection to the internet for this to work)

---

### Post by SaniOK on 2008-01-08
None of the variants above worked for me.

My solution, that worked for me:
add to /etc/hosts

130.59.138.20  surfnet.dl.sourceforge.net

This caused to resolve host quickly, and msttcorefonts successfully installed.

---

