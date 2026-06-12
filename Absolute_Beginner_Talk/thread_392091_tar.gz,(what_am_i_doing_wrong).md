---
title: "tar.gz,(what am i doing wrong)"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by STREETURCHINE on 2007-03-24
ok i am trying to install flock,i have gotten to here

```
rex@rex-rex:~$ cd
flock/
flock/.autoreg
flock/chrome/
flock/chrome/en-US.jar
flock/chrome/en-US.manifest
flock/chrome/browser.jar
flock/chrome/browser.manifest
flock/chrome/classic.jar
flock/chrome/classic.manifest
flock/chrome/comm.jar
flock/chrome/comm.manifest
flock/chrome/toolkit.jar
flock/chrome/toolkit.manifest
flock/chrome/icons/
flock/chrome/icons/default/
flock/chrome/icons/default/default.xpm
flock/chrome/spellbound.jar
flock/chrome/spellbound.manifest
flock/chrome/fbranding.jar
flock/chrome/fbranding.manifest
flock/chrome/installed-chrome.txt
flock/chrome/pippki.jar
flock/chrome/pippki.manifest
flock/defaults/
flock/defaults/pref/
flock/defaults/pref/firefox-l10n.js
flock/defaults/pref/flock.js
flock/defaults/pref/fbranding-prefs.js
flock/defaults/profile/
flock/defaults/profile/bookmarks.html
flock/defaults/profile/localstore.rdf
flock/defaults/profile/prefs.js
flock/defaults/profile/search.rdf
flock/defaults/profile/mimeTypes.rdf
flock/defaults/profile/chrome/
flock/defaults/profile/chrome/userChrome-example.css
flock/defaults/profile/chrome/userContent-example.css
flock/defaults/autoconfig/
flock/defaults/autoconfig/platform.js
flock/defaults/autoconfig/prefcalls.js
flock/browserconfig.properties
flock/searchplugins/
flock/searchplugins/amazondotcom.png
flock/searchplugins/amazondotcom.src
flock/searchplugins/eBay.gif
flock/searchplugins/eBay.src
flock/searchplugins/google.gif
flock/searchplugins/google.src
flock/searchplugins/jajah.gif
flock/searchplugins/jajah.src
flock/searchplugins/jeeves.gif
flock/searchplugins/jeeves.src
flock/searchplugins/shadows.gif
flock/searchplugins/shadows.src
flock/searchplugins/technorati.png
flock/searchplugins/technorati.src
flock/searchplugins/wikipedia.png
flock/searchplugins/wikipedia.src
flock/searchplugins/winkflock.png
flock/searchplugins/winkflock.src
flock/searchplugins/yahoo.gif
flock/searchplugins/yahoo.src
flock/updater.ini
flock/libmozjs.so
flock/libplc4.so
flock/libplds4.so
flock/libxpcom.so
flock/libxpcom_core.so
flock/libxpistub.so
flock/libnspr4.so
flock/components/
flock/components/libxpinstall.so
flock/components/libxpcomclucene.so
flock/components/libflockFeedService.so
flock/components/libimgscaler.so
flock/components/libhtml2xhtml.so
flock/components/libhtml2text.so
flock/components/libspellchecker.so
flock/components/libmyspell.so
flock/components/libjsd.so
flock/components/myspell/
flock/components/myspell/en-US.aff
flock/components/myspell/en-US.dic
flock/components/flockCluster.js
flock/components/flockScrapbookService.js
flock/components/flockBlogService.js
flock/components/flockBlogWebServiceMovabletype.js
flock/components/flockBlogWebServiceAtom.js
flock/components/flockBlogWebServiceBlogger.js
flock/components/xmlrpc.js.lib
flock/components/flockError.js
flock/components/flockLogger.js
flock/components/flockPhotoAPIManager.js
flock/components/flockPhotoPeopleService.js
flock/components/flockPhotoPerson.js
flock/components/flockPhoto.js
flock/components/flockPhotoAlbum.js
flock/components/flockPhotoAccount.js
flock/components/flockPhotoUpload.js
flock/components/flockPhotoUploadService.js
flock/components/flockPhotoAPIFlickr.js
flock/components/flockPhotoAPIPhotoBucket.js
flock/components/flockFavoritesQueue.js
flock/components/flockFavoritesService.js
flock/components/flockFavoritesWebServiceDelicious.js
flock/components/flockFavoritesWebServiceShadows.js
flock/components/flockFeedProtocol.js
flock/components/flockFeedService.js
flock/components/flockFeedUtility.js
flock/components/flockOpmlProtocol.js
flock/components/flockOpmlService.js
flock/components/flockLuceneIndexer.js
flock/components/flockXmlRpcHelper.js.lib
flock/components/flockXmlRpc.js
flock/components/flockXPCOMTemplate.js.lib
flock/components/mnChromeMessenger.js
flock/components/nsBrowserContentHandler.js
flock/components/nsSetDefaultBrowser.js
flock/components/jsconsole-clhandler.js
flock/components/nsCloseAllWindows.js
flock/components/nsDictionary.js
flock/components/nsFilePicker.js
flock/components/nsInterfaceInfoToIDL.js
flock/components/nsProxyAutoConfig.js
flock/components/nsSidebar.js
flock/components/nsXmlRpcClient.js
flock/components/nsExtensionManager.js
flock/components/nsUpdateService.js
flock/components/nsBrowserGlue.js
flock/components/nsDefaultCLH.js
flock/components/nsHelperAppDlg.js
flock/components/nsKillAll.js
flock/components/nsProgressDialog.js
flock/components/nsResetPref.js
flock/components/libmozgnome.so
flock/components/libnkgnomevfs.so
flock/components/browser.xpt
flock/libxpcom_compat.so
flock/flock-bin
flock/flock
flock/gm
flock/mozilla-xremote-client
flock/run-mozilla.sh
flock/plugins/
flock/plugins/libnullplugin.so
flock/res/
flock/res/cmessage.txt
flock/res/hiddenWindow.html
flock/res/ua.css
flock/res/html.css
flock/res/quirk.css
flock/res/forms.css
flock/res/EditorOverride.css
flock/res/table-add-column-after-active.gif
flock/res/table-add-column-after-hover.gif
flock/res/table-add-column-after.gif
flock/res/table-add-column-before-active.gif
flock/res/table-add-column-before-hover.gif
flock/res/table-add-column-before.gif
flock/res/table-add-row-after-active.gif
flock/res/table-add-row-after-hover.gif
flock/res/table-add-row-after.gif
flock/res/table-add-row-before-active.gif
flock/res/table-add-row-before-hover.gif
flock/res/table-add-row-before.gif
flock/res/table-remove-column-active.gif
flock/res/table-remove-column-hover.gif
flock/res/table-remove-column.gif
flock/res/table-remove-row-active.gif
flock/res/table-remove-row-hover.gif
flock/res/table-remove-row.gif
flock/res/arrowd.gif
flock/res/grabber.gif
flock/res/viewsource.css
flock/res/mathml.css
flock/res/arrow.gif
flock/res/loading-image.gif
flock/res/broken-image.gif
flock/res/fonts/
flock/res/fonts/fontEncoding.properties
flock/res/fonts/mathfont.properties
flock/res/fonts/mathfontCMEX10.properties
flock/res/fonts/mathfontCMSY10.properties
flock/res/fonts/mathfontMath1.properties
flock/res/fonts/mathfontMath2.properties
flock/res/fonts/mathfontMath4.properties
flock/res/fonts/mathfontMTExtra.properties
flock/res/fonts/mathfontPUA.properties
flock/res/fonts/mathfontSymbol.properties
flock/res/fonts/pangoFontEncoding.properties
flock/res/dtd/
flock/res/dtd/mathml.dtd
flock/res/dtd/xhtml11.dtd
flock/res/html/
flock/res/html/gopher-audio.gif
flock/res/html/gopher-binary.gif
flock/res/html/gopher-find.gif
flock/res/html/gopher-image.gif
flock/res/html/gopher-menu.gif
flock/res/html/gopher-movie.gif
flock/res/html/gopher-sound.gif
flock/res/html/gopher-telnet.gif
flock/res/html/gopher-text.gif
flock/res/html/gopher-unknown.gif
flock/res/unixcharset.properties
flock/res/charsetalias.properties
flock/res/charsetData.properties
flock/res/langGroups.properties
flock/res/language.properties
flock/res/entityTables/
flock/res/entityTables/html40Latin1.properties
flock/res/entityTables/html40Special.properties
flock/res/entityTables/html40Symbols.properties
flock/res/entityTables/htmlEntityVersions.properties
flock/res/entityTables/mathml20.properties
flock/res/entityTables/transliterate.properties
flock/res/svg.css
flock/xpicleanup
flock/extensions/
flock/extensions/{b01bf10c-302a-11da-b67b-000d60ca027b}/
flock/extensions/{b01bf10c-302a-11da-b67b-000d60ca027b}/install.rdf
flock/icons/
flock/icons/mozicon16.xpm
flock/icons/mozicon50.xpm
flock/icons/document.png
flock/icons/mozicon128.png
flock/greprefs/
flock/greprefs/all.js
flock/greprefs/security-prefs.js
flock/greprefs/xpinstall.js
flock/libnssckbi.so
flock/libnss3.so
flock/libsmime3.so
flock/libsoftokn3.chk
flock/libsoftokn3.so
flock/libfreebl3.chk
flock/libfreebl3.so
flock/libssl3.so
flock/updater
rex@rex-rex:~$ 


```

