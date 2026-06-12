---
title: "Appimage and Snap not working (Alderon Games Launcher)"
date: 2023-04-19
forum: Apple Hardware Users
---

### Post by endzeit1 on 2023-04-19
Hi all, I just set up a new Ubuntu system on an older iMac. System is running fine (as far as I can tell) but I cant get the Alderon Games Launcher to do anything.


Alderon offers a Snap and Appimage file for download. Both simply do nothing. The Snap produces an error message (Failed to install file: not supported) from the built-in Snap Store app.


Any idea on how to get the Launcher to work?

I have succesfully installed other apps without issues.

You can find the launcher files directly on the front page of alderongames dot com. Anyone who could give this a try? Any help appreciated. ):P

---

### Post by TenPlus1 on 2023-04-19
In Terminal type: sudo apt install libfuse2

This installs a missing library required for some AppImage files to run.

---

### Post by ActionParsnip on 2023-04-19
There is a deb
[https://github.com/lutris/lutris/releases/download/v0.5.12/lutris_0.5.12_all.deb](https://github.com/lutris/lutris/releases/download/v0.5.12/lutris_0.5.12_all.deb)

---

### Post by slickymaster on 2023-04-19
Thread moved to **Apple Hardware Users** for a better fit

---

### Post by deadflowr on 2023-04-19
I see the snap isn't part of Ubuntu's snap publishing system, so to install it you need to run a command line.
Usually you'd need to add the assertions first, but i see there are no assertion files to add, so you will need to install it using the --dangerous flag like so
```
cd Downloads
snap install AlderonGamesLauncher-1.1.79.snap --dangerous
```
Note I probably misspelled it. Make sure the name is correct.

See if that works. At least if you want to try the snap version.

Otherwise, installing the libfuse2 package should allow the appimage version to work.
As already suggested.




Edit: Nevermind, the snap is broken, as far as i can tell.
Testing it failed and running via command line outputs this
```
snap run alderongamelauncher
error: cannot find current revision for snap alderongamelauncher: readlink /snap/alderongamelauncher/current: no such file or directory
```
The file does exist, but it's wrong so not linked correctly or something.
Probably not worth the effort to fiddle around to try to fix it.

++1 to just try the appimage version and ignore the snap.

---

### Post by Holger_Gehrke on 2023-04-19
When I start the AppImage from the command line on my XUbuntu system it just spits out a few GTK Warnings and then doesn't do anything until I ctrl-c out of it. libfuse2 is installed and I have run other AppImages without any problems. 'strace' shows that it's connecting to the X Server through a socket and keeps reading from that socket and getting EAGAIN (an error code that means: nothing to read from that source, try again later).

Holger

---

### Post by #&amp;thj^% on 2023-04-19
It works here 23.04 and same as Holger (Xfce 4.18):
```
>> '/home/me/Downloads/AlderonGamesLauncher-1.1.79.AppImage' 
OSVersionCheck OSVersion { type: 'Linux', version: '6.2.0-20-generic' }
OSVersionCheck ProductVersion { type: 'Linux', version: '6.2.0-20-generic' }
[15:03:58.234:app:info] Logger Initiated
[15:03:58.236:app:info] Pre Global Logger
[15:03:58.236:app:info] Post Global Logger
[15:03:58.344:app:info] libtorrent::constructor session
[15:03:58.344:app:info] libtorrent::constructor pack
[15:03:58.346:app:info] libtorrent::constructor flags
[15:03:58.377:app:info] libtorrent::constructor new session
[15:03:58.377:app:info] Notifier
[15:03:58.377:app:info] Store
[15:03:58.377:app:info] Icon
[15:03:58.378:app:info] Logout
[15:03:58.378:app:info] Host
[15:03:58.378:app:info] Libtorrent
[15:03:58.402:app:info] AppIdentity
[15:03:58.403:app:info] EnsureQuitting
[15:03:58.403:app:info] ChromiumFlags
[15:03:58.403:app:info] AutoUpdate
[15:03:58.403:app:info] AutoLaunch
[15:03:58.403:app:info] WebContentsSecurity
[15:03:58.403:app:info] Tray
[15:03:58.403:app:info] WorkerWindow
[15:03:58.403:app:info] LoginWindow
[15:03:58.403:app:info] MainWindow
[15:03:58.404:app:info] SingleInstance
[15:03:58.404:app:info] RegainFocus
[15:03:58.404:app:info] DevTools
[15:03:58.404:app:info] ConfigureAutoLaunch
[15:03:58.404:app:info] ConfigureLauncherChannel
[15:03:58.404:app:info] store::ready
(node:871264) DeprecationWarning: findLogPath() is deprecated and will be removed in v5.
(Use `alderon-games-launcher --trace-deprecation ...` to show where the warning was created)
(node:871264) DeprecationWarning: file property is deprecated and will be removed in v5.
(node:871264) DeprecationWarning: file property is deprecated and will be removed in v5.
[15:03:59.633:app:debug] checkForUpdates.
[15:03:59.634:app:info] Calling checkForUpdates() method.
[15:03:59.634:app:info] Checking for update
[15:03:59.634:app:debug] AutoUpdate::emit { type: 'state', data: 'checking' }
[15:03:59.634:app:debug] got window
[15:03:59.662:app:info] Generated new staging user ID: 41274420-12a1-5b48-a523-8c5d6a9220f0
[15:04:00.814:app:info] Update for version 1.1.79 is not available (latest version: 1.1.79, downgrade is disallowed).
[15:04:00.815:app:info] autoUpdater: Update not available.
[15:04:00.815:app:debug] AutoUpdate::emit { type: 'state', data: 'updated' }
[15:04:00.816:app:debug] got window

```
Maybe something shows in my return

---

### Post by endzeit1 on 2023-04-20
Hey everyone, I fear this is beyond my level of expertise with Linux. I understand the file is somewhat corrupt. I contacted Alderon about this and might get a response from them at some point. Will report back.

---

