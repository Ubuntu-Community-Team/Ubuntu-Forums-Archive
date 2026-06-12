---
title: "[SOLVED] Need help installing Thunderbird 2.0.0.9 from source"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by iClouseau88 on 2007-11-14
Hi,

Could you help me?  After downloading the file to Desktop and unpacking or tarring it, I am not able to go any further.  Please note the last line of the terminal output.  Thanks.



root@hoe1-laptop:/home/hoe1/Desktop# tar xvzf thunderbird-2.0.0.9.tar.gz
thunderbird/
thunderbird/removed-files
thunderbird/chrome/
thunderbird/chrome/installed-chrome.txt
thunderbird/chrome/en-US.manifest
thunderbird/chrome/en-US.jar
thunderbird/chrome/toolkit.jar
thunderbird/chrome/comm.manifest
thunderbird/chrome/comm.jar
thunderbird/chrome/toolkit.manifest
thunderbird/chrome/classic.jar
thunderbird/chrome/classic.manifest
thunderbird/chrome/pippki.manifest
thunderbird/chrome/pippki.jar
thunderbird/chrome/messenger.jar
thunderbird/chrome/icons/
thunderbird/chrome/icons/default/
thunderbird/chrome/icons/default/abcardWindow.xpm
thunderbird/chrome/icons/default/addressbookWindow.xpm
thunderbird/chrome/icons/default/messengerWindow.xpm
thunderbird/chrome/icons/default/msgcomposeWindow.xpm
thunderbird/chrome/icons/default/abcardWindow16.xpm
thunderbird/chrome/icons/default/addressbookWindow16.xpm
thunderbird/chrome/icons/default/messengerWindow16.xpm
thunderbird/chrome/icons/default/msgcomposeWindow16.xpm
thunderbird/chrome/icons/default/default.xpm
thunderbird/chrome/US.jar
thunderbird/chrome/newsblog.jar
thunderbird/chrome/messenger.manifest
thunderbird/chrome/newsblog.manifest
thunderbird/components/
thunderbird/components/xpcom_base.xpt
thunderbird/components/xpcom_ds.xpt
thunderbird/components/xpcom_io.xpt
thunderbird/components/xpcom_components.xpt
thunderbird/components/xpcom_threads.xpt
thunderbird/components/xpcom_xpti.xpt
thunderbird/components/proxyObjInst.xpt
thunderbird/components/xpcom_obsolete.xpt
thunderbird/components/xpconnect.xpt
thunderbird/components/unicharutil.xpt
thunderbird/components/uconv.xpt
thunderbird/components/locale.xpt
thunderbird/components/intl.xpt
thunderbird/components/lwbrk.xpt
thunderbird/components/chardet.xpt
thunderbird/components/storage.xpt
thunderbird/components/libjsd.so
thunderbird/components/jsdservice.xpt
thunderbird/components/necko.xpt
thunderbird/components/nsProxyAutoConfig.js
thunderbird/components/necko_cookie.xpt
thunderbird/components/necko_dns.xpt
thunderbird/components/necko_socket.xpt
thunderbird/components/mimetype.xpt
thunderbird/components/necko_strconv.xpt
thunderbird/components/necko_cache.xpt
thunderbird/components/necko_about.xpt
thunderbird/components/necko_data.xpt
thunderbird/components/necko_res.xpt
thunderbird/components/necko_file.xpt
thunderbird/components/necko_http.xpt
thunderbird/components/necko_viewsource.xpt
thunderbird/components/necko_ftp.xpt
thunderbird/components/libjar50.so
thunderbird/components/jar.xpt
thunderbird/components/uriloader.xpt
thunderbird/components/exthandler.xpt
thunderbird/components/prefetch.xpt
thunderbird/components/pref.xpt
thunderbird/components/caps.xpt
thunderbird/components/rdf.xpt
thunderbird/components/saxparser.xpt
thunderbird/components/htmlparser.xpt
thunderbird/components/gfx.xpt
thunderbird/components/imglib2.xpt
thunderbird/components/dom_base.xpt
thunderbird/components/dom_canvas.xpt
thunderbird/components/dom_core.xpt
thunderbird/components/dom_html.xpt
thunderbird/components/dom_events.xpt
thunderbird/components/dom_stylesheets.xpt
thunderbird/components/dom_views.xpt
thunderbird/components/dom_css.xpt
thunderbird/components/dom_sidebar.xpt
thunderbird/components/dom_traversal.xpt
thunderbird/components/dom_range.xpt
thunderbird/components/dom_xbl.xpt
thunderbird/components/dom_xpath.xpt
thunderbird/components/dom_loadsave.xpt
thunderbird/components/dom_xul.xpt
thunderbird/components/dom_storage.xpt
thunderbird/components/dom.xpt
thunderbird/components/widget.xpt
thunderbird/components/content_base.xpt
thunderbird/components/content_html.xpt
thunderbird/components/content_htmldoc.xpt
thunderbird/components/content_xmldoc.xpt
thunderbird/components/xuldoc.xpt
thunderbird/components/xultmpl.xpt
thunderbird/components/content_xslt.xpt
thunderbird/components/content_xtf.xpt
thunderbird/components/layout_base.xpt
thunderbird/components/layout_printing.xpt
thunderbird/components/layout_xul.xpt
thunderbird/components/layout_xul_tree.xpt
thunderbird/components/inspector.xpt
thunderbird/components/shistory.xpt
thunderbird/components/docshell.xpt
thunderbird/components/webshell_idls.xpt
thunderbird/components/embed_base.xpt
thunderbird/components/windowwatcher.xpt
thunderbird/components/find.xpt
thunderbird/components/webbrowserpersist.xpt
thunderbird/components/commandhandler.xpt
thunderbird/components/nsHelperAppDlg.js
thunderbird/components/progressDlg.xpt
thunderbird/components/nsProgressDialog.js
thunderbird/components/jsconsole.xpt
thunderbird/components/webBrowser_core.xpt
thunderbird/components/editor.xpt
thunderbird/components/txtsvc.xpt
thunderbird/components/txmgr.xpt
thunderbird/components/composer.xpt
thunderbird/components/appshell.xpt
thunderbird/components/accessibility-atk.xpt
thunderbird/components/accessibility.xpt
thunderbird/components/chrome.xpt
thunderbird/components/profile.xpt
thunderbird/components/mozbrwsr.xpt
thunderbird/components/mozfind.xpt
thunderbird/components/windowds.xpt
thunderbird/components/filepicker.xpt
thunderbird/components/nsFilePicker.js
thunderbird/components/xpautocomplete.xpt
thunderbird/components/jsconsole-clhandler.js
thunderbird/components/history.xpt
thunderbird/components/bookmarks.xpt
thunderbird/components/toolkitremote.xpt
thunderbird/components/urlformatter.xpt
thunderbird/components/nsURLFormatter.js
thunderbird/components/alerts.xpt
thunderbird/components/fastfind.xpt
thunderbird/components/autocomplete.xpt
thunderbird/components/feeds.xpt
thunderbird/components/FeedProcessor.js
thunderbird/components/downloads.xpt
thunderbird/components/url-classifier.xpt
thunderbird/components/nsUrlClassifierTable.js
thunderbird/components/nsUrlClassifierLib.js
thunderbird/components/nsUrlClassifierListManager.js
thunderbird/components/commandlines.xpt
thunderbird/components/appstartup.xpt
thunderbird/components/nsCloseAllWindows.js
thunderbird/components/nsDefaultCLH.js
thunderbird/components/toolkitprofile.xpt
thunderbird/components/xulapp.xpt
thunderbird/components/extensions.xpt
thunderbird/components/nsExtensionManager.js
thunderbird/components/update.xpt
thunderbird/components/nsUpdateService.js
thunderbird/components/xpinstall.xpt
thunderbird/components/libxpinstall.so
thunderbird/components/pipboot.xpt
thunderbird/components/pipnss.xpt
thunderbird/components/pippki.xpt
thunderbird/components/mozldap.xpt
thunderbird/components/libmozgnome.so
thunderbird/components/mozgnome.xpt
thunderbird/components/mailnews.xpt
thunderbird/components/msgbase.xpt
thunderbird/components/msgsearch.xpt
thunderbird/components/msgdb.xpt
thunderbird/components/msgnews.xpt
thunderbird/components/msglocal.xpt
thunderbird/components/mime.xpt
thunderbird/components/msgcompose.xpt
thunderbird/components/msgimap.xpt
thunderbird/components/addrbook.xpt
thunderbird/components/nsLDAPPrefsService.js
thunderbird/components/nsAbLDAPAttributeMap.js
thunderbird/components/import.xpt
thunderbird/components/impComm4xMail.xpt
thunderbird/components/mdn-service.js
thunderbird/components/mailview.xpt
thunderbird/components/offlineStartup.js
thunderbird/components/msgsmime.xpt
thunderbird/components/smime-service.js
thunderbird/components/wallet.xpt
thunderbird/components/walleteditor.xpt
thunderbird/components/signonviewer.xpt
thunderbird/components/walletpreview.xpt
thunderbird/components/libspellchecker.so
thunderbird/components/spellchecker.xpt
thunderbird/components/libmyspell.so
thunderbird/components/autoconfig.xpt
thunderbird/components/websrvcs.xpt
thunderbird/components/nsInterfaceInfoToIDL.js
thunderbird/components/nsComposerCmdLineHandler.js
thunderbird/components/mailprofilemigration.xpt
thunderbird/components/shellservice.xpt
thunderbird/components/nsSetDefaultMail.js
thunderbird/components/nsMailDefaultHandler.js
thunderbird/components/nsPhishingProtectionApplication.js
thunderbird/components/newsblog.js
thunderbird/defaults/
thunderbird/defaults/autoconfig/
thunderbird/defaults/autoconfig/prefcalls.js
thunderbird/defaults/autoconfig/platform.js
thunderbird/defaults/pref/
thunderbird/defaults/pref/mdn.js
thunderbird/defaults/pref/smime.js
thunderbird/defaults/pref/mailnews.js
thunderbird/defaults/pref/thunderbird-branding.js
thunderbird/defaults/pref/composer.js
thunderbird/defaults/pref/all-l10n.js
thunderbird/defaults/pref/all-thunderbird.js
thunderbird/defaults/pref/channel-prefs.js
thunderbird/defaults/messenger/
thunderbird/defaults/messenger/mailViews.dat
thunderbird/defaults/messenger/US/
thunderbird/defaults/messenger/US/mailViews.dat
thunderbird/defaults/wallet/
thunderbird/defaults/wallet/DistinguishedSchema.tbl
thunderbird/defaults/wallet/FieldSchema.tbl
thunderbird/defaults/wallet/VcardSchema.tbl
thunderbird/defaults/wallet/SchemaConcat.tbl
thunderbird/defaults/wallet/SchemaStrings.tbl
thunderbird/defaults/wallet/PositionalSchema.tbl
thunderbird/defaults/wallet/StateSchema.tbl
thunderbird/defaults/profile/
thunderbird/defaults/profile/mimeTypes.rdf
thunderbird/defaults/profile/localstore.rdf
thunderbird/defaults/profile/US/
thunderbird/defaults/profile/US/mimeTypes.rdf
thunderbird/defaults/profile/US/localstore.rdf
thunderbird/defaults/profile/prefs.js
thunderbird/dependentlibs.list
thunderbird/dictionaries/
thunderbird/dictionaries/en-US.dic
thunderbird/dictionaries/en-US.aff
thunderbird/extensions/
thunderbird/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/
thunderbird/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/install.rdf
thunderbird/extensions/talkback@mozilla.org/
thunderbird/extensions/talkback@mozilla.org/chrome.manifest
thunderbird/extensions/talkback@mozilla.org/install.rdf
thunderbird/extensions/talkback@mozilla.org/components/
thunderbird/extensions/talkback@mozilla.org/components/talkback/
thunderbird/extensions/talkback@mozilla.org/components/talkback/XTalkback.ad
thunderbird/extensions/talkback@mozilla.org/components/talkback/talkback.so
thunderbird/extensions/talkback@mozilla.org/components/talkback/talkback
thunderbird/extensions/talkback@mozilla.org/components/talkback/master.ini
thunderbird/extensions/talkback@mozilla.org/components/qfaservices.xpt
thunderbird/extensions/talkback@mozilla.org/components/libqfaservices.so
thunderbird/greprefs/
thunderbird/greprefs/security-prefs.js
thunderbird/greprefs/all.js
thunderbird/greprefs/xpinstall.js
thunderbird/icons/
thunderbird/icons/mozicon50.xpm
thunderbird/icons/mozicon16.xpm
thunderbird/init.d/
thunderbird/init.d/README
thunderbird/isp/
thunderbird/isp/SpamAssassin.sfd
thunderbird/isp/SpamPal.sfd
thunderbird/isp/movemail.rdf
thunderbird/isp/en-US/
thunderbird/isp/en-US/gmail.rdf
thunderbird/isp/rss.rdf
thunderbird/libfreebl3.chk
thunderbird/libfreebl3.so
thunderbird/libldap50.so
thunderbird/libmozjs.so
thunderbird/libnspr4.so
thunderbird/libnss3.so
thunderbird/libnssckbi.so
thunderbird/libplc4.so
thunderbird/libplds4.so
thunderbird/libprldap50.so
thunderbird/libsmime3.so
thunderbird/libsoftokn3.chk
thunderbird/libsoftokn3.so
thunderbird/libssl3.so
thunderbird/libxpcom_compat.so
thunderbird/libxpcom_core.so
thunderbird/libxpcom.so
thunderbird/libxpistub.so
thunderbird/license.html
thunderbird/LICENSE.txt
thunderbird/mozilla-installer-bin
thunderbird/mozilla-xremote-client
thunderbird/README.txt
thunderbird/res/
thunderbird/res/entityTables/
thunderbird/res/entityTables/htmlEntityVersions.properties
thunderbird/res/entityTables/html40Latin1.properties
thunderbird/res/entityTables/html40Symbols.properties
thunderbird/res/entityTables/html40Special.properties
thunderbird/res/entityTables/transliterate.properties
thunderbird/res/charsetalias.properties
thunderbird/res/charsetData.properties
thunderbird/res/unixcharset.properties
thunderbird/res/langGroups.properties
thunderbird/res/language.properties
thunderbird/res/sample.unixpsfonts.properties
thunderbird/res/fonts/
thunderbird/res/fonts/fontEncoding.properties
thunderbird/res/fonts/pangoFontEncoding.properties
thunderbird/res/hiddenWindow.html
thunderbird/res/dtd/
thunderbird/res/dtd/xhtml11.dtd
thunderbird/res/forms.css
thunderbird/res/ua.css
thunderbird/res/html.css
thunderbird/res/quirk.css
thunderbird/res/broken-image.gif
thunderbird/res/EditorOverride.css
thunderbird/res/grabber.gif
thunderbird/res/table-add-column-after-active.gif
thunderbird/res/table-add-column-after-hover.gif
thunderbird/res/table-add-column-after.gif
thunderbird/res/table-add-column-before-active.gif
thunderbird/res/table-add-column-before-hover.gif
thunderbird/res/table-add-column-before.gif
thunderbird/res/table-add-row-after-active.gif
thunderbird/res/table-add-row-after-hover.gif
thunderbird/res/table-add-row-after.gif
thunderbird/res/table-add-row-before-active.gif
thunderbird/res/table-add-row-before-hover.gif
thunderbird/res/table-add-row-before.gif
thunderbird/res/table-remove-column-active.gif
thunderbird/res/table-remove-column-hover.gif
thunderbird/res/table-remove-column.gif
thunderbird/res/table-remove-row-active.gif
thunderbird/res/table-remove-row-hover.gif
thunderbird/res/table-remove-row.gif
thunderbird/run-mozilla.sh
thunderbird/thunderbird
thunderbird/thunderbird-bin
thunderbird/updater
thunderbird/updater.ini
thunderbird/updates/
thunderbird/updates/0/
thunderbird/xpicleanup
root@hoe1-laptop:/home/hoe1/Desktop# cd thunderbird/
root@hoe1-laptop:/home/hoe1/Desktop/thunderbird# ./configure
bash: ./configure: No such file or directory