then i try to configure

```
rex@rex-rex:~$ cd '/home/rex/flock' 
rex@rex-rex:~/flock$ ./configure
bash: ./configure: No such file or directory
rex@rex-rex:~/flock$ 


```

tried checkinstall


 ```
rex@rex-rex:~/flock$ sudo checkinstall 

checkinstall 1.6.0, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

*** No known documentation files were found. The new package 
*** won't include a documentation directory.

*****************************************
**** Debian package creation selected ***
*****************************************
/usr/bin/checkinstall: line 1151: dpkg-architecture: command not found

This package will be built according to these values: 

0 -  Maintainer: [ root@rex-rex ]
1 -  Summary: [ browse the world wide web. ]
2 -  Name:    [ flock ]
3 -  Version: [ 20070324 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ flock ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

rex@rex-rex:~/flock$ sudo chekinstall flock-0.7.12
sudo: chekinstall: command not found
re
```

so what stage am i missing ,

ps i know checkinstall was probably not needed but i have been trying to work out what command to give  as there are no readme files with the tar.gz

---

### Post by xopher on 2007-03-24
That seems to be a java program - and the only thing you need for it to run is Java, so you should be able to run it 'as is', without configuring and installing it first, which, as you probably noticed, didn't work anyway.

---

### Post by jordanmthomas on 2007-03-24
To install flock, just copy the flock directory (that you just created upon extraction) into /opt
```
tar xvzf whateverflockis.tar.gz
sudo mv flock /opt
sudo ln -s /opt/flock/flock /usr/bin/flock
```

After this, you'll be able to run flock just by typing flock at the command line or creating a launcher to launch flock or whatever.

**edit** and I don't think flock requires java.  It's basically just firefox.

---

### Post by STREETURCHINE on 2007-03-24
> **jordanmthomas said:**
> To install flock, just copy the flock directory (that you just created upon extraction) into /opt
```
tar xvzf whateverflockis.tar.gz
sudo mv flock /opt
sudo ln -s /opt/flock/flock /usr/bin/flock
```

After this, you'll be able to run flock just by typing flock at the command line or creating a launcher to launch flock or whatever.

**edit** and I don't think flock requires java.  It's basically just firefox.

thanks that sorted it out created the launcher all is well :)

---

