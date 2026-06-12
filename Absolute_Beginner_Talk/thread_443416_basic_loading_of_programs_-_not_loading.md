---
title: "basic loading of programs - not loading"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by GoneWithTheWind on 2007-05-14
I loaded up Ubuntu a year ago, used it for awhile and then unfortunately have been using W since then - due to not finding a suitable chat program in Linux.  Hopefully now this has changed as I would much rather use Linux and it's a hassle trying to go back and forth.

Anyway my Firefox version is 1.5 on Ubuntu.  This morning I **uploaded the new version from Firefox**, saved and clicked all the buttons, closed the browser, clicked "applications/internet/firefox, clicked "about", and viola!** it's still version 1.5**.  This issue is not just Firefox, as originally I had the same problems getting programs to show up that I'd downloaded with Ubuntu, and noticed that many others were having the same issues as per their posts on the Forum.

Is there any solution to this so that programs open where and when they are supposed to, or is it automatic that I need to do a few other things and if so, what might they be.  Thanks.

---

### Post by taurus on 2007-05-14
How did you install the latest version of firefox?  What's the output of this command from a terminal?

```
whereis firefox
```

---

### Post by Cypher on 2007-05-14
You left Ubuntu because of a chat client?? :) GAIM was, as is today, available back then and was excellent. They've renamed it to Pidgin now, but it's good. Also check out aMSN.

Now, what steps did you use to upgrade Firefox from 1.5 to the  newer version? That might clue us in as to why things aren't showing up. What are your steps for upgrading any app?

P.S., I'm telling you..one day..I'm going to beat Taurus! :)

---

### Post by GoneWithTheWind on 2007-05-14
> **taurus said:**
> How did you install the latest version of firefox?  What's the output of this command from a terminal?

I followed all the instructions on the Firefox page for the download.

:~$ whereis firefox
firefox: /usr/bin/firefox /etc/firefox /usr/lib/firefox /usr/bin/X11/firefox /usr/include/firefox /usr/share/firefox /usr/share/man/man1/firefox.1.gz

> **Cypher said:**
> You left Ubuntu because of a chat client??

Primarily, yes.

---

### Post by taurus on 2007-05-14
Perhaps you downloaded the installer which means you have to install it first before you can use it.  If you want to use the latest version of firefox, maybe this guide helps.

[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Install_Official_Mozilla_Build_of_Firefox](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Install_Official_Mozilla_Build_of_Firefox)

---

### Post by Ink-Jet on 2007-05-14
I'd recommend using Add/Remove to remove all your Firefox programs, and then use it to install the new version, instead of downloading from the website - Add/Remove is always the best way to install programs, in Ubuntu, pretty much.

---

### Post by GoneWithTheWind on 2007-05-14
> **taurus said:**
> Perhaps you downloaded the installer which means you have to install it first before you can use it.  If you want to use the latest version of firefox, maybe this guide helps.

[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Install_Official_Mozilla_Build_of_Firefox](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Install_Official_Mozilla_Build_of_Firefox)

Thanks.  So far not found - will check another command.

:~$ bash ~/Desktop/installnewthunderbird.sh -install
bash: /home/john/Desktop/installnewthunderbird.sh: No such file or directory

Correction:

:~$ bash ~/Desktop/installnewfirefox.sh -install
bash: /home/john/Desktop/installnewfirefox.sh: No such file or directory

**Update:  I've transferred all my bookmarks to Delicious.**

---

### Post by taurus on 2007-05-14
Are we talking about a new version of firefox or thunderbird here?  Maybe I need to learn how to read again but I sure thought we are talking about firefox!

---

### Post by GoneWithTheWind on 2007-05-14
I missed that was thunderbird but it's doing the same for Firefox.

bash ~/Desktop/installnewfirefox.sh -install
bash: /home/john/Desktop/installnewfirefox.sh: No such file or directory

---

### Post by taurus on 2007-05-14
Did you download the **installnewfirefox.sh** from this site first?