:confused:

---

### Post by llamakc on 2007-11-14
You didn't download the source. That's ready to run by typing IN THAT DIRECTORY 

```

./thunderbird

```

Of course you could have easily installed Thunderbird from within Synaptic and received a package that would be updated/upgraded for any security or flaw issues later down the line.

---

### Post by Inxsible on 2007-11-15
Synaptic has the Thunderbird 2.0.0.8 as the latest. Is there a reason you have to have 2.0.0.9 ?

---

### Post by Irihapeti on 2007-11-15
There is more about installing the Mozilla version of Thunderbird here:

[https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion)

---

### Post by iClouseau88 on 2007-11-15
Synaptic only shows 2.0.0.8 as transitional package.  The latest version for Linux is 2.0.0.9 in Mozilla web site.

---

### Post by llamakc on 2007-11-15
> **iClouseau88 said:**
> Synaptic only shows 2.0.0.8 as transitional package.  The latest version for Linux is 2.0.0.9 in Mozilla web site.

So are you going to regularly check the Thunderbird mailing list for security vulnerabilities and re-download the package with each one? Or are you going to install via Synaptic and let those fixes be backported into the Ubuntu version?

---

### Post by iClouseau88 on 2007-11-15
Hi,

Thanks for replying.  I normally install softwares & updates via Synaptic, but in this case I am anxious to install the latest version and to learn how to do this from source.  I found it very frustrating because I read Howtos many times but there's no consistency among the tutorials, also what comes out on screen is not what's in the tutorials.  I am talking about installing softwares from source here.

