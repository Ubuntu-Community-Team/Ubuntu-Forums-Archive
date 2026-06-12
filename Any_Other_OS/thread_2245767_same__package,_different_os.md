---
title: "same  package, different os?"
date: 2014-09-25
forum: Any Other OS
---

### Post by Jonathan_Stein on 2014-09-25
I am dual booting linux mint and Ubuntu, and I was wondering if there was anyway that I could have only one /bin folder, you know, using the same software on two systems, or at least the same folder. Let me give you the idea of what I want to set up- ubuntu on one partition(/dev/sda1) linux mint on the other(/dev/sda2) and theoretically, devian on another (/dev/sda3), and I want to mount /bin for all of them to /dev/sda4, is that possible? and if so, will compatible packages be recognized on multiple systems?

---

### Post by ian-weisser on 2014-09-26
You cannot do it using packages. 
Each package manger will erroneously assume it's the only package manager with access to shared /bin. Each package manager will try to update the /bin applications normally, which will break either the application (no longer compatible with the other distros) or the package manager (overwrite error or permission error).

---

### Post by Jonathan_Stein on 2014-09-26
Why would it break the package? If they both operating systems use the same exact package, why would it break, or even if it would, is there anyway to move all /bin folders to just one seperate harddrive?

---

### Post by QIII on 2014-09-26
It is not likely that all the OSes would use all the same packages and versions of any given software, and a change to some dependency as decided by one OS might cause problems when you started the other.

---

### Post by tgalati4 on 2014-09-26
Now wait.  If you set up symbolic links in the other distros to point to the "master" distro, then it might work.  Of course, I'm going to remember not to answer any of your future support posts.

This idea ranks with saving disk space by deleting unused files in /usr/bin.

---

### Post by QIII on 2014-09-26
But then you'd have to have a "master distro", which would kind of defeat the purpose.

---

### Post by Jonathan_Stein on 2014-09-27
so when i find a software which install file is the exact same for linux mint, debian, and ubuntu, it wont work? wven if the installed files would also be the same?

---

### Post by Jonathan_Stein on 2014-09-27
how exactly would you do this?

---

### Post by tgalati4 on 2014-09-27
```
man ln
```

I can't believe I am doing this.  Do not follow any of these steps:

Let us say that *bash* is exactly the same package in each distro.

```
apt-cache policy bash
```

It might look like:

> tgalati4@Mint14-Extensa ~ $ apt-cache policy bash
bash:
  Installed: 4.2-5ubuntu1
  Candidate: 4.2-5ubuntu1
  Version table:
 *** 4.2-5ubuntu1 0
        500 [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) quantal/main amd64 Packages
        100 /var/lib/dpkg/status


Now find where the files are located:

> 
tgalati4@Mint14-Extensa ~ $ which bash
/bin/bash
tgalati4@Mint14-Extensa ~ $ whereis bash
bash: /bin/bash /etc/bash.bashrc /usr/share/man/man1/bash.1.gz
tgalati4@Mint14-Extensa ~ $ ls -la /bin/b*
-rwxr-xr-x 1 root root  959168 Sep 19  2012 /bin/bash
-rwxr-xr-x 1 root root   31152 Aug  3  2012 /bin/bunzip2
-rwxr-xr-x 1 root root 1819608 Nov 16  2012 /bin/busybox
-rwxr-xr-x 1 root root   31152 Aug  3  2012 /bin/bzcat
lrwxrwxrwx 1 root root       6 Dec 28  2012 /bin/bzcmp -> bzdiff
-rwxr-xr-x 1 root root    2140 Aug  3  2012 /bin/bzdiff
lrwxrwxrwx 1 root root       6 Dec 28  2012 /bin/bzegrep -> bzgrep
-rwxr-xr-x 1 root root    4877 Aug  3  2012 /bin/bzexe
lrwxrwxrwx 1 root root       6 Dec 28  2012 /bin/bzfgrep -> bzgrep
-rwxr-xr-x 1 root root    3642 Aug  3  2012 /bin/bzgrep
-rwxr-xr-x 1 root root   31152 Aug  3  2012 /bin/bzip2
-rwxr-xr-x 1 root root   10376 Aug  3  2012 /bin/bzip2recover
lrwxrwxrwx 1 root root       6 Dec 28  2012 /bin/bzless -> bzmore
-rwxr-xr-x 1 root root    1297 Aug  3  2012 /bin/bzmore


