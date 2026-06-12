---
title: "Com instal·lar Firefox 3 amb tots els plugins"
date: 2010-04-10
forum: Catalan Team
---

### Post by ximoberna on 2010-04-10
Aquesta setmana m'he trobat amb el problema d'actualitzar el Firefox a la darrera versió i m'he enrecordat que no l'havia compartit amb la resta de la comunitat ubuntaire. Vet aquí la meua experiència que des de fa anys em permet tenir actualitzat en linux el navegador Firefox.

Primer anem a rebost del [Sofcatalà]("http://www.softcatala.org/wiki/Rebost:Firefox") (o [Softvalencià]("http://www.softvalencia.org/guies/firefox-en-valencia/")... Encara que a mi em funciona en valencià gràcies al [paquet català-valencià]("http://www.softcatala.org/wiki/Rebost:Paquet_catal%C3%A0_%28valenci%C3%A0%29_per_al_Firefox") del del rebost de Softcatalà; tot fent-lo còrrer una volta instal·lat per primera volta el navegador, després tot rutlla automàticament ;) 

Segon ens fiquem en un Terminal i fem això:

```

usuari@usuari-desktop:~$ sudo su

[sudo] password for usuari: 

root@usuari-desktop:/home/usuari# cd /opt/firefox/

root@usuari-desktop:/opt/firefox# rm -rf *

root@usuari-desktop:/opt/firefox# tar -xvf /home/usuari/Baixades/firefox-3.6.3.tar.bz2 -C /opt/

tar: Record size = 8 blocks

firefox/

firefox/update.locale

firefox/plugins/

firefox/plugins/libnullplugin.so

firefox/Throbber-small.gif

firefox/components/

firefox/components/nsSessionStore.js

firefox/components/components.list

firefox/components/nsFilePicker.js

firefox/components/nsBadCertHandler.js

firefox/components/libmozgnome.so

firefox/components/browser.xpt

firefox/components/libbrowserdirprovider.so

firefox/components/nsPrivateBrowsingService.js

firefox/components/nsTryToClose.js

firefox/components/FeedProcessor.js

firefox/components/pluginGlue.js

firefox/components/txEXSLTRegExFunctions.js

firefox/components/nsHelperAppDlg.js

firefox/components/nsPlacesTransactionsService.js

firefox/components/nsMicrosummaryService.js

firefox/components/nsTaggingService.js

firefox/components/nsUpdateServiceStub.js

firefox/components/nsBrowserContentHandler.js

firefox/components/nsBlocklistService.js

firefox/components/nsSearchService.js

firefox/components/nsSidebar.js

firefox/components/nsDefaultCLH.js

firefox/components/nsWebHandlerApp.js

firefox/components/nsLoginManager.js

firefox/components/nsUpdateService.js

firefox/components/nsUrlClassifierLib.js

firefox/components/nsUpdateTimerManager.js

firefox/components/nsSetDefaultBrowser.js

firefox/components/nsDownloadManagerUI.js

firefox/components/nsSafebrowsingApplication.js

firefox/components/nsUrlClassifierListManager.js

firefox/components/nsSearchSuggestions.js

firefox/components/NetworkGeolocationProvider.js

firefox/components/storage-mozStorage.js

firefox/components/fuelApplication.js

firefox/components/nsContentDispatchChooser.js

firefox/components/nsLivemarkService.js

firefox/components/GPSDGeolocationProvider.js

firefox/components/jsconsole-clhandler.js

firefox/components/nsExtensionManager.js

firefox/components/nsURLFormatter.js

firefox/components/nsFormAutoComplete.js

firefox/components/nsSessionStartup.js

firefox/components/storage-Legacy.js

firefox/components/FeedConverter.js

firefox/components/libdbusservice.so

firefox/components/FeedWriter.js

firefox/components/libbrowsercomps.so

firefox/components/nsPlacesDBFlush.js

firefox/components/nsPlacesAutoComplete.js

firefox/components/nsProxyAutoConfig.js

firefox/components/WebContentConverter.js

firefox/components/nsAddonRepository.js

firefox/components/libnkgnomevfs.so

firefox/components/nsHandlerService.js

firefox/components/nsBrowserGlue.js

firefox/components/nsContentPrefService.js

firefox/components/libimgicon.so

firefox/components/nsLoginInfo.js

firefox/components/nsLoginManagerPrompter.js

firefox/platform.ini

firefox/libnssutil3.so

firefox/blocklist.xml

firefox/firefox

firefox/removed-files

firefox/LICENSE

firefox/libnssdbm3.so

firefox/browserconfig.properties

firefox/firefox-bin

firefox/crashreporter-override.ini

firefox/libsmime3.so

firefox/libnspr4.so

firefox/libnssdbm3.chk

firefox/crashreporter.ini

firefox/libsqlite3.so

firefox/libsoftokn3.chk

firefox/updater.ini

firefox/run-mozilla.sh

firefox/libnssckbi.so

firefox/libssl3.so

firefox/libfreebl3.chk

firefox/updater

firefox/crashreporter

firefox/.autoreg

firefox/libxpcom.so

firefox/chrome/

firefox/chrome/comm.manifest

firefox/chrome/pippki.jar

firefox/chrome/comm.jar

firefox/chrome/pippki.manifest

firefox/chrome/reporter.jar

firefox/chrome/ca.manifest

firefox/chrome/toolkit.jar

firefox/chrome/reporter.manifest

firefox/chrome/toolkit.manifest

firefox/chrome/browser.manifest

firefox/chrome/ca.jar

firefox/chrome/classic.manifest

firefox/chrome/icons/

firefox/chrome/icons/default/

firefox/chrome/icons/default/default32.png

firefox/chrome/icons/default/default16.png

firefox/chrome/icons/default/default48.png

firefox/chrome/classic.jar

firefox/chrome/browser.jar

firefox/libnss3.so

firefox/greprefs/

firefox/greprefs/xpinstall.js

firefox/greprefs/all.js

firefox/greprefs/security-prefs.js

firefox/extensions/

firefox/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/

firefox/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/install.rdf

firefox/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/icon.png

firefox/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/preview.png

firefox/res/

firefox/res/table-add-row-after-hover.gif

firefox/res/svg.css

firefox/res/arrow.gif

firefox/res/table-remove-row-hover.gif

firefox/res/grabber.gif

firefox/res/hiddenWindow.html

firefox/res/table-remove-row-active.gif

firefox/res/html.css

firefox/res/langGroups.properties

firefox/res/EditorOverride.css

firefox/res/table-add-column-before-active.gif

firefox/res/table-remove-column.gif

firefox/res/fonts/

firefox/res/fonts/mathfont.properties

firefox/res/fonts/mathfontSTIXNonUnicode.properties

firefox/res/fonts/mathfontStandardSymbolsL.properties

firefox/res/fonts/mathfontUnicode.properties

firefox/res/fonts/mathfontSTIXSize1.properties

firefox/res/table-remove-column-active.gif

firefox/res/forms.css

firefox/res/table-add-row-after.gif

firefox/res/entityTables/

firefox/res/entityTables/html40Latin1.properties

firefox/res/entityTables/html40Special.properties

firefox/res/entityTables/htmlEntityVersions.properties

firefox/res/entityTables/transliterate.properties

firefox/res/entityTables/html40Symbols.properties

firefox/res/entityTables/mathml20.properties

firefox/res/table-add-column-before.gif

firefox/res/ua.css

firefox/res/table-remove-row.gif

firefox/res/table-add-column-after.gif

firefox/res/table-add-column-after-hover.gif

firefox/res/quirk.css

firefox/res/table-add-column-before-hover.gif

firefox/res/charsetalias.properties

firefox/res/mathml.css

firefox/res/table-add-row-before-active.gif

firefox/res/table-add-row-before.gif

firefox/res/table-remove-column-hover.gif

firefox/res/table-add-row-before-hover.gif

firefox/res/designmode.css

firefox/res/viewsource.css

firefox/res/contenteditable.css

firefox/res/arrowd.gif

firefox/res/charsetData.properties

firefox/res/table-add-row-after-active.gif

firefox/res/html/

firefox/res/html/folder.png

firefox/res/loading-image.png

firefox/res/broken-image.png

firefox/res/dtd/

firefox/res/dtd/xhtml11.dtd

firefox/res/dtd/mathml.dtd

firefox/res/unixcharset.properties

firefox/res/table-add-column-after-active.gif

firefox/res/language.properties

firefox/libsoftokn3.so

firefox/libfreebl3.so

firefox/modules/

firefox/modules/NetUtil.jsm

firefox/modules/PluralForm.jsm

firefox/modules/distribution.js

firefox/modules/WindowDraggingUtils.jsm

firefox/modules/Microformats.js

firefox/modules/NetworkPrioritizer.jsm

firefox/modules/PlacesDBUtils.jsm

firefox/modules/LightweightThemeConsumer.jsm

firefox/modules/XPCOMUtils.jsm

firefox/modules/utils.js

firefox/modules/DownloadUtils.jsm

firefox/modules/ISO8601DateUtils.jsm

firefox/modules/openLocationLastURL.jsm

firefox/modules/ctypes.jsm

firefox/modules/LightweightThemeManager.jsm

firefox/modules/debug.js

firefox/modules/DownloadLastDir.jsm

firefox/modules/CertUtils.jsm

firefox/modules/SpatialNavigation.js

firefox/modules/FileUtils.jsm

firefox/README.txt

firefox/libplc4.so

firefox/application.ini

firefox/searchplugins/

firefox/searchplugins/google.xml

firefox/searchplugins/yahoo-ca.xml

firefox/searchplugins/llibres.xml

firefox/searchplugins/diec2.xml

firefox/searchplugins/wikipedia-ca.xml

firefox/searchplugins/huubs.xml

firefox/icons/

firefox/icons/updater.png

firefox/icons/document.png

firefox/icons/mozicon128.png

firefox/libplds4.so

firefox/mozilla-xremote-client

firefox/libxul.so

firefox/defaults/

firefox/defaults/profile/

firefox/defaults/profile/bookmarks.html

firefox/defaults/profile/mimeTypes.rdf

firefox/defaults/profile/localstore.rdf

firefox/defaults/profile/chrome/

firefox/defaults/profile/chrome/userChrome-example.css

firefox/defaults/profile/chrome/userContent-example.css

firefox/defaults/pref/

firefox/defaults/pref/channel-prefs.js

firefox/defaults/pref/firefox.js

firefox/defaults/pref/reporter.js

firefox/defaults/pref/firefox-branding.js

firefox/defaults/pref/firefox-l10n.js

firefox/defaults/autoconfig/

firefox/defaults/autoconfig/platform.js

firefox/defaults/autoconfig/prefcalls.js

firefox/libmozjs.so

root@usuari-desktop:/opt/firefox# rm -rf /plugins

root@usuari-desktop:/opt/firefox# ln -s /usr/lib/mozilla/plugins plugins

root@usuari-desktop:/opt/firefox# 


```

Canvieu el nom d'usuari pel vostre nom d'usuari i l'adreça de baixada per l'adreça on heu descarregada la nova versió del navegador i en tindreu la sortida en Terminal.

Ara només heu d'editar el llançador del panell de d'alt amb l'ordre: /opt/firefox/firefox
O si el preferiu fer una llançadora nova a l'escriptori amb un altra icona...

I a navegar!

Espere que vos siga útil!

Salutacions i bona primavera 2010!

---

