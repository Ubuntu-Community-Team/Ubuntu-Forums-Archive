---
title: "Getting really frustrated"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by julie_lebou on 2007-04-09
PLEASE help me! When I open Azureus, it loads, than close up by itself... I tried rebooting lots of times, unistalling and reinstalling.. nothing works!

---

### Post by mand0 on 2007-04-09
Try running Azureus via the Terminal and paste the error it gives you.  You could also try another torrent program. [Deluge]("http://deluge-torrent.org/") is quite good and easy to install.

---

### Post by justin whitaker on 2007-04-09
> **julie_lebou said:**
> PLEASE help me! When I open Azureus, it loads, than close up by itself... I tried rebooting lots of times, unistalling and reinstalling.. nothing works!

Julie, there is a java bug that causes Azureus, Frostwire, and a couple of others to exit on load.

Try reinstalling Sun Java, or use this method to reinstall Azureus:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_P2P_BitTorrent_Client_.28Azureus.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_P2P_BitTorrent_Client_.28Azureus.29)

Also, Deluge, BitTornado, and BitTorrent work fine.

---

### Post by julie_lebou on 2007-04-09
julie@julie-desktop:~$ azureus
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb05e7d02, pid=5084, tid=3085457072
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_08-b03 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0x8d02]
#
# An error report file with more information is saved as hs_err_pid5084.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
Aborted (core dumped)
julie@julie-desktop:~$

---

### Post by jvc26 on 2007-04-09
justin whitaker hit the nail on the head mate its the java bug - follow the intructions he's given you - reinstall java or follow the links instructions.
Il

---

### Post by poppers1957 on 2007-04-09
Hi Canada!  
I use Fedora Core Linux Mostly myself, but have recently gotten ubuntu so I can introcuce people to Linux.  It is a little bit easier to install then Fedora.  All that aside, I agree that Deluge is worth the try.  Keep at it, you will be happy you did.:) 

Patrick

---

