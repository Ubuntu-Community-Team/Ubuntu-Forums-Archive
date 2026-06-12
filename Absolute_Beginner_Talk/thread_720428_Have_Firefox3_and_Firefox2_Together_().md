---
title: "Have Firefox3 and Firefox2 Together (?)"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by Hoom@n on 2008-03-10
Hello! I wanted to install and test Firefox3b5pre on my Ubuntu, I found "http://www.ubuntugeek.com/howto-install-firefox-3-beta-2-in-ubuntu-710-gutsy-gibbon.html" but it seems that it'll replace firefox3 with firefox2. How can I have them together?
This is the file list:
```
Archive \Downloads\firefox-3.0b5pre.en-US.linux-i686.tar.bz2

firefox

firefox\dictionaries

firefox\dictionaries\en-US.dic

firefox\dictionaries\en-US.aff

firefox\libsqlite3.so

firefox\libsmime3.so

firefox\libfreebl3.chk

firefox\libfreebl3.so

firefox\mozilla-xremote-client

firefox\defaults

firefox\defaults\profile

firefox\defaults\profile\prefs.js

firefox\defaults\profile\bookmarks.html

firefox\defaults\profile\chrome

firefox\defaults\profile\chrome\userContent-example.css

firefox\defaults\profile\chrome\userChrome-example.css

firefox\defaults\profile\localstore.rdf

firefox\defaults\profile\mimeTypes.rdf

firefox\defaults\pref

firefox\defaults\pref\firefox-l10n.js

firefox\defaults\pref\firefox-branding.js

firefox\defaults\pref\firefox.js

firefox\defaults\pref\reporter.js

firefox\defaults\pref\channel-prefs.js

firefox\defaults\autoconfig

firefox\defaults\autoconfig\platform.js

firefox\defaults\autoconfig\prefcalls.js

firefox\plugins

firefox\plugins\libnullplugin.so

firefox\Throbber-small.gif

firefox\libjemalloc.so

firefox\old-homepage-default.properties

firefox\libnssckbi.so

firefox\libnss3.so

firefox\icons

firefox\icons\mozicon50.xpm

firefox\icons\mozicon128.png

firefox\icons\document.png

firefox\icons\mozicon16.xpm

firefox\res

firefox\res\table-add-row-after-hover.gif

firefox\res\table-add-column-after.gif

firefox\res\mathml.css

firefox\res\table-add-column-before.gif

firefox\res\table-add-row-after-active.gif

firefox\res\language.properties

firefox\res\EditorOverride.css

firefox\res\table-add-row-before-active.gif

firefox\res\viewsource.css

firefox\res\table-remove-row-active.gif

firefox\res\arrow.gif

firefox\res\forms.css

firefox\res\arrowd.gif

firefox\res\table-remove-row.gif

firefox\res\langGroups.properties

firefox\res\fonts

firefox\res\fonts\mathfont.properties

firefox\res\fonts\mathfontSTIXNonUnicode.properties

firefox\res\fonts\mathfontSTIXSize1.properties

firefox\res\fonts\mathfontStandardSymbolsL.properties

firefox\res\fonts\mathfontUnicode.properties

firefox\res\loading-image.gif

firefox\res\broken-image.gif

firefox\res\dtd

firefox\res\dtd\xhtml11.dtd

firefox\res\dtd\mathml.dtd

firefox\res\contenteditable.css

firefox\res\table-add-row-after.gif

firefox\res\table-add-column-after-hover.gif

firefox\res\table-add-column-before-active.gif

firefox\res\table-remove-column.gif

firefox\res\designmode.css

firefox\res\quirk.css

firefox\res\table-add-column-after-active.gif

firefox\res\charsetData.properties

firefox\res\table-remove-row-hover.gif

firefox\res\hiddenWindow.html

firefox\res\svg.css

firefox\res\charsetalias.properties

firefox\res\entityTables

firefox\res\entityTables\mathml20.properties

firefox\res\entityTables\html40Special.properties

firefox\res\entityTables\html40Symbols.properties

firefox\res\entityTables\html40Latin1.properties

firefox\res\entityTables\transliterate.properties

firefox\res\entityTables\htmlEntityVersions.properties

firefox\res\html.css

firefox\res\grabber.gif

firefox\res\table-add-column-before-hover.gif

firefox\res\table-remove-column-hover.gif

firefox\res\unixcharset.properties

firefox\res\html

firefox\res\html\folder.png

firefox\res\table-add-row-before-hover.gif

firefox\res\table-remove-column-active.gif

firefox\res\ua.css

firefox\res\table-add-row-before.gif

firefox\firefox-bin

firefox\application.ini

firefox\libnspr4.so

firefox\updater.ini

firefox\libxpcom.so

firefox\modules

firefox\modules\Microformats.js

firefox\modules\ISO8601DateUtils.jsm

firefox\modules\XPCOMUtils.jsm

firefox\modules\DownloadUtils.jsm

firefox\modules\JSON.jsm

firefox\modules\distribution.js

firefox\modules\PluralForm.jsm

firefox\chrome

firefox\chrome\reporter.jar

firefox\chrome\icons

firefox\chrome\icons\default

firefox\chrome\icons\default\default16.png

firefox\chrome\icons\default\default32.png

firefox\chrome\icons\default\default48.png

firefox\chrome\comm.jar

firefox\chrome\pippki.manifest

firefox\chrome\pippki.jar

firefox\chrome\browser.manifest

firefox\chrome\classic.manifest

firefox\chrome\toolkit.jar

firefox\chrome\comm.manifest

firefox\chrome\browser.jar

firefox\chrome\en-US.manifest

firefox\chrome\classic.jar

firefox\chrome\toolkit.manifest

firefox\chrome\en-US.jar

firefox\chrome\reporter.manifest

firefox\run-mozilla.sh

firefox\searchplugins

firefox\searchplugins\amazondotcom.xml

firefox\searchplugins\yahoo.xml

firefox\searchplugins\wikipedia.xml

firefox\searchplugins\google.xml

firefox\searchplugins\creativecommons.xml

firefox\searchplugins\answers.xml

firefox\searchplugins\eBay.xml

firefox\libssl3.so

firefox\libsoftokn3.so

firefox\crashreporter.ini

firefox\README.txt

firefox\libxul.so

firefox\removed-files

firefox\crashreporter

firefox\updater

firefox\components

firefox\components\nsUrlClassifierListManager.js

firefox\components\FeedConverter.js

firefox\components\nsSearchService.js

firefox\components\nsTryToClose.js

firefox\components\nsFilePicker.js

firefox\components\nsMicrosummaryService.js

firefox\components\nsDownloadManagerUI.js

firefox\components\nsSessionStartup.js

firefox\components\libnkgnomevfs.so

firefox\components\nsSearchSuggestions.js

firefox\components\nsExtensionManager.js

firefox\components\nsURLFormatter.js

firefox\components\nsHelperAppDlg.js

firefox\components\nsLoginManagerPrompter.js

firefox\components\nsPlacesTransactionsService.js

firefox\components\nsWebHandlerApp.js

firefox\components\nsUrlClassifierLib.js

firefox\components\nsSetDefaultBrowser.js

firefox\components\nsContentPrefService.js

firefox\components\nsSessionStore.js

firefox\components\pluginGlue.js

firefox\components\nsLivemarkService.js

firefox\components\libimgicon.so

firefox\components\libdbusservice.so

firefox\components\nsHandlerService.js

firefox\components\nsSafebrowsingApplication.js

firefox\components\nsBlocklistService.js

firefox\components\WebContentConverter.js

firefox\components\nsTaggingService.js

firefox\components\nsContentDispatchChooser.js

firefox\components\nsLoginManager.js

firefox\components\fuelApplication.js

firefox\components\libmozgnome.so

firefox\components\FeedWriter.js

firefox\components\nsUpdateService.js

firefox\components\nsAddonRepository.js

firefox\components\txEXSLTRegExFunctions.js

firefox\components\nsProxyAutoConfig.js

firefox\components\libbrowsercomps.so

firefox\components\libbrowserdirprovider.so

firefox\components\nsDefaultCLH.js

firefox\components\nsSidebar.js

firefox\components\browser.xpt

firefox\components\storage-Legacy.js

firefox\components\FeedProcessor.js

firefox\components\nsBrowserContentHandler.js

firefox\components\nsLoginInfo.js

firefox\components\jsconsole-clhandler.js

firefox\components\nsBrowserGlue.js

firefox\firefox

firefox\crashreporter-override.ini

firefox\extensions

firefox\extensions\{972ce4c6-7e08-4474-a285-3208198ce6fd}

firefox\extensions\{972ce4c6-7e08-4474-a285-3208198ce6fd}\install.rdf

firefox\libsoftokn3.chk

firefox\libnssutil3.so

firefox\libplds4.so

firefox\libmozjs.so

firefox\greprefs

firefox\greprefs\all.js

firefox\greprefs\security-prefs.js

firefox\greprefs\xpinstall.js

firefox\libnssdbm3.so

firefox\browserconfig.properties

firefox\libplc4.so

firefox\platform.ini

firefox\.autoreg
```
Thank you!