---

### Post by llamakc on 2007-11-15
Well as I said earlier you did NOT download the source. You downloaded an archive of all of the files needed to run Thunderbird.

[http://developer.mozilla.org/en/docs/Download_Mozilla_Source_Code](http://developer.mozilla.org/en/docs/Download_Mozilla_Source_Code)

Is the official page that points to the source. And here are the instructions.

[http://developer.mozilla.org/en/docs/Build_Documentation](http://developer.mozilla.org/en/docs/Build_Documentation)

I found this by searching "thunderbird source" in Google.

---

### Post by Inxsible on 2007-11-15
Installing from source is a 3 step process
1) ```
tar -xvzf *filename*
```2) cd into the extracted directory then do ```
./configure && sudo make
```3)```
sudo make install
```

---

### Post by llamakc on 2007-11-15
Edit in the "./configure" command for when the OP actually downloads the source. Also, "configure" and "make" do NOT need to be run with sudo. Only the "make install" does.

---

### Post by iClouseau88 on 2007-11-15
Hi folks,

Thanks a lot for your help but I am about to give up.  I don't know what I did wrong or failed to do.  I followed exactly the instructions from the book called "Ubuntu Hacks" by Jonathan Oxer et al (O'Reilly Pub.).

I don't want to go back to Windows.  Any other suggestions?

