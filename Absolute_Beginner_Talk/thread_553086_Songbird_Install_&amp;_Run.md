---
title: "Songbird Install &amp; Run"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by mlhudson on 2007-09-17
So I installed Songbird 0.2.5. It automatically ran the first time. I enjoyed using it, no errors, no issues. 

It did not--the newbie moans--install a shortcut or launcher of any kind. Now, I cannot find it to run it. Can anyone be my Ubuntu-GPS and give me the turn-by-turn to find and launch Songbird?

Thanks.
Matt

---

### Post by kellemes on 2007-09-17
Have you tried "songbird" or "Songbird" from the commandline?

---

### Post by Maestro23 on 2007-09-17
Open terminal:

> locate songbird

Will give you the path to the launcher.  You can then create a desktop icon for it or add it to your menu, depending on what desktop you have.

And as noted above, you can just type the name of the program in terminal and it should run.

---

### Post by mlhudson on 2007-09-17
I tried
```
songbird
```
and
```
Songbird
```
and received
```
bash: songbird: command not found
```

After typine "locate songbird" I received:
```
/home/matt/.Trash/Songbird/chrome/songbird.manifest
/home/matt/.Trash/Songbird/chrome/songbird.jar
/home/matt/.Trash/Songbird/defaults/preferences/songbird-prefs.js
/home/matt/.Trash/Songbird/defaults/preferences/songbird-channel-prefs.js
/home/matt/.Trash/Songbird/xulrunner/extensions/dove@songbirdnest.com
/home/matt/.Trash/Songbird/xulrunner/extensions/dove@songbirdnest.com/chrome.manifest
/home/matt/.Trash/Songbird/xulrunner/extensions/dove@songbirdnest.com/dove.jar
/home/matt/.Trash/Songbird/xulrunner/extensions/dove@songbirdnest.com/install.rdf
/home/matt/.Trash/Songbird/xulrunner/extensions/rubberducky@songbirdnest.com
/home/matt/.Trash/Songbird/xulrunner/extensions/rubberducky@songbirdnest.com/install.rdf
/home/matt/.Trash/Songbird/xulrunner/extensions/rubberducky@songbirdnest.com/chrome.manifest
/home/matt/.Trash/Songbird/xulrunner/extensions/classic@songbirdnest.com
/home/matt/.Trash/Songbird/xulrunner/extensions/classic@songbirdnest.com/chrome.manifest
/home/matt/.Trash/Songbird/xulrunner/extensions/classic@songbirdnest.com/classic.jar
/home/matt/.Trash/Songbird/xulrunner/extensions/classic@songbirdnest.com/install.rdf
/home/matt/.songbird
/home/matt/.songbird/d7pqug1b.default
/home/matt/.songbird/d7pqug1b.default/US
/home/matt/.songbird/d7pqug1b.default/US/chrome
/home/matt/.songbird/d7pqug1b.default/US/chrome/userChrome-example.css
/home/matt/.songbird/d7pqug1b.default/US/chrome/userContent-example.css
/home/matt/.songbird/d7pqug1b.default/US/localstore.rdf
/home/matt/.songbird/d7pqug1b.default/chrome
/home/matt/.songbird/d7pqug1b.default/chrome/userChrome-example.css
/home/matt/.songbird/d7pqug1b.default/chrome/userContent-example.css
/home/matt/.songbird/d7pqug1b.default/localstore.rdf
/home/matt/.songbird/d7pqug1b.default/.parentlock
/home/matt/.songbird/d7pqug1b.default/compatibility.ini
/home/matt/.songbird/d7pqug1b.default/XPC.mfasl
/home/matt/.songbird/d7pqug1b.default/xpti.dat
/home/matt/.songbird/d7pqug1b.default/extensions
/home/matt/.songbird/d7pqug1b.default/extensions/{C78745AB-F8C0-4fc6-BA46-C7AC4A2941B3}
/home/matt/.songbird/d7pqug1b.default/extensions/{C78745AB-F8C0-4fc6-BA46-C7AC4A2941B3}/components
/home/matt/.songbird/d7pqug1b.default/extensions/{C78745AB-F8C0-4fc6-BA46-C7AC4A2941B3}/components/ComponentLoader.so
/home/matt/.songbird/d7pqug1b.default/extensions/{C78745AB-F8C0-4fc6-BA46-C7AC4A2941B3}/components/IIPodDevice.xpt
/home/matt/.songbird/d7pqug1b.default/extensions/{C78745AB-F8C0-4fc6-BA46-C7AC4A2941B3}/chrome
/home/matt/.songbird/d7pqug1b.default/extensions/{C78745AB-F8C0-4fc6-BA46-C7AC4A2941B3}/chrome/content
/home/matt/.songbird/d7pqug1b.default/extensions/{C78745AB-F8C0-4fc6-BA46-C7AC4A2941B3}/chrome/content/SyncIPod.js
/home/matt/.songbird/d7pqug1b.default/extensions/{C78745AB-F8C0-4fc6-BA46-C7AC4A2941B3}/chrome/content/SBIPodDevice.js
/home/matt/.songbird/d7pqug1b.default/extensions/{C78745AB-F8C0-4fc6-BA46-C7AC4A2941B3}/chrome/content/SimpleDialog.xul
/home/matt/.songbird/d7pqug1b.default/extensions/{C78745AB-F8C0-4fc6-BA46-C7AC4A2941B3}/chrome/content/SetUp.xul
/home/matt/.songbird/d7pqug1b.default/extensions/{C78745AB-F8C0-4fc6-BA46-C7AC4A2941B3}/chrome/content/SimpleDialog.js
/home/matt/.songbird/d7pqug1b.default/extensions/{C78745AB-F8C0-4fc6-BA46-C7AC4A2941B3}/chrome/content/StorageStatus.xul
/home/matt/.songbird/d7pqug1b.default/extensions/{C78745AB-F8C0-4fc6-BA46-C7AC4A2941B3}/chrome/content/SetUp.js
/home/matt/.songbird/d7pqug1b.default/extensions/{C78745AB-F8C0-4fc6-BA46-C7AC4A2941B3}/chrome/content/Prefs.xul
/home/matt/.songbird/d7pqug1b.default/extensions/{C78745AB-F8C0-4fc6-BA46-C7AC4A2941B3}/chrome/content/Prefs.js
/home/matt/.songbird/d7pqug1b.default/extensions/{C78745AB-F8C0-4fc6-BA46-C7AC4A2941B3}/chrome/content/SyncDialog.xul
/home/matt/.songbird/d7pqug1b.default/extensions/{C78745AB-F8C0-4fc6-BA46-C7AC4A2941B3}/chrome/content/SBIPodDevice.xul
/home/matt/.songbird/d7pqug1b.default/extensions/{C78745AB-F8C0-4fc6-BA46-C7AC4A2941B3}/chrome/content/PrefsIcon.png
/home/matt/.songbird/d7pqug1b.default/extensions/{C78745AB-F8C0-4fc6-BA46-C7AC4A2941B3}/chrome/content/PrefsOpen.xul
/home/matt/.songbird/d7pqug1b.default/extensions/{C78745AB-F8C0-4fc6-BA46-C7AC4A2941B3}/libraries
/home/matt/.songbird/d7pqug1b.default/extensions/{C78745AB-F8C0-4fc6-BA46-C7AC4A2941B3}/libraries/IPodDevice.dll
/home/matt/.songbird/d7pqug1b.default/extensions/{C78745AB-F8C0-4fc6-BA46-C7AC4A2941B3}/locales
/home/matt/.songbird/d7pqug1b.default/extensions/{C78745AB-F8C0-4fc6-BA46-C7AC4A2941B3}/locales/en-US
/home/matt/.songbird/d7pqug1b.default/extensions/{C78745AB-F8C0-4fc6-BA46-C7AC4A2941B3}/locales/en-US/IPodDevice.properties
/home/matt/.songbird/d7pqug1b.default/extensions/{C78745AB-F8C0-4fc6-BA46-C7AC4A2941B3}/locales/en-US/IPodDevice.dtd
/home/matt/.songbird/d7pqug1b.default/extensions/{C78745AB-F8C0-4fc6-BA46-C7AC4A2941B3}/install.rdf
/home/matt/.songbird/d7pqug1b.default/extensions/{C78745AB-F8C0-4fc6-BA46-C7AC4A2941B3}/chrome.manifest
/home/matt/.songbird/d7pqug1b.default/extensions/{7D5C0110-FAA5-44D2-9558-D26D9A6577FC}
/home/matt/.songbird/d7pqug1b.default/extensions/{7D5C0110-FAA5-44D2-9558-D26D9A6577FC}/chrome
/home/matt/.songbird/d7pqug1b.default/extensions/{7D5C0110-FAA5-44D2-9558-D26D9A6577FC}/chrome/content
/home/matt/.songbird/d7pqug1b.default/extensions/{7D5C0110-FAA5-44D2-9558-D26D9A6577FC}/chrome/content/SiteOverlay.xul
/home/matt/.songbird/d7pqug1b.default/extensions/{7D5C0110-FAA5-44D2-9558-D26D9A6577FC}/chrome/content/Site.js
/home/matt/.songbird/d7pqug1b.default/extensions/{7D5C0110-FAA5-44D2-9558-D26D9A6577FC}/install.rdf
/home/matt/.songbird/d7pqug1b.default/extensions/{7D5C0110-FAA5-44D2-9558-D26D9A6577FC}/chrome.manifest
/home/matt/.songbird/d7pqug1b.default/extensions/audioscrobbler@songbirdnest.com
/home/matt/.songbird/d7pqug1b.default/extensions/audioscrobbler@songbirdnest.com/components
/home/matt/.songbird/d7pqug1b.default/extensions/audioscrobbler@songbirdnest.com/components/sbAudioscrobblerService.js
/home/matt/.songbird/d7pqug1b.default/extensions/audioscrobbler@songbirdnest.com/components/sbPlayHistoryService.js
/home/matt/.songbird/d7pqug1b.default/extensions/audioscrobbler@songbirdnest.com/components/nsConsoleListener.js
/home/matt/.songbird/d7pqug1b.default/extensions/audioscrobbler@songbirdnest.com/components/sbPlayHistoryItem.js
/home/matt/.songbird/d7pqug1b.default/extensions/audioscrobbler@songbirdnest.com/components/sbXMLTreeView.js
/home/matt/.songbird/d7pqug1b.default/extensions/audioscrobbler@songbirdnest.com/components/audioscrobbler.xpt
/home/matt/.songbird/d7pqug1b.default/extensions/audioscrobbler@songbirdnest.com/chrome
/home/matt/.songbird/d7pqug1b.default/extensions/audioscrobbler@songbirdnest.com/chrome/chromelist.txt
/home/matt/.songbird/d7pqug1b.default/extensions/audioscrobbler@songbirdnest.com/chrome/audioscrobbler.jar
/home/matt/.songbird/d7pqug1b.default/extensions/audioscrobbler@songbirdnest.com/defaults
/home/matt/.songbird/d7pqug1b.default/extensions/audioscrobbler@songbirdnest.com/defaults/preferences
/home/matt/.songbird/d7pqug1b.default/extensions/audioscrobbler@songbirdnest.com/defaults/preferences/audioscrobbler.js
/home/matt/.songbird/d7pqug1b.default/extensions/audioscrobbler@songbirdnest.com/xslt
/home/matt/.songbird/d7pqug1b.default/extensions/audioscrobbler@songbirdnest.com/xslt/recenttracks.xslt
/home/matt/.songbird/d7pqug1b.default/extensions/audioscrobbler@songbirdnest.com/install.rdf
/home/matt/.songbird/d7pqug1b.default/extensions/audioscrobbler@songbirdnest.com/chrome.manifest
/home/matt/.songbird/d7pqug1b.default/XUL.mfasl
/home/matt/.songbird/d7pqug1b.default/prefs.js
/home/matt/.songbird/d7pqug1b.default/db
/home/matt/.songbird/d7pqug1b.default/db/downloadDB.db
/home/matt/.songbird/d7pqug1b.default/db/songbird.db
/home/matt/.songbird/d7pqug1b.default/db/watch_folders.db
/home/matt/.songbird/d7pqug1b.default/db/history.db
/home/matt/.songbird/d7pqug1b.default/db/webplaylist.db
/home/matt/.songbird/d7pqug1b.default/extensions.rdf
/home/matt/.songbird/d7pqug1b.default/extensions.cache
/home/matt/.songbird/d7pqug1b.default/extensions.ini
/home/matt/.songbird/d7pqug1b.default/compreg.dat
/home/matt/.songbird/d7pqug1b.default/Cache
/home/matt/.songbird/d7pqug1b.default/Cache/_CACHE_MAP_
/home/matt/.songbird/d7pqug1b.default/Cache/_CACHE_001_
/home/matt/.songbird/d7pqug1b.default/Cache/_CACHE_002_
/home/matt/.songbird/d7pqug1b.default/Cache/_CACHE_003_
/home/matt/.songbird/d7pqug1b.default/Cache/5606D57Fd01
/home/matt/.songbird/d7pqug1b.default/Cache/7C4C6EB9d01
/home/matt/.songbird/d7pqug1b.default/Cache/0DEF6C8Ad01
/home/matt/.songbird/d7pqug1b.default/Cache/1A460FC5d01
/home/matt/.songbird/d7pqug1b.default/Cache/38D8D35Dd01
/home/matt/.songbird/d7pqug1b.default/Cache/727405D5d01
/home/matt/.songbird/d7pqug1b.default/cookies.txt
/home/matt/.songbird/d7pqug1b.default/history.dat
/home/matt/.songbird/d7pqug1b.default/secmod.db
/home/matt/.songbird/d7pqug1b.default/cert8.db
/home/matt/.songbird/d7pqug1b.default/key3.db
/home/matt/.songbird/profiles.ini
/home/matt/.songbird/pluginreg.dat
/usr/share/automatix2/conf/songbird.desktop
/usr/share/automatix2/conf/songbirdicon.png
/usr/share/automatix2/conf/songbirdversion

```

