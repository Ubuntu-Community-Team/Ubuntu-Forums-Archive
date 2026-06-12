---
title: "dpkg error"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by TehCJ on 2007-07-01
I got this Error Help please

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by bodhi.zazen on 2007-07-01
1. Close "add programs" or synaptic  or update manager if any are open.

2. Open a terminal.

3. Enter this : ```
sudo dpkg --configure -a
```

Post any errors.

---

### Post by Seisen on 2007-07-01
Type in 

```
sudo dpgk --configure -a
``` in the terminal like it says and it should fix if it doesn't let us know.

You beat me to it, Bodhi.

---

### Post by Virgilius on 2007-07-09
okay, I tried doing that but this happens:

```
me@me-desktop:~$ sudo dpkg --configure -a
Setting up msttcorefonts (1.2ubuntu3) ...
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 5.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 5.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 5.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 8.
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN1> line 12.
warning: /usr/share/fonts/X11/truetype does not exist or is not a directory
warning: /usr/lib/X11/fonts/truetype does not exist or is not a directory
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--14:41:00--  http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... failed: Connection timed out.
--14:41:10--  http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... 69.16.168.245
Connecting to easynews.dl.sourceforge.net|69.16.168.245|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 198,384 (194K) [application/octet-stream]

100%[====================================>] 198,384       22.47K/s    ETA 00:00

14:41:26 (17.42 KB/s) - `./andale32.exe' saved [198384/198384]

--14:41:26--  http://easynews.dl.sourceforge.net/sourceforge/corefonts/arialb32.exe
           => `./arialb32.exe'
Resolving easynews.dl.sourceforge.net... 69.16.168.245
Connecting to easynews.dl.sourceforge.net|69.16.168.245|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 168,176 (164K) [application/octet-stream]

100%[====================================>] 168,176       26.27K/s    ETA 00:00

14:41:35 (23.51 KB/s) - `./arialb32.exe' saved [168176/168176]

--14:41:35--  http://easynews.dl.sourceforge.net/sourceforge/corefonts/arial32.exe
           => `./arial32.exe'
Resolving easynews.dl.sourceforge.net... 69.16.168.245
Connecting to easynews.dl.sourceforge.net|69.16.168.245|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 554,208 (541K) [application/octet-stream]

100%[====================================>] 554,208       49.25K/s    ETA 00:00

14:42:02 (33.21 KB/s) - `./arial32.exe' saved [554208/554208]

--14:42:02--  http://easynews.dl.sourceforge.net/sourceforge/corefonts/comic32.exe
           => `./comic32.exe'
Resolving easynews.dl.sourceforge.net... 69.16.168.245
Connecting to easynews.dl.sourceforge.net|69.16.168.245|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 246,008 (240K) [application/octet-stream]

100%[====================================>] 246,008       43.34K/s    ETA 00:00

14:42:18 (21.16 KB/s) - `./comic32.exe' saved [246008/246008]

--14:42:18--  http://easynews.dl.sourceforge.net/sourceforge/corefonts/courie32.exe
           => `./courie32.exe'
Resolving easynews.dl.sourceforge.net... 69.16.168.245
Connecting to easynews.dl.sourceforge.net|69.16.168.245|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 646,368 (631K) [application/octet-stream]

100%[====================================>] 646,368       49.99K/s    ETA 00:00

14:42:42 (28.77 KB/s) - `./courie32.exe' saved [646368/646368]

--14:42:42--  http://easynews.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe
           => `./georgi32.exe'
Resolving easynews.dl.sourceforge.net... failed: Connection timed out.
--14:42:52--  http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe
           => `./georgi32.exe'
Resolving twtelecom.dl.sourceforge.net... 207.250.4.12
Connecting to twtelecom.dl.sourceforge.net|207.250.4.12|:80... failed: Connection timed out.
Giving up.

--14:43:05--  http://aleron.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe
           => `./georgi32.exe'
Resolving aleron.dl.sourceforge.net... failed: Connection timed out.
--14:43:15--  http://cesnet.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe
           => `./georgi32.exe'
Resolving cesnet.dl.sourceforge.net... failed: Connection timed out.
--14:43:25--  http://switch.dl.sourceforge.net/sourceforge/corefonts/georgi32.exe
           => `./georgi32.exe'
Resolving switch.dl.sourceforge.net... 130.59.138.20, 2001:620:0:1b::20
Connecting to switch.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 392,440 (383K) [application/octet-stream]

100%[====================================>] 392,440       48.99K/s    ETA 00:00

14:43:46 (30.97 KB/s) - `./georgi32.exe' saved [392440/392440]

--14:43:46--  http://switch.dl.sourceforge.net/sourceforge/corefonts/impact32.exe
           => `./impact32.exe'
Resolving switch.dl.sourceforge.net... failed: Connection timed out.
Extracting cabinet: andale32.exe
  extracting fontinst.inf
  extracting andale.inf
  extracting fontinst.exe
  extracting AndaleMo.TTF
  extracting ADVPACK.DLL
  extracting W95INF32.DLL
  extracting W95INF16.DLL

All done, no errors.
Extracting cabinet: arialb32.exe
  extracting fontinst.exe
  extracting fontinst.inf
  extracting AriBlk.TTF

All done, no errors.
Extracting cabinet: arial32.exe
  extracting FONTINST.EXE
  extracting fontinst.inf
  extracting Ariali.TTF
  extracting Arialbd.TTF
  extracting Arialbi.TTF
  extracting Arial.TTF

All done, no errors.
Extracting cabinet: comic32.exe
  extracting fontinst.inf
  extracting Comicbd.TTF
  extracting Comic.TTF
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: courie32.exe
  extracting cour.ttf
  extracting courbd.ttf
  extracting courbi.ttf
  extracting fontinst.inf
  extracting couri.ttf
  extracting fontinst.exe

All done, no errors.
Extracting cabinet: georgi32.exe
  extracting fontinst.inf
  extracting Georgiaz.TTF
  extracting Georgiab.TTF
  extracting Georgiai.TTF
  extracting Georgia.TTF
  extracting fontinst.exe

All done, no errors.
impact32.exe: No such file or directory

All done, errors in processing 1 file(s)
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83, <GEN6> line 4.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84, <GEN6> line 4.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83, <GEN6> line 4.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84, <GEN6> line 4.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83, <GEN6> line 4.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84, <GEN6> line 4.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83, <GEN6> line 4.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84, <GEN6> line 4.
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83, <GEN6> line 4.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84, <GEN6> line 4.
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
me@me-desktop:~$ 


```

Help, please?

---

