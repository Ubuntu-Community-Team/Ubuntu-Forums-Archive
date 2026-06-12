---
title: "Lime Wire install problems"
date: 2005-09-08
forum: Absolute Beginner Talk
---

### Post by ronlondre on 2005-09-08
Hello all,

I am having a problem with my limewire installation.  Everything seems to have gone correctly. I followed the starters guide (AMD64). After following the instructions and cutting and pasting everything the limewire icon in now listed under applications->internet->Limewire, however, when I click on the icon nothing happens.
Could someone review what I did and let me know what I might have done wrong?

Here are the terminal commands:
[SIZE=1]ronlondre@ubuntu:~$ wget -c wget -c [http://frankandjacq.com/ubuntuguide/LimeWireSoftOther.zip](http://frankandjacq.com/ubuntuguide/LimeWireSoftOther.zip)
--08:31:11--  [http://wget/](http://wget/)
           => `index.html'
Resolving wget... failed: Host not found.
--08:31:11--  [http://frankandjacq.com/ubuntuguide/LimeWireSoftOther.zip](http://frankandjacq.com/ubuntuguide/LimeWireSoftOther.zip)
           => `LimeWireSoftOther.zip'
Resolving frankandjacq.com... 66.113.130.205
Connecting to frankandjacq.com[66.113.130.205]:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4,901,697 [application/zip]

100%[====================================>] 4,901,697    300.48K/s    ETA 00:00

08:31:33 (218.70 KB/s) - `LimeWireSoftOther.zip' saved [4,901,697/4,901,697]


FINISHED --08:31:33--
Downloaded: 4,901,697 bytes in 1 files
ronlondre@ubuntu:~$ sudo unzip -u LimeWireSoftOther.zip -d /opt/
Archive:  LimeWireSoftOther.zip
   creating: /opt/LimeWire/
  inflating: /opt/LimeWire/clink.jar
  inflating: /opt/LimeWire/commons-httpclient.jar
  inflating: /opt/LimeWire/commons-logging.jar
  inflating: /opt/LimeWire/COPYING
 extracting: /opt/LimeWire/cygwin.bat
  inflating: /opt/LimeWire/cygwin.ico
  inflating: /opt/LimeWire/daap.jar
  inflating: /opt/LimeWire/data.ser
 extracting: /opt/LimeWire/donotremove.htm
  inflating: /opt/LimeWire/GenericWindowsUtils.dll
  inflating: /opt/LimeWire/hashes
  inflating: /opt/LimeWire/i18n.jar
  inflating: /opt/LimeWire/icu4j.jar
  inflating: /opt/LimeWire/id3v2.jar
  inflating: /opt/LimeWire/jcraft.jar
  inflating: /opt/LimeWire/jdic.jar
  inflating: /opt/LimeWire/jl011.jar
  inflating: /opt/LimeWire/jmdns.jar
  inflating: /opt/LimeWire/libIdleTime.so
  inflating: /opt/LimeWire/libtray.so
  inflating: /opt/LimeWire/LimeWire.exe
  inflating: /opt/LimeWire/LimeWire.ico
  inflating: /opt/LimeWire/LimeWire.jar
  inflating: /opt/LimeWire/LimeWire20.dll
  inflating: /opt/LimeWire/log4j.jar
  inflating: /opt/LimeWire/logicrypto.jar
  inflating: /opt/LimeWire/looks.jar
  inflating: /opt/LimeWire/MessagesBundle.properties
  inflating: /opt/LimeWire/MessagesBundles.jar
  inflating: /opt/LimeWire/mp3sp14.jar
  inflating: /opt/LimeWire/pmf.ico
  inflating: /opt/LimeWire/ProgressTabs.jar
  inflating: /opt/LimeWire/README.txt
   creating: /opt/LimeWire/root/
   creating: /opt/LimeWire/root/magnet10/
  inflating: /opt/LimeWire/root/magnet10/badge.img
  inflating: /opt/LimeWire/root/magnet10/canHandle.img
 extracting: /opt/LimeWire/root/magnet10/limewire.gif
  inflating: /opt/LimeWire/root/magnet10/options.js
  inflating: /opt/LimeWire/root/magnet10/silentdetect.js
  inflating: /opt/LimeWire/runLime.sh
  inflating: /opt/LimeWire/SOURCE
  inflating: /opt/LimeWire/spacer.gif
  inflating: /opt/LimeWire/themes.jar
  inflating: /opt/LimeWire/tritonus.jar
  inflating: /opt/LimeWire/update.ver
  inflating: /opt/LimeWire/vorbis.jar
  inflating: /opt/LimeWire/WindowsV5PlusUtils.dll
  inflating: /opt/LimeWire/xerces.jar
  inflating: /opt/LimeWire/xml-apis.jar
  inflating: /opt/LimeWire/xml.war
ronlondre@ubuntu:~$ sudo chown -R root:root /opt/LimeWire/
ronlondre@ubuntu:~$ sudo gedit /usr/bin/runLime.sh
ronlondre@ubuntu:~$ sudo chmod +x /usr/bin/runLime.sh
ronlondre@ubuntu:~$ sudo gedit /usr/share/applications/LimeWire.desktop
ronlondre@ubuntu:~$ killall gnome-panel[/SIZE]


Here are the lines I entered into the files** /usr/bin/runLime.sh**  &  /**usr/share/applications/LimeWire.desktop**  respectively:
[SIZE=1]
cd /opt/LimeWire/
./runLime.sh[/SIZE]
[SIZE=1]
[Desktop Entry]
Name=LimeWire
Comment=LimeWire
Exec=runLime.sh
Icon=/opt/LimeWire/LimeWire.ico
Terminal=false
Type=Application
Categories=Application;Network;[/SIZE]

If someone could advise me I would appreciate it. Thank you.

---

### Post by kkvenkit on 2005-09-08
Hi.

To find out what's happening when you click on the icon do this:

1. Right-click on the desktop and choose *Open Terminal*.
2. Enter */usr/bin/runLime.sh*

Report back what it displays. I have a feeling the j2re you installed is not designed for 64-bit amd systems.

---

### Post by ronlondre on 2005-09-08
I do not have j2re installed. So I suppose that is the problem.  I see that there is a j2re1.5 in an AMD 64 repository so I'll try to install that and see if that helps with my limewire issues.

---

### Post by sdude on 2006-12-09
> **ronlondre said:**
> Hello all,

I am having a problem with my limewire installation.  Everything seems to have gone correctly. I followed the starters guide (AMD64). After following the instructions and cutting and pasting everything the limewire icon in now listed under applications->internet->Limewire, however, when I click on the icon nothing happens.
Could someone review what I did and let me know what I might have done wrong?


I'm having the same problem, ive installed it i go to apps, internet, lime wire, nothing happens :(

---

### Post by haxer on 2006-12-09
Why not use frostwire its the same ;)

---

