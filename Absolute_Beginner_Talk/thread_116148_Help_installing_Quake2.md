---
title: "Help installing Quake2"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by Harimwakairi on 2006-01-12
I recently installed the quake2 packages from synaptic.  After that I searched the forums nad found out how to use dpkg-reconfigure to install the files on my quake2 cd.  However, when I attempt to run the game, I receive errors.  I was hoping someone could look at the message I'm getting and point me in the general area of a fix:

```
andrew@rectangle:~$ sudo dpkg-reconfigure quake2-data
Password:
Installing data from CD-ROM
find: /cdrom/Install/Data/baseq2: No such file or directory
Downloading q2-3.20-x86-full-ctf.exe from ftp://ftp.idsoftware.com/idstuff/quake2/...
--03:19:54--  ftp://ftp.idsoftware.com/idstuff/quake2/q2-3.20-x86-full-ctf.exe
           => `/home/andrew/q2-3.20-x86-full-ctf.exe'
Resolving ftp.idsoftware.com... 192.246.40.185
Connecting to ftp.idsoftware.com|192.246.40.185|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /idstuff/quake2 ... done.
==> PASV ... done.    ==> RETR q2-3.20-x86-full-ctf.exe ... done.
Length: 19,267,584 (18M) (unauthoritative)

100%[====================================>] 19,267,584    49.99K/s    ETA 00:00

03:26:29 (47.79 KB/s) - `/home/andrew/q2-3.20-x86-full-ctf.exe' saved [19267584]
done.
Installing data from q2-3.20-x86-full-ctf.exe
andrew@rectangle:~$ quake2
***** WARNING *****

   The networking part of Quake II (especially the server part) contains
   several unfixed security issues. Therefore, Quake II should not be
   used over untrusted networks (like the internet). The version
   included in Debian is intended only for local play.

   See for an possibly non-exhaustive list of issues:
   http://archives.neohapsis.com/archives/bugtraq/2004-10/0299.html
   http://www.r1ch.net/stuff/r1q2/
   http://bugs.debian.org/280573

*******************

Do you understand the security implications of continuing?
y
QuakeIIForge 0.3
Added packfile /usr/share/games/quake2/baseq2/pak1.pak (279 files)
Added packfile /usr/share/games/quake2/baseq2/pak2.pak (2 files)
using /home/andrew/.quake2/baseq2/ for writing
execing default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
loading oss sound output driver, ok
/dev/dsp: Input/output error
SNDDMA_Init: Could not mmap /dev/dsp.
------- Loading ref_softx.so -------
LoadLibrary("ref_softx.so")
No joysticks found
recursive shutdown
Error: Couldn't load pics/colormap.pcx

```

---

### Post by pmj on 2006-01-12
You need to have the file pak0.pak in the baseq2 directory. It's on your Quake 2 CD.

---

