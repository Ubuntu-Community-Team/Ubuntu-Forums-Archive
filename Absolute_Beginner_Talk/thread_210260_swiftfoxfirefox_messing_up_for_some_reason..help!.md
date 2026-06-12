---
title: "swiftfox/firefox messing up for some reason..help!"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by maddbaron on 2006-07-06
i dont know what happened. i closed swiftfox but when i tried to restart it it said it was still running. i am using the kde desktop and have no idea how to kill the process. so I restarted my entire system and when i tried to open swiftfox/firefox again i get a flashing swiftfox start screen of my homepage with the words really huge and saying it crashed but nothing was saved and to restart. i have restarted about 3 times and i keep getting same thing. when  i log in can i get a brand new session b/c when i restart the gaim i had running along with other stuff i had running start up again.

How can I fix this? do i need to reinstall and if i do can someone tell me the code to uninstall i'll use automatix to reinstall.

---

### Post by Rackerz on 2006-07-06
Did you use Automatix to install Swiftfox in the first place?

---

### Post by maddbaron on 2006-07-06
[QUOTE=Rackerz]Did you use Automatix to install Swiftfox in the first place?[/QUOTE]

yes i did. its been running pretty fine since i installed it. i recently added superkaramamba and klamav could they have caused the problem?

---

### Post by maddbaron on 2006-07-06
[QUOTE=maddbaron]yes i did. its been running pretty fine since i installed it. i recently added superkaramamba and klamav could they have caused the problem?[/QUOTE]

here are two attachments showing what i am getting...minus the flashing screen, screen capture isnt fast enough for capture that sadly.

---

### Post by Rackerz on 2006-07-06
I'm not sure if they could have caused it. Here is the post you need to go to.

