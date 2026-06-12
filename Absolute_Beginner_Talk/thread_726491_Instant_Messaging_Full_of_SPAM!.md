---
title: "Instant Messaging: Full of SPAM!"
date: 2008-03-16
forum: Absolute Beginner Talk
---

### Post by karlo on 2008-03-16
After leaving my computer on for a while, of course you will be excited when you receive many IM's. But you will be annoyed if you saw someone PM you, well that is, in a SPAM way.

For example, from kellyschneider47 ... just sends you your name via YM Protocol, via Pidgin.

After reasearching I saw this site [http://www.tipstrs.com/tip/2651/Stop-Pidgin-SPAM](http://www.tipstrs.com/tip/2651/Stop-Pidgin-SPAM) a very very useful site and I came up with Pidgin Bot Sentry.

I downloaded this plugin, now I don't know how to do with it so I researched again.

Based on this [http://ubuntuforums.org/showthread.php?t=667770](http://ubuntuforums.org/showthread.php?t=667770)

I did the following:

```
sudo aptitude install build-essential pidgin-dev checkinstall
```

but I receive the following message:

```
karlo@karlo-laptop:~$ sudo aptitude install build-essential pidgin-dev checkinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  libc6-dev 
The following NEW packages will be automatically installed:
  g++ g++-4.1 libatk1.0-dev libcairo2-dev libdbus-1-dev libdbus-glib-1-dev 
  libexpat1-dev libfontconfig1-dev libfreetype6-dev libgtk2.0-dev 
  libice-dev libpango1.0-dev libpng12-dev libpurple-dev libsm-dev 
  libstdc++6-4.1-dev libx11-dev libxau-dev libxcomposite-dev libxcursor-dev 
  libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev 
  libxi-dev libxinerama-dev libxrandr-dev libxrender-dev linux-libc-dev 
  x11proto-composite-dev x11proto-core-dev x11proto-damage-dev 
  x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev 
  x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev xtrans-dev 
  zlib1g-dev 
The following NEW packages will be installed:
  build-essential g++ g++-4.1 libatk1.0-dev libcairo2-dev libdbus-1-dev 
  libdbus-glib-1-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev 
  libgtk2.0-dev libice-dev libpango1.0-dev libpng12-dev libpurple-dev 
  libsm-dev libstdc++6-4.1-dev libx11-dev libxau-dev libxcomposite-dev 
  libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev 
  libxft-dev libxi-dev libxinerama-dev libxrandr-dev libxrender-dev 
  linux-libc-dev pidgin-dev x11proto-composite-dev x11proto-core-dev 
  x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev 
  x11proto-randr-dev x11proto-render-dev x11proto-xext-dev 
  x11proto-xinerama-dev xtrans-dev zlib1g-dev 
0 packages upgraded, 45 newly installed, 0 to remove and 0 not upgraded.
Need to get 19.3MB/23.0MB of archives. After unpacking 77.4MB will be used.
The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.6.1-1ubuntu10) but 2.7-5ubuntu2 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
libc6 [2.7-5ubuntu2 (now) -> 2.6.1-1ubuntu10 (gutsy-updates)]

Score is 80

Accept this solution? [Y/n/q/?] y
The following NEW packages will be automatically installed:
  g++ g++-4.1 libatk1.0-dev libc6-dev libcairo2-dev libdbus-1-dev 
  libdbus-glib-1-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev 
  libgtk2.0-dev libice-dev libpango1.0-dev libpng12-dev libpurple-dev 
  libsm-dev libstdc++6-4.1-dev libx11-dev libxau-dev libxcomposite-dev 
  libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev 
  libxft-dev libxi-dev libxinerama-dev libxrandr-dev libxrender-dev 
  linux-libc-dev x11proto-composite-dev x11proto-core-dev 
  x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev 
  x11proto-randr-dev x11proto-render-dev x11proto-xext-dev 
  x11proto-xinerama-dev xtrans-dev zlib1g-dev 
The following packages will be DOWNGRADED:
  libc6 
The following NEW packages will be installed:
  build-essential g++ g++-4.1 libatk1.0-dev libc6-dev libcairo2-dev 
  libdbus-1-dev libdbus-glib-1-dev libexpat1-dev libfontconfig1-dev 
  libfreetype6-dev libgtk2.0-dev libice-dev libpango1.0-dev libpng12-dev 
  libpurple-dev libsm-dev libstdc++6-4.1-dev libx11-dev libxau-dev 
  libxcomposite-dev libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev 
  libxfixes-dev libxft-dev libxi-dev libxinerama-dev libxrandr-dev 
  libxrender-dev linux-libc-dev pidgin-dev x11proto-composite-dev 
  x11proto-core-dev x11proto-damage-dev x11proto-fixes-dev 
  x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev 
  x11proto-xext-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev 
0 packages upgraded, 45 newly installed, 1 downgraded, 0 to remove and 0 not upgraded.
Need to get 23.5MB/27.2MB of archives. After unpacking 77.3MB will be used.
Do you want to continue? [Y/n/?] yy
Writing extended state information... Done
Get:1 http://tw.archive.ubuntu.com gutsy/main x11proto-core-dev 7.0.10-2 [86.3kB]
Media Change: Please insert the disc labeled 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)' in the drive '/cdrom/' and press [Enter].
```

Now is it safe to DOWNGRADE packages? I think the gutsy-updates means, that package is replaced by the Updates that Ubuntu is offering.

And why do I have to use my Ubuntu CD since I have the internet with me?

Another one, I am planning to remove the development files after compiling Pidgin Bot Sentry pack. Will it remove lib6 etc.. too? Can I update it to the latest version? The original version before the downgrading? HELP!!!

---

### Post by Xiong Chiamiov on 2008-03-17
I can't answer all of your questions, but I *think* you'll be ok downgrading that package.  As far as the CD goes, if you uncheck the CD option in your repositories (know how to get there?) then it will download them from the 'nets instead.  It's an option as some may prefer to avoid downloading large amounts of data if they have it locally instead.

---

### Post by karlo on 2008-03-22
> **Xiong Chiamiov said:**
> I can't answer all of your questions, but I *think* you'll be ok downgrading that package.  As far as the CD goes, if you uncheck the CD option in your repositories (know how to get there?) then it will download them from the 'nets instead.  It's an option as some may prefer to avoid downloading large amounts of data if they have it locally instead.

Do you think it's a **BUG**?

---

