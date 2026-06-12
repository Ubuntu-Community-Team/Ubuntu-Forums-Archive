---
title: "Mplayer plugin still not working after Firefox upgrade"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by keheikev on 2006-09-28
Hi all,
Ive uninstalled the mozilla-firefox plugin at least 5-6 times and still cannot get it to add to about:plugins. I am a dapper 6.06 user and installed the thing with synaptic as well as the uninstall. I am thinking synaptic is adding it to the wrong directory. Has anyone had the same problem. It used to work great for streaming and for watching inbeded video in web pages. Now it just says missing plugin.
It all started when I upgraded from 1.5.01 to 1.5.03 I believe. 
Kiheikev
Aloha!:confused:

---

### Post by Albi on 2006-09-28
Did you try it with automatix?

---

### Post by keheikev on 2006-09-28
No, I have kind of avoided automatix as I want something I can uninstall cleanly.
Thanks anyway
Kiheikev

---

### Post by Kilz on 2006-09-28
> **keheikev said:**
> Hi all,
Ive uninstalled the mozilla-firefox plugin at least 5-6 times and still cannot get it to add to about:plugins. I am a dapper 6.06 user and installed the thing with synaptic as well as the uninstall. I am thinking synaptic is adding it to the wrong directory. Has anyone had the same problem. It used to work great for streaming and for watching inbeded video in web pages. Now it just says missing plugin.
It all started when I upgraded from 1.5.01 to 1.5.03 I believe. 
Kiheikev
Aloha!:confused:

Open a terminal and type in 
```
ls -l /usr/lib/firefox/plugins
```
paste the output in a reply.

---

### Post by keheikev on 2006-09-28
Somehow I knew you would save my bacon Kilz...lol

kevin@kevinscomputer:~$ ls -l /usr/lib/firefox/plugins
total 12
-rw-r--r-- 1 root root 8652 2006-09-21 03:27 libunixprintplugin.so
lrwxrwxrwx 1 root root   43 2006-09-28 19:14 mplayerplug-in-gmp.so -> ../../mozilla/plugins/mplayerplug-in-gmp.so
lrwxrwxrwx 1 root root   44 2006-09-28 19:14 mplayerplug-in-gmp.xpt -> ../../mozilla/plugins/mplayerplug-in-gmp.xpt
lrwxrwxrwx 1 root root   42 2006-09-28 19:14 mplayerplug-in-qt.so -> ../../mozilla/plugins/mplayerplug-in-qt.so
lrwxrwxrwx 1 root root   43 2006-09-28 19:14 mplayerplug-in-qt.xpt -> ../../mozilla/plugins/mplayerplug-in-qt.xpt
lrwxrwxrwx 1 root root   42 2006-09-28 19:14 mplayerplug-in-rm.so -> ../../mozilla/plugins/mplayerplug-in-rm.so
lrwxrwxrwx 1 root root   43 2006-09-28 19:14 mplayerplug-in-rm.xpt -> ../../mozilla/plugins/mplayerplug-in-rm.xpt
lrwxrwxrwx 1 root root   39 2006-09-28 19:14 mplayerplug-in.so -> ../../mozilla/plugins/mplayerplug-in.so
lrwxrwxrwx 1 root root   43 2006-09-28 19:14 mplayerplug-in-wmp.so -> ../../mozilla/plugins/mplayerplug-in-wmp.so
lrwxrwxrwx 1 root root   44 2006-09-28 19:14 mplayerplug-in-wmp.xpt -> ../../mozilla/plugins/mplayerplug-in-wmp.xpt
lrwxrwxrwx 1 root root   40 2006-09-28 19:14 mplayerplug-in.xpt -> ../../mozilla/plugins/mplayerplug-in.xpt
what now :-|

---

### Post by Kilz on 2006-09-28
> **keheikev said:**
> Somehow I knew you would save my bacon Kilz...lol