---

### Post by sayakb on 2008-03-10
I am using them together.. just installed them through apt.. you should get both of them through the repos..

---

### Post by Hoom@n on 2008-03-10
Thank you for the answer, but please tell me how? I know "sudo apt-get install," but what should I install?
Thanks again!

---

### Post by sayakb on 2008-03-10
> **Hoom@n said:**
> Thank you for the answer, but please tell me how? I know "sudo apt-get install," but what should I install?
Thanks again!

```
sudo apt-get install firefox
sudo apt-get install firefox-3.0
```

---

### Post by le_renouveau on 2008-03-10
Hey Hoom@n,

I just installed Ubuntu this weekend, but the one problem that I was faced with early is that you may not have your plugins installed in Firefox 3.03beta. I suggest finding where the beta is installed and copying the files in the directory /plugins/ from 2.0 to 3.03b.

Hope this helps, it solved my issues with Firefox Beta

---

### Post by Hoom@n on 2008-03-10
No, no. It's not ubuntu's problem. Most of firefox plugins are not campatible with firefox3, because most of developers wait until the stable release and then they make their addons compatible with firefox3. You can do this at your own risk to disable addons check compatibility: (so all the plugins will install, but just some of them will work and some of them might be harmful for your firefox3)
1-Type "about:config" in your firefox addressbar
2-Write click in a free space and choose "_N_ew>**B**oolean"
3-Write "extensions.checkCompatibility" as the name
4-Chose "false"
5-Restart Firefox
**Warning:** Some addons or plugins can harm your firefox and even stop it from work!
(And you can use [https://addons.mozilla.org/en-US/firefox/addon/1391](https://addons.mozilla.org/en-US/firefox/addon/1391) which is not as good as the previous way, but it won't harm you!)
+++
Could you please tell me which is the "sudo apt-get install firefox-3.0"'s version?
____
Thank you!

---

### Post by sayakb on 2008-03-10
> **Hoom@n said:**
> Could you please tell me which is the "sudo apt-get install firefox-3.0"'s version?
____
Thank you!

If your repos are updated you would get beta3..

---

### Post by forrestcupp on 2008-03-10
You won't get Pre5 in the repos.

In order to get newer than an alpha, you have to make sure you enable extra repos.  Open up Synaptic and go to Settings->Repositories and click the Updates tab.  Check the boxes that say 'Proposed updates' and 'Unsupported updates'.  Then click the Reload button.  You should be able to search for Firefox and find the very latest version that the repos have.

Also, if you don't know what to sudo apt-get install, Synaptic is a good place to search.  In Synaptic, just doing a search for Firefox will bring up the Firefox 3 package for you.  It's the graphical way to do a sudo apt-get.

---

### Post by sayakb on 2008-03-10
> **forrestcupp said:**
> You won't get Pre5 in the repos.

In order to get newer than an alpha, you have to make sure you enable extra repos.  Open up Synaptic and go to Settings->Repositories and click the Updates tab.  Check the boxes that say 'Proposed updates' and 'Unsupported updates'.  Then click the Reload button.  You should be able to search for Firefox and find the very latest version that the repos have.

Also, if you don't know what to sudo apt-get install, Synaptic is a good place to search.  In Synaptic, just doing a search for Firefox will bring up the Firefox 3 package for you.  It's the graphical way to do a sudo apt-get.

Even I use synaptic.. I might be wrong, but is apt faster than synaptic because of complete CLI based interface (whatever that meant)?

---

### Post by forrestcupp on 2008-03-10
> **LinuxIsInnovation said:**
> Even I use synaptic.. I might be wrong, but is apt faster than synaptic because of complete CLI based interface (whatever that meant)?

Synaptic is just a GUI frontend for apt.  Using apt in the CLI doesn't install things faster than Synaptic.  The only time it is faster is when you already know the name of the package you want to install.  It's a lot faster to open up a terminal and type sudo apt-get install package than it is to wait for Synaptic to open up, do a search, check the box, then install the package.

But some people are just a lot more comfortable doing things graphically.  Also Synaptic is a lot easier to search for packages when you don't know exactly what you need.

---

### Post by sayakb on 2008-03-10
> **forrestcupp said:**
> Synaptic is just a GUI frontend for apt.  Using apt in the CLI doesn't install things faster than Synaptic.  The only time it is faster is when you already know the name of the package you want to install.  It's a lot faster to open up a terminal and type sudo apt-get install package than it is to wait for Synaptic to open up, do a search, check the box, then install the package.

But some people are just a lot more comfortable doing things graphically.  Also Synaptic is a lot easier to search for packages when you don't know exactly what you need.

That clears a misconcept of mine..

---

### Post by Hoom@n on 2008-03-10
Hello again! It seems that it installed **alpha8**. *But my problem is I can't find firefox3! I don't know where it is! Please tell me were it is.:solved*
+++
What is "roeps"?
____
Thanks!

---

### Post by sayakb on 2008-03-10
> **Hoom@n said:**
> Hello again! It seems that it installed **alpha8**. But my problrm is I can't find firefox3! I don't know where it is! Please tell me were it is.
+++
What is "roeps"?
____
Thanks!

"Repos" referes to repositories, more like software sources.
Goto System->Administration->Software sources, click on the Updates Tab, and tick all the checkboxes. Then click the reload button after you close the software sources window. Now open synaptic and search for firefox 3.0

---

### Post by Hoom@n on 2008-03-10
Thanks for the answers!
+++
**"Check f_o_r Updates" in the "Help" menu is disabled! How can I update my firefox?** (I set ubuntu to get prerelease softwares and it installed beta3 for me, but I don't want even this!)

---

### Post by sayakb on 2008-03-10
> **Hoom@n said:**
> Thanks for the answers!
+++
**"Check f_o_r Updates" in the "Help" menu is disabled! How can I update my firefox?** (I set ubuntu to get prerelease softwares and it installed beta3 for me, but I don't want even this!)

Beta 3 is the latest available version through the repositories anyway, you might not get anything new through the software sources..

---

### Post by forrestcupp on 2008-03-10
You need to do what I said in this post.  This enables extra software repositories (repos) that aren't officially supported, but they have newer versions of things.  The official repos only have an alpha of FF3, but the Proposed and Unsupported updates repos have a fairly new Beta3.  Repositories are basically just servers that have lots of software that you can install with Synaptic or apt-get.

> **forrestcupp said:**
> 
In order to get newer than an alpha, you have to make sure you enable extra repos.  Open up Synaptic and go to Settings->Repositories and click the Updates tab.  Check the boxes that say 'Proposed updates' and 'Unsupported updates'.  Then click the Reload button.  You should be able to search for Firefox and find the very latest version that the repos have.

---

### Post by Hoom@n on 2008-03-10
Thanks for your help, I did what you said!So I have b3 now. But I don't want to have only the released version. I wanna install and test all nighty builds. In windows I can simply use the "check for updates" in the "Help" menu, but it is disabled here. Is there any way to install latest nighty build or not?
Thanks a lot again for all the helps!

---

### Post by forrestcupp on 2008-03-10
No.  If you want the nightly builds, you'll have to go to [their nightly build page](http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-trunk/) and download and install it the hard way.

---

