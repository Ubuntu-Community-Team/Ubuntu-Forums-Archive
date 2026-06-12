---
title: "Firef***ed"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by therunnyman on 2006-04-14
Hi all,

I thought I'd give the newest iteration of Firefox a whirl, and I regret it.  The scene: I did that, worked well, but wouldn't "remember" me, that is, my bookmarks, mods and whatnot would vanish after I restarted it.  My "profile" I guess would be the word.  I removed 1.5, got the elder version up and running, and now 1.0.7 is forgetting me.

It's not that big a deal, but it does kinda bite to have to reload my backed-up bookmarks and themes every time I start Firefox.

Any ideas?

therunnyman

---

### Post by vruum on 2006-04-14
It could be a permissions problem on the ~/.mozilla folder, try closing down firefox, and move the folder like this. "sudo mv ~/.mozilla ~/mozilla-bak" restart firefox, and see if it works. If that doesnt work, a few words on how you installed the new version, and how you restored the old one, might make it easier to figure out what's wrong.

---

### Post by therunnyman on 2006-04-14
Thanks Vruum!  Handy tip, and that was probably it.  I followed the Wiki's instructions to install Firefox 1.5.0.1; here, I had 1.5.0.2, but no matter, I thought.

To correct the problem, I nabbed Automatix, and installed 1.5.0.1 from there.  All is well now.

For reference, I saw mention of bugginess about 1.5.0.2 more than once.  Could be the iteration...but it's more likely this dangling symlink of a user.

therunnyman

---

### Post by Kimm on 2006-04-14
There is almost no change between 1.5.0.1 and 1.5.0.2, and all the changes that do exist target OS X only.

---

### Post by OffHand on 2006-04-14
[QUOTE=Kimm]There is almost no change between 1.5.0.1 and 1.5.0.2, and all the changes that do exist target OS X only.[/QUOTE]
I wouldn't call 5 critical bug fixes 'almost no change'. How did you upgrade your Firefox to 1.5.0.2?

---

### Post by steve.horsley on 2006-04-14
[QUOTE=subsonic_shadow]I wouldn't call 5 critical bug fixes 'almost no change'. How did you upgrade your Firefox to 1.5.0.2?[/QUOTE]
I just did that.

My firefox is a shared install, so I need root permissions to upgrade it. I did it this way:

1: Alt-Ctrl-F1 to a text console and log in as root.
2: use **/etc/init.d/gdm stop** to kill X
3: use **startx** to start a root desktop
4: start firefox and use the menu **Help->Check for updates** to do the update
5: Gnome->logout to kill X and drop back to the console
6: **/etc/init.d/gdm start** to restart GDM and X

Log back in and check firefox still works for mortals.

---

### Post by OffHand on 2006-04-14
[QUOTE=steve.horsley]I just did that.

My firefox is a shared install, so I need root permissions to upgrade it. I did it this way:

1: Alt-Ctrl-F1 to a text console and log in as root.
2: use **/etc/init.d/gdm stop** to kill X
3: use **startx** to start a root desktop
4: start firefox and use the menu **Help->Check for updates** to do the update
5: Gnome->logout to kill X and drop back to the console
6: **/etc/init.d/gdm start** to restart GDM and X

Log back in and check firefox still works for mortals.[/QUOTE]
Easier would be 
```
gksudo firefox
``` 
and then use update from the Firefox menu.

---

### Post by towsonu2003 on 2006-04-14
If you're updating with gksudo firefox, be sure to fix ownerships later on: 
close firefox,
open terminal,
```

sudo chown -R username:username ~/.mozilla/firefox
```

username is your username. wiki.ubuntu.com/FirefoxNewVersion has instructions on how to update using a better way.

---

### Post by OffHand on 2006-04-14
[QUOTE=towsonu2003]If you're updating with gksudo firefox, be sure to fix ownerships later on: 
close firefox,
open terminal,
```

sudo chown -R username:username ~/.mozilla/firefox
```

username is your username. wiki.ubuntu.com/FirefoxNewVersion has instructions on how to update using a better way.[/QUOTE]

> Once the update is completed, close Firefox and than restore ownership to root: sudo chown -R root:root /opt/firefox Again, do NOT browse other sites while firefox has these elevated permissions, that is without changing back the ownership of /opt/firefox over to root. Such a practice is not safe. That's from the wiki. I opened the terminal and typed ```
sudo chown -R root:root /opt/firefox