[http://ubuntuforums.org/showthread.php?t=90797](http://ubuntuforums.org/showthread.php?t=90797) - If you go there and ask how to remove Swiftfox they should be able to tell you :).

---

### Post by maddbaron on 2006-07-06
i restarted in gnome where superkaramaba and klam/clamav both dont work for some reason and i got the same issue....this is frustrating....i am using opera now but i like swiftfox alot... :( if i could add extensions to konqueror i would since i like that one also and its fast...very confusing...maybe i can kill all the mozilla processes that would do the trick? how do i kill processes?

---

### Post by maddbaron on 2006-07-06
ok i just reinstalled firefox/swiftfox and got the same problem does anyone kno what can b done?

attachment included

---

### Post by mstlyevil on 2006-07-06
[QUOTE=maddbaron]ok i just reinstalled firefox/swiftfox and got the same problem does anyone kno what can b done?[/QUOTE]

To remove firefox use this command:

```
sudo apt-get remove firefox
```

To remove swiftfox use these commands one at a time:

```
cd /opt
sudo rm -rf swiftfox
cd
```

Make sure all your sources are enabled by going into adept and enabling the repositories or by doing this:

```
sudo kate /etc/apt/sources.list
```

If any sources look like this

```
# Dapper Final Release Repository
# deb http://archive.ubuntu.com/ubuntu dapper main
# deb-src http://archive.ubuntu.com/ubuntu dapper main

```

Make them look like this

```
# Dapper Final Release Repository
deb http://archive.ubuntu.com/ubuntu dapper main
deb-src http://archive.ubuntu.com/ubuntu dapper main

```

Then you will save the file and want to use this command:

```
sudo apt-get update
```


Try reinstalling Firefox first and see if it works properly. If not then the problem is with firefox. Install it manually this time by using this command:

```
sudo apt-get install firefox
```

If that fixes the issue then go ahead and install Swiftfox with Automatix. If not let us know and we will point you to the right place to get help.

---

### Post by maddbaron on 2006-07-06
[QUOTE=mstlyevil]To remove firefox use this command:

```
sudo apt-get remove firefox
```

To remove swiftfox use these commands one at a time:

```
cd /opt
sudo rm -rf swiftfox
cd
```

Make sure all your sources are enabled by going into adept and enabling the repositories or by doing this:

```
sudo kate /etc/apt/sources.list
```

If any sources look like this

```
# Dapper Final Release Repository
# deb http://archive.ubuntu.com/ubuntu dapper main
# deb-src http://archive.ubuntu.com/ubuntu dapper main

```

Make them look like this

```
# Dapper Final Release Repository
deb http://archive.ubuntu.com/ubuntu dapper main
deb-src http://archive.ubuntu.com/ubuntu dapper main

```

Then you will save the file and want to use this command:

```
sudo apt-get update
```


Try reinstalling Firefox first and see if it works properly. If not then the problem is with firefox. Install it manually this time by using this command:

```
sudo apt-get install firefox
```

If that fixes the issue then go ahead and install Swiftfox with Automatix. If not let us know and we will point you to the right place to get help.[/QUOTE]

same problem ](*,) 

> 
maddbaron@ubuntu:~$ sudo apt-get remove firefox
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  firefox firefox-gnome-support firefox-themes-ubuntu gnome-app-install
  gnome-core gnome-office ubuntu-desktop yelp
0 upgraded, 0 newly installed, 8 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 28.9MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 154003 files and directories currently installed.)
Removing gnome-office ...
Removing gnome-core ...
Removing ubuntu-desktop ...
Removing yelp ...
Removing gnome-app-install ...
I/O warning : failed to load external entity "/var/lib/scrollkeeper/(null)/scrollkeeper_cl.xml"
Removing firefox-gnome-support ...
Removing firefox-themes-ubuntu ...
Removing firefox ...
maddbaron@ubuntu:~$ cd /opt
maddbaron@ubuntu:/opt$ sudo rm -rf swiftfox
maddbaron@ubuntu:/opt$ cd
maddbaron@ubuntu:~$ sudo kate /etc/apt/sources.list
X Error: BadDevice, invalid or uninitialized input device 155
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 155
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Link points to "/tmp/ksocket-root"
Link points to "/tmp/kde-root"
X Error: BadDevice, invalid or uninitialized input device 155
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 155
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
KWrited - Listening on Device /dev/pts/4
kded: Launching previous backup analyse.
ScimInputContextPlugin()
kate: WARNING: Can't open /root/share/apps/konqueror/bookmarks.xml
QObject::disconnect: Unexpected null parameter
~ScimInputContextPlugin()
maddbaron@ubuntu:~$ sudo apt-get update
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release [30.9kB]
Err [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release

Get:7 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release [2743B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release [30.9kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release [19.6kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages [27.4kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Sources [7105B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages [4253B]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Sources [974B]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages [6042B]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Sources [902B]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages [1677B]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Sources [533B]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages [38.4kB]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources [23.6kB]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages [8592B]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources [2010B]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages [866B]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources [427B]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages [14B]
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources [14B]
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources [14B]
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages [14B]
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources [14B]
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages [14B]
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources [14B]
Fetched 208kB in 5s (37.6kB/s)
Reading package lists... Done
W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release: The following signatures were invalid: BADSIG 18B52FE3521A9C7C Justin Hayes (Automatix Repository Master) <wildtangent@w1ldt4ng3nt.net>
W: You may want to run apt-get update to correct these problems
maddbaron@ubuntu:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  firefox-gnome-support libthai0
The following NEW packages will be installed:
  firefox
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7911kB of archives.
After unpacking 23.4MB of additional disk space will be used.
Selecting previously deselected package firefox.
(Reading database ... 153402 files and directories currently installed.)
Unpacking firefox (from .../firefox_1.5.dfsg+1.5.0.4-0ubuntu6.06_i386.deb) ...
Setting up firefox (1.5.dfsg+1.5.0.4-0ubuntu6.06) ...


could klamav or superkaramaba have done this?

perhaps unrelated related question i ran virus scan with klam av and it found some viruses that i moved into quarantine and others i couldnt move in mostly in my mozilla and firefox files. 

i didnt think linux could be infected but i was and when i moved them could that have set this off? i mean this was last night and i have this problem since a few hours ago...do i have to restore the infected files?

---

### Post by maddbaron on 2006-07-06
ok, i did some net searching and the forum for firefox said it looks like a broken theme, i did update a theme but it wasnt my default theme. i have firefox completely uninstalled now. swiftfox too. how do i install and choose a custom folder for it to go into since i assume the Mozillia-Firefox folder in the urs area of ubuntu has the problem. i cant delete that folder either.

i am still in Kubuntu.

how do i reinstall in a custom made folder please?

---

### Post by maddbaron on 2006-07-06
what are the sudo codes to remove the urs/lib/firefox and urs/lib/mozilla-firefox folders please? i need to do a complete new install i tried deleting via konqueror but the files wouldnt move so i assume i need to be in root to do so. i reinstalled it and tried safe mode and still couldnt get it running got same issue. so these two folders have to go so i can reinstall and hopefully fix the problem since even with the uninstall/reinstalling i have been doing when i start it keeps picking up the left over start page i set up along with the additions in extensions like fasterfox and the weather etc.

is the code 

sudo rm urs/lib/firefox    

?

---

### Post by maddbaron on 2006-07-06
ok been working on this now...i found my .mozilla folder, if i delete the contents of that folder but not the folder itself and do a fresh install that should remove any conflicts right?

and as an aside how can i view all my .whatever folders?

---

### Post by maddbaron on 2006-07-06
problem fixed. i am good now thanks for the help

---

### Post by cjm5229 on 2006-07-06
I always keep a backup of my Bookmarks, Manage bookmarks>file.export. just in case something like that happens. About the .hidden files, if you use Ubuntu, just open Nautilus, then Edit>preferences>views>show hidden files, check box. I can't tell you how to do it in KDE.

---

