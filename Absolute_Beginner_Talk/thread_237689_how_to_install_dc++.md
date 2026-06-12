---
title: "how to install dc++"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by vilto on 2006-08-16
i tried to install linuxdc++ by the method given in
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

when i compiled the tar.gz file the result was 
~$ sudo tar zxvf linuxdcpp.tar.gz -C /opt
linuxdcpp/CVS/Root
linuxdcpp/CVS/Repository
linuxdcpp/CVS/Entries
linuxdcpp/CVS/Entries.Log
linuxdcpp/client/CVS/Root
linuxdcpp/client/CVS/Repository
linuxdcpp/client/CVS/Entries
linuxdcpp/client/ADLSearch.cpp
linuxdcpp/client/ADLSearch.h
linuxdcpp/client/AdcCommand.cpp
linuxdcpp/client/AdcCommand.h
linuxdcpp/client/AdcHub.cpp
linuxdcpp/client/AdcHub.h
linuxdcpp/client/BZUtils.cpp
linuxdcpp/client/BZUtils.h
linuxdcpp/client/BitInputStream.h
linuxdcpp/client/BitOutputStream.h
linuxdcpp/client/BloomFilter.h
linuxdcpp/client/BufferedSocket.cpp
linuxdcpp/client/BufferedSocket.h
linuxdcpp/client/CID.h
linuxdcpp/client/Client.cpp
linuxdcpp/client/Client.h
linuxdcpp/client/ClientManager.cpp
linuxdcpp/client/ClientManager.h
linuxdcpp/client/ClientManagerListener.h
linuxdcpp/client/ConnectionManager.cpp
linuxdcpp/client/ConnectionManager.h
linuxdcpp/client/ConnectionManagerListener.h
linuxdcpp/client/CriticalSection.h
linuxdcpp/client/CryptoManager.cpp
linuxdcpp/client/CryptoManager.h
linuxdcpp/client/DCPlusPlus.cpp
linuxdcpp/client/DCPlusPlus.h
linuxdcpp/client/DirectoryListing.cpp
linuxdcpp/client/DirectoryListing.h
linuxdcpp/client/DownloadManager.cpp
linuxdcpp/client/DownloadManager.h
linuxdcpp/client/Encoder.cpp
linuxdcpp/client/Encoder.h
linuxdcpp/client/Exception.cpp
linuxdcpp/client/Exception.h
linuxdcpp/client/FastAlloc.h
linuxdcpp/client/FavoriteUser.h
linuxdcpp/client/File.h
linuxdcpp/client/FilteredFile.h
linuxdcpp/client/FinishedManager.cpp
linuxdcpp/client/FinishedManager.h
linuxdcpp/client/HashManager.cpp
linuxdcpp/client/HashManager.h
linuxdcpp/client/HashValue.h
linuxdcpp/client/HttpConnection.cpp
linuxdcpp/client/HttpConnection.h
linuxdcpp/client/HubManager.cpp
linuxdcpp/client/HubManager.h
linuxdcpp/client/LogManager.cpp
linuxdcpp/client/LogManager.h
linuxdcpp/client/Makefile.am
linuxdcpp/client/MerkleCheckOutputStream.h
linuxdcpp/client/MerkleTree.h
linuxdcpp/client/NmdcHub.cpp
linuxdcpp/client/NmdcHub.h
linuxdcpp/client/Pointer.h
linuxdcpp/client/QueueItem.h
linuxdcpp/client/QueueManager.cpp
linuxdcpp/client/QueueManager.h
linuxdcpp/client/QueueManagerListener.h
linuxdcpp/client/ResourceManager.cpp
linuxdcpp/client/ResourceManager.h
linuxdcpp/client/SConstruct
linuxdcpp/client/SFVReader.cpp
linuxdcpp/client/SFVReader.h
linuxdcpp/client/SearchManager.cpp
linuxdcpp/client/SearchManager.h
linuxdcpp/client/SearchManagerListener.h
linuxdcpp/client/Semaphore.h
linuxdcpp/client/ServerSocket.cpp
linuxdcpp/client/ServerSocket.h
linuxdcpp/client/SettingsManager.cpp
linuxdcpp/client/SettingsManager.h
linuxdcpp/client/ShareManager.cpp
linuxdcpp/client/ShareManager.h
linuxdcpp/client/SimpleXML.cpp
linuxdcpp/client/SimpleXML.h
linuxdcpp/client/Singleton.h
linuxdcpp/client/Socket.cpp
linuxdcpp/client/Socket.h
linuxdcpp/client/Speaker.h
linuxdcpp/client/Streams.h
linuxdcpp/client/StringDefs.cpp
linuxdcpp/client/StringDefs.h
linuxdcpp/client/StringSearch.h
linuxdcpp/client/StringTokenizer.cpp
linuxdcpp/client/StringTokenizer.h
linuxdcpp/client/Text.cpp
linuxdcpp/client/Text.h
linuxdcpp/client/Thread.cpp
linuxdcpp/client/Thread.h
linuxdcpp/client/TigerHash.cpp
linuxdcpp/client/TigerHash.h
linuxdcpp/client/TimerManager.cpp
linuxdcpp/client/TimerManager.h
linuxdcpp/client/UploadManager.cpp
linuxdcpp/client/UploadManager.h
linuxdcpp/client/User.cpp
linuxdcpp/client/User.h
linuxdcpp/client/UserCommand.h
linuxdcpp/client/UserConnection.cpp
linuxdcpp/client/UserConnection.h
linuxdcpp/client/Util.cpp
linuxdcpp/client/Util.h
linuxdcpp/client/ZUtils.cpp
linuxdcpp/client/ZUtils.h
linuxdcpp/client/config.h
linuxdcpp/client/stdinc.cpp
linuxdcpp/client/stdinc.h
linuxdcpp/client/version.h
linuxdcpp/client/.sconsign
linuxdcpp/glade/CVS/Root
linuxdcpp/glade/CVS/Repository
linuxdcpp/glade/CVS/Entries
linuxdcpp/glade/downloadqueue.glade
linuxdcpp/glade/favoritehubs.glade
linuxdcpp/glade/finishedtransfers.glade
linuxdcpp/glade/hash.glade
linuxdcpp/glade/hub.glade
linuxdcpp/glade/mainwindow.glade
linuxdcpp/glade/privatemessage.glade
linuxdcpp/glade/publichubs.glade
linuxdcpp/glade/search.glade
linuxdcpp/glade/settingsdialog.glade
linuxdcpp/glade/sharebrowser.glade
linuxdcpp/linux/CVS/Root
linuxdcpp/linux/CVS/Repository
linuxdcpp/linux/CVS/Entries
linuxdcpp/linux/SConstruct
linuxdcpp/linux/WulforUtil.cc
linuxdcpp/linux/WulforUtil.hh
linuxdcpp/linux/bookentry.cc
linuxdcpp/linux/bookentry.hh
linuxdcpp/linux/callback.hh
linuxdcpp/linux/dialogentry.cc
linuxdcpp/linux/dialogentry.hh
linuxdcpp/linux/downloadqueue.cc
linuxdcpp/linux/downloadqueue.hh
linuxdcpp/linux/eggtrayicon.c
linuxdcpp/linux/eggtrayicon.h
linuxdcpp/linux/favoritehubs.cc
linuxdcpp/linux/favoritehubs.hh
linuxdcpp/linux/finishedtransfers.cc
linuxdcpp/linux/finishedtransfers.hh
linuxdcpp/linux/func.hh
linuxdcpp/linux/hashdialog.cc
linuxdcpp/linux/hashdialog.hh
linuxdcpp/linux/hub.cc
linuxdcpp/linux/hub.hh
linuxdcpp/linux/mainwindow.cc
linuxdcpp/linux/mainwindow.hh
linuxdcpp/linux/prefix.cc
linuxdcpp/linux/prefix.hh
linuxdcpp/linux/privatemessage.cc
linuxdcpp/linux/privatemessage.hh
linuxdcpp/linux/publichubs.cc
linuxdcpp/linux/publichubs.hh
linuxdcpp/linux/search.cc
linuxdcpp/linux/search.hh
linuxdcpp/linux/selecter.cc
linuxdcpp/linux/selecter.hh
linuxdcpp/linux/settingsdialog.cc
linuxdcpp/linux/settingsdialog.hh
linuxdcpp/linux/settingsmanager.cc
linuxdcpp/linux/settingsmanager.hh
linuxdcpp/linux/sharebrowser.cc
linuxdcpp/linux/sharebrowser.hh
linuxdcpp/linux/treeview.cc
linuxdcpp/linux/treeview.hh
linuxdcpp/linux/wulfor.cc
linuxdcpp/linux/wulformanager.cc
linuxdcpp/linux/wulformanager.hh
linuxdcpp/linux/.sconsign
linuxdcpp/pixmaps/CVS/Root
linuxdcpp/pixmaps/CVS/Repository
linuxdcpp/pixmaps/CVS/Entries
linuxdcpp/pixmaps/FinishedDL.png
linuxdcpp/pixmaps/FinishedUL.png
linuxdcpp/pixmaps/dc++-fw-op.png
linuxdcpp/pixmaps/dc++-fw.png
linuxdcpp/pixmaps/dc++-op.png
linuxdcpp/pixmaps/dc++.png
linuxdcpp/pixmaps/download.png
linuxdcpp/pixmaps/favhubs.png
linuxdcpp/pixmaps/linuxdcpp.svg
linuxdcpp/pixmaps/normal-fw-op.png
linuxdcpp/pixmaps/normal-fw.png
linuxdcpp/pixmaps/normal-op.png
linuxdcpp/pixmaps/normal.png
linuxdcpp/pixmaps/publichubs.png
linuxdcpp/pixmaps/queue.png
linuxdcpp/pixmaps/search.png
linuxdcpp/pixmaps/settings.png
linuxdcpp/pixmaps/upload.png
linuxdcpp/.sconf_temp/conftest_4.c
linuxdcpp/.sconf_temp/conftest_4.o
linuxdcpp/.sconf_temp/conftest_5.c
linuxdcpp/.sconf_temp/conftest_5.o
linuxdcpp/.sconf_temp/conftest_6.c
linuxdcpp/.sconf_temp/conftest_6.o
linuxdcpp/.sconf_temp/conftest_7.c
linuxdcpp/.sconf_temp/conftest_7.o
linuxdcpp/.sconf_temp/conftest_8.c
linuxdcpp/.sconf_temp/conftest_8.o
linuxdcpp/.sconf_temp/conftest_8
linuxdcpp/.sconf_temp/conftest_9.c
linuxdcpp/.sconf_temp/conftest_9.o
linuxdcpp/.sconf_temp/conftest_9
linuxdcpp/.sconf_temp/conftest_10.c
linuxdcpp/.sconf_temp/conftest_10.o
linuxdcpp/.sconf_temp/conftest_10
linuxdcpp/.sconf_temp/.cache
linuxdcpp/.sconf_temp/.sconsign
linuxdcpp/build/client/ADLSearch.o
linuxdcpp/build/client/FinishedManager.o
linuxdcpp/build/client/Socket.o
linuxdcpp/build/client/AdcCommand.o
linuxdcpp/build/client/HashManager.o
linuxdcpp/build/client/StringDefs.o
linuxdcpp/build/client/AdcHub.o
linuxdcpp/build/client/HttpConnection.o
linuxdcpp/build/client/StringTokenizer.o
linuxdcpp/build/client/BZUtils.o
linuxdcpp/build/client/HubManager.o
linuxdcpp/build/client/Text.o
linuxdcpp/build/client/BufferedSocket.o
linuxdcpp/build/client/LogManager.o
linuxdcpp/build/client/Thread.o
linuxdcpp/build/client/Client.o
linuxdcpp/build/client/NmdcHub.o
linuxdcpp/build/client/TigerHash.o
linuxdcpp/build/client/ClientManager.o
linuxdcpp/build/client/QueueManager.o
linuxdcpp/build/client/TimerManager.o
linuxdcpp/build/client/ConnectionManager.o
linuxdcpp/build/client/ResourceManager.o
linuxdcpp/build/client/UploadManager.o
linuxdcpp/build/client/CryptoManager.o
linuxdcpp/build/client/SFVReader.o
linuxdcpp/build/client/User.o
linuxdcpp/build/client/DCPlusPlus.o
linuxdcpp/build/client/SearchManager.o
linuxdcpp/build/client/UserConnection.o
linuxdcpp/build/client/DirectoryListing.o
linuxdcpp/build/client/ServerSocket.o
linuxdcpp/build/client/Util.o
linuxdcpp/build/client/DownloadManager.o
linuxdcpp/build/client/SettingsManager.o
linuxdcpp/build/client/ZUtils.o
linuxdcpp/build/client/Encoder.o
linuxdcpp/build/client/ShareManager.o
linuxdcpp/build/client/stdinc.o
linuxdcpp/build/client/Exception.o
linuxdcpp/build/client/SimpleXML.o
linuxdcpp/build/client/.sconsign
linuxdcpp/build/gui/selecter.o
linuxdcpp/build/gui/wulformanager.o
linuxdcpp/build/gui/bookentry.o
linuxdcpp/build/gui/mainwindow.o
linuxdcpp/build/gui/wulfor.o
linuxdcpp/build/gui/prefix.o
linuxdcpp/build/gui/publichubs.o
linuxdcpp/build/gui/treeview.o
linuxdcpp/build/gui/hub.o
linuxdcpp/build/gui/privatemessage.o
linuxdcpp/build/gui/downloadqueue.o
linuxdcpp/build/gui/favoritehubs.o
linuxdcpp/build/gui/settingsdialog.o
linuxdcpp/build/gui/sharebrowser.o
linuxdcpp/build/gui/search.o
linuxdcpp/build/gui/hashdialog.o
linuxdcpp/build/gui/finishedtransfers.o
linuxdcpp/build/gui/dialogentry.o
linuxdcpp/build/gui/settingsmanager.o
linuxdcpp/build/gui/WulforUtil.o
linuxdcpp/build/gui/eggtrayicon.o
linuxdcpp/build/gui/.sconsign
linuxdcpp/Changelog.txt
linuxdcpp/Credits.txt
linuxdcpp/License.txt
linuxdcpp/Readme.txt
linuxdcpp/SConstruct
linuxdcpp/config.log
linuxdcpp/ldcpp

gzip: stdin: unexpected end of file
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now
atul@atul-desktop:~$ sudo gedit /usr/share/applications/dcpp.desktop

(gedit:8519): Gdk-WARNING **: locale not supported by Xlib

(gedit:8519): Gdk-WARNING **: cannot set locale modifiers



and when i went to internet----->dc++
its not openning

how do i get it working ......im new to linux:???:

---

### Post by Klaidas on 2006-08-16
You could use Valknut for DC++
[http://www.ubuntuforums.org/showthread.php?t=33183](http://www.ubuntuforums.org/showthread.php?t=33183)

---

### Post by jive_turkey on 2006-08-16
Valknut is definatley the way to go, I've used it quite a bit and its avalable through Synaptic.

---

### Post by mrazster on 2006-08-16
Just fire up synaptic..search for valknut, install and enjoy.

Personally I'm enjoying DC++ ...i followed [THIS](http://www.ubuntuforums.org/showthread.php?t=193984) howto...it's not that hard really. And with the latest release it's very stable..atleast to me.

---

### Post by vilto on 2006-08-22
thanx to all for help i got dc++ worked out:p :)

---