[http://sourceforge.net/project/showfiles.php?group_id=147501&package_id=231543](http://sourceforge.net/project/showfiles.php?group_id=147501&package_id=231543)

---

### Post by GoneWithTheWind on 2007-05-14
> **taurus said:**
> Did you download the **installnewfirefox.sh** from this site first?

[http://sourceforge.net/project/showfiles.php?group_id=147501&package_id=231543](http://sourceforge.net/project/showfiles.php?group_id=147501&package_id=231543)

Thanks for your response.  No, I downloaded the update from Firefox - but have gotten it now.  

There's a huge installnewfirefox_3.1.1.sh script in the gedit window.  

Not sure what to do with that.

---

### Post by GoneWithTheWind on 2007-05-14
Guessing that I click "save" on this, to save it to desktop (?) so here goes.

Okay.... I clicked "save" and nothing happened.  The script is still open in gedit.

---

### Post by GoneWithTheWind on 2007-05-14
Do I copy this script and paste it into the terminal?

---

### Post by GoneWithTheWind on 2007-05-14
I clicked the script off.

Downloaded installnewfirefox_3.1.1.sh again from:
[http://sourceforge.net/project/showfiles.php?group_id=147501&package_id=231543](http://sourceforge.net/project/showfiles.php?group_id=147501&package_id=231543)

Clicked Save

Clicked Open (again)

The long script opened again in gedit - clicked it off.

There is a firefox/install icon on the desktop - I"ll see about that.

Update: getting this again
john@ubuntu:~$ bash ~/Desktop/installnewfirefox.sh -install
**bash: /home/john/Desktop/installnewfirefox.sh: No such file or directory**

It seems like I should be able to click the icon to have it install.  Am looking for more commands for terminal.

Update:  
john@ubuntu:~$ bash ~/Desktop/installnewfirefox.sh -install
**bash: /home/john/Desktop/installnewfirefox.sh: No such file or directory**

Nothing is working as instructed.

I clicked the "installnewfirefox" icon on the desktop.  It opened the long script in gedit again.

Oh isn't this fun - NOT - clicked the script off.

---

### Post by taurus on 2007-05-14
Save that script to your ~/Desktop (you already did since you see an icon on your desktop for it).  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
cd ~/Desktop
bash ./installnewfirefox_3.1.1.sh -install
```

---

### Post by GoneWithTheWind on 2007-05-14
> **taurus said:**
> Save that script to your ~/Desktop (you already did since you see an icon on your desktop for it).  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
cd ~/Desktop
bash ./installnewfirefox_3.1.1.sh -install
```

That worked, thank you!

Now at the bottom it says "Enter your choice of localization"

Whoops I accidently clicked return - had no clue what to type there anyway - testing it now.

Update:  clicked Firefox off to test for new version
> Applications > Internet > Firefox
> Help > About Firefox > **Firefox 1.5 - still not updated**

---

### Post by GoneWithTheWind on 2007-05-14
> Help > About Firefox > version 1.5.0.11

Any more ideas?

---

### Post by taurus on 2007-05-14
Where did you install the new version?

```
whereis firefox
```

or

```
sudo find / -name firefox -print
```

---

### Post by GoneWithTheWind on 2007-05-14
$ whereis firefox
firefox: /usr/bin/firefox /etc/firefox /usr/lib/firefox /usr/bin/X11/firefox /usr/include/firefox /usr/share/firefox /usr/share/man/man1/firefox.1.gz

$ sudo find / -name firefox -print
Password:
/etc/firefox
/usr/lib/mime/packages/firefox
/usr/lib/firefox
/usr/lib/firefox/firefox
/usr/share/bug/firefox
/usr/share/menu/firefox
/usr/share/firefox
/usr/share/doc/firefox
/usr/include/firefox
/usr/bin/firefox
/home/john/Desktop/firefox
/home/john/Desktop/firefox/firefox
/home/john/.mozilla/firefox
/root/.mozilla/firefox

---

### Post by taurus on 2007-05-14
If you have firefox running right now.  Shut it down.  And from a terminal, type

```
cd ~/Desktop/firefox
./firefox
```
Now, what version is that one?

---

### Post by GoneWithTheWind on 2007-05-14
1.5.0.11

---

### Post by taurus on 2007-05-14
What's the output of this command?

```
ls -la ~/Desktop/firefox
```

---

### Post by GoneWithTheWind on 2007-05-14
Got it!  I did the 
cd ~/Desktop/firefox
./firefox
again and it works.

Thanks very much for your helpfulness.  :)

---

### Post by GoneWithTheWind on 2007-05-14
Omg... now I did > applications > internet > firefox - and it's still 1.5.0.11.  :(

---

### Post by GoneWithTheWind on 2007-05-14
> **taurus said:**
> What's the output of this command?

```
ls -la ~/Desktop/firefox
```

$ ls -la ~/Desktop/firefox
total 13676
drwxr-xr-x 13 john john     4096 2007-05-14 14:46 .
drwxr-xr-x  4 john john     4096 2007-05-14 13:06 ..
-rw-r--r--  1 john john        0 2007-03-09 18:42 .autoreg
-rw-r--r--  1 john john      232 2007-03-09 18:42 browserconfig.properties
drwxr-xr-x  3 john john     4096 2007-03-09 18:43 chrome
drwxr-xr-x  2 john john     4096 2007-03-09 18:43 components
drwxr-xr-x  5 john john     4096 2007-03-09 18:43 defaults
drwxr-xr-x  2 john john     4096 2007-03-09 18:42 dictionaries
drwxr-xr-x  5 john john     4096 2007-05-14 14:45 extensions
-rwxr-xr-x  1 john john     5247 2007-03-09 18:43 firefox
-rwxr-xr-x  1 john john 10534772 2007-03-09 18:43 firefox-bin
drwxr-xr-x  2 john john     4096 2007-03-09 18:43 greprefs
drwxr-xr-x  2 john john     4096 2007-03-09 18:43 icons
-rw-r--r--  1 john john      476 2007-03-09 18:43 libfreebl3.chk
-rwxr-xr-x  1 john john   231468 2007-03-09 18:43 libfreebl3.so
-rwxr-xr-x  1 john john   627004 2007-03-09 18:43 libmozjs.so
-rwxr-xr-x  1 john john   176716 2007-03-09 18:43 libnspr4.so
-rwxr-xr-x  1 john john   430608 2007-03-09 18:43 libnss3.so
-rwxr-xr-x  1 john john   260832 2007-03-09 18:43 libnssckbi.so
-rwxr-xr-x  1 john john    15304 2007-03-09 18:43 libplc4.so
-rwxr-xr-x  1 john john     8240 2007-03-09 18:43 libplds4.so
-rwxr-xr-x  1 john john   138316 2007-03-09 18:43 libsmime3.so
-rw-r--r--  1 john john      476 2007-03-09 18:43 libsoftokn3.chk
-rwxr-xr-x  1 john john   309624 2007-03-09 18:43 libsoftokn3.so
-rwxr-xr-x  1 john john   155560 2007-03-09 18:43 libssl3.so
-rwxr-xr-x  1 john john    94924 2007-03-09 18:43 libxpcom_compat.so
-rwxr-xr-x  1 john john   698672 2007-03-09 18:43 libxpcom_core.so
-rwxr-xr-x  1 john john     9240 2007-03-09 18:43 libxpcom.so
-rwxr-xr-x  1 john john     8284 2007-03-09 18:43 libxpistub.so
-rwxr-xr-x  1 john john    10336 2007-03-09 18:43 mozilla-xremote-client
-rw-r--r--  1 john john      112 2007-03-09 18:42 old-homepage-default.properties
drwxr-xr-x  2 john john     4096 2007-03-09 18:43 plugins
-rw-r--r--  1 john john      177 2007-03-09 18:43 readme.txt
-rwxr-xr-x  1 john john     2257 2007-03-09 18:42 removed-files
drwxr-xr-x  6 john john     4096 2007-03-09 18:43 res
-rwxr-xr-x  1 john john    10492 2007-03-09 18:43 run-mozilla.sh
drwxr-xr-x  2 john john     4096 2007-03-09 18:42 searchplugins
-rwxr-xr-x  1 john john    67496 2007-03-09 18:43 updater
-rw-r--r--  1 john john      145 2007-03-09 18:42 updater.ini
drwxr-xr-x  3 john john     4096 2007-05-14 14:45 updates
-rwxr-xr-x  1 john john    21368 2007-03-09 18:43 xpicleanup

---

### Post by taurus on 2007-05-14
> **John Rupp said:**
> Omg... now I did > applications > internet > firefox - and it's still 1.5.0.11.  :(

You still have version 1.5.0.11 on your machine so if you use the one from Applications -> Internet -> Firefox, you will get that old version.  Your new version is in ~/Desktop/firefox/firefox so you have a few options.  

1.  You can create a launcher on the panel to run it.
2.  Run it from a terminal like you just did
or
3.  Edit the menu, replacing the path to the older version with the new version.

---

### Post by GoneWithTheWind on 2007-05-14
> **taurus said:**
> Edit the menu, replacing the path to the older version with the new version.

Thanks.

Anyway I don't know how to do that so will keep using the old one.

---

### Post by taurus on 2007-05-14
Put a cursor on an up panel and click the right button.  You will get a menu and one of them says something like "Create a launcher" or something similar to that.  Pick that.  Then, put in the whole path to your latest version of firefox.

```
/home/john/Desktop/firefox/firefox
```
And you can click the ICON to pick firefox icon from the list, /usr/share/pixmaps.

Click OK when done and all you have to do now is double-click that icon on the panel to run it.

---

### Post by GoneWithTheWind on 2007-05-16
Thanks.

What I'd like to do is have the latest version open at > applications > internet > firefox.

I'm ready to delete the 1.5 version, as have moved all bookmarks to del.icio.us .

If I just delete the 1.5 version, will the 2.0 version then come up at > applications > internet > firefox?

Also I'd like to remove the icon from my desktop.

---

### Post by GoneWithTheWind on 2007-05-17
1.  The launcher asks me for "name, generic name, comment, and command".  Do I just paste _/home/john/Desktop/firefox/firefox_ in command and ignore the rest of it?

2.  I'd like to run it from > applications > internet > firefox, and remove the icons, or is it better to use them on the desktop.

3.  I'm still not sure how to do this, and if I remove the icons from the desktop will the path still be the same.  Basically I"d just like to delete version 1.5 and replace it with 2.0, which is on my computer somewhere.

4.  Do most people delete Ubuntu 6.06 and reinstall the new version, and would this help things run more smoothly.

---

### Post by GoneWithTheWind on 2007-05-20
I downloaded Xampp today which went well but then came a problem at the terminal.

"After downloading simply type in the following commands:

   1. Go to a Linux shell and login as the system administrator root:

      su
"

I keep doing this and the terminal won't accept my password.  The terminal works fine otherwise and accepts my password for other things, example after I type "sudo" but not this.  How do I get the password to work?

Edit:  This was answered, by typing "sudo su".  Thanks.

---

### Post by GoneWithTheWind on 2007-05-23
I am still having major problems starting the new version of firefox.  I have downloaded the latest version and it is on the desktop.  When I click applications > internet > firefox, or when I click the icon on the desktop, or when I type "firefox" in the terminal - regardless of which of these - firefox 1.5 is the one that opens.

Also if I open thunderbird or firefox with the terminal then close the terminal, the programs close too.  :o

My questions are:

1)  How do I get the firefox 2.0 upgrade to open, then delete the older 1.5 version;

2)  How do I get programs to stay open, when the terminal is closed;