---

### Post by Inxsible on 2007-11-15
I just gave you a 3 step process, did you try that?

first and foremost, are you sure you have downloaded the source?

can you give us the link where you downloaded the source?

---

### Post by iClouseau88 on 2007-11-15
Hi,

I went to [www.mozilla.org/products/thunderbird](www.mozilla.org/products/thunderbird), clicked on Linux version of Thunderbird 2.0.0.9 to download and save "thunderbird-2.0.0.9.tar.gz".

As I said earlier, I followed instructions from "Ubuntu Hacks".  Now I just noticed that the book's instruction does not have the hyphen in front of the xvzf command.  May be this is where the problem starts.

Anyhow, it's getting late (1:11a.m. EST) so I am going to bed.  I will try your suggestion tomorrow.  Thank you.

---

### Post by rsambuca on 2007-11-15
You still haven't said exactly what you have done, other that refer to some book or something.  In any event, in order to compile anything from source, you first have to install the necessary packages for compilation.  To do this, open a terminal and enter```
sudo apt-get install build-essential
```

Then [download the tarball from this link]("ftp://ftp.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.9/source/thunderbird-2.0.0.9-source.tar.bz2").

Take the tarball and run```
tar -xvzf thunderbird-2.0.0.9-source.tar.bz2
```
Change Directories (cd) into the new directory, and read the readme files.
Then, unless the instructions say otherwise, run```
./configure
```
Then ```
make
```
Then ```
sudo make install
```or as an alternative to this last command, run ```
sudo checkinstall
```This will create a .deb package which you can then double click to install (you will just have to install the 'checkinstall' package first).

---

### Post by iClouseau88 on 2007-11-15
Hi,

Thanks for replying to me.

1) I omitted "build-essential" because it's already installed.

2) I can see that the file I downloaded from [www.mozilla.org/products/thunderbird](www.mozilla.org/products/thunderbird) does NOT have the word "source".

3) In the same token, your source is different from mine, so are your filename and command.    Mine does not have the hyphen in front of it.

I hope you understand the frustration that a newbie like me is feeling, especially about the lack of consisstency among guides and tutorials.

I will try your suggestion later today.  Thanks again.

---

### Post by Irihapeti on 2007-11-15
If you downloaded the file from mozilla.org, then you have an already-compiled binary file, not the source code.

There are instructions on what to do with this in [https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion)

Essentially, it copies the files to /opt/thunderbird and then allows you to launch the program by typing

```
thunderbird
```

in a terminal.

You can also add a launcher to the top or bottom of your screen and/or to the applications menu.

---

### Post by iClouseau88 on 2007-11-16
Irihapeti,

Thank you so much for your explanation.  I followed the instructions in the link you provided, selected the Ubuntuzilla script method and was able to update or rather install TB 2.0.0.9 over the existing version 2.0.0.6.  It was relatively effortless.

Again, thank you kindly for your help.

:lolflag:

---

### Post by stchman on 2007-11-16
I have a script that will install TBird 2.0.0.9 on your Ubuntu system.

[http://www.stchman.com/tools_page.html](http://www.stchman.com/tools_page.html)

---

### Post by Irihapeti on 2007-11-16
> **iClouseau88 said:**
> 

Again, thank you kindly for your help.



You're most welcome.

---

### Post by rsambuca on 2007-11-16
After all of this you just installed the binary???  :mad:

What about your comment> Thanks for replying. I normally install softwares & updates via Synaptic, **but in this case I am anxious to install the latest version and to learn how to do this from source.**?   :confused:

---

### Post by iClouseau88 on 2007-11-16
Thank you Bob.  Your web page seems very well organized and contains lots of useful tips for Linux users, including newbies like me. I did bookmarked your page.

My hat off to you!

;-))

---

### Post by iClouseau88 on 2007-11-16
Hi rsambuca,

Like water, I chose the path of "least resistance".  If you read all my threads on this subject, you will know why.  There's always another time and opportunity for me to compile from "source".  I am just disappointed that there are no consistent standard procedure  and file format to help new Linux users.  I hope there are people out there being in the same boat or had the same experience, and being sympathetic to me.

Anyway, I like your Angela Jolie's avatar!

---

### Post by rsambuca on 2007-11-16
No sweat!  We have all been there.  I just thought I would give you a little bit of a shot since so many of us went through a lot of unnecessary typing for you! ;)

Good luck!

---

### Post by rsambuca on 2007-11-16
> **iClouseau88 said:**
> Hi rsambuca,

Like water, I chose the path of "least resistance".  If you read all my threads on this subject, you will know why.  There's always another time and opportunity for me to compile from "source".  **I am just disappointed that there are no consistent standard procedure  and file format to help new Linux users**.  I hope there are people out there being in the same boat or had the same experience, and being sympathetic to me.

Anyway, I like your Angela Jolie's avatar!

I thought I would just briefly comment on this.  Actually, there is a fairly standard procedure for Ubuntu.  Basically, unless you are doing something outside a regular user's needs, you should never have to do any compiling from source.  The Synaptic Package Manager will install over 20,000 packages from the Ubuntu repositories.  It was you who decided you couldn't wait to move from 2.0.0.8 to 2.0.0.9.  I mean, really is there any feature that you had to have?

Ubuntu as a rule doesn't upgrade versions of programs until the next release of Ubuntu.  If you are one of those users who require immediate upgrades to new versions of software, I might suggest that a "Rolling Release" Distro might be better suited to you.  These distros release the new packages on a continuous basis.  The benefit is that you don't have to wait the max 6 months, but the downside is that there may be a few extra bugs that you have to live with.  

In any event, I would suggest not getting too fancy at first since you are new to linux, but as you acquire more skills and knowledge, then you may enjoy trying a Rolling Release Distro such as Foresight Linux, Debian Sid, or, if you are really brave, Gentoo or Arch.

Take care!

---

### Post by mastergunner on 2007-11-24
Well I have tried everything on this page and I cant get the latest TBird. I have downloaded the latest from the mozilla site. I extracted it to my desktop. After that nothing workins to actuall install it. HELP!!!!

---

### Post by Irihapeti on 2007-11-24
> **mastergunner said:**
> Well I have tried everything on this page and I cant get the latest TBird. I have downloaded the latest from the mozilla site. I extracted it to my desktop. After that nothing workins to actuall install it. HELP!!!!

You need to use the instructions in the link I gave in an earlier message in this thread. There are commands that can be copied and pasted to the terminal. The files will be extracted to /opt/thunderbird. It does work - I've just used it to upgrade my own installation.

---

### Post by mastergunner on 2007-11-24
If you are talking about the commans below I just tried and it didnt upgrade mine.

Installing instructions for newest Thunderbird
Download the gzipped tarball for version you want to install

As of this writing, the latest version is 2.0.0.6

wget -c [http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.6/linux-i686/en-US/thunderbird-2.0.0.6.tar.gz](http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.6/linux-i686/en-US/thunderbird-2.0.0.6.tar.gz) 

If you are interested in the latest nightly build of Thunderbird 3.0 (DANGEROUS)

wget -c [http://ftp.mozilla.org/pub/mozilla.org/thunderbird/nightly/latest-trunk/thunderbird-3.0a1pre.en-US.linux-i686.tar.bz2](http://ftp.mozilla.org/pub/mozilla.org/thunderbird/nightly/latest-trunk/thunderbird-3.0a1pre.en-US.linux-i686.tar.bz2) 

and substitute the package name in the instructions below accordingly.
Extract the zipped archive

sudo tar -C /opt -zxvf thunderbird-2.0.0.6.tar.gz 

Make launcher command available to all users

sudo dpkg-divert --divert /usr/bin/mozilla-thunderbird.ubuntu --rename /usr/bin/mozilla-thunderbird 
sudo ln -s /opt/thunderbird/thunderbird /usr/bin/mozilla-thunderbird
sudo ln -s /opt/thunderbird/thunderbird /usr/bin/thunderbird
sudo ln -s /opt/thunderbird/thunderbird-bin /opt/thunderbird/mozilla-thunderbird-bin

---

### Post by mastergunner on 2007-11-24
.

---

### Post by mastergunner on 2007-11-24
Nothing has updated after trying again. Yes I replaced 2.0.0.6 with 2.0.0.9

---

### Post by Irihapeti on 2007-11-24
I'm sorry I can't tell you what's going on here. It might be worth starting a new thread with a different title, and someone who knows more than I do may be able to help.

---

### Post by D@vidITA on 2008-02-04
> **llamakc said:**
> Well as I said earlier you did NOT download the source. You downloaded an archive of all of the files needed to run Thunderbird.

[http://developer.mozilla.org/en/docs/Download_Mozilla_Source_Code](http://developer.mozilla.org/en/docs/Download_Mozilla_Source_Code)

Is the official page that points to the source. And here are the instructions.

[http://developer.mozilla.org/en/docs/Build_Documentation](http://developer.mozilla.org/en/docs/Build_Documentation)

I found this by searching "thunderbird source" in Google.

Great

---