``` How do I check if the permissions are ok now?

---

### Post by towsonu2003 on 2006-04-14
[QUOTE=subsonic_shadow]That's from the wiki. I opened the terminal and typed ```
sudo chown -R root:root /opt/firefox

``` How do I check if the permissions are ok now?[/QUOTE]
ls -l /opt

firefox here (output) should be owned by root

ls -l /opt/firefox

everything here should be owned by root.

---

### Post by OffHand on 2006-04-14
Looks good. Thanks for your time.


ls -l /opt/firefox
total 12832
-rw-r--r--  1 root root      57 2006-04-14 13:00 active-update.xml
-rw-r--r--  1 root root     230 2006-01-25 01:32 browserconfig.properties
drwxr-xr-x  3 root root    4096 2006-04-14 13:00 chrome
drwxr-xr-x  2 root root    4096 2006-04-14 13:00 components
drwxr-xr-x  5 root root    4096 2006-01-25 01:32 defaults
drwxr-xr-x  5 root root    4096 2006-01-25 01:32 extensions
-rwxr-xr-x  1 root root    5247 2006-04-14 13:00 firefox
-rwxr-xr-x  1 root root 9934280 2006-04-14 13:00 firefox-bin
drwxr-xr-x  2 root root    4096 2006-04-14 13:00 greprefs
drwxr-xr-x  2 root root    4096 2006-01-25 01:32 icons
-rwxr-xr-x  1 root root  567584 2006-04-14 13:00 libmozjs.so
-rwxr-xr-x  1 root root  176328 2006-04-14 13:00 libnspr4.so
-rwxr-xr-x  1 root root  426044 2006-04-14 13:00 libnss3.so
-rwxr-xr-x  1 root root  241260 2006-04-14 13:00 libnssckbi.so
-rwxr-xr-x  1 root root   15232 2006-04-14 13:00 libplc4.so
-rwxr-xr-x  1 root root    8612 2006-04-14 13:00 libplds4.so
-rwxr-xr-x  1 root root  138200 2006-04-14 13:00 libsmime3.so
-rw-r--r--  1 root root     476 2006-04-14 13:00 libsoftokn3.chk
-rwxr-xr-x  1 root root  421088 2006-04-14 13:00 libsoftokn3.so
-rwxr-xr-x  1 root root  126908 2006-04-14 13:00 libssl3.so
-rwxr-xr-x  1 root root   94844 2006-01-25 01:32 libxpcom_compat.so
-rwxr-xr-x  1 root root  687068 2006-04-14 13:00 libxpcom_core.so
-rwxr-xr-x  1 root root   10144 2006-01-25 01:32 libxpcom.so
-rwxr-xr-x  1 root root    8648 2006-01-25 01:32 libxpistub.so
-rwxr-xr-x  1 root root   10256 2006-01-25 01:32 mozilla-xremote-client
drwxr-xr-x  2 root root    4096 2006-03-19 02:27 plugins
-rw-r--r--  1 root root     177 2006-01-25 01:32 readme.txt
-rw-r--r--  1 root root    1646 2006-04-14 13:00 removed-files
drwxr-xr-x  6 root root    4096 2006-01-25 01:32 res
-rwxr-xr-x  1 root root   10492 2006-01-25 01:32 run-mozilla.sh
drwxr-xr-x  2 root root    4096 2006-01-25 01:32 searchplugins
-rwxr-xr-x  1 root root   67444 2006-01-25 01:32 updater
-rw-r--r--  1 root root     145 2006-01-25 01:32 updater.ini
drwxr-xr-x  3 root root    4096 2006-04-14 13:00 updates
-rw-r--r--  1 root root     964 2006-04-14 13:00 updates.xml
-rwxr-xr-x  1 root root   21320 2006-04-14 13:00 xpicleanup

---

### Post by towsonu2003 on 2006-04-14
looks fine, have fun :)

---

### Post by Mustard on 2006-04-14
I updated today using this method described earlier (from the wiki guide)

```
sudo chown -R ${USER}:${USER} /opt/firefox
```

Start up firefox and run the update.  Restart firefox after the update. Look at the update confirmation page.  Blink twice.  Shutdown firefox

```
sudo chown -R root:root /opt/firefox
```

All is good.

---