kevin@kevinscomputer:~$ ls -l /usr/lib/firefox/plugins
total 12
-rw-r--r-- 1 root root 8652 2006-09-21 03:27 libunixprintplugin.so
lrwxrwxrwx 1 root root   43 2006-09-28 19:14 mplayerplug-in-gmp.so -> ../../mozilla/plugins/mplayerplug-in-gmp.so
lrwxrwxrwx 1 root root   44 2006-09-28 19:14 mplayerplug-in-gmp.xpt -> ../../mozilla/plugins/mplayerplug-in-gmp.xpt
lrwxrwxrwx 1 root root   42 2006-09-28 19:14 mplayerplug-in-qt.so -> ../../mozilla/plugins/mplayerplug-in-qt.so
lrwxrwxrwx 1 root root   43 2006-09-28 19:14 mplayerplug-in-qt.xpt -> ../../mozilla/plugins/mplayerplug-in-qt.xpt
lrwxrwxrwx 1 root root   42 2006-09-28 19:14 mplayerplug-in-rm.so -> ../../mozilla/plugins/mplayerplug-in-rm.so
lrwxrwxrwx 1 root root   43 2006-09-28 19:14 mplayerplug-in-rm.xpt -> ../../mozilla/plugins/mplayerplug-in-rm.xpt
lrwxrwxrwx 1 root root   39 2006-09-28 19:14 mplayerplug-in.so -> ../../mozilla/plugins/mplayerplug-in.so
lrwxrwxrwx 1 root root   43 2006-09-28 19:14 mplayerplug-in-wmp.so -> ../../mozilla/plugins/mplayerplug-in-wmp.so
lrwxrwxrwx 1 root root   44 2006-09-28 19:14 mplayerplug-in-wmp.xpt -> ../../mozilla/plugins/mplayerplug-in-wmp.xpt
lrwxrwxrwx 1 root root   40 2006-09-28 19:14 mplayerplug-in.xpt -> ../../mozilla/plugins/mplayerplug-in.xpt
what now :-|


Well I have messed around with these plugins to get them running on 64bit. Perhaps we can get them running for you. :D 
It looks like you have symlinks in place. This is a good thing.
Next we will make sure you have the codecs.
```
ls -l /usr/lib/win32
```
That command should return a list of codecs.
```
which mplayer
```
should return the path to mplayer.
Let me know what you get.

---

### Post by keheikev on 2006-09-28
kevin@kevinscomputer:~$ ls -l /usr/lib/win32
lrwxrwxrwx 1 root root 6 2006-09-23 14:56 /usr/lib/win32 -> codecs

kevin@kevinscomputer:~$ which mplayer
kevin@kevinscomputer:~$

I did reply to your posts on 64bit but this is good as I am a amd athlon 2100 user right now.
Kevin

---

### Post by Kilz on 2006-09-28
> **keheikev said:**
> kevin@kevinscomputer:~$ ls -l /usr/lib/win32
lrwxrwxrwx 1 root root 6 2006-09-23 14:56 /usr/lib/win32 -> codecs

kevin@kevinscomputer:~$ which mplayer
kevin@kevinscomputer:~$

I did reply to your posts on 64bit but this is good as I am a amd athlon 2100 user right now.
Kevin

If the -> codecs is a long list of codecs great, if not you need them. But it doesnt look like you have mplayer installed. I am pretty sure you need it. 
```
sudo apt-get install mplayer
``` should install it.

---

### Post by keheikev on 2006-09-29
assword:
Reading package lists... Done
Building dependency tree... Done
mplayer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

hmm I am sure mplayer is here. I can open the application from the gnome menu...
Er that was I used to have it but it doesnt seem to be on the applications list any longer.

---

### Post by Kilz on 2006-09-29
> **keheikev said:**
> assword:
Reading package lists... Done
Building dependency tree... Done
mplayer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

hmm I am sure mplayer is here. I can open the application from the gnome menu...
Er that was I used to have it but it doesnt seem to be on the applications list any longer.

hmmmm , what dose ```
about:plugins
``` say? Type it in the adress bar, the plugin list will show as a web page, You should see  something like the screenshot I posted in this message under QuickTime.

---

### Post by keheikev on 2006-09-29
Heres my about plugins Is it possible that the installs are screwed up? How about using the terminal to open mplayer? I am thinking the plugin keeps getting written to the wrong directory. ie plugin vs plug-ins ???
Kiheikev

---

### Post by Kilz on 2006-09-29
> **keheikev said:**
> Heres my about plugins

Its possible it isnt following the symlink for some strange reason

Just to make sure the orignals are there
```
ls -l /usr/lib/mozilla/plugins
```
If you see the list of plugins
```
sudo cp -f /usr/lib/mozilla/plugins/* /usr/lib/firefox/plugins
```
Then close all open browsers , open it again and try ```
about:plugins
``` again

---