Now create symbolic links to *bash* to your "Master" distro location.  Repeat these steps for each "Slave" distro.  Now, when you update the "Master" distro, the "Slave" distros should be running the latest version.

This is a bad idea.  No, it is a terrible idea.  But you asked.

---

### Post by Jonathan_Stein on 2014-09-27
Why is it a terrible idea if it would work? And its all on a virtual machine im starting from scratch anyway(long story) If i fail, i just rinse and repeat. I just realized I may be incredibly stupid, but can I also just mount each /bin from each distro to a partition on a harddrive? ex. (ubuntu's /bin mounted to /dev/sdf1, debians to /dev/sdf2, linux mints to /dev/sdf3?) with each having equal space? If so I am an idiot and I never should have created this post to begin with

---

### Post by ian-weisser on 2014-09-27
I think you should try it.
Then tell us why it did or didn't work well.

I think you will run into problems of binaries compiled against different toolchains, and of package managers overwriting each other's updates.
And, honestly, I would love to know if I was right or wrong.

I say do it. Doooo iiiitttt. (Do NOT risk your data! I think you risk data loss in the VM)
Have some VM fun.

---

### Post by tgalati4 on 2014-09-27
I've run Linux Mint (MATE and older Gnome2 desktop versions) and several flavors of Ubuntu and I know for a fact that the /bin and /usr/bin have different binaries.  So you have to drill down to individual files not directories to find similarities between distros.  

For instance run this on an Ubuntu machine:

```
apropos mate
```

If you don't get something like:

> 
tgalati4@Mint14-Extensa ~ $ apropos mate
animate (1)          - animates an image or image sequence on any X server.
animate.im6 (1)      - animates an image or image sequence on any X server.
atril (1)            - MATE document viewer
caja (1)             - the MATE File Manager
chat (8)             - Automated conversational script with a modem
Class::Accessor (3pm) - Automated accessor generation
du (1)               - estimate file space usage
fancontrol (8)       - automated software based fan speed regulation
ico (1)              - animate an icosahedron or other polyhedron
mate-about (1)       - Learn more about MATE
mate-autogen (1)     - generates all makefiles for MATE packages
mate-bluetooth-applet (1) - MATE applet for prompting the user for a Bluetooth passkey (PIN)
mate-bluetooth-properties (1) - GTK dialog for managing properties of the Linux Bluetooth stack
mate-bluetooth-sendto (1) - GTK application for transfering files over Bluetooth
mate-bluetooth-wizard (1) - GTK wizard for setting up devices with the Linux Bluetooth stack
mate-calc (1)        - a desktop calculator
mate-dictionary (1)  - Look up words on dictionaries
mate-disk-usage-analyzer (1) - A graphical tool to analyse disk usage
mate-doc-common (1)  - include the standard user documentation build files
mate-options (7)     - Standard Command Line Options for MATE Programs
mate-panel (1)       - Display the MATE panel
mate-power-manager (1) - mate power manager userspace daemon
mate-power-preferences (1) - mate power preferences gui
mate-power-statistics (1) - mate power statistics gui
mate-screensaver (1) - screen saver and locker
mate-screensaver-command (1) - controls MATE screensaver
mate-screensaver-preferences (1) - configure MATE Screensaver
mate-screenshot (1)  - capture the screen, a window, or an user-defined area and save the snapshot image to a file.
mate-search-tool (1) - the MATE Search Tool
mate-session (1)     - Start the MATE desktop environment
mate-session-properties (1) - Configure applications to start on login
mate-session-save (1) - End or save the current MATE session
mate-system-log (1)  - the MATE System Log Viewer
mate-wm (1)          - Start the window manager configured by the user
matecomponent-activation-server (1) - MATE component tracker
mateconf-editor (1)  - an editor for the MateConf configuration system
mateconf-gsettings-data-convert (1) - MateConf to GSettings data migration
mateconf-gsettings-schema-convert (1) - MateConf to GSettings schema conversion
mateconftool-2 (1)   - MATE configuration tool
matedialog (1)       - display GTK+ dialogs
pluma (1)            - text editor for the MATE Desktop
x-session-manager (1) - Start the MATE desktop environment


Then that is just the start of the differences between distros.

---

### Post by Jonathan_Stein on 2014-09-27
im starting from scratch with a backed up vm from th install- there is no data yet

---

### Post by cariboo on 2014-09-28
Closed by request.

---