Can you point me to the place I need to go? The stuff in the trash I think is the installer.

---

### Post by Maestro23 on 2007-09-17
How did you install?  Did you use the following: [http://www.psychocats.net/ubuntu/songbird](http://www.psychocats.net/ubuntu/songbird)

or

Automatix?

---

### Post by por100pre1 on 2007-09-17
```
which xulrunner
```

```
locate xulrunner
```

---

### Post by mlhudson on 2007-09-17
I installed by downloading the tar.gz from [www.songbirdnest.com](www.songbirdnest.com) and then double-clicked the songbird install executable. Then it autoran the program, which worked flawlessly, but now...I've lost it.

---

### Post by mlhudson on 2007-09-17
Here's the "locate xulrunner" output:
```
matt@matt-laptop:~$ locate xulrunner
/home/matt/.Trash/Songbird/xulrunner
/home/matt/.Trash/Songbird/xulrunner/updater.ini
/home/matt/.Trash/Songbird/xulrunner/bloaturls.txt
/home/matt/.Trash/Songbird/xulrunner/chrome
/home/matt/.Trash/Songbird/xulrunner/chrome/comm.manifest
/home/matt/.Trash/Songbird/xulrunner/chrome/chromelist.txt
/home/matt/.Trash/Songbird/xulrunner/chrome/pippki.jar
/home/matt/.Trash/Songbird/xulrunner/chrome/toolkit.jar
/home/matt/.Trash/Songbird/xulrunner/chrome/icons
/home/matt/.Trash/Songbird/xulrunner/chrome/icons/default
/home/matt/.Trash/Songbird/xulrunner/chrome/icons/default/default.xpm
/home/matt/.Trash/Songbird/xulrunner/chrome/classic.manifest
/home/matt/.Trash/Songbird/xulrunner/chrome/en-US.jar
/home/matt/.Trash/Songbird/xulrunner/chrome/pippki.manifest
/home/matt/.Trash/Songbird/xulrunner/chrome/venkman.jar
/home/matt/.Trash/Songbird/xulrunner/chrome/classic.jar
/home/matt/.Trash/Songbird/xulrunner/chrome/en-US.manifest
/home/matt/.Trash/Songbird/xulrunner/chrome/comm.jar
/home/matt/.Trash/Songbird/xulrunner/chrome/toolkit.manifest
/home/matt/.Trash/Songbird/xulrunner/chrome/installed-chrome.txt
/home/matt/.Trash/Songbird/xulrunner/chrome/app-chrome.manifest
/home/matt/.Trash/Songbird/xulrunner/components
/home/matt/.Trash/Songbird/xulrunner/components/appshell.xpt
/home/matt/.Trash/Songbird/xulrunner/components/dom_xbl.xpt
/home/matt/.Trash/Songbird/xulrunner/components/jsconsole.xpt
/home/matt/.Trash/Songbird/xulrunner/components/dom.xpt
/home/matt/.Trash/Songbird/xulrunner/components/feeds.xpt
/home/matt/.Trash/Songbird/xulrunner/components/storage.xpt
/home/matt/.Trash/Songbird/xulrunner/components/dom_core.xpt
/home/matt/.Trash/Songbird/xulrunner/components/content_html.xpt
/home/matt/.Trash/Songbird/xulrunner/components/pipnss.xpt
/home/matt/.Trash/Songbird/xulrunner/components/necko_data.xpt
/home/matt/.Trash/Songbird/xulrunner/components/caps.xpt
/home/matt/.Trash/Songbird/xulrunner/components/content_xtf.xpt
/home/matt/.Trash/Songbird/xulrunner/components/layout_base.xpt
/home/matt/.Trash/Songbird/xulrunner/components/saxparser.xpt
/home/matt/.Trash/Songbird/xulrunner/components/libpippki.so
/home/matt/.Trash/Songbird/xulrunner/components/necko_strconv.xpt
/home/matt/.Trash/Songbird/xulrunner/components/mozgnome.xpt
/home/matt/.Trash/Songbird/xulrunner/components/xpcom_io.xpt
/home/matt/.Trash/Songbird/xulrunner/components/dom_range.xpt
/home/matt/.Trash/Songbird/xulrunner/components/commandlines.xpt
/home/matt/.Trash/Songbird/xulrunner/components/uriloader.xpt
/home/matt/.Trash/Songbird/xulrunner/components/necko_http.xpt
/home/matt/.Trash/Songbird/xulrunner/components/necko_file.xpt
/home/matt/.Trash/Songbird/xulrunner/components/toolkitprofile.xpt
/home/matt/.Trash/Songbird/xulrunner/components/necko_socket.xpt
/home/matt/.Trash/Songbird/xulrunner/components/downloads.xpt
/home/matt/.Trash/Songbird/xulrunner/components/webshell_idls.xpt
/home/matt/.Trash/Songbird/xulrunner/components/dom_xpath.xpt
/home/matt/.Trash/Songbird/xulrunner/components/necko_ftp.xpt
/home/matt/.Trash/Songbird/xulrunner/components/chardet.xpt
/home/matt/.Trash/Songbird/xulrunner/components/toolkitremote.xpt
/home/matt/.Trash/Songbird/xulrunner/components/dom_loadsave.xpt
/home/matt/.Trash/Songbird/xulrunner/components/htmlparser.xpt
/home/matt/.Trash/Songbird/xulrunner/components/necko_cookie.xpt
/home/matt/.Trash/Songbird/xulrunner/components/pipboot.xpt
/home/matt/.Trash/Songbird/xulrunner/components/nsCloseAllWindows.js
/home/matt/.Trash/Songbird/xulrunner/components/websrvcs.xpt
/home/matt/.Trash/Songbird/xulrunner/components/gfx.xpt
/home/matt/.Trash/Songbird/xulrunner/components/directory.xpt
/home/matt/.Trash/Songbird/xulrunner/components/progressDlg.xpt
/home/matt/.Trash/Songbird/xulrunner/components/satchel.xpt
/home/matt/.Trash/Songbird/xulrunner/components/proxyObjInst.xpt
/home/matt/.Trash/Songbird/xulrunner/components/xpcom_base.xpt
/home/matt/.Trash/Songbird/xulrunner/components/xultmpl.xpt
/home/matt/.Trash/Songbird/xulrunner/components/fastfind.xpt
/home/matt/.Trash/Songbird/xulrunner/components/layout_xul_tree.xpt
/home/matt/.Trash/Songbird/xulrunner/components/windowwatcher.xpt
/home/matt/.Trash/Songbird/xulrunner/components/nsFilePicker.js
/home/matt/.Trash/Songbird/xulrunner/components/exthandler.xpt
/home/matt/.Trash/Songbird/xulrunner/components/oji.xpt
/home/matt/.Trash/Songbird/xulrunner/components/pippki.xpt
/home/matt/.Trash/Songbird/xulrunner/components/nsUpdateService.js
/home/matt/.Trash/Songbird/xulrunner/components/plugin.xpt
/home/matt/.Trash/Songbird/xulrunner/components/xulapp.xpt
/home/matt/.Trash/Songbird/xulrunner/components/shistory.xpt
/home/matt/.Trash/Songbird/xulrunner/components/libmozgnome.so
/home/matt/.Trash/Songbird/xulrunner/components/dom_storage.xpt
/home/matt/.Trash/Songbird/xulrunner/components/prefetch.xpt
/home/matt/.Trash/Songbird/xulrunner/components/libpipnss.so
/home/matt/.Trash/Songbird/xulrunner/components/nsHelperAppDlg.js
/home/matt/.Trash/Songbird/xulrunner/components/alerts.xpt
/home/matt/.Trash/Songbird/xulrunner/components/dom_xul.xpt
/home/matt/.Trash/Songbird/xulrunner/components/venkman-service.js
/home/matt/.Trash/Songbird/xulrunner/components/libnkgnomevfs.so
/home/matt/.Trash/Songbird/xulrunner/components/commandhandler.xpt
/home/matt/.Trash/Songbird/xulrunner/components/jar.xpt
/home/matt/.Trash/Songbird/xulrunner/components/dom_events.xpt
/home/matt/.Trash/Songbird/xulrunner/components/nsDefaultCLH.js
/home/matt/.Trash/Songbird/xulrunner/components/libfileview.so
/home/matt/.Trash/Songbird/xulrunner/components/chrome.xpt
/home/matt/.Trash/Songbird/xulrunner/components/dom_sidebar.xpt
/home/matt/.Trash/Songbird/xulrunner/components/editor.xpt
/home/matt/.Trash/Songbird/xulrunner/components/embed_base.xpt
/home/matt/.Trash/Songbird/xulrunner/components/windowds.xpt
/home/matt/.Trash/Songbird/xulrunner/components/content_htmldoc.xpt
/home/matt/.Trash/Songbird/xulrunner/components/accessibility-atk.xpt
/home/matt/.Trash/Songbird/xulrunner/components/dom_views.xpt
/home/matt/.Trash/Songbird/xulrunner/components/mozfind.xpt
/home/matt/.Trash/Songbird/xulrunner/components/libsystem-pref.so
/home/matt/.Trash/Songbird/xulrunner/components/nsExtensionManager.js
/home/matt/.Trash/Songbird/xulrunner/components/content_base.xpt
/home/matt/.Trash/Songbird/xulrunner/components/xpconnect.xpt
/home/matt/.Trash/Songbird/xulrunner/components/xulapp_setup.xpt
/home/matt/.Trash/Songbird/xulrunner/components/layout_xul.xpt
/home/matt/.Trash/Songbird/xulrunner/components/libpipboot.so
/home/matt/.Trash/Songbird/xulrunner/components/history.xpt
/home/matt/.Trash/Songbird/xulrunner/components/libwebsrvcs.so
/home/matt/.Trash/Songbird/xulrunner/components/libautoconfig.so
/home/matt/.Trash/Songbird/xulrunner/components/libxulutil.so
/home/matt/.Trash/Songbird/xulrunner/components/necko_about.xpt
/home/matt/.Trash/Songbird/xulrunner/components/necko_res.xpt
/home/matt/.Trash/Songbird/xulrunner/components/xpcom_threads.xpt
/home/matt/.Trash/Songbird/xulrunner/components/dom_base.xpt
/home/matt/.Trash/Songbird/xulrunner/components/profile.xpt
/home/matt/.Trash/Songbird/xulrunner/components/extensions.xpt
/home/matt/.Trash/Songbird/xulrunner/components/xulrunner.xpt
/home/matt/.Trash/Songbird/xulrunner/components/webbrowserpersist.xpt
/home/matt/.Trash/Songbird/xulrunner/components/txtsvc.xpt
/home/matt/.Trash/Songbird/xulrunner/components/FeedProcessor.js
/home/matt/.Trash/Songbird/xulrunner/components/nsProxyAutoConfig.js
/home/matt/.Trash/Songbird/xulrunner/components/libxmlextras.so
/home/matt/.Trash/Songbird/xulrunner/components/dom_canvas.xpt
/home/matt/.Trash/Songbird/xulrunner/components/imglib2.xpt
/home/matt/.Trash/Songbird/xulrunner/components/nsDictionary.js
/home/matt/.Trash/Songbird/xulrunner/components/dom_svg.xpt
/home/matt/.Trash/Songbird/xulrunner/components/composer.xpt
/home/matt/.Trash/Songbird/xulrunner/components/find.xpt
/home/matt/.Trash/Songbird/xulrunner/components/docshell.xpt
/home/matt/.Trash/Songbird/xulrunner/components/libimgicon.so
/home/matt/.Trash/Songbird/xulrunner/components/dom_html.xpt
/home/matt/.Trash/Songbird/xulrunner/components/autocomplete.xpt
/home/matt/.Trash/Songbird/xulrunner/components/update.xpt
/home/matt/.Trash/Songbird/xulrunner/components/necko_dns.xpt
/home/matt/.Trash/Songbird/xulrunner/components/dom_traversal.xpt
/home/matt/.Trash/Songbird/xulrunner/components/widget.xpt
/home/matt/.Trash/Songbird/xulrunner/components/content_xmldoc.xpt
/home/matt/.Trash/Songbird/xulrunner/components/inspector.xpt
/home/matt/.Trash/Songbird/xulrunner/components/appstartup.xpt
/home/matt/.Trash/Songbird/xulrunner/components/nsXULAppInstall.js
/home/matt/.Trash/Songbird/xulrunner/components/nsInterfaceInfoToIDL.js
/home/matt/.Trash/Songbird/xulrunner/components/mozbrwsr.xpt
/home/matt/.Trash/Songbird/xulrunner/components/jsconsole-clhandler.js
/home/matt/.Trash/Songbird/xulrunner/components/necko.xpt
/home/matt/.Trash/Songbird/xulrunner/components/dom_stylesheets.xpt
/home/matt/.Trash/Songbird/xulrunner/components/xpinstall.xpt
/home/matt/.Trash/Songbird/xulrunner/components/imgicon.xpt
/home/matt/.Trash/Songbird/xulrunner/components/mimetype.xpt
/home/matt/.Trash/Songbird/xulrunner/components/layout_printing.xpt
/home/matt/.Trash/Songbird/xulrunner/components/urlformatter.xpt
/home/matt/.Trash/Songbird/xulrunner/components/autoconfig.xpt
/home/matt/.Trash/Songbird/xulrunner/components/xpcom_components.xpt
/home/matt/.Trash/Songbird/xulrunner/components/rdf.xpt
/home/matt/.Trash/Songbird/xulrunner/components/necko_viewsource.xpt
/home/matt/.Trash/Songbird/xulrunner/components/passwordmgr.xpt
/home/matt/.Trash/Songbird/xulrunner/components/filepicker.xpt
/home/matt/.Trash/Songbird/xulrunner/components/content_xslt.xpt
/home/matt/.Trash/Songbird/xulrunner/components/lwbrk.xpt
/home/matt/.Trash/Songbird/xulrunner/components/intl.xpt
/home/matt/.Trash/Songbird/xulrunner/components/xml-rpc.xpt
/home/matt/.Trash/Songbird/xulrunner/components/txmgr.xpt
/home/matt/.Trash/Songbird/xulrunner/components/xpcom_xpti.xpt
/home/matt/.Trash/Songbird/xulrunner/components/nsResetPref.js
/home/matt/.Trash/Songbird/xulrunner/components/nsXmlRpcClient.js
/home/matt/.Trash/Songbird/xulrunner/components/necko_cache.xpt
/home/matt/.Trash/Songbird/xulrunner/components/gksvgrenderer.xpt
/home/matt/.Trash/Songbird/xulrunner/components/webBrowser_core.xpt
/home/matt/.Trash/Songbird/xulrunner/components/nsProgressDialog.js
/home/matt/.Trash/Songbird/xulrunner/components/locale.xpt
/home/matt/.Trash/Songbird/xulrunner/components/xuldoc.xpt
/home/matt/.Trash/Songbird/xulrunner/components/pref.xpt
/home/matt/.Trash/Songbird/xulrunner/components/dom_css.xpt
/home/matt/.Trash/Songbird/xulrunner/components/libauth.so
/home/matt/.Trash/Songbird/xulrunner/components/xpcom_obsolete.xpt
/home/matt/.Trash/Songbird/xulrunner/components/libuniversalchardet.so
/home/matt/.Trash/Songbird/xulrunner/components/accessibility.xpt
/home/matt/.Trash/Songbird/xulrunner/components/uconv.xpt
/home/matt/.Trash/Songbird/xulrunner/components/jsdservice.xpt
/home/matt/.Trash/Songbird/xulrunner/components/xpcom_ds.xpt
/home/matt/.Trash/Songbird/xulrunner/components/nsKillAll.js
/home/matt/.Trash/Songbird/xulrunner/components/libtransformiix.so
/home/matt/.Trash/Songbird/xulrunner/components/unicharutil.xpt
/home/matt/.Trash/Songbird/xulrunner/components/nsURLFormatter.js
/home/matt/.Trash/Songbird/xulrunner/defaults
/home/matt/.Trash/Songbird/xulrunner/defaults/pref
/home/matt/.Trash/Songbird/xulrunner/defaults/pref/xulrunner.js
/home/matt/.Trash/Songbird/xulrunner/defaults/autoconfig
/home/matt/.Trash/Songbird/xulrunner/defaults/autoconfig/prefcalls.js
/home/matt/.Trash/Songbird/xulrunner/defaults/autoconfig/platform.js
/home/matt/.Trash/Songbird/xulrunner/defaults/profile
/home/matt/.Trash/Songbird/xulrunner/defaults/profile/US
/home/matt/.Trash/Songbird/xulrunner/defaults/profile/US/chrome
/home/matt/.Trash/Songbird/xulrunner/defaults/profile/US/chrome/userChrome-example.css
/home/matt/.Trash/Songbird/xulrunner/defaults/profile/US/chrome/userContent-example.css
/home/matt/.Trash/Songbird/xulrunner/defaults/profile/US/localstore.rdf
/home/matt/.Trash/Songbird/xulrunner/defaults/profile/chrome
/home/matt/.Trash/Songbird/xulrunner/defaults/profile/chrome/userChrome-example.css
/home/matt/.Trash/Songbird/xulrunner/defaults/profile/chrome/userContent-example.css
/home/matt/.Trash/Songbird/xulrunner/defaults/profile/localstore.rdf
/home/matt/.Trash/Songbird/xulrunner/dependentlibs.list
/home/matt/.Trash/Songbird/xulrunner/elf-dynstr-gc
/home/matt/.Trash/Songbird/xulrunner/extensions
/home/matt/.Trash/Songbird/xulrunner/extensions/inspector@mozilla.org
/home/matt/.Trash/Songbird/xulrunner/extensions/inspector@mozilla.org/components
/home/matt/.Trash/Songbird/xulrunner/extensions/inspector@mozilla.org/components/inspector-cmdline.js
/home/matt/.Trash/Songbird/xulrunner/extensions/inspector@mozilla.org/chrome.manifest
/home/matt/.Trash/Songbird/xulrunner/extensions/inspector@mozilla.org/defaults
/home/matt/.Trash/Songbird/xulrunner/extensions/inspector@mozilla.org/defaults/preferences
/home/matt/.Trash/Songbird/xulrunner/extensions/inspector@mozilla.org/defaults/preferences/inspector.js
/home/matt/.Trash/Songbird/xulrunner/extensions/inspector@mozilla.org/install.rdf
/home/matt/.Trash/Songbird/xulrunner/extensions/inspector@mozilla.org/chrome
/home/matt/.Trash/Songbird/xulrunner/extensions/inspector@mozilla.org/chrome/chromelist.txt
/home/matt/.Trash/Songbird/xulrunner/extensions/inspector@mozilla.org/chrome/inspector.jar
/home/matt/.Trash/Songbird/xulrunner/extensions/dove@songbirdnest.com
/home/matt/.Trash/Songbird/xulrunner/extensions/dove@songbirdnest.com/chrome.manifest
/home/matt/.Trash/Songbird/xulrunner/extensions/dove@songbirdnest.com/dove.jar
/home/matt/.Trash/Songbird/xulrunner/extensions/dove@songbirdnest.com/install.rdf
/home/matt/.Trash/Songbird/xulrunner/extensions/rubberducky@songbirdnest.com
/home/matt/.Trash/Songbird/xulrunner/extensions/rubberducky@songbirdnest.com/install.rdf
/home/matt/.Trash/Songbird/xulrunner/extensions/rubberducky@songbirdnest.com/chrome.manifest
/home/matt/.Trash/Songbird/xulrunner/extensions/classic@songbirdnest.com
/home/matt/.Trash/Songbird/xulrunner/extensions/classic@songbirdnest.com/chrome.manifest
/home/matt/.Trash/Songbird/xulrunner/extensions/classic@songbirdnest.com/classic.jar
/home/matt/.Trash/Songbird/xulrunner/extensions/classic@songbirdnest.com/install.rdf
/home/matt/.Trash/Songbird/xulrunner/greprefs
/home/matt/.Trash/Songbird/xulrunner/greprefs/all.js
/home/matt/.Trash/Songbird/xulrunner/greprefs/security-prefs.js
/home/matt/.Trash/Songbird/xulrunner/greprefs/xpinstall.js
/home/matt/.Trash/Songbird/xulrunner/icons
/home/matt/.Trash/Songbird/xulrunner/icons/document.png
/home/matt/.Trash/Songbird/xulrunner/icons/mozicon16.xpm
/home/matt/.Trash/Songbird/xulrunner/icons/mozicon50.xpm
/home/matt/.Trash/Songbird/xulrunner/libfreebl3.chk
/home/matt/.Trash/Songbird/xulrunner/libfreebl3.so
/home/matt/.Trash/Songbird/xulrunner/libgtkembedmoz.so
/home/matt/.Trash/Songbird/xulrunner/libmozjs.so
/home/matt/.Trash/Songbird/xulrunner/libnspr4.so
/home/matt/.Trash/Songbird/xulrunner/libnss3.so
/home/matt/.Trash/Songbird/xulrunner/libnssckbi.so
/home/matt/.Trash/Songbird/xulrunner/libplc4.so
/home/matt/.Trash/Songbird/xulrunner/libplds4.so
/home/matt/.Trash/Songbird/xulrunner/libsmime3.so
/home/matt/.Trash/Songbird/xulrunner/libsoftokn3.chk
/home/matt/.Trash/Songbird/xulrunner/libsoftokn3.so
/home/matt/.Trash/Songbird/xulrunner/libssl3.so
/home/matt/.Trash/Songbird/xulrunner/libxpcom.so
/home/matt/.Trash/Songbird/xulrunner/libxul.so
/home/matt/.Trash/Songbird/xulrunner/LICENSE
/home/matt/.Trash/Songbird/xulrunner/mangle
/home/matt/.Trash/Songbird/xulrunner/mozilla-installer-bin
/home/matt/.Trash/Songbird/xulrunner/mozilla-xremote-client
/home/matt/.Trash/Songbird/xulrunner/nsinstall
/home/matt/.Trash/Songbird/xulrunner/plugins
/home/matt/.Trash/Songbird/xulrunner/plugins/libnullplugin.so
/home/matt/.Trash/Songbird/xulrunner/plugins/libunixprintplugin.so
/home/matt/.Trash/Songbird/xulrunner/README.txt
/home/matt/.Trash/Songbird/xulrunner/regxpcom
/home/matt/.Trash/Songbird/xulrunner/res
/home/matt/.Trash/Songbird/xulrunner/res/table-add-column-after-active.gif
/home/matt/.Trash/Songbird/xulrunner/res/table-add-column-before-hover.gif
/home/matt/.Trash/Songbird/xulrunner/res/table-add-row-before-active.gif
/home/matt/.Trash/Songbird/xulrunner/res/forms.css
/home/matt/.Trash/Songbird/xulrunner/res/EditorOverride.css
/home/matt/.Trash/Songbird/xulrunner/res/table-remove-row-active.gif
/home/matt/.Trash/Songbird/xulrunner/res/charsetalias.properties
/home/matt/.Trash/Songbird/xulrunner/res/arrow.gif
/home/matt/.Trash/Songbird/xulrunner/res/html
/home/matt/.Trash/Songbird/xulrunner/res/html/gopher-telnet.gif
/home/matt/.Trash/Songbird/xulrunner/res/html/gopher-find.gif
/home/matt/.Trash/Songbird/xulrunner/res/html/gopher-menu.gif
/home/matt/.Trash/Songbird/xulrunner/res/html/gopher-unknown.gif
/home/matt/.Trash/Songbird/xulrunner/res/html/gopher-text.gif
/home/matt/.Trash/Songbird/xulrunner/res/html/gopher-sound.gif
/home/matt/.Trash/Songbird/xulrunner/res/html/gopher-image.gif
/home/matt/.Trash/Songbird/xulrunner/res/html/gopher-audio.gif
/home/matt/.Trash/Songbird/xulrunner/res/html/gopher-binary.gif
/home/matt/.Trash/Songbird/xulrunner/res/html/gopher-movie.gif
/home/matt/.Trash/Songbird/xulrunner/res/svg.css
/home/matt/.Trash/Songbird/xulrunner/res/fonts
/home/matt/.Trash/Songbird/xulrunner/res/fonts/mathfontSymbol.properties
/home/matt/.Trash/Songbird/xulrunner/res/fonts/mathfontPUA.properties
/home/matt/.Trash/Songbird/xulrunner/res/fonts/mathfontMath4.properties
/home/matt/.Trash/Songbird/xulrunner/res/fonts/mathfontCMSY10.properties
/home/matt/.Trash/Songbird/xulrunner/res/fonts/mathfontMath2.properties
/home/matt/.Trash/Songbird/xulrunner/res/fonts/mathfontMath1.properties
/home/matt/.Trash/Songbird/xulrunner/res/fonts/pangoFontEncoding.properties
/home/matt/.Trash/Songbird/xulrunner/res/fonts/fontEncoding.properties
/home/matt/.Trash/Songbird/xulrunner/res/fonts/mathfontCMEX10.properties
/home/matt/.Trash/Songbird/xulrunner/res/fonts/mathfontMTExtra.properties
/home/matt/.Trash/Songbird/xulrunner/res/fonts/mathfont.properties
/home/matt/.Trash/Songbird/xulrunner/res/langGroups.properties
/home/matt/.Trash/Songbird/xulrunner/res/charsetData.properties
/home/matt/.Trash/Songbird/xulrunner/res/cmessage.txt
/home/matt/.Trash/Songbird/xulrunner/res/table-remove-row-hover.gif
/home/matt/.Trash/Songbird/xulrunner/res/table-remove-column-hover.gif
/home/matt/.Trash/Songbird/xulrunner/res/table-add-column-after.gif
/home/matt/.Trash/Songbird/xulrunner/res/sample.unixpsfonts.properties
/home/matt/.Trash/Songbird/xulrunner/res/table-add-row-after-active.gif
/home/matt/.Trash/Songbird/xulrunner/res/table-add-row-after.gif
/home/matt/.Trash/Songbird/xulrunner/res/table-add-row-after-hover.gif
/home/matt/.Trash/Songbird/xulrunner/res/grabber.gif
/home/matt/.Trash/Songbird/xulrunner/res/language.properties
/home/matt/.Trash/Songbird/xulrunner/res/table-add-row-before.gif
/home/matt/.Trash/Songbird/xulrunner/res/table-add-column-after-hover.gif
/home/matt/.Trash/Songbird/xulrunner/res/bloatcycle.html
/home/matt/.Trash/Songbird/xulrunner/res/viewer.properties
/home/matt/.Trash/Songbird/xulrunner/res/entityTables
/home/matt/.Trash/Songbird/xulrunner/res/entityTables/html40Latin1.properties
/home/matt/.Trash/Songbird/xulrunner/res/entityTables/transliterate.properties
/home/matt/.Trash/Songbird/xulrunner/res/entityTables/mathml20.properties
/home/matt/.Trash/Songbird/xulrunner/res/entityTables/html40Special.properties
/home/matt/.Trash/Songbird/xulrunner/res/entityTables/htmlEntityVersions.properties
/home/matt/.Trash/Songbird/xulrunner/res/entityTables/html40Symbols.properties
/home/matt/.Trash/Songbird/xulrunner/res/samples
/home/matt/.Trash/Songbird/xulrunner/res/samples/treeTest1.css
/home/matt/.Trash/Songbird/xulrunner/res/samples/test1.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/test6.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/test_pr.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/printsetup.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/test14.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/bg.jpg
/home/matt/.Trash/Songbird/xulrunner/res/samples/image_props.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/test_lbox.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/Anieyes.gif
/home/matt/.Trash/Songbird/xulrunner/res/samples/test2.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/test5.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/test10.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/toolbarTest1.xul
/home/matt/.Trash/Songbird/xulrunner/res/samples/test3.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/test8-1.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/sliderTest1.xul
/home/matt/.Trash/Songbird/xulrunner/res/samples/raptor.jpg
/home/matt/.Trash/Songbird/xulrunner/res/samples/test7.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/gear1.gif
/home/matt/.Trash/Songbird/xulrunner/res/samples/treeTest1.xul
/home/matt/.Trash/Songbird/xulrunner/res/samples/test15.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/test8tab.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/scrollbarTest2.xul
/home/matt/.Trash/Songbird/xulrunner/res/samples/test_gfx.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/test_ed.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/test_form.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/test0.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/test16.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/cform.css
/home/matt/.Trash/Songbird/xulrunner/res/samples/find.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/checkboxTest.xul
/home/matt/.Trash/Songbird/xulrunner/res/samples/test13.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/test.wav
/home/matt/.Trash/Songbird/xulrunner/res/samples/xulTest.css
/home/matt/.Trash/Songbird/xulrunner/res/samples/test9b.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/bform.css
/home/matt/.Trash/Songbird/xulrunner/res/samples/scrollbarTest1.xul
/home/matt/.Trash/Songbird/xulrunner/res/samples/test8.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/mozform.css
/home/matt/.Trash/Songbird/xulrunner/res/samples/test_weight.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/demoform.css
/home/matt/.Trash/Songbird/xulrunner/res/samples/test8siz.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/test12.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/rock_gra.gif
/home/matt/.Trash/Songbird/xulrunner/res/samples/soundtest.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/test11.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/test9a.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/test8dom.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/beeptest.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/aform.css
/home/matt/.Trash/Songbird/xulrunner/res/samples/test9.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/test4.html
/home/matt/.Trash/Songbird/xulrunner/res/samples/test8sca.html
/home/matt/.Trash/Songbird/xulrunner/res/table-add-column-before.gif
/home/matt/.Trash/Songbird/xulrunner/res/arrowd.gif
/home/matt/.Trash/Songbird/xulrunner/res/quirk.css
/home/matt/.Trash/Songbird/xulrunner/res/throbber
/home/matt/.Trash/Songbird/xulrunner/res/throbber/anims27.gif
/home/matt/.Trash/Songbird/xulrunner/res/throbber/anims24.gif
/home/matt/.Trash/Songbird/xulrunner/res/throbber/anims09.gif
/home/matt/.Trash/Songbird/xulrunner/res/throbber/anims28.gif
/home/matt/.Trash/Songbird/xulrunner/res/throbber/anims18.gif
/home/matt/.Trash/Songbird/xulrunner/res/throbber/anims03.gif
/home/matt/.Trash/Songbird/xulrunner/res/throbber/anim.gif
/home/matt/.Trash/Songbird/xulrunner/res/throbber/anims21.gif
/home/matt/.Trash/Songbird/xulrunner/res/throbber/anims15.gif
/home/matt/.Trash/Songbird/xulrunner/res/throbber/anims04.gif
/home/matt/.Trash/Songbird/xulrunner/res/throbber/anims08.gif
/home/matt/.Trash/Songbird/xulrunner/res/throbber/anims20.gif
/home/matt/.Trash/Songbird/xulrunner/res/throbber/anims11.gif
/home/matt/.Trash/Songbird/xulrunner/res/throbber/anims22.gif
/home/matt/.Trash/Songbird/xulrunner/res/throbber/anims29.gif
/home/matt/.Trash/Songbird/xulrunner/res/throbber/anims12.gif
/home/matt/.Trash/Songbird/xulrunner/res/throbber/anims19.gif
/home/matt/.Trash/Songbird/xulrunner/res/throbber/anims14.gif
/home/matt/.Trash/Songbird/xulrunner/res/throbber/anims00.gif
/home/matt/.Trash/Songbird/xulrunner/res/throbber/anims01.gif
/home/matt/.Trash/Songbird/xulrunner/res/throbber/anims25.gif
/home/matt/.Trash/Songbird/xulrunner/res/throbber/anims23.gif
/home/matt/.Trash/Songbird/xulrunner/res/throbber/anims05.gif
/home/matt/.Trash/Songbird/xulrunner/res/throbber/anims17.gif
/home/matt/.Trash/Songbird/xulrunner/res/throbber/anims13.gif
/home/matt/.Trash/Songbird/xulrunner/res/throbber/anims02.gif
/home/matt/.Trash/Songbird/xulrunner/res/throbber/anims16.gif
/home/matt/.Trash/Songbird/xulrunner/res/throbber/anims06.gif
/home/matt/.Trash/Songbird/xulrunner/res/throbber/anims26.gif
/home/matt/.Trash/Songbird/xulrunner/res/throbber/anims10.gif
/home/matt/.Trash/Songbird/xulrunner/res/throbber/anims07.gif
/home/matt/.Trash/Songbird/xulrunner/res/unixcharset.properties
/home/matt/.Trash/Songbird/xulrunner/res/viewsource.css
/home/matt/.Trash/Songbird/xulrunner/res/mathml.css
/home/matt/.Trash/Songbird/xulrunner/res/table-add-row-before-hover.gif
/home/matt/.Trash/Songbird/xulrunner/res/loading-image.gif
/home/matt/.Trash/Songbird/xulrunner/res/table-remove-column.gif
/home/matt/.Trash/Songbird/xulrunner/res/ua.css
/home/matt/.Trash/Songbird/xulrunner/res/table-remove-row.gif
/home/matt/.Trash/Songbird/xulrunner/res/table-add-column-before-active.gif
/home/matt/.Trash/Songbird/xulrunner/res/table-remove-column-active.gif
/home/matt/.Trash/Songbird/xulrunner/res/html.css
/home/matt/.Trash/Songbird/xulrunner/res/hiddenWindow.html
/home/matt/.Trash/Songbird/xulrunner/res/dtd
/home/matt/.Trash/Songbird/xulrunner/res/dtd/xhtml11.dtd
/home/matt/.Trash/Songbird/xulrunner/res/dtd/mathml.dtd
/home/matt/.Trash/Songbird/xulrunner/res/broken-image.gif
/home/matt/.Trash/Songbird/xulrunner/run-mozilla.sh
/home/matt/.Trash/Songbird/xulrunner/shlibsign
/home/matt/.Trash/Songbird/xulrunner/TestGtkEmbed
/home/matt/.Trash/Songbird/xulrunner/updater
/home/matt/.Trash/Songbird/xulrunner/xpcshell
/home/matt/.Trash/Songbird/xulrunner/xpicleanup
/home/matt/.Trash/Songbird/xulrunner/xpidl
/home/matt/.Trash/Songbird/xulrunner/xpt_dump
/home/matt/.Trash/Songbird/xulrunner/xpt_link
/home/matt/.Trash/Songbird/xulrunner/xulrunner
/home/matt/.Trash/Songbird/xulrunner/xulrunner-bin
/home/matt/.Trash/Songbird/xulrunner/xulrunner-config
/home/matt/.Trash/Songbird/xulrunner/libid3-3.8.so.3.0.0
/home/matt/.Trash/Songbird/xulrunner/libid3-3.8.so.3
/home/matt/.Trash/Songbird/xulrunner/libid3.so
/home/matt/.Trash/Songbird/xulrunner/updates
/home/matt/.Trash/Songbird/xulrunner/updates/0
/usr/lib/xulrunner
/usr/lib/xulrunner/libnssckbi.so
/usr/lib/xulrunner/libfreebl3.so
/usr/lib/xulrunner/libfreebl3.chk

```

---

### Post by FuturePilot on 2007-09-17
It looks like half of the songbird install ended up in the Trash somehow.
I would highly recommend installing it with this script.
[http://www.psychocats.net/ubuntu/songbird]("http://www.psychocats.net/ubuntu/songbird")

---

### Post by forestpixie on 2007-09-17
I did it that way > I installed by downloading the tar.gz - it put it in a hidden folder in my home folder - ran a desktop launcher from there - think it was a ,sh file - worked fine until I deleted it :)

---

### Post by mlhudson on 2007-09-17
So, I installed from the script and am now getting

 "Could not launch menu item - Failed to execute child process "Songbird" (No such file or directory)"

I moved the Songbird folder out of the trash, and I can reinstall the file from the extracted folder and it runs...but, if I close it, I can't launch it again - - probably because I'm green & am missing the obvious. 

So, I've unstalled the script version.

---