### Post by keheikev on 2006-09-29
Hmm, 
Maybe I should just uninstall the whole firefox/mplayer/plugin and reinstall?
Here is what the last command yielded.
 sudo cp -f /usr/lib/mozilla/plugins/* /usr/lib/firefox/plugins
Password:
cp: `/usr/lib/mozilla/plugins/mplayerplug-in-gmp.so' and `/usr/lib/firefox/plugins/mplayerplug-in-gmp.so' are the same file
cp: `/usr/lib/mozilla/plugins/mplayerplug-in-gmp.xpt' and `/usr/lib/firefox/plugins/mplayerplug-in-gmp.xpt' are the same file
cp: `/usr/lib/mozilla/plugins/mplayerplug-in-qt.so' and `/usr/lib/firefox/plugins/mplayerplug-in-qt.so' are the same file
cp: `/usr/lib/mozilla/plugins/mplayerplug-in-qt.xpt' and `/usr/lib/firefox/plugins/mplayerplug-in-qt.xpt' are the same file
cp: `/usr/lib/mozilla/plugins/mplayerplug-in-rm.so' and `/usr/lib/firefox/plugins/mplayerplug-in-rm.so' are the same file
cp: `/usr/lib/mozilla/plugins/mplayerplug-in-rm.xpt' and `/usr/lib/firefox/plugins/mplayerplug-in-rm.xpt' are the same file
cp: `/usr/lib/mozilla/plugins/mplayerplug-in.so' and `/usr/lib/firefox/plugins/mplayerplug-in.so' are the same file
cp: `/usr/lib/mozilla/plugins/mplayerplug-in-wmp.so' and `/usr/lib/firefox/plugins/mplayerplug-in-wmp.so' are the same file
cp: `/usr/lib/mozilla/plugins/mplayerplug-in-wmp.xpt' and `/usr/lib/firefox/plugins/mplayerplug-in-wmp.xpt' are the same file
cp: `/usr/lib/mozilla/plugins/mplayerplug-in.xpt' and `/usr/lib/firefox/plugins/mplayerplug-in.xpt' are the same file
:-k  I wont give up. But this is something I expect of an operating system is video and sound.
kiheikev

---

### Post by Kilz on 2006-09-29
> **keheikev said:**
> Hmm, 
Maybe I should just uninstall the whole firefox/mplayer/plugin and reinstall?
Here is what the last command yielded.
 sudo cp -f /usr/lib/mozilla/plugins/* /usr/lib/firefox/plugins
Password:
cp: `/usr/lib/mozilla/plugins/mplayerplug-in-gmp.so' and `/usr/lib/firefox/plugins/mplayerplug-in-gmp.so' are the same file
cp: `/usr/lib/mozilla/plugins/mplayerplug-in-gmp.xpt' and `/usr/lib/firefox/plugins/mplayerplug-in-gmp.xpt' are the same file
cp: `/usr/lib/mozilla/plugins/mplayerplug-in-qt.so' and `/usr/lib/firefox/plugins/mplayerplug-in-qt.so' are the same file
cp: `/usr/lib/mozilla/plugins/mplayerplug-in-qt.xpt' and `/usr/lib/firefox/plugins/mplayerplug-in-qt.xpt' are the same file
cp: `/usr/lib/mozilla/plugins/mplayerplug-in-rm.so' and `/usr/lib/firefox/plugins/mplayerplug-in-rm.so' are the same file
cp: `/usr/lib/mozilla/plugins/mplayerplug-in-rm.xpt' and `/usr/lib/firefox/plugins/mplayerplug-in-rm.xpt' are the same file
cp: `/usr/lib/mozilla/plugins/mplayerplug-in.so' and `/usr/lib/firefox/plugins/mplayerplug-in.so' are the same file
cp: `/usr/lib/mozilla/plugins/mplayerplug-in-wmp.so' and `/usr/lib/firefox/plugins/mplayerplug-in-wmp.so' are the same file
cp: `/usr/lib/mozilla/plugins/mplayerplug-in-wmp.xpt' and `/usr/lib/firefox/plugins/mplayerplug-in-wmp.xpt' are the same file
cp: `/usr/lib/mozilla/plugins/mplayerplug-in.xpt' and `/usr/lib/firefox/plugins/mplayerplug-in.xpt' are the same file
:-k  I wont give up. But this is something I expect of an operating system is video and sound.
kiheikev

If at first we dont suceed, try try again. But its time for bed here so this is a last try tonight.

```
sudo rm -f /usr/lib/firefox/plugins/mplayerplug*
```
then
```
sudo cp -f /usr/lib/mozilla/plugins/* /usr/lib/firefox/plugins
```
Then close the browsers and restart them then try ```
about:plugins
```
If it doesn't work just leave a message and Ill check it tomorrow and we will figure it out.

---

### Post by keheikev on 2006-09-29
> **Kilz said:**
> If at first we dont suceed, try try again. But its time for bed here so this is a last try tonight.> 

 
It didnt work I'll be back in the words of the governator...Thanks I am looking forward to getting this fixed.
Kevin

---

### Post by Kilz on 2006-09-29
> **keheikev said:**
> It didnt work I'll be back in the words of the governator...Thanks I am looking forward to getting this fixed.
Kevin

Ok so when you say it didnt work, were you able to do the last commands? Whan does the command of 
```
ls -l /usr/lib/firefox/plugins
``` give

---

### Post by keheikev on 2006-09-29
I will try those tonite but one thing occurs to me if I type mplayer in terminal mplayer should launch. Is it possible when I uninstalled it I havent yet got the program back from synaptic?
Kevin

---

### Post by Dillinger on 2006-09-29
I've been having the exact same problem since I upgraded and I've tried the same steps and it too isn't working for me.  Just thought I'd share, I look forward to an answer I haven't had to troubleshoot on ubuntu for a very long time.

---

### Post by keheikev on 2006-09-29
kevin@kevinscomputer:~$ ls -l /usr/lib/firefox/plugins
total 1292
-rw-r--r-- 1 root root   8652 2006-09-21 03:27 libunixprintplugin.so
-rw-r--r-- 1 root root 251804 2006-09-28 22:03 mplayerplug-in-gmp.so
-rw-r--r-- 1 root root    981 2006-09-28 22:03 mplayerplug-in-gmp.xpt
-rw-r--r-- 1 root root 251804 2006-09-28 22:03 mplayerplug-in-qt.so
-rw-r--r-- 1 root root    981 2006-09-28 22:03 mplayerplug-in-qt.xpt
-rw-r--r-- 1 root root 251836 2006-09-28 22:03 mplayerplug-in-rm.so
-rw-r--r-- 1 root root    981 2006-09-28 22:03 mplayerplug-in-rm.xpt
-rw-r--r-- 1 root root 253148 2006-09-28 22:03 mplayerplug-in.so
-rw-r--r-- 1 root root 252124 2006-09-28 22:03 mplayerplug-in-wmp.so
-rw-r--r-- 1 root root    981 2006-09-28 22:03 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 root root    981 2006-09-28 22:03 mplayerplug-in.xpt

here is my output of the terminal of ls -l /usr/lib/firefox/plugins above Ive got a few more commands I can use that another friend suggested to me. Lets lick this bug!:p

---

### Post by keheikev on 2006-09-29
kevin@kevinscomputer:~$ sudo apt-cache policy mplayer
mplayer:
  Installed: 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8
  Candidate: 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8
  Version table:
 *** 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
        100 /var/lib/dpkg/status
Here is one maybe this will help where are you in this Dillinger?

---

### Post by Dillinger on 2006-09-29
tyler@Spike:~$ sudo apt-cache policy mplayer
Password:
mplayer:
  Installed: 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8
  Candidate: 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8
  Version table:
 *** 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
        100 /var/lib/dpkg/status


I followed all the same steps in this thread and have had the exact same results as you

---

### Post by keheikev on 2006-09-29
sudo apt-cache show mozilla-mplayer
Package: mozilla-mplayer
Priority: optional
Section: multiverse/misc
Installed-Size: 1556
Maintainer: Ari Pollak <ari@debian.org>
Architecture: i386
Source: mplayerplug-in
Version: 3.25-7ubuntu1~dapper1

Replaces: mplayerplug-in

Provides: mplayerplug-in
Depends: libatk1.0-0 (>= 1.9.0), libc6 (>= 2.3.4-1), libcairo2 (>= 1.0.2-2), libfontconfig1 (>= 2.3.0), libgcc1 (>= 1:4.0.2), libglib2.0-0 (>= 2.9.1), libgtk2.0-0 (>= 2.8.0), libice6, libpango1.0-0 (>= 1.11.1), libsm6, libstdc++6 (>= 4.0.2-4), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3, libxi6, libxinerama1, libxpm4, libxrandr2, libxt6, firefox | mozilla-firefox | mozilla-browser, mplayer (>= 1.0-pre5) | mplayer-custom (>= 1.0-pre5) | mplayer-386 (>= 1.0-pre5) | mplayer-586 (>= 1.0-pre5) | mplayer-686 (>= 1.0-pre5) | mplayer-k6 (>= 1.0-pre5) | mplayer-k7 (>= 1.0-pre5) | mplayer-powerpc (>= 1.0-pre5) | mplayer-g4 (>= 1.0-pre5) | mplayer-amd64 (>= 1.0-pre5) | mplayer-nogui (>= 1.0-pre5)
Suggests: konqueror, openoffice.org
[COLOR="DarkRed"]Conflicts: mplayerplug-in[/COLOR]
Filename: pool/multiverse/m/mplayerplug-in/mozilla-mplayer_3.17-1ubuntu1_i386.deb
Size: 431334
MD5sum: 29571e50f3631bcb6c1f1e447a93ebf4
Description: MPlayer-Plugin for Mozilla
 mplayerplug-in is a Mozilla browser plugin to allow playing embedded
 movies on web pages using mplayer.
More stuff

---

### Post by keheikev on 2006-09-29
> First delete the plugins folder from /home/YOUR-PROFILE/.mozilla/
WARNING: if you have installed any plugins through firefox your will need to reinstall them from synaptic.
then make a link to the plugins folder at /usr/lib/mozilla/
finally move the link to /home/YOUR-PROFILE/.mozilla/
and name it plugins.
end quote
I do not no how to make such a link or do the above rather. Anyway synaptic is contradicting whats installed...
I did uninstall and reinstall mozilla-mplayer and w32codecs but no Joy
I am thinking about doing the above but I am waiting on a word from Kilz
[http://www.ubuntuforums.org/showthread.php?t=135364](http://www.ubuntuforums.org/showthread.php?t=135364)

---

### Post by keheikev on 2006-09-30
Thing is if I ```
sudo mplayer
``` nothing at all happens and there is no mplayer menu choice on gnome menu either.
Kevin:mad:

---

### Post by Kilz on 2006-09-30
> **keheikev said:**
> Thing is if I ```
sudo mplayer
``` nothing at all happens and there is no mplayer menu choice on gnome menu either.
Kevin:mad:

I dont think you have it installed. [Go here and download the package]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmultiverse%2Fm%2Fmplayer%2Fmplayer_0.99%2B1.0pre7try2%2Bcvs20060117-0ubuntu8_i386.deb&md5sum=e555e36885e8d99dfc4b8dd48df3c216&arch=i386&type=main") from a local mirror and double click on it for Gdebi to install it.

---

### Post by keheikev on 2006-09-30
Well now I definitely have mplayer. But still no plugin working. It added the link you gave the menu choice and the command at the gterm window. I think I will repeat those commands you gave with the plugin before.
kevin

---

### Post by keheikev on 2006-09-30
I tried the code you suggested yesterday again
ls -l /usr/lib/mozilla/plugins
kevin@kevinscomputer:~$ which mplayer
/usr/bin/mplayer  **this is better**
and this

> sudo rm -f /usr/lib/firefox/plugins/mplayerplug*
and
sudo cp -f /usr/lib/mozilla/plugins/* /usr/lib/firefox/plugins
Still no change to about: plugins hmmmm maybe I should uninstall the plugin and w32codecs I am thinking I have to be careful and not uninstall the mplayer application just the codecs and firefox plugin? I am thinking Ive been uninstalling everything each time from synaptic...
BTW what is cvs and cvn are they repositories?
Kevin

---

### Post by Kilz on 2006-09-30
> **keheikev said:**
> I tried the code you suggested yesterday again
ls -l /usr/lib/mozilla/plugins
kevin@kevinscomputer:~$ which mplayer
/usr/bin/mplayer  **this is better**
and this


Still no change to about: plugins hmmmm maybe I should uninstall the plugin and w32codecs I am thinking I have to be careful and not uninstall the mplayer application just the codecs and firefox plugin? I am thinking Ive been uninstalling everything each time from synaptic...
BTW what is cvs and cvn are they repositories?
Kevin


I think the whole problem is that firefox isnt seeing those plugins. Even after they have been copied into firefox's own plugin folder. Here is [a link to the plugin package]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmultiverse%2Fm%2Fmplayerplug-in%2Fmozilla-mplayer_3.17-1ubuntu1_i386.deb&md5sum=29571e50f3631bcb6c1f1e447a93ebf4&arch=i386&type=main") to reinstall it.

---

### Post by keheikev on 2006-09-30
Well that link was for an older plugin as gdebi gave a conflict with mozilla=mplayer so where are we now? Maybe firefox is somewhat broke and I need to uninstall everything? I did get an update notice for mplayer Version 3.25-7ubuntu1~dapper1: from software updates.
Kevin

---

### Post by keheikev on 2006-09-30
Its really kooky too. Mplayer wont play a dvd on my system. I just put a disk in but it would not open the dvd although it is mounted. crap it! Maybe the whole operating system needs reinstall from a fresh dapper download? I really havent done much to this except I did upgrade rather than a clean install...
Kevin

---

### Post by Kilz on 2006-09-30
> **keheikev said:**
> Well that link was for an older plugin as gdebi gave a conflict with mozilla=mplayer so where are we now? Maybe firefox is somewhat broke and I need to uninstall everything? I did get an update notice for mplayer Version 3.25-7ubuntu1~dapper1: from software updates.
Kevin

Maybe thats the problem. Try the older version.

> **keheikev said:**
> Its really kooky too. Mplayer wont play a dvd on my system. I just put a disk in but it would not open the dvd although it is mounted. crap it! Maybe the whole operating system needs reinstall from a fresh dapper download? I really havent done much to this except I did upgrade rather than a clean install...
Kevin You may not have dvdcss installed. Reinstalling Ubuntu wont solve that.

---

### Post by keheikev on 2006-09-30
Well I got the conflict after I clicked on the older version and after I had used synaptic to remove mozilla-mplayer. I dont know how to remove it without synaptic.

---

### Post by keheikev on 2006-09-30
Well dvd playback is backburner but I attached a copy of my synaptic dvdcss installs. Mplayer doesnt find anything except it does have a complete menu set. That being said what about uninstalling everything including firefox completely and installing one thing at a time?:KS  
Thanks for sticking with me on this what seems so close but so far a problem to solve.
Kevin

---

### Post by keheikev on 2006-09-30
> **keheikev said:**
> Well I got the conflict after I clicked on the older version and after I had used synaptic to remove mozilla-mplayer. I dont know how to remove it without synaptic.
Hmm it is alwo strange that I removed completely with synaptic the current version of the plugin and then clicked on the gdebi file it warned me that there was a more current version which I ignored and installed it finally said there is a conflict with the installed mplayer plugin version  even though I had thought I had  installed it...
Kevin
So the older version would not install. ](*,)

---

### Post by Kilz on 2006-09-30
> **keheikev said:**
> Hmm it is alwo strange that I removed completely with synaptic the current version of the plugin and then clicked on the gdebi file it warned me that there was a more current version which I ignored and installed it finally said there is a conflict with the installed mplayer plugin version  even though I had thought I had  installed it...
Kevin
So the older version would not install. ](*,)

Try ```
sudo dpkg -i --force-overwrite /path/to/the/debfile
```
Editing the /path/to/the/debfile to where you have it, including it.

---

### Post by keheikev on 2006-09-30
Version 3.25-7ubuntu1~dapper1: its prompting me to install this now that we have mplayer plugin working!!!!!! Wow I wonder why it would not let us install it and have to force it. I guess thats a good thing. I would think I should make it so that the plugin does not upgrade till I upgrade the firefox browser. How to I tell synaptic not to offer an upgrade to this version of the plugin?
Kevin:D

---

### Post by Kilz on 2006-10-01
> **keheikev said:**
> Version 3.25-7ubuntu1~dapper1: its prompting me to install this now that we have mplayer plugin working!!!!!! Wow I wonder why it would not let us install it and have to force it. I guess thats a good thing. I would think I should make it so that the plugin does not upgrade till I upgrade the firefox browser. How to I tell synaptic not to offer an upgrade to this version of the plugin?
Kevin:D

It had to be forced because we were replacing it with an older version. To stop it from upgrading do a search for mozilla-mplayer in synaptic, highlight it. Click on Package at the top. Then Lock version.

---

### Post by TooDamFast on 2006-10-20
thanks for the help guys!  I had the same issue.  the last 3 post fixed it!

---