3)  How can I move the new versions of thunderbird and firefox to > applications > internet.

Thanks.

---

### Post by GoneWithTheWind on 2007-05-23
I followed the instructions on here and **now Firefox won't start from anywhere**.  

To get on here I had to sign on to Windows, where the Firefox upgrade took less than 5 minutes.

Is there a known solution to getting this upgrade to work?

---

### Post by GoneWithTheWind on 2007-05-23
I right clicked on the desktop to create a launcher for Firefox, which put an icon on the desktop.

Then clicking the icon opened Firefox.

It looks like desktop icons are the easiest and fastest way to open programs.

This link says to keep the old version, as it has many settings that are used by the new one.
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by Iokua on 2007-05-23
Maybe I don't understand what's going on here, so correct me if I'm wrong, but is there a specific reason why you're not installing Firefox from the repositories? If you want to backup your bookmarks, just make a backup copy of your ~/.mozilla/firefox folder and then install the new version using Synaptic and then import your bookmarks.

---

### Post by GoneWithTheWind on 2007-05-23
> **Iokua said:**
> Maybe I don't understand what's going on here, so correct me if I'm wrong, but is there a specific reason why you're not installing Firefox from the repositories?

Yeah, I downloaded Firefox from Mozilla a week ago and it's been sitting on my desktop this past week.

Now I have gotten it working. 

If you have a good reason to uninstall and go to repositories then feel free to post it.

I've transferred all my bookmarks to Delicious and don't want them on Firefox.

---

