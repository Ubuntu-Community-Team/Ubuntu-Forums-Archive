---
title: "Tutorial - How to Install Mozilla Firefox 1.5.0.1"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-02-27
Hello ALL !!!

This is for all of you that want to TEST the NEW Mozilla Firefox 1.5.0.1:


_Tutorial - How to Install Mozilla Firefox 1.5.0.1_:


_For Ubuntu 5.10_:

_Source_:
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

_Note_:
Even though, the commands found below, are (almost) the same like those found in the above "Source" Internet Page, you will find that it is easier to install "Firefox 1.5.0.1" with the method shown below.

What I basically do, is I create ONE Script file & type ONLY ONE command in the Terminal.

Unfortunately, the method suggested in the above "Source" Internet Page, requires that YOU type each & EVERY command (one-by-one) in the Terminal.

... and if you make any "typo" mistakes:

a. You might mess up everything & an install might NEVER work out for you,

OR:

b. If you are lucky, you are just going to have to retype the command until you get it right.

However, my method is much more better, because if you EVER decide to Format Your Ubuntu again, you will only have to type ONE command, as opposed to many...


So, Here it goes:


_Part 1 – Backup your Bookmarks_: 
Before you start, make sure you Backup your "Bookmarks" or there is a chance that you might loose them...
To do this, perform the following:

1. Launch a Mozilla Firefox window.

2. From the Menu, select "Bookmarks\Manage Bookmarks"

3. From the New window that pops up, from the Menu select "File\Export"

4. Click on the button named "Save" & your "Bookmarks" will be saved on the 
    Desktop.

Congratulations, your "Bookmarks" Backup (file: "bookmarks.html"), was performed successfully.


_Part 2a – Install your Mozilla Firefox 1.5.0.1_: 
To Install, perform the following steps:

1. Visit the site:

	[http://www.mozilla.com/firefox/](http://www.mozilla.com/firefox/)

2. Click on the link named "Download Firefox" to download your Mozilla Firefox 
    1.5.0.1.
    Save it on your Desktop folder (mine is "/home/dimitris/Desktop")

3. From your Ubuntu's Menu, select "Applications\Accessories\Text Editor"

4. From the Text Editor's Menu, select "File\Save As"

5. Delete the name suggested "Unsaved Document 1" & type the name 
    "installfirefox.sh".

6. Under the "Save in Folder:", instead of "Home" select "Desktop".

7. Click on the button named "Save"

8. Copy & Paste the following text inside your Text Editor opened file (e.g. 
    "installfirefox.sh").

	#!/bin/bash

	## How to install the latest Firefox 1.5.0.1 Internet Browser:
	##
	## Source: "https://wiki.ubuntu.com/FirefoxNewVersion"

	## First download the file "firefox-1.5.0.1.tar.gr" to your Desktop.

	## Then run this file from the Terminal with the command "sh installfirefox.sh"


	cd /

	cd /home/dimitris/Desktop


	## The following command un-zips your downloaded file to inside your folder 
	## named "/opt". 

	sudo tar -C /opt -x -z -v -f firefox-1.5.0.1.tar.gz


	cd /

	cd /opt/firefox/plugins

	## The following command removes "totem-mozilla" because it does NOT 
	## work with the program you are trying to install (Firefox 1.5).

	sudo ln -s /usr/lib/mozilla-firefox/plugins/* .

	## For some reason I could NOT remove the following (as required):

	# sudo rm libtotem_mozilla.*


	cd /

	cd /home/dimitris

	## Rename your old profile in your "/home/dimitris" directory, leaving it as
	## a Backup:


	mv .mozilla/firefox .mozilla/firefox1.0.x.ubuntu


	## We modify the symbolic link in "/usr/bin", to ensure that the NEW Firefox 
	## is used as the default version:


	## 1. First, we modify the old Firefox in the "/usr/bin/firefox":

	sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
	
	sudo ln -s /opt/firefox/firefox /usr/bin/firefox


	## 2. Then, we modify the NEW Firefox in the "/usr/bin/mozilla-firefox" (it 
	##    will be used as the default gnome browser):

	sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox

	sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox


	## The "dpkg-divert" command moves the OLD system-wide "/usr/bin/firefox" 
        ## to a new name.

	## The "ln" command places a symbolic link to the newly installed Firefox in 
	## "/usr/bin". 


	## Congratulations, you have now installed successfully your Mozilla Firefox 
	## 1.5.0.1 Internet Browser.

	## Go & Check it out !

9. In the above part that you Copied & Pasted, you MUST replace wherever you 
    see the word "dimitris", with YOUR name (e.g. the username you type every 
    time you boot your computer – mine is "dimitris").

10. When finished, from the Text Editor's Menu, select "File\Save" & then again 
      "File\Quit".

11. From your Ubuntu's Menu, select "Applications\Accessories\Terminal"

12. Inside the Terminal, type "sudo -i", to get root privileges. 

13. Then type your Password.

14. Then type "cd /home/dimitris/Desktop" while replacing the "dimitris" with YOUR 
      username (e.g. the username you type every time you boot your computer – 
      mine is "dimitris").

15. Type the command "sh installfirefox.sh" to Run your Script file, named 
      "installfirefox.sh".

Congratulations, you have successfully installed Firefox 1.5.0.1 in your Ubuntu PC.

To test whether it works OK, launch a Mozilla Firefox window & surf around.
Alternatively, from within your Mozilla Firefox's window select "Help\About Mozilla Firefox".
The version stated in the new window should be v1.5.0.1.


_Part 2b - Removing your Mozilla Firefox 1.5.0.1_:
If for some reason you want to undo the installation & revert back to the standard Firefox 1.0.7, perform the following:

1. Part 2: steps 3 & 4.

2. Part 2: step 5, replacing "installfirefox.sh" with "restorefirefox.sh"

3. Part 2: steps 6 & 7.

4. Part 2: step 8, only this time, type the following:

	#!/bin/bash

	## How to Restore your OLD Firefox Internet Browser:
	##
	## Source: "https://wiki.ubuntu.com/FirefoxNewVersion"

	## Run this file from the Terminal with the command "sh restorefirefox.sh"

	cd /

	cd /home/dimitris/Desktop


	## Restore the symbolic link: 

	sudo rm /usr/bin/firefox
	
	sudo dpkg-divert --rename --remove /usr/bin/firefox


	## Restore your old profile:
	## (This is different to what the "Source" Site suggested – the "Source's" 
        ##   site version, created errors).

	cd /home/dimitris/.mozilla

	mv firefox firefox1.5.0.1

	mv firefox1.0.x.ubuntu firefox

	## (optional) Delete the firefox directory 

	sudo rm -r /opt/firefox


	## Congratulations, you have now Restored successfully your OLD Mozilla 
	## Firefox Internet Browser.

	## Go & Check it out ! 

5. In the above part that you Copied & Pasted, you MUST replace wherever you 
    see the word "dimitris", with YOUR name (e.g. the username you type every 
    time you boot your computer – mine is "dimitris").

6. Part 2: steps 10 - 14.

7. Part 2: step 15, replacing "sh installfirefox.sh" with "sh restorefirefox.sh"

Congratulations, you have successfully removed Firefox 1.5.0.1 from your Ubuntu PC.


_Part 3 – Re-install your Bookmarks_: 
To do this, perform the following:

1. Part 1: steps 1 & 2.

2. Part 1: step 3, replacing "File\Export" with "File\Import"

3. Click on the button named "Next".

4. On the right-hand side, click on the button named "Desktop".

5. Scroll down to locate the file named "bookmarks.html" & select it.

6. Click on the button named "Open".

7. From the Menu, select "File\Close".

Congratulations, you have successfully installed ALL your "Bookmarks" to your Firefox 1.5.0.1 in your Ubuntu PC.


_Conclusion_:
Backup the files lying on your Desktop:

1. The downloaded Mozilla Firefox 1.5.0.1 program

2. The file named "installfirefox.sh" you created in this Tutorial

3. The file named "restorefirefox.sh" you created in this Tutorial (if you decided to 
    remove Firefox 1.5)

4.  The file named "bookmarks.html" (your Bookmarks Backup), you created in this 
     Tutorial.


_Advantages_:
If you ever have to Format your Hard Drive & Re-install Ubuntu, you only have to perform "Part 2: steps 11-15", to install your Mozilla Firefox 1.5.0.1.
At the same time, this Install file ("installfirefox.sh"), would work great if you had to install Firefox 1.5.0.1 on multiple PCs.

That was pretty Quick & Neat, wasn't it?

_Note_:
You will probably wonder why there is NO ".deb" file to install, from the "Synaptic Package Manager" or from the "Terminal" (with a command like "dpkg -i package_name.deb")...
To learn why, read the following Ubuntu Forum's thread:

	[http://ubuntuforums.org/showthread.php?t=96595](http://ubuntuforums.org/showthread.php?t=96595)


Have Fun !!!

---

### Post by TrendyDark on 2006-02-27
This should be in the "Customization Tips & Tricks" forum, but it's very simple to install 1.5.0.1, just get automatix :)

---

### Post by dvarsam on 2006-02-27
I have Posted there too !!!

But it takes around one Day to go through...

So, I always put it here first...

---

### Post by Haegin on 2006-02-28
your script will only work for your user. If you change
```

 cd /

cd /home/dimitris/Desktop

```
to
```

cd
cd Desktop

```
then it will work for all users.
Also if you remove all the sudo bits at the beginning of the lines and then run
```

sudo sh installfirefox.sh

```
instead of opening the terminal and using sudo -i.
This makes it simpler as you are running it as root. You could also check the user is root before it begins by adding this before the cd command at the beginning
```

if [ `id -u` != "0" ]; then
	echo "Sorry, you are not root."
	exit 1
fi

```

With these changes I end up with this code:
```

 #!/bin/bash

## How to install the latest Firefox 1.5.0.1 Internet Browser:
##
## Source: "https://wiki.ubuntu.com/FirefoxNewVersion"
## First download the file "firefox-1.5.0.1.tar.gr" to your Desktop.
## Then run this file from the Terminal with the command "sudo installfirefox.sh"

## Check if the user is root and if not then tell them off and end the script
if [ `id -u` != "0" ]; then
	echo "Sorry, you are not root."
	exit 1
fi

cd 
cd Desktop

## The following command un-zips your downloaded file to inside your folder
## named "/opt".
tar -C /opt -x -z -v -f firefox-1.5.0.1.tar.gz
cd /
cd /opt/firefox/plugins

## The following command removes "totem-mozilla" because it does NOT
## work with the program you are trying to install (Firefox 1.5).
ln -s /usr/lib/mozilla-firefox/plugins/* .

## For some reason I could NOT remove the following (as required):
# sudo rm libtotem_mozilla.*
cd /
cd 

## Rename your old profile in your "/home/dimitris" directory, leaving it as
## a Backup:
mv .mozilla/firefox .mozilla/firefox1.0.x.ubuntu

## We modify the symbolic link in "/usr/bin", to ensure that the NEW Firefox
## is used as the default version:

## 1. First, we modify the old Firefox in the "/usr/bin/firefox":
dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
ln -s /opt/firefox/firefox /usr/bin/firefox

## 2. Then, we modify the NEW Firefox in the "/usr/bin/mozilla-firefox" (it
## will be used as the default gnome browser):
dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox

## The "dpkg-divert" command moves the OLD system-wide "/usr/bin/firefox"
## to a new name.
## The "ln" command places a symbolic link to the newly installed Firefox in
## "/usr/bin".

## Congratulations, you have now installed successfully your Mozilla Firefox
## 1.5.0.1 Internet Browser.

## Go & Check it out !

```

---

### Post by carverj on 2006-02-28
Right, I think I'm doing OK (fingers crossed) until the link (ln) command in terminal

```
jeremy@UBUNTU:/opt$ ln -s /opt/firefox/firefox 
/usr/bin/mozilla-firefox ln: `/usr/bin/mozilla-firefox': File exists

```
when i try to open firefox from the desktop now I get
Cannot launch icon : Details: Failed to execute child process "firefox" (No such file or directory)
:confused:   

  To bring up to speed I downloaded 1.5 from website, installed to home partition, changed the theme , then followed the directions above.
tried the commands above to try to solve problem with firefox 1.5 of menu options not openign correctly (would try to open edit > preferences in 1.5 and not functioning correctly)

 Then I noticed that firefox 1.07 looks similarly incorrect (see pic below)
Oh, how do you add a screenshot here? tried entering URL location and cut and paste but it just inserted text
anyway, there is a gap at the bottom of browser with a small red ^ right on the left hand side of the gap!
any advice would be very helpful
Thanks

____________
Any intelligent fool can make things bigger, more complex, and more violent. It takes a touch of genius -- and a lot of courage -- to move in the opposite direction. -Albert Einstein

---

### Post by pinguinus on 2006-03-01
On the Wiki page FirefoxNewVersion they also mention the experimental Firefox 1.5 deb package building script for Breezy as a convenient method of installing Firefox 1.5* as a deb package: [https://wiki.ubuntu.com/FirefoxNewVersion#head-a14697a00e2bbd64f4d6ee098d69e97b5209ad44]("https://wiki.ubuntu.com/FirefoxNewVersion#head-a14697a00e2bbd64f4d6ee098d69e97b5209ad44") 

However, I haven't found anyone sharing their experiences with that deb file installation method here. Does that installation method work or not? How does it compare with the installation method detailed above? How does it deal with the default Breezy Firefox? What problems there might be, with Firefox extensions etc, if using the deb file instead of using the instructions above? 

I thought that I might try that deb installation method but I would like to first read if anybody could share some experiences with it.

---

### Post by pinguinus on 2006-03-04
Still haven't tried that deb installation method - but instead tried Automatix  for the first time (especially as everyones seems to be talking about it here...) Automatix works great, and not only when installing Firefox 1.5 but in a lot of other cases too. I'd now recommend Automatix as the best - read: most newbie-friendly - way of installing Firefox 1.5 in Breezy.

Automatix:
[http://www.ubuntuforums.org/showthread.php?t=114251](http://www.ubuntuforums.org/showthread.php?t=114251)
[http://ubuntuforums.org/showthread.php?t=90797](http://ubuntuforums.org/showthread.php?t=90797)

---

### Post by Jabbadahut on 2006-03-22
[QUOTE=dvarsam]Hello ALL !!!

This is for all of you that want to TEST the NEW Mozilla Firefox 1.5.0.1: [/QUOTE]

I tried to install the program using your script, and **making sure** I replaced  your username with my own.  The script ran without any problems, & I launched Mozilla Firefox via the shortcut on the toolbar.  Firefox's Feedback Agent started, & I selected to turn it on, so in case there's a problem with the program crashing, I could send it in.

However, after that, nothing happens.  I tried launching the browser again - same thing.  The browser does not start.  So now, I have access to the internet, but I can't browse the web.  

So I am now using Windows XP to view the web, and apparantly cannot use Firefox under Ubuntu until I can get this problem resolved. :(

I suppose I could reformat & re-install Ubuntu to get back the original browser, but that's overkill, lol.  One user above mentioned making changes to the script, but I am cautious about doing that, as I don't want to mess up the installation any further than it seems to be.

Any help for this newbie Linux user who is learning by "trial & error" would much appreciated. :)

---

### Post by Haegin on 2006-03-23
have you tried this:
[code]
## How to Restore your OLD Firefox Internet Browser:
##
## Source: "https://wiki.ubuntu.com/FirefoxNewVersion"
## Run this file from the Terminal with the command "sh restorefirefox.sh"

cd /
cd /home/dimitris/Desktop
## Restore the symbolic link:

sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox

## Restore your old profile:
## (This is different to what the "Source" Site suggested – the "Source's"
## site version, created errors).

cd $HOME/.mozilla
mv firefox firefox1.5.0.1
mv firefox1.0.x.ubuntu firefox

## (optional) Delete the firefox directory
sudo rm -r /opt/firefox

## Congratulations, you have now Restored successfully your OLD Mozilla
## Firefox Internet Browser.

/code]

---

### Post by Jabbadahut on 2006-03-23
Thanks for replying.  Restoring the original version of Firefox worked as you suggested.  So at least I have a functional web  browser.

However, I tried installing the newer version once more using your code, but I am still having the same problem.  After clicking on the Firefox icon, nothing happens.

I tried using the code "cd Desktop" at first, but I kept getting a "No such file or directory" error, and everything after that wouldn't work, because of that.  I would get the same problem that carverj metioned above was getting.

Okay, I thought I the problem was, so I edited the code from "cd Dekstop" to the following:

```


cd /home/[myloginname]/Desktop


```

Where [myloginname] is what I use to login to Ubuntu.  This seemed to work, as the code actually unpacked the Firefox package (as beforehand, I'd get the "no such file or directory" error right here).  But after the install, I click on the Firefox icon and I get the same problem I originally had.  Nothing happens after I click on the icon.  Is the icon somehow pointing to the wrong place, or . . . ? :confused: 

I am not an expert on Linux commands, so I am submitting what I had in the Terminal too see if we can root out the problem.  For the sake of simplicity, and to save space here, I'll omit to what I believe are "remarks" in the script, which the OS would ignore.  If someone here thinks I should put them in, let me know.

```


jay@c-24-19-38-82LANPARTY:~$ sudo -i
root@c-24-19-38-82LANPARTY:~# #!/bin/bash
root@c-24-19-38-82LANPARTY:~# if [ `id -u` != "0" ]; then
>
> echo "Sorry, you are not root."
>
> exit 1
>
> fi
root@c-24-19-38-82LANPARTY:~#
root@c-24-19-38-82LANPARTY:~#
root@c-24-19-38-82LANPARTY:~#
root@c-24-19-38-82LANPARTY:~# cd
root@c-24-19-38-82LANPARTY:~#
root@c-24-19-38-82LANPARTY:~# cd /home/jay/Desktop
root@c-24-19-38-82LANPARTY:/home/jay/Desktop#
root@c-24-19-38-82LANPARTY:/home/jay/Desktop# tar -C /opt -x -z -v -f firefox-1.5.0.1.tar.gz
firefox/
firefox/.autoreg
firefox/chrome/
firefox/chrome/en-US.jar
firefox/chrome/en-US.manifest
firefox/chrome/browser.jar
firefox/chrome/browser.manifest
firefox/chrome/classic.jar
firefox/chrome/classic.manifest
firefox/chrome/comm.jar
firefox/chrome/comm.manifest
firefox/chrome/toolkit.jar
firefox/chrome/toolkit.manifest
firefox/chrome/icons/
firefox/chrome/icons/default/
firefox/chrome/icons/default/default.xpm
firefox/chrome/reporter.manifest
firefox/chrome/reporter.jar
firefox/chrome/pippki.jar
firefox/chrome/pippki.manifest
firefox/defaults/
firefox/defaults/pref/
firefox/defaults/pref/firefox-l10n.js
firefox/defaults/pref/reporter.js
firefox/defaults/pref/firefox.js
firefox/defaults/pref/channel-prefs.js
firefox/defaults/profile/
firefox/defaults/profile/bookmarks.html
firefox/defaults/profile/localstore.rdf
firefox/defaults/profile/prefs.js
firefox/defaults/profile/search.rdf
firefox/defaults/profile/mimeTypes.rdf
firefox/defaults/profile/chrome/
firefox/defaults/profile/chrome/userChrome-example.css
firefox/defaults/profile/chrome/userContent-example.css
firefox/defaults/autoconfig/
firefox/defaults/autoconfig/platform.js
firefox/defaults/autoconfig/prefcalls.js
firefox/browserconfig.properties
firefox/searchplugins/
firefox/searchplugins/amazondotcom.png
firefox/searchplugins/amazondotcom.src
firefox/searchplugins/answers.png
firefox/searchplugins/answers.src
firefox/searchplugins/creativecommons.png
firefox/searchplugins/creativecommons.src
firefox/searchplugins/eBay.gif
firefox/searchplugins/eBay.src
firefox/searchplugins/google.gif
firefox/searchplugins/google.src
firefox/searchplugins/yahoo.gif
firefox/searchplugins/yahoo.src
firefox/updater.ini
firefox/libmozjs.so
firefox/libplc4.so
firefox/libplds4.so
firefox/libxpcom.so
firefox/libxpcom_core.so
firefox/libxpistub.so
firefox/libnspr4.so
firefox/components/
firefox/components/libxpinstall.so
firefox/components/libjar50.so
firefox/components/libjsd.so
firefox/components/nsBrowserContentHandler.js
firefox/components/nsBrowserGlue.js
firefox/components/nsSetDefaultBrowser.js
firefox/components/jsconsole-clhandler.js
firefox/components/nsCloseAllWindows.js
firefox/components/nsDictionary.js
firefox/components/nsFilePicker.js
firefox/components/nsHelperAppDlg.js
firefox/components/nsInterfaceInfoToIDL.js
firefox/components/nsProxyAutoConfig.js
firefox/components/nsSidebar.js
firefox/components/nsXmlRpcClient.js
firefox/components/nsExtensionManager.js
firefox/components/nsUpdateService.js
firefox/components/libmozgnome.so
firefox/components/libnkgnomevfs.so
firefox/components/browser.xpt
firefox/libxpcom_compat.so
firefox/firefox-bin
firefox/firefox
firefox/mozilla-xremote-client
firefox/run-mozilla.sh
firefox/plugins/
firefox/plugins/libnullplugin.so
firefox/res/
firefox/res/cmessage.txt
firefox/res/hiddenWindow.html
firefox/res/ua.css
firefox/res/html.css
firefox/res/quirk.css
firefox/res/forms.css
firefox/res/EditorOverride.css
firefox/res/table-add-column-after-active.gif
firefox/res/table-add-column-after-hover.gif
firefox/res/table-add-column-after.gif
firefox/res/table-add-column-before-active.gif
firefox/res/table-add-column-before-hover.gif
firefox/res/table-add-column-before.gif
firefox/res/table-add-row-after-active.gif
firefox/res/table-add-row-after-hover.gif
firefox/res/table-add-row-after.gif
firefox/res/table-add-row-before-active.gif
firefox/res/table-add-row-before-hover.gif
firefox/res/table-add-row-before.gif
firefox/res/table-remove-column-active.gif
firefox/res/table-remove-column-hover.gif
firefox/res/table-remove-column.gif
firefox/res/table-remove-row-active.gif
firefox/res/table-remove-row-hover.gif
firefox/res/table-remove-row.gif
firefox/res/arrowd.gif
firefox/res/grabber.gif
firefox/res/viewsource.css
firefox/res/mathml.css
firefox/res/arrow.gif
firefox/res/loading-image.gif
firefox/res/broken-image.gif
firefox/res/fonts/
firefox/res/fonts/fontEncoding.properties
firefox/res/fonts/mathfont.properties
firefox/res/fonts/mathfontCMEX10.properties
firefox/res/fonts/mathfontCMSY10.properties
firefox/res/fonts/mathfontMath1.properties
firefox/res/fonts/mathfontMath2.properties
firefox/res/fonts/mathfontMath4.properties
firefox/res/fonts/mathfontMTExtra.properties
firefox/res/fonts/mathfontPUA.properties
firefox/res/fonts/mathfontSymbol.properties
firefox/res/fonts/pangoFontEncoding.properties
firefox/res/dtd/
firefox/res/dtd/mathml.dtd
firefox/res/dtd/xhtml11.dtd
firefox/res/html/
firefox/res/html/gopher-audio.gif
firefox/res/html/gopher-binary.gif
firefox/res/html/gopher-find.gif
firefox/res/html/gopher-image.gif
firefox/res/html/gopher-menu.gif
firefox/res/html/gopher-movie.gif
firefox/res/html/gopher-sound.gif
firefox/res/html/gopher-telnet.gif
firefox/res/html/gopher-text.gif
firefox/res/html/gopher-unknown.gif
firefox/res/unixcharset.properties
firefox/res/charsetalias.properties
firefox/res/charsetData.properties
firefox/res/langGroups.properties
firefox/res/language.properties
firefox/res/entityTables/
firefox/res/entityTables/html40Latin1.properties
firefox/res/entityTables/html40Special.properties
firefox/res/entityTables/html40Symbols.properties
firefox/res/entityTables/htmlEntityVersions.properties
firefox/res/entityTables/mathml20.properties
firefox/res/entityTables/transliterate.properties
firefox/res/svg.css
firefox/xpicleanup
firefox/extensions/
firefox/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/
firefox/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/install.rdf
firefox/extensions/inspector@mozilla.org/
firefox/extensions/inspector@mozilla.org/install.rdf
firefox/extensions/inspector@mozilla.org/components/
firefox/extensions/inspector@mozilla.org/components/inspector-cmdline.js
firefox/extensions/inspector@mozilla.org/components/libinspector.so
firefox/extensions/inspector@mozilla.org/components/inspector.xpt
firefox/extensions/inspector@mozilla.org/chrome.manifest
firefox/extensions/inspector@mozilla.org/chrome/
firefox/extensions/inspector@mozilla.org/chrome/inspector.jar
firefox/extensions/inspector@mozilla.org/defaults/
firefox/extensions/inspector@mozilla.org/defaults/preferences/
firefox/extensions/inspector@mozilla.org/defaults/preferences/inspector.js
firefox/extensions/talkback@mozilla.org/
firefox/extensions/talkback@mozilla.org/install.rdf
firefox/extensions/talkback@mozilla.org/chrome.manifest
firefox/extensions/talkback@mozilla.org/components/
firefox/extensions/talkback@mozilla.org/components/libqfaservices.so
firefox/extensions/talkback@mozilla.org/components/qfaservices.xpt
firefox/extensions/talkback@mozilla.org/components/talkback/
firefox/extensions/talkback@mozilla.org/components/talkback/master.ini
firefox/extensions/talkback@mozilla.org/components/talkback/talkback
firefox/extensions/talkback@mozilla.org/components/talkback/talkback.so
firefox/extensions/talkback@mozilla.org/components/talkback/XTalkback.ad
firefox/icons/
firefox/icons/mozicon16.xpm
firefox/icons/mozicon50.xpm
firefox/icons/document.png
firefox/icons/mozicon128.png
firefox/greprefs/
firefox/greprefs/all.js
firefox/greprefs/security-prefs.js
firefox/greprefs/xpinstall.js
firefox/libnssckbi.so
firefox/libnss3.so
firefox/libsmime3.so
firefox/libsoftokn3.chk
firefox/libsoftokn3.so
firefox/libssl3.so
firefox/updater
firefox/readme.txt
firefox/removed-files
root@c-24-19-38-82LANPARTY:/home/jay/Desktop#
root@c-24-19-38-82LANPARTY:/home/jay/Desktop# cd /
root@c-24-19-38-82LANPARTY:/#
root@c-24-19-38-82LANPARTY:/# cd /opt/firefox/plugins
root@c-24-19-38-82LANPARTY:/opt/firefox/plugins#
root@c-24-19-38-82LANPARTY:/opt/firefox/plugins# ln -s /usr/lib/mozilla-firefox/plugins/* .
root@c-24-19-38-82LANPARTY:/opt/firefox/plugins#
root@c-24-19-38-82LANPARTY:/opt/firefox/plugins# cd /
root@c-24-19-38-82LANPARTY:/#
root@c-24-19-38-82LANPARTY:/# cd
root@c-24-19-38-82LANPARTY:~#
root@c-24-19-38-82LANPARTY:~# mv .mozilla/firefox .mozilla/firefox1.0.x.ubuntu
mv: cannot stat `.mozilla/firefox': No such file or directory
root@c-24-19-38-82LANPARTY:~#
root@c-24-19-38-82LANPARTY:~# dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
Adding `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
root@c-24-19-38-82LANPARTY:~#
root@c-24-19-38-82LANPARTY:~# ln -s /opt/firefox/firefox /usr/bin/firefox
root@c-24-19-38-82LANPARTY:~#
root@c-24-19-38-82LANPARTY:~# dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
Leaving `local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu'
root@c-24-19-38-82LANPARTY:~#
root@c-24-19-38-82LANPARTY:~# ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
ln: `/usr/bin/mozilla-firefox': File exists
root@c-24-19-38-82LANPARTY:~#
root@c-24-19-38-82LANPARTY:~#


```

Everything seems okay,  but further down, I noticed the following problem:

```


mv .mozilla/firefox .mozilla/firefox1.0.x.ubuntu
mv: cannot stat `.mozilla/firefox': No such file or directory


```

Hmm. Is this what's preventing it from working, or is it somewhere else? :-k

One would say that for the sake of simplicity, I might use Automatix.  Unfortunately, I have the AMD64 version of Ubuntu, which isn't compatible with that.

I hate to be a pest, but I do appreciate everyone's help - especially those who helped me get the OS to recognize & mount my windows partitions.

You know, I have a feeling that the solution is just right in front of me, and I am blind, lol. :p

---

### Post by aysiu on 2006-03-23
The problem is that you're logged in as root.

Log in as user--that's what the tutorial tells you to do.
If you log in as user, there is a Desktop to *cd* to. There is a .mozilla folder.

---

### Post by dvarsam on 2006-03-23
Hello!

I was the author of this thread.

Sorry I did not help you guys with your concerns & problems, but please consider me a newbie too!

I am NOT a very acqainted to Ubuntu & that is the reason I avoided responding...
...I did NOT respond, because I an not an experienced user in this...

I have created better scripts now to do this...

But that does NOT mean that the better scripts will SOLVE your problems...

In this thread, I created the scripts so that they help ME install the "newest" Mozilla Firefox in no time & with no typos during the process (compared to if I did this from CLI).
Then I decided to share my experience with you...

To be honest I, myself, did NOT manage to finally install a workable Mozilla Firefox (latest version), with the above method, at all...

AND please NOTE that my thread came right from the Ubuntu Wiki pages.
So, do NOT put the blame on me...
I am a beginner too!!!
I just automated the Ubuntu Wiki's procedure & corrected some of its mistakes...
IF the Ubuntu Wiki was faulty, THEN so is my script!!!
At least, though, MY script is capable to turn things back to normal IF you do not manage to make it work... (compared to the Ubuntu wiki which can NOT...)

_Outcome_:
So, currently I use the Mozilla Firefox that comes pre-installed with Breezy (the old version)!

I would have continued my efforts on installing the Mozilla Firefox latest version (& written a response), only after I had managed to create Ubuntu Backups.

...because I wanted to experiment on installing the latest Mozilla Firefox on a "newly" installed Ubuntu System.

So, IF I failed to install, I wanted to turn my Ubuntu (from the Backup), into a "freshly" install & try again.
IF I failed again, again, I would turn my Ubuntu (from the Backup), into a "freshly" install & try again.

My goal was to give instructions on how to install, on a "freshly" installed Ubuntu.

IF I had installed tons of software & then created the tutorial, probably the tutorial could work for MY PC, but NOT work on YOURS... which would turn this Tutorial effort into "useless"...

So, I wanted to figure out an installation proccess that would solve this right from the start...

Unfortunately, making Backups in Ubuntu was NOT as easy as I expected (& compared to the Windows world).

Using the TAR command suggested in the "Customization Tips & Tricks" Forum, it did NOT really backup PROGRAMS - only personal folders...

So, the procedure to re-install from a TAR backup did NOT put my Ubuntu back to the "newly" installed phase I really wanted... (and get rid of programs I personally installed - the additional programs remained intact whenever I would re-install the Backup...)

To make my Ubuntu look as "new", I would have to perform a fresh install from the CD, every time...

That I did NOT like...

Other Backup procedures created other problems... (& had other limitations)...

So, I have NOT even managed to make Backups...

... and that is why I am not getting back trying to figure out how to solve this...

_Conclusion_:
So, to help you out, I consider this case as UNSOLVED.

Forgive me, as my knowledge is limited to help you...

Besides, I thought that the rest of the people is THIS Forum (with higher knowledge & skills compared to mine) would have a way to make this work, for ALL of us...

Unfortunately, that was NOT the case...

From my personal experience, only in rare times do I get REAL help...

Till today, I have posted many questions, and the most difficult ones are left unanswered...

I would suggest that you try to use the other method suggested - the Automatix.

I have not yet used it because (in my opinion), it installs also other software that I do NOT want them installed on my Ubuntu.

_What I do NOT really understand HERE is this_:
If there is a program called "Automatix" that performs ALL these installs for US successfully...,
...why don't they give us the Script that the program "Automatix" uses, so that we can use (from the Script), ONLY the part that we are interested, which is the Installation of the Mozilla Firefox latest version!!!

Why???

Why do we have to be FORCED to install everything, while we just want to install ONLY Firefox's latest version?

Some things function REALLY weird in this community dude...

Good Luck with whatever you decide to do!

dvarsam.

---

### Post by Jabbadahut on 2006-03-24
[QUOTE=aysiu]The problem is that you're logged in as root.

Log in as user--that's what the tutorial tells you to do.
If you log in as user, there is a Desktop to *cd* to. There is a .mozilla folder.[/QUOTE]

Thanks for responding.  Actually, I should mention that there is a remark at the beginning, which I omitted in my code above, because it's ignored by the system and only there for the benefit of the user, to show them what's going on:

"## Check if the user is root and if not then tell them off and end the script"

That's at the beginning.  Please understand I am not disagreeing with you, but you say I should be logged in as user.  So why would the remark state to check to see if the user is root, otherwise stop the script? :confused:

How do I login as user?  I thought I always was doing so, whenever Ubuntu boots and I'm prompted to put in my username & password.  Or is that something totally different?

[QUOTE=dvarsam]

AND please NOTE that my thread came right from the Ubuntu Wiki pages.
So, do NOT put the blame on me...
I am a beginner too!!![/QUOTE]

Dvarsam, I am not blaming you.  If I came across that way, than I apologize.  I am a newbie to Linux myself, too.  I have used Windows & DOS for several years, so much that typing commands have become 2nd nature.  I thought that using a command line for Linux would be similar in concept.  I would use Automatix, but unfortunately  the version of Ubuntu I have is AMD64,  which is the kind of processor I have, but it's not comptatible with Automatix.  

My only reason for wanting to install the newest version of Firefox is to get the same look and feel that I saw on the Windows version.  Like, when I go to 'Tools', in the browser, why don't I see an options menu, to configure Firefox the way I want?  All I see is "Web Search", "Downloads", "Extensions", "Themes", etc., but not "Options", where I can adjust settings to how I want Firefox to work.  I thought that perhaps this is something not available in the version I have, and installing a newer version would be a solution.

Looking at this whole issue, if I can't get the new version of Firefox installed, then at least I could chalk this up to a learning experience. :)  And, if possible, can anyone here tell me where I could find the "options" menu in the version of Firefox I got? (version 1.0.7)  I can't find it. :p

I appreciate everyone's patience with me.  I am learning little by little.  I'll get this solved sooner or later. :mrgreen:

---

### Post by dvarsam on 2006-03-24
[QUOTE=Jabbada]
...I am not blaming you. If I came across that way, than I apologize...

...if possible, can anyone here tell me where I could find the "options" menu in the version of Firefox I got (version 1.0.7)?
I can't find it...
[/QUOTE]

Hello Jabbada, got your message!

No need to apologize...
I was not referring to you, I was just talking to everybody...
I am trying to offer everything I know to the Ubuntu community...
And of course NOT all my Tutorials might be considered useful to everybody...
But when I posted this, I thought that it was some kind of my mistake...
not the Wiki's one...
I only found out, it was a faulty wiki afterwards...
I even thought that I was probably the only one having such a problem...
But at the same time, I hoped that people with more experience would provide a solution in NO time...
Seems this is not the case...

The options menu in Mozilla Firefox - you probably mean selecting from the Menu "Edit\Preferences"?

Take care & hope we solve this out cause I would like to have installed the latest Mozilla too!

---

### Post by aysiu on 2006-03-24
[QUOTE=Jabbadahut]Thanks for responding.  Actually, I should mention that there is a remark at the beginning, which I omitted in my code above, because it's ignored by the system and only there for the benefit of the user, to show them what's going on:

"## Check if the user is root and if not then tell them off and end the script"

That's at the beginning.  Please understand I am not disagreeing with you, but you say I should be logged in as user.  So why would the remark state to check to see if the user is root, otherwise stop the script? :confused:[/quote] I don't know. Who wrote the script? The Wiki certainly doesn't have you log in as root.

I wrote a quick script based on the Wiki, and I tested it on a test partition--it works. 

Just download the attached file to your desktop. Then go to

(Gnome): Applications > Accessories > Terminal
(KDE): KMenu > System > Konsole

and type ```
cd Desktop
mv installnewfirefox.sh.txt installnewfirefox.sh
chmod +x installnewfirefox.sh
./installnewfirefox.sh
``` If you want to avoid the command-line altogether, this is what the above commands mean (and you can do these all graphically, except the *sudo ./installnewfirefox.sh* command--*that* you have to do in the terminal):

**cd Desktop**: change to the "desktop" directory (this is where you downloaded the file to, remember?
**mv installnewfirefox.sh.txt installnewfirefox.sh**: basically, rename the file and remove the .txt extension
**chmod +x installnewfirefox.sh**: right-click on the file, go to permissions, and make sure it's "executable."

The attached screenshot walks you through all the point-and-click steps if you're afraid of the command-line (the steps are in order based on green number).

The advantage of this script is that you need only the script (no other steps except running it, essentially). It will download Firefox for you. It will back up your Firefox preferences folder.

**Edit**: If you're following the screenshot tutorial instead of the terminal commands, do not type ```
sudo ./installnewfirefox.sh
``` as this will make root the owner of your backed up profile.

---

### Post by Jabbadahut on 2006-03-24
Thanks, aysiu for the script, and I appreciate your assistance.

Unfortunately, I am still having problems.  I ran the script in the Terminal as instructed, and it runs fine.  However, when I try to click on the iFirefox icon on the toolbar on top, nothing happens.  I do see the screen "blip" something on for a very brief instant, like it's doing something, but nothing after that.  I click the icon again, and the "hourglass" appears doing its proceedure, but still nothing after that.

I examined the code and I no errors that I can tell from.

Why am I having trouble installing this program?!? :confused: ](*,)  First of all, let's backup for a moment.  As I understand,  someone in this thread mentioned earlier the script that was used here are for Breezy Badger (whatever that is), am I correct?  I looked at the Synaptic Package Manager, and when I select "settings", then "repositories" I see "Breezy Badger 5.10" with a checkmark by it for the binary & source, so that means I do indeed have Breezy Badger, right?

Aisyu, you say that it ran fine on a test partition on your system.  Maybe I should un-install Ubuntu, re-install it, and try again?  I realize that is overkill, as I had absolutely no trouble getting it up & running as far as my hardware & internet connection was concerned, but I am running out of ideas.

Does anyone else here have a suggestion?  Maybe I am neglecting something?

---

### Post by aysiu on 2006-03-24
A reinstall is a bit extreme. I guess it all depends on how much time you have. I've found reinstalls to be a good learning experience.

Let me spell out for you, though, exactly what both the Wiki steps *and* my script do.

1. It's quite simple, actually. The first thing is that you have to install libstdc++5. You can check in Synaptic Package Manager to see if you have that installed.

2. The second is unzipping the Firefox .tar.gz. The script and the Wiki have you do it from the command-line because it's easier from a script/Wiki point of view. You can just as easily unzip the .tar.gz by double-clicking on it and selecting "extract."

3. Once that happens, go into the newly unzipped folder, and you'll see a file called *firefox*. If you see another one called *firefox.bin*, ignore it. Double-click on *firefox* (yes, right from the folder on your desktop). Firefox 1.5.0.1 *should* open.

4. The rest of the Wiki/script just integrates the new Firefox into your system, replacing the launch command to 1.0.7 to redirect to 1.5.0.1 and making sure that the new version links to your plugins (so you can watch Flash, for example).

Try to do it graphically. If you can get through step #3, I'll walk you through how to do step #4. Let me know if you get stuck before step #3, though.

---

### Post by Jabbadahut on 2006-03-24
Many thanks again.  I do have libstdc++5 installed, & have the firefox package extracted.

What's next after getting to the Firefox folder at the desktop? :)

---

### Post by aysiu on 2006-03-24
[QUOTE=Jabbadahut]Many thanks again.  I do have libstdc++5 installed, & have the firefox package extracted.

What's next after getting to the Firefox folder at the desktop? :)[/QUOTE] Okay. So, if all is well, you should have two items on your desktop: one is the Firefox 1.5 .tar.gz file you downloaded from Mozilla; the other is the newly extracted folder from the .tar.gz

Go ahead and open that folder. Inside is a file called *firefox*. Do not click on *firefox-bin*. Click on **firefox**.

Double-click that file. If Firefox opens, we can move on to the next step. If not... well, we'll see what we can do.

I'm attaching a screenshot to show you which file to click on. I'm using KDE, but the same principle applies in Gnome, too.

---

### Post by Haegin on 2006-03-24
Hi,
I wrote the script from the original script.
You dont need to login as root but you do need to run it using sudo.
Once you have run the script (mine not the original), right click on the icon in the toolbar, click properties and set the command to be: 
```

/home/<your username>/.swiftfox/firefox %u

```
Then click it as normal and it should start.

---

### Post by Jabbadahut on 2006-03-24
Alright.  I have to take a deep breath here, because I am about to throw my machine out the 3rd floor window, lol. :mrgreen:

Aysiu, I clicked on Firefox (not firefox.bin, as you mentioned) in the Firefox folder and I get a dialog box asking if I wanted to execute in the Terminal or Display it or cancel the proceedure.  I chose to run in the Terminal, and there was some code that ran but then I got an error stating that Firefox was still running and it stopped.

So, I closed Firefox, and tried again.  Nothing happens.  I double-click on Firefox & it does start, but when I look at the version via "Help" then "About", it still says version 1.0.7.

I also tried Human Prototype's code as well again, this time modifying the Firefox icon as he said, replacing "yourusername" with the one  I use.  However, I still get the error "cannot start Firefox blah blah blah", but this time it mentions the command I typed in, according to Human Prototype.

"/home/<myusername>/.swiftfox/firefox %u" (where "myusername" is my login name.)

It's been mentioned that I don't have to be logged in as root.  Well, I tried executing the code without the "sudo -i" command in the terminal, but after I copied & pasted the code from "installfirefox.sh", the Terminal would disappear all of a sudden and nothing happens. :confused: 

Now, I have a real problem.  I tried running the restore script, but now it won't start still, even when I changed the command line in the icon back to what it was, although I think I might've typed it in wrong. "Firefox %u" is what I typed in, but that doesn't work.  I still get the "cannot start Firefox" error with that command, so I have no idea what the original command line stated.

Now I can't run Firefox PERIOD - I have to use Windows to browse the web & all.  I am very frustrated right now. :( Not at you guys - please understand that.  I do appreciate your time and effort, and this isn't your guys fault.

But now it seems my only solution is to completely axe Ubuntu PC64 version and start over again with a differnt type & use Automatix - seems others have done so without so much tedius work. :)  How do I do this on a dual-boot system using GRUB?  I have 2 hard disks - one has Linux on it, the other has windows, and is split up into 6 partitions - each approx. 20 GB.  I think I read somewhere that I need my Windows XP CD and choose restore to fix the mbr to remove GRUB?

Or is there some other "magical" way to get Firefox back, & install the upgrade?  I'm open to any suggestions.  We'll get this problem resolved yet. :)

---

### Post by aysiu on 2006-03-24
[QUOTE=Jabbadahut]
Aysiu, I clicked on Firefox (not firefox.bin, as you mentioned) in the Firefox folder and I get a dialog box asking if I wanted to execute in the Terminal or Display it or cancel the proceedure.  I chose to run in the Terminal, and there was some code that ran but then I got an error stating that Firefox was still running and it stopped.[/quote] To make sure Firefox is *not* running, you should enter the command ```
killall firefox
``` in the terminal before launching Firefox.

And when you double-click on the *firefox* file, you should just run it (not in terminal).

> 
But now it seems my only solution is to completely axe Ubuntu PC64 version  It's entirely possible it's a 64 version issue. I don't know, as I don't have a 64 computer (I'm just using the regular x86 version).

---

### Post by Haegin on 2006-03-25
Go into /home/<username>/ and delete anything mentioning swiftfox (.swiftfox and swiftfox probably so make sure you have show hidden items turned on (Ctrl + H in nautilus).
Now open a terminal and
```

gedit removeFirefox.sh

```
Then past this into the text doc that opens
```

#!/bin/bash
## How to Restore your OLD Firefox Internet Browser:
##
## Source: "https://wiki.ubuntu.com/FirefoxNewVersion"
## Run this file from the Terminal with the command "sh restorefirefox.sh"
cd /
cd $HOME/Desktop

## Restore the symbolic link:
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox

## Restore your old profile:
## (This is different to what the "Source" Site suggested – the "Source's"
## site version, created errors).
cd $HOME/.mozilla
mv firefox firefox1.5.0.1
mv firefox1.0.x.ubuntu firefox

## (optional) Delete the firefox directory
sudo rm -r /opt/firefox

## Congratulations, you have now Restored successfully your OLD Mozilla
## Firefox Internet Browser.
## Go & Check it out !

```
And now
```

chmod +x removeFirefox.sh

```
then finally
```

./removeFirefox.sh

```

This should get rid of firefox for you and leave you back with the old firefox 1.0.7. If it doesn't then fire up synaptic and reinstall firefox.
The command for the launcher should be "firefox %f" (no capital).

Finally if it still doesn't work type (in a terminal)
```

updatedb -u
[code]
That takes a while and builds a slocate db starting at /
Next search for firefox
[code]
locate firefox>firefoxSearch

```
This produces a lot of output so I dumped it into a file (using the >firefoxSearch bit). You wont see anything on the screen because of this so dont worry about the fact that nothing comes up.
If you open nautilus and go to your home folder there will now be a file called "firefoxSearch" with the output. Post it up here as an attachment and I will try and help you from there.

Hope this helps

---

### Post by Jabbadahut on 2006-03-25
Thanks for the suggestion Human, but it won't be neccesary.  I decided to un-install my version of Ubuntu (PC64) and use the x86 version & install it with Automatix. :)  Sometimes, it's best to KISS, no? ;)  Everything is working fine, now.

Now - I do have one more question.  How do I merge my "profiles" folder from the Windows version of Firefox with the Linux version?  You know, where my passwords, data on handling cookies from certain web sites (i.e. either block or allow), & the overall "look and feel" of Firefox are stored.  Manually inputing this information in is a lot of tedius work - to say the least. ;)

Whenever I did a re-install of either the Windows OS or Firefox, all I did was keep a backup of the Profiles folder and then moving it to the appropriate place, usually "c:\documents and settings\<username>\mozilla firefox".  That said, I am assuming that the file & directory structure on Linux is way different, and I need to know exactly where I should put this.

---

### Post by aysiu on 2006-03-25
Put the contents of your Windows Firefox profile in /home/jabbadahut/.mozilla

It's a hidden folder, so you need to either Control-H (Gnome) or Alt-V, H (KDE).

---

