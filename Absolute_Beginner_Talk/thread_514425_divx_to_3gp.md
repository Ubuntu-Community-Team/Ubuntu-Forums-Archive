---
title: "divx to 3gp"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by zerobinary on 2007-07-31
is there a way to convert divx to 3gp

---

### Post by zerobinary on 2007-07-31
anyone

---

### Post by zerobinary on 2007-07-31
come on need ur help plz

---

### Post by punx45 on 2007-07-31
mencoder might do the trick.   might need to get extra codecs.

[http://www.mplayerhq.hu/DOCS/HTML/en/mencoder.html](http://www.mplayerhq.hu/DOCS/HTML/en/mencoder.html)

VLC can also do conversions.   [http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

---

### Post by zerobinary on 2007-07-31
is there a gui app that do that sort of work i have vlc but don't know how to convert it

---

### Post by punx45 on 2007-07-31
then read the documentation on the VLC site.

I don't know exactly how to do it either.

---

### Post by zerobinary on 2007-07-31
na maybe an online convertor is better

---

### Post by zerobinary on 2007-07-31
anyone know online video converter for divx to 3gp

---

### Post by Gremlinzzz on 2007-07-31
You could check this one out 
[http://linux.softpedia.com/get/Multimedia/Video/3gp-movie-wizard-9764.shtml](http://linux.softpedia.com/get/Multimedia/Video/3gp-movie-wizard-9764.shtml)

---

### Post by zerobinary on 2007-07-31
don't know how to install it i am a newbie don't quite know about compiling things

---

### Post by zerobinary on 2007-07-31
come on anyone

---

### Post by zerobinary on 2007-07-31
i need help

---

### Post by zerobinary on 2007-07-31
plz help

---

### Post by zerobinary on 2007-08-01
help plz

---

### Post by zerobinary on 2007-08-01
come on plz

---

### Post by st33med on 2007-08-01
I remember I did that in the terminal, though I don't remember how. Get back to you in a sec.

---

### Post by st33med on 2007-08-01
OK, go to download these packages like by doing this:

```
sudo apt-get install kommander ffmpeg
```

Now go to [this link]("http://sourceforge.net/project/downloading.php?group_id=192375&use_mirror=easynews&filename=3gpconverter-0.6.tar.bz2&83660658") to download it to your desktop. Open it and extract it to your profile.




Now do this:
```
kmdr-executor ~/3gpconverter-0.6/3gpconverter-0.6.kmdr
```
A window will open. Choose the file you want to convert and what you want to convert it to.

EDIT: Actually, I'm sorry for saying this, but coituld you read the readme inside the file? I'm sorry, please don't follow the above instruction, but download the package and follow it's instructions? I'm just tired. I might come back later and help.

---

### Post by zerobinary on 2007-08-01
```
kmdr-executor ~/3gpconverter-0.6/3gpconverter-0.6.kmdr
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
zerobinary@zerobinary-desktop:~$ kmdr-executor ~/3gpconverter-0.6/3gpconverter-0.6.kmdr
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
DCOPClient::attachInternal. Attach failed Could not open network socket
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Launched ok, pid = 6318
zerobinary@zerobinary-desktop:~$ 
zerobinary@zerobinary-desktop:~$ ICE default IO error handler doing an exit(), pid = 6315, errno = 0

```
i actually have kommander according to the thing already

---

### Post by zerobinary on 2007-08-01
Details: Failed to execute child process "/usr/bin/3gpwiz" (No such file or directory)
```

zerobinary@zerobinary-desktop:~$ /home/zerobinary/Desktop/3gpwiz/install-ffmpeg
/home/zerobinary/Desktop/3gpwiz/install-ffmpeg: line 6: cvs: command not found
/home/zerobinary/Desktop/3gpwiz/install-ffmpeg: line 7: cd: ffmpeg/libavcodec: No such file or directory
mkdir: cannot create directory `amr_float': Permission denied
/home/zerobinary/Desktop/3gpwiz/install-ffmpeg: line 9: cd: amr_float: No such file or directory
--20:09:22--  http://www.3gpp.org/ftp/Specs/archive/26_series/26.104/26104-510.zip
           => `26104-510.zip'
Resolving www.3gpp.org... 212.234.161.21
Connecting to www.3gpp.org|212.234.161.21|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 291,836 (285K) [application/x-zip-compressed]
26104-510.zip: Permission denied

Cannot write to `26104-510.zip' (Permission denied).
unzip:  cannot find or open *.zip, *.zip.zip or *.zip.ZIP.

No zipfiles found.
unzip:  cannot find or open *code.zip, *code.zip.zip or *code.zip.ZIP.

No zipfiles found.
mkdir: cannot create directory `amrwb_float': Permission denied
/home/zerobinary/Desktop/3gpwiz/install-ffmpeg: line 15: cd: amrwb_float: No such file or directory
--20:09:23--  http://www.3gpp.org/ftp/Specs/archive/26_series/26.204/26204-510.zip
           => `26204-510.zip'
Resolving www.3gpp.org... 212.234.161.21
Connecting to www.3gpp.org|212.234.161.21|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 246,663 (241K) [application/x-zip-compressed]
26204-510.zip: Permission denied

Cannot write to `26204-510.zip' (Permission denied).
unzip:  cannot find or open *.zip, *.zip.zip or *.zip.ZIP.

No zipfiles found.
unzip:  cannot find or open *code.zip, *code.zip.zip or *code.zip.ZIP.

No zipfiles found.
/home/zerobinary/Desktop/3gpwiz/install-ffmpeg: line 20: ./configure: No such file or directory
make: *** No targets specified and no makefile found.  Stop.
cp: cannot stat `ffmpeg': No such file or directory
cp: cannot stat `ffplay': No such file or directory

```

---

### Post by zerobinary on 2007-08-01
newest error code
```

zerobinary@zerobinary-desktop:~$ sudo kmdr-executor ~/3gpconverter-0.6/3gpconverter-0.6.kmdr
Password:
\X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Launched ok, pid = 6745

```

---

### Post by zerobinary on 2007-08-02
hand plz is there a deb file

---

