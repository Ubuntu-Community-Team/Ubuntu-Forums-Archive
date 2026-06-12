---
title: "nautilius problem"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-07-12
a few hours ago I've installed kernel 686 and thunder
an hour after the restart I found out that when I try to open folders with nautilius I cannot see the content for some reason
how can I fix it ?

---

### Post by Miguel on 2006-07-12
Hi!

Can you post a screenshot? If possible, open a terminal, go to the same folder, and type "ls" to check that the content is actually different.

First: check that nautilus is actually working. To do this, go to Applications -> System Tools -> Run as another user. Select "root". The command should be
```

nautilus --nodekstop

```

Try to navigate a bit. **Be careful! you have full privileges!**. As soon as you check that it works or not, *close* that window and tell us. If it works, it is likely that the problem lies in one of your personal settings.

Next thing I would try would be reconfiguring Nautilus. You can do this by typing the command
```

sudo dpkg-reconfigure nautilus

```
in a terminal. "dpkg-reconfigure" is the standard way to reconfigure programs from the command-line. In some ocassions it might ask you questions.

In a similar fashion, reinstalling nautilus and/or libnautilus-extension1 (this one might be subject of "dpkg-reconfigure") can also solve your problems.

Next try. What do you mean by "thunder"? Is it the file manager "thunar" (lightweight)? I suppose you don't run linux [here](http://www.llnl.gov/linux/thunder/) (I know a couple of guys that do). So the next thing to attempt would be uninstalling thunar (if you did it via synaptic) and trying again. 

Another suggestion (more desperate) would be deleting your user's nautilus config and see if it works now. This has a worse version in deleting all your gnome preferences, but we'll try to stay clear of this one, right?

---

### Post by MaximB on 2006-07-12
I've tried some things you said :

maxim@maxim-home:~$ sudo dpkg-reconfigure nautilus



** (process:6353): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

** (process:6353): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed
maxim@maxim-home:~$
maxim@maxim-home:~$
maxim@maxim-home:~$ dpkg-reconfigure
/usr/sbin/dpkg-reconfigure must be run as root
maxim@maxim-home:~$ root
bash: root: command not found
maxim@maxim-home:~$ su
Password:
root@maxim-home:/home/maxim# sudo dpkg-reconfigure nautilus 
** (process:6387): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

** (process:6387): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed
root@maxim-home:/home/maxim# dpkg-reconfigure nautilus

** (process:6405): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

** (process:6405): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

BTW - I've install thunder via command line
how to remove it via command line I have a no idea
but they worked both before the rebot.

---

### Post by Miguel on 2006-07-12
Hi again Maxddark,

Does all that crap appear in the terminal? It doesn't look good at all. I would try to reinstall it. From the terminal:
```

su
aptitude reinstall nautilus

```

OK, "su" will make you root. After that, aptitude is a similar tool to apt-get. And reinstall is more or less explanatory.

HOWEVER, you might want to do all this with the mouse. Yes, it can be done. However, the terminal offers support when all GUI's have betrayed us. To install/reinstall/uninstall apps with the mouse, go to "System"-> "Administration" -> "Synaptic package manager". Search for nautilus (using the search function), right-click on it and select reinstall.

---

### Post by MaximB on 2006-07-12
I've tried to reinstall it via the command line :

nautilus (using troot@maxim-home:/home/maxim# aptitude reinstall nautilus
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be REINSTALLED:
  nautilus
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 851kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main nautilus 2.14.1-0ubuntu9 [851kB]
Fetched 851kB in 20s (40.7kB/s)
(Reading database ... 171724 files and directories currently installed.)
Preparing to replace nautilus 2.14.1-0ubuntu9 (using .../nautilus_2.14.1-0ubuntu9_i386.deb) ...
Unpacking replacement nautilus ...
Setting up nautilus (2.14.1-0ubuntu9) ...

** (process:6564): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

** (process:6564): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed

other instersting thing is that I can see the files and folders if I use ICONS mode and not the list mode.

---

### Post by Miguel on 2006-07-12
Hi again,

I've just read in your other thread that you've been playing with permissions. Am I right? Well, this might be a permissions problem more than a nautilus problem. It could explain many things. It boils down to a question:

What permissions have you changed? To what?

I tell you because, unintuitively, if you want to access a folder, you need execute permission. If you don't, you won't be allowed to even ls the content of that folder.

How can you check if permissions are the root of your problems? Type this:

```

nautilus --nodesktop /etc

```

There is no need to be root. This should open a nautilus window (without creating the background again) in folder /etc. I suppose you haven't touched this folder, so this should be readable. You can try to browse it. Does it work? Do you get any errors in the terminal?

If it works OK, we will try to add "read" "write" and "execute" permissions to your user in your home folder (I suppose it's the one in the commands above):
```

chmod u+rwx /home/maxim

```

What happens now if you open nautilus from "Places" -> "Personal folder"?

*EDIT:* Just noticed you are from Israel. It must be late in your country now (just 12:00am in Spain right now). If you want, we can leave this for tomorrow. I won't be up much longer.

---

### Post by MaximB on 2006-07-12
I can see that you heaven't completley read my last pose on this thread
as I said :
other instersting thing is that I can see the files and folders if I use ICONS mode and not the list mode.

as to premissions thing - well I'm learning MCSE and they got dozens of premissions file/folder/user...and more
so I didn't want to belive that linux has fewer premissions then xp...
but I guess it's true :(

---

### Post by Miguel on 2006-07-12
Hi again,

I did read the part concernign the Icon view and the List view. I sincerely do not understand why you have no problems in the Icons mode. Is there any difference between "ls" and "ls -l"? 

About the permissions... I agree that in some situations the unix model might not be the most efficient in some cases, but IMHO it works pretty well. Please note I am not an IT guy. However, what can you do in XP with permissions that can't be done in UNIX? I mean, the audio relevant folders are owned by "root" and the group is "audio". Other users (outside root and the ones in audio) have no business with audio. Do you want audio for a certain user? You add that user to group audio. You want to keep your brother from listening that horrible music? You drop him from "audio" (well, this is a bit drastic :mrgreen: ). Just remember that every single file has user group and other permissions. And everything is a file in UNIX ;)

---

### Post by MaximB on 2006-07-13
well about the premmisions - I've opened a thread so we can talk about it there
but how can I compete reinstall nautilus without having thouse errors ?

---

### Post by Miguel on 2006-07-13
Hi again,

Mind you, I'm nervous and I'll make lots of questions. I have a wild router.

First of all, I do really need to know if you changed permissions to folders like /etc (system configuration) /var (*very important* for apt-get or synaptic). If you didn't touch anything, tell me. If you did, tell me.

Anyway, try reinstalling the following packages: nautilus-data and shared-mime-info. Do you get any error messages? I've found that some similar error messages appear when updating the mime database. To do this, type:

```

sudo update-desktop-database -v

```

Or run this as root without the sudo part. This is also related to desktop-file-utils. An attemtp to reinstall this package could also help. ¿Do you still get these error messages? If so, do you see anything weird in in "ls -l /usr/share/applications | tail"? I get the following:
```

$ ls -l /usr/share/applications | tail
-rw-r--r-- 1 root root  2257 2006-05-18 14:55 xfce-workspaces-settings.desktop
-rw-r--r-- 1 root root  4084 2006-05-18 14:52 xfce-xfcalendar-settings.desktop
-rw-r--r-- 1 root root  3950 2006-05-12 19:37 xfce-xfprint-settings.desktop
-rw-r--r-- 1 root root   171 2006-05-15 02:48 xfig.desktop
-rw-r--r-- 1 root root  1852 2006-05-09 10:38 xfmedia.desktop
-rw-r--r-- 1 root root  2801 2006-05-12 19:37 xfprint.desktop
-rw-r--r-- 1 root root  3481 2006-05-12 19:37 xfprint-manager.desktop
-rw-r--r-- 1 root root   207 2006-03-11 02:42 xpdf.desktop
-rw-r--r-- 1 root root  2408 2006-03-16 16:10 xsane.desktop
-rw-r--r-- 1 root root  3427 2006-06-15 17:56 yelp.desktop

```

I've read that some guy had this probem in warty, but solved it by uninstalling the package mplayer-custom. ¿Do you have any mplayer package installed? ¿What happens if you install?

---

### Post by MaximB on 2006-07-13
I didn't change the premmisions
I didn't install custom Mplayer

maxim@maxim-home:~$ sudo update-desktop-database -v
Password:
Search path is now: [/usr/local/share/applications, /usr/share/applications]
Could not create cache file in directory '/usr/local/share/applications':
        Error opening directory '/usr/local/share/applications': No such file or directory
File '/usr/share/applications/accessibility-keyboard.desktop' lacks MimeType keyFile '/usr/share/applications/alacarte.desktop' lacks MimeType key
File '/usr/share/applications/at-properties.desktop' lacks MimeType key
File '/usr/share/applications/background.desktop' lacks MimeType key
File '/usr/share/applications/blackjack.desktop' lacks MimeType key
File '/usr/share/applications/bug-buddy.desktop' lacks MimeType key
File '/usr/share/applications/cddb-slave.desktop' lacks MimeType key
File '/usr/share/applications/default-applications.desktop' lacks MimeType key
File '/usr/share/applications/disks.desktop' lacks MimeType key
File '/usr/share/applications/display-properties.desktop' lacks MimeType key
File '/usr/share/applications/ekiga.desktop' lacks MimeType key
File '/usr/share/applications/evolution-2.2.desktop' lacks MimeType key
File '/usr/share/applications/evolution-mail.desktop' lacks MimeType key
File '/usr/share/applications/evolution.desktop' lacks MimeType key
File '/usr/share/applications/font-properties.desktop' lacks MimeType key
File '/usr/share/applications/freecell.desktop' lacks MimeType key
File '/usr/share/applications/gaim.desktop' lacks MimeType key
File '/usr/share/applications/gataxx.desktop' lacks MimeType key
File '/usr/share/applications/gcalctool.desktop' lacks MimeType key
File '/usr/share/applications/gconf-editor.desktop' lacks MimeType key
File '/usr/share/applications/gdmflexiserver-xnest.desktop' lacks MimeType key
File '/usr/share/applications/gdmflexiserver.desktop' lacks MimeType key
File '/usr/share/applications/gdmphotosetup.desktop' lacks MimeType key
File '/usr/share/applications/gdmsetup.desktop' lacks MimeType key
File '/usr/share/applications/gksu.desktop' lacks MimeType key
File '/usr/share/applications/gksuexec.desktop' lacks MimeType key
File '/usr/share/applications/glines.desktop' lacks MimeType key
File '/usr/share/applications/gmenu-simple-editor.desktop' lacks MimeType key
File '/usr/share/applications/gnect.desktop' lacks MimeType key
File '/usr/share/applications/gnibbles.desktop' lacks MimeType key
File '/usr/share/applications/gnobots2.desktop' lacks MimeType key
File '/usr/share/applications/gnome-about-me.desktop' lacks MimeType key
File '/usr/share/applications/gnome-about.desktop' lacks MimeType key
File '/usr/share/applications/gnome-app-install.desktop' lacks MimeType key
File '/usr/share/applications/gnome-cd.desktop' lacks MimeType key
File '/usr/share/applications/gnome-cups-icon.desktop' lacks MimeType key
File '/usr/share/applications/gnome-dictionary.desktop' lacks MimeType key
File '/usr/share/applications/gnome-nettool.desktop' lacks MimeType key
File '/usr/share/applications/gnome-network-preferences.desktop' lacks MimeType key
File '/usr/share/applications/gnome-power-preferences.desktop' lacks MimeType key
File '/usr/share/applications/gnome-screensaver-preferences.desktop' lacks MimeType key
File '/usr/share/applications/gnome-screenshot.desktop' lacks MimeType key
File '/usr/share/applications/gnome-search-tool.desktop' lacks MimeType key
File '/usr/share/applications/gnome-settings-mouse.desktop' lacks MimeType key
File '/usr/share/applications/gnome-settings-sound.desktop' lacks MimeType key
File '/usr/share/applications/gnome-sound-recorder.desktop' lacks MimeType key
File '/usr/share/applications/gnome-system-log.desktop' lacks MimeType key
File '/usr/share/applications/gnome-system-monitor.desktop' lacks MimeType key
File '/usr/share/applications/gnome-terminal.desktop' lacks MimeType key
File '/usr/share/applications/gnome-ui-properties.desktop' lacks MimeType key
File '/usr/share/applications/gnome-volume-control.desktop' lacks MimeType key
File '/usr/share/applications/gnome-volume-properties.desktop' lacks MimeType key
File '/usr/share/applications/gnomecc.desktop' lacks MimeType key
File '/usr/share/applications/gnometris.desktop' lacks MimeType key
File '/usr/share/applications/gnomine.desktop' lacks MimeType key
File '/usr/share/applications/gnopernicus.desktop' lacks MimeType key
File '/usr/share/applications/gnotravex.desktop' lacks MimeType key
File '/usr/share/applications/gnotski.desktop' lacks MimeType key
File '/usr/share/applications/gok.desktop' lacks MimeType key
File '/usr/share/applications/abuse.desktop' lacks MimeType key
File '/usr/share/applications/gstreamer-properties.desktop' lacks MimeType key
File '/usr/share/applications/gtali.desktop' lacks MimeType key
File '/usr/share/applications/gtk-theme-selector.desktop' lacks MimeType key
File '/usr/share/applications/gucharmap.desktop' lacks MimeType key
File '/usr/share/applications/hplip.desktop' lacks MimeType key
File '/usr/share/applications/hwdb.desktop' lacks MimeType key
File '/usr/share/applications/iagno.desktop' lacks MimeType key
File '/usr/share/applications/keybinding.desktop' lacks MimeType key
File '/usr/share/applications/keyboard.desktop' lacks MimeType key
File '/usr/share/applications/language-selector.desktop' lacks MimeType key
File '/usr/share/applications/mahjongg.desktop' lacks MimeType key
File '/usr/share/applications/nautilus-cd-burner.desktop' lacks MimeType key
File '/usr/share/applications/nautilus-computer.desktop' lacks MimeType key
File '/usr/share/applications/nautilus-file-management-properties.desktop' lacks MimeType key
File '/usr/share/applications/nautilus-home.desktop' lacks MimeType key
File '/usr/share/applications/nautilus.desktop' lacks MimeType key
File '/usr/share/applications/network-scheme.desktop' lacks MimeType key
File '/usr/share/applications/network.desktop' lacks MimeType key
File '/usr/share/applications/reclevel.desktop' lacks MimeType key
File '/usr/share/applications/same-gnome.desktop' lacks MimeType key
File '/usr/share/applications/scim-setup.desktop' lacks MimeType key
File '/usr/share/applications/services.desktop' lacks MimeType key
File '/usr/share/applications/session-properties.desktop' lacks MimeType key
File '/usr/share/applications/shares.desktop' lacks MimeType key
File '/usr/share/applications/software-properties.desktop' lacks MimeType key
File '/usr/share/applications/sol.desktop' lacks MimeType key
File '/usr/share/applications/sound-juicer.desktop' lacks MimeType key
File '/usr/share/applications/synaptic-kde.desktop' lacks MimeType key
File '/usr/share/applications/synaptic.desktop' lacks MimeType key
File '/usr/share/applications/template.desktop' lacks MimeType key
File '/usr/share/applications/time.desktop' lacks MimeType key
File '/usr/share/applications/tsclient.desktop' lacks MimeType key
File '/usr/share/applications/icebreaker.desktop' lacks MimeType key
File '/usr/share/applications/ubuntu-about.desktop' lacks MimeType key
File '/usr/share/applications/update-manager.desktop' lacks MimeType key
File '/usr/share/applications/users.desktop' lacks MimeType key
File '/usr/share/applications/vino-preferences.desktop' lacks MimeType key
File '/usr/share/applications/vumeter.desktop' lacks MimeType key
File '/usr/share/applications/window-properties.desktop' lacks MimeType key
File '/usr/share/applications/xsane.desktop' lacks MimeType key
File '/usr/share/applications/yelp.desktop' lacks MimeType key
File '/usr/share/applications/freeciv.desktop' lacks MimeType key
File '/usr/share/applications/kde/kjumpingcube.desktop' lacks MimeType key
File '/usr/share/applications/kde/kresources.desktop' lacks MimeType key
File '/usr/share/applications/kde/kbackgammon.desktop' lacks MimeType key
File '/usr/share/applications/kde/kreversi.desktop' lacks MimeType key
File '/usr/share/applications/kde/kmines.desktop' lacks MimeType key
File '/usr/share/applications/kde/ksudoku.desktop' lacks MimeType key
File '/usr/share/applications/kde/kleansweep.desktop' lacks MimeType key
File '/usr/share/applications/kde/kde-hal-device-manager.desktop' lacks MimeType key
File '/usr/share/applications/kde/componentchooser.desktop' lacks MimeType key
File '/usr/share/applications/kde/artscontrol.desktop' lacks MimeType key
File '/usr/share/applications/kde/ksayit.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmkttsd.desktop' lacks MimeType key
File '/usr/share/applications/kde/kttsmgr.desktop' lacks MimeType key
File '/usr/share/applications/kde/kgeography.desktop' lacks MimeType key
File '/usr/share/applications/kde/ksame.desktop' lacks MimeType key
File '/usr/share/applications/kde/ksokoban.desktop' lacks MimeType key
File '/usr/share/applications/kde/kpoker.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcalc.desktop' lacks MimeType key
File '/usr/share/applications/kde/ktip.desktop' lacks MimeType key
File '/usr/share/applications/kde/kwindecoration.desktop' lacks MimeType key
File '/usr/share/applications/kde/kwinoptions.desktop' lacks MimeType key
File '/usr/share/applications/kde/kwinrules.desktop' lacks MimeType key

** (process:7472): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed
File '/usr/share/applications/kde/kcmkbfx.desktop' lacks MimeType key

** (process:7472): CRITICAL **: egg_desktop_entries_add_group: assertion `egg_desktop_entries_lookup_group (entries, group_name) == NULL' failed
File '/usr/share/applications/kde/kdmtheme.desktop' lacks MimeType key
File '/usr/share/applications/kde/keyboard.desktop' lacks MimeType key
File '/usr/share/applications/kde/keyboard_layout.desktop' lacks MimeType key
File '/usr/share/applications/kde/khotkeys.desktop' lacks MimeType key
File '/usr/share/applications/kde/knetattach.desktop' lacks MimeType key
File '/usr/share/applications/kde/kdcop.desktop' lacks MimeType key
File '/usr/share/applications/kde/automatix-kubuntu.desktop' lacks MimeType key
File '/usr/share/applications/kde/konsole.desktop' lacks MimeType key
File '/usr/share/applications/kde/adept_installer.desktop' lacks MimeType key
File '/usr/share/applications/kde/adept.desktop' lacks MimeType key
File '/usr/share/applications/kde/adept_updater.desktop' lacks MimeType key
File '/usr/share/applications/kde/adept_notifier.desktop' lacks MimeType key
File '/usr/share/applications/kde/kompile.desktop' lacks MimeType key
File '/usr/share/applications/kde/kxmame.desktop' lacks MimeType key
File '/usr/share/applications/kde/kftpgrabber.desktop' lacks MimeType key
File '/usr/share/applications/kde/libkcddb.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmkicker.desktop' lacks MimeType key
File '/usr/share/applications/kde/arts.desktop' lacks MimeType key
File '/usr/share/applications/kde/background.desktop' lacks MimeType key
File '/usr/share/applications/kde/bell.desktop' lacks MimeType key
File '/usr/share/applications/kde/cache.desktop' lacks MimeType key
File '/usr/share/applications/kde/clock.desktop' lacks MimeType key
File '/usr/share/applications/kde/colors.desktop' lacks MimeType key
File '/usr/share/applications/kde/desktopbehavior.desktop' lacks MimeType key
File '/usr/share/applications/kde/cookies.desktop' lacks MimeType key
File '/usr/share/applications/kde/crypto.desktop' lacks MimeType key
File '/usr/share/applications/kde/desktoppath.desktop' lacks MimeType key
File '/usr/share/applications/kde/desktop.desktop' lacks MimeType key
File '/usr/share/applications/kde/ebrowsing.desktop' lacks MimeType key
File '/usr/share/applications/kde/devices.desktop' lacks MimeType key
File '/usr/share/applications/kde/display.desktop' lacks MimeType key
File '/usr/share/applications/kde/dma.desktop' lacks MimeType key
File '/usr/share/applications/kde/filebrowser.desktop' lacks MimeType key
File '/usr/share/applications/kde/filetypes.desktop' lacks MimeType key
File '/usr/share/applications/kde/fonts.desktop' lacks MimeType key
File '/usr/share/applications/kde/icons.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmperformance.desktop' lacks MimeType key
File '/usr/share/applications/kde/interrupts.desktop' lacks MimeType key
File '/usr/share/applications/kde/ioports.desktop' lacks MimeType key
File '/usr/share/applications/kde/ioslaveinfo.desktop' lacks MimeType key
File '/usr/share/applications/kde/joystick.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmaccess.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmcss.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmfontinst.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmkded.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmlaunch.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmnotify.desktop' lacks MimeType key
File '/usr/share/applications/kde/khtml_behavior.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmsmserver.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmtaskbar.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmusb.desktop' lacks MimeType key
File '/usr/share/applications/kde/kcmview1394.desktop' lacks MimeType key
File '/usr/share/applications/kde/KControl.desktop' lacks MimeType key
File '/usr/share/applications/kde/kdm.desktop' lacks MimeType key
File '/usr/share/applications/kde/keys.desktop' lacks MimeType key
File '/usr/share/applications/kde/khtml_java_js.desktop' lacks MimeType key
File '/usr/share/applications/kde/khtml_fonts.desktop' lacks MimeType key
File '/usr/share/applications/kde/kthememanager.desktop' lacks MimeType key
File '/usr/share/applications/kde/kinfocenter.desktop' lacks MimeType key
File '/usr/share/applications/kde/krandrtray.desktop' lacks MimeType key
File '/usr/share/applications/kde/panel_appearance.desktop' lacks MimeType key
File '/usr/share/applications/kde/lanbrowser.desktop' lacks MimeType key
File '/usr/share/applications/kde/language.desktop' lacks MimeType key
File '/usr/share/applications/kde/media.desktop' lacks MimeType key
File '/usr/share/applications/kde/memory.desktop' lacks MimeType key
File '/usr/share/applications/kde/mouse.desktop' lacks MimeType key
File '/usr/share/applications/kde/netpref.desktop' lacks MimeType key
File '/usr/share/applications/kde/nic.desktop' lacks MimeType key
File '/usr/share/applications/kde/opengl.desktop' lacks MimeType key
File '/usr/share/applications/kde/partitions.desktop' lacks MimeType key
File '/usr/share/applications/kde/panel.desktop' lacks MimeType key
File '/usr/share/applications/kde/privacy.desktop' lacks MimeType key
File '/usr/share/applications/kde/pci.desktop' lacks MimeType key
File '/usr/share/applications/kde/spellchecking.desktop' lacks MimeType key
File '/usr/share/applications/kde/processor.desktop' lacks MimeType key
File '/usr/share/applications/kde/proxy.desktop' lacks MimeType key
File '/usr/share/applications/kde/screensaver.desktop' lacks MimeType key
File '/usr/share/applications/kde/scsi.desktop' lacks MimeType key
File '/usr/share/applications/kde/smbstatus.desktop' lacks MimeType key
File '/usr/share/applications/kde/sound.desktop' lacks MimeType key
File '/usr/share/applications/kde/useragent.desktop' lacks MimeType key
File '/usr/share/applications/kde/style.desktop' lacks MimeType key
File '/usr/share/applications/kde/xserver.desktop' lacks MimeType key
File '/usr/share/applications/glob2.desktop' lacks MimeType key
File '/usr/share/applications/Mozilla-editor.desktop' lacks MimeType key
File '/usr/share/applications/scorched3d.desktop' lacks MimeType key
File '/usr/share/applications/spider.desktop' lacks MimeType key
File '/usr/share/applications/wormux.desktop' lacks MimeType key
File '/usr/share/applications/xboard.desktop' lacks MimeType key
File '/usr/share/applications/amule.desktop' lacks MimeType key
File '/usr/share/applications/alc.desktop' lacks MimeType key
File '/usr/share/applications/wxcas.desktop' lacks MimeType key
File '/usr/share/applications/Mozilla.desktop' lacks MimeType key
File '/usr/share/applications/gtkboard.desktop' lacks MimeType key
File '/usr/share/applications/xsensors.desktop' lacks MimeType key
File '/usr/share/applications/xshogi.desktop' lacks MimeType key
File '/usr/share/applications/wesnoth.desktop' lacks MimeType key
File '/usr/share/applications/gnome-sudoku.desktop' lacks MimeType key
File '/usr/share/applications/widelands.desktop' lacks MimeType key
File '/usr/share/applications/gnome-splashscreen-manager.desktop' lacks MimeType key
File '/usr/share/applications/gabber2.desktop' lacks MimeType key
File '/usr/share/applications/nicotine.desktop' lacks MimeType key
File '/usr/share/applications/gkrellm.desktop' lacks MimeType key
File '/usr/share/applications/praat.desktop' lacks MimeType key
File '/usr/share/applications/qgis.desktop' lacks MimeType key
File '/usr/share/applications/arkhart.desktop' lacks MimeType key
File '/usr/share/applications/barrage.desktop' lacks MimeType key
File '/usr/share/applications/bzflag.desktop' lacks MimeType key
File '/usr/share/applications/chromium.desktop' lacks MimeType key
File '/usr/share/applications/memprof.desktop' lacks MimeType key
File '/usr/share/applications/falconseye.desktop' lacks MimeType key
File '/usr/share/applications/gnome-art.desktop' lacks MimeType key
File '/usr/share/applications/kcmgtk-xdg.desktop' lacks MimeType key
File '/usr/share/applications/automatix.desktop' lacks MimeType key
File '/usr/share/applications/gnomebaker.desktop' lacks MimeType key
File '/usr/share/applications/penguintv.desktop' lacks MimeType key
File '/usr/share/applications/wings3d.desktop' lacks MimeType key
File '/usr/share/applications/xaos.desktop' lacks MimeType key
File '/usr/share/applications/gtksee.desktop' lacks MimeType key
File '/usr/share/applications/dc_gui2.desktop' lacks MimeType key
File '/usr/share/applications/stopmotion.desktop' lacks MimeType key
File '/usr/share/applications/mlterm.desktop' lacks MimeType key
File '/usr/share/applications/debian-reference-common.desktop' lacks MimeType key
File '/usr/share/applications/configure-debian.desktop' lacks MimeType key
File '/usr/share/applications/qt-language-selector.desktop' lacks MimeType key
File '/usr/share/applications/galternatives.desktop' lacks MimeType key
File '/usr/share/applications/gnome-apt.desktop' lacks MimeType key
File '/usr/share/applications/gtk-gnutella.desktop' lacks MimeType key
File '/usr/share/applications/netpanzer.desktop' lacks MimeType key
File '/usr/share/applications/rrootage.desktop' lacks MimeType key
File '/usr/share/applications/torcs.desktop' lacks MimeType key
File '/usr/share/applications/trigger.desktop' lacks MimeType key
File '/usr/share/applications/xqf.desktop' lacks MimeType key
File '/usr/share/applications/Cedega.desktop' lacks MimeType key
File '/usr/share/applications/sbackup.desktop' lacks MimeType key
File '/usr/share/applications/srestore.desktop' lacks MimeType key
File '/usr/share/applications/xnc-gnome2.desktop' lacks MimeType key
File '/usr/share/applications/sysinfo.desktop' lacks MimeType key
File '/usr/share/applications/xfburn.desktop' lacks MimeType key
File '/usr/share/applications/frostwire.desktop' lacks MimeType key
File '/usr/share/applications/exo-preferred-applications.desktop' lacks MimeType key
File '/usr/share/applications/apkg-autopackage-manager-gtk.desktop' lacks MimeType key
File '/usr/share/applications/apkg-scourge.desktop' lacks MimeType key
File '/usr/share/applications/Thunar-bulk-rename.desktop' lacks MimeType key
File '/usr/share/applications/google-picasa.desktop' lacks MimeType key
File '/usr/share/applications/Thunar.desktop' lacks MimeType key
File '/usr/share/applications/f-spot.desktop' lacks MimeType key

and I tried to reinstall it in tty1 mode...but with no luck.
I've tried to go back to the 386 kernek - but also without luck

help ?

---

### Post by MaximB on 2006-07-13
other thing...
for some unknown resion I can see in the "file system" the files and folders as a list
but not when I enter folders there...

---

### Post by Miguel on 2006-07-13
Hi again

Well, OK I'm more calmed and relaxed now. Sorry if I was a bit of an **** previously, My router decided to reconfigure itself and the bloatware and spyware of my ISP really got on my nerves.

You have checked that this wasn't a permission issue (we are improving) and you have also checked that  this isn't a kernel issue. Great. Step by step. Don't worry about the "lacks MimeType key file". I see the same. What is the last file that appears if you type 
```

ls -lhtr /usr/share/applications

```

This will present a list (l variable) of all files and folders in /usr/share/applications in human-readable size (h variable), time-ordered (-t) and in reverse order (r). The last file that appears will be the last file modified. The last one will be mimeinfo.cache (you have just rebuilt it) and close to it you will see gimp and some files related to openoffice (ooo-whatever). These appear because a recent security update. Programs relating to something newer than 2006-06-16 will be our next suspect.

Anyway, I must confess I am hitting blinded strikes and there would probably be more knowledgeable people than me in this forum.

EDIT: Do you get those errors when installing other packages?

---

### Post by MaximB on 2006-07-13
other packages install without errors.
best tell me how to reinstall nautilus without errors.

---

### Post by Miguel on 2006-07-13
> **MAXDDARK said:**
> other thing...
for some unknown resion I can see in the "file system" the files and folders as a list
but not when I enter folders there...

From a console? What do you mean? I am afraid I don't get it. I suppose that "ls folder" will give a result but that "cd folder" and then "ls" won't? This is really really weird.

---

### Post by Miguel on 2006-07-13
> **MAXDDARK said:**
> other packages install without errors.
best tell me how to reinstall nautilus without errors.

Let's try to download directly nautilus and then install it with dpkg instead of apt. This should make it:

```

wget http://archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus_2.14.1-0ubuntu9_i386.deb
sudo dpkg -i nautilus_2.14.1-0ubuntu9_i386.deb

```

Well, you could download the ubuntu deb with firefox and then try to install it with gdebi, but this should be faster and more straightforward. I really hope this works.

---

### Post by MaximB on 2006-07-13
no it didn't work - it think it's b/z I've downloaded 386 version and my kernel is 686
were do I get the 686 version ?
I mean from the terminal

---

### Post by avtolle on 2006-07-13
I noticed in the original post, he indicated he had installed "thunder". I expect that he installed "Thundar", which, as I understand it, is an alternative file manager. So, at the risk of being very wrong, as I am new to the process, I suggest the issue w/reinstalling Nautilus has something to do with Thundar being installed. Perhaps he needs to uninstall Thundar, then attempt to reinstall Nautilus.

---

### Post by Miguel on 2006-07-13
Hi again,

The issue is not betwee 686 and 386. Mathematically, 386 instructions are a subset of 686 instructions, so if your system understands 86 instructions it will also understand 386 instructions. nautilus_blabla-i386 only means that the developers haven't applied newer processors' optimizations. I think it is a different issue than the one appearing in a mixed 32 and 64 bit system. 

There is no 686 nautilus version for ubuntu, although you can download the source and build it that way (I AM joking, don't do this, my medication hasn't done the desired effect).

Avtolle, thanks for your suggestion. I also think it is somewhat related to thunar but, I wasn't fully sure this was the original package he installed. In case it's thunar, it might help uninstalling it. If it is one of it's dependencies, it will be more difficult to track.

---

### Post by MaximB on 2006-07-13
after your suggestion I removed thunar and tried to install nautilus again
but to no avail
I posed my second problem that might have somthing with this problem
the source-list problem

---

### Post by MaximB on 2006-07-13
now it's really getting wierd
when I open nautilus as SU I can see the list anywere but not as normal user (the first user I built) with ALL the privilages.
how ? why ? what can I do ?

---

### Post by Miguel on 2006-07-13
Do you still get the same error messages? It would really help if you put the whole error message (just remember that highlighting and then middle-clicking will copy-paste things).

OT: This forum breakdown is killing my eyes.

---

### Post by MaximB on 2006-07-13
> **Miguel said:**
> Do you still get the same error messages? It would really help if you put the whole error message (just remember that highlighting and then middle-clicking will copy-paste things).

OT: This forum breakdown is killing my eyes.

same old sh*t
but how can su can view folders and files as a list ?
and I cannot ?
the errors are the same as above....

---

### Post by Miguel on 2006-07-13
> 
what can I do ?


First, we would all love a screenshot. Second, you might want to add a new user to your system (but *do not* add it to the admin group). Log out and then log in with the new user you created. Does this new user suffer from the same nautilus problems that you had or is he free of trouble?

You can add users on System -> Administration -> Users and Groups. Equivalently, you can use the command useradd (needs sudo or root), but I don't know the syntax by heart. You can delete your new user from here too.

EDIT: I suspect that root can open a nautilus session without problems because one of your preference files is corrupted or something. That's why I ask you to add a new user. If it works, we can restrict ourselves to fixing nautilus for you. Those crap messages will get later.

EDIT 2: In case it is related to the preferences, to save you time, to delete nautilus preferences you have delete the folders ~/.gconf/apps/nautilus and ~/.nautilus. Terminal work would be:

```

cd
rm -rf .gconf/apps/nautilus .nautilus

```

You can do this without any special privilege.

---

### Post by MaximB on 2006-07-13
other user can see list
so the problem is with my user
I run your command in terminal but i still cannot see list

---

### Post by Miguel on 2006-07-13
Well, let me ask you a question. Do you have a heavily customized gnome? In terms of applets, keyboard shortcuts, gdesklets, etc. Because I will suggest to kill all your gnome preferences. 

Sincerely, I am out of resources. If a normal fresh user is able to use nautilus OK, if root is able to use nautilus OK, then the problem must lie in some obscure file in your $HOME.

Wait! Before doing anything of this, log out of gnome. Yes, go to the login screen. From there, go to tty1 (Ctrl+Alt+F1), login, delete the files I told you a couple of posts ago and see if it works.

If you delete these folders, gnome should look again like a fresh install of Ubuntu, like the new user you have created. Folders to be deleted:
~/.gnome
~/.gnome2
~/.gnome2_private
~/.gconf
~/.gconfd

If you delete these after logging out from gnome and from tty1 you make sure your current gnome status isn't saved on exit.

Good luck

---

### Post by MaximB on 2006-07-13
I've done it but nothing seems to change...
maybe I can copy a file from the root user to my user...some nautilus file maybe so that my conf will be like su conf for nautilus ?

---

### Post by Miguel on 2006-07-13
What have you done? The whole deletion from tty1 after logging out of gnome? Do you now see a default ubuntu gnome (brown background, default human theme, no applets)? Please be slightly more specific. And remember you MUST delete those folders as yourself.

---

### Post by MaximB on 2006-07-13
I hit ctrl+alt+F1 > tty1
then :
rm -rf .gconf/apps/nautilus .nautilus
and all the other commands
then got back to desktop F7
and nothing happened
I tried to do this as a SU and as myself.

---

### Post by Miguel on 2006-07-13
Hi again,

I suppose you logged out of gnome.

> hit ctrl+alt+F1 > tty1
then :
rm -rf .gconf/apps/nautilus .nautilus
and all the other commands
then got back to desktop F7
and nothing happened

OK, so deletin the nautilus keys in gconf didn't help. When you go back to the desktop, do you see the default Ubuntu? If not, it's my fault, all the folders I listed must be deleted as YOU (not as root) the exact command is:

```

rm -rf ~/.gnome ~/.gnome2 ~/.gnome2_private ~/.gconf ~/.gconfd 

```

It's better if you do this from tty1 after logging out of gnome. After that you should definitely see a default gnome. Or at least the same gnome that you saw in your newly created user.

---

### Post by MaximB on 2006-07-13
I did excactly what you wrote - and it still didn't apear to delete anything

---

### Post by Miguel on 2006-07-13
If it makes you feel better, I've had the same issues. I made a user and changed the theme and background. And yes, logging in again would show me the exact same desktop as before. It seems that last preferences are stored somewhere.

So my suggestion is: [list][*] Log out of gnome
[*]Go to tty1
[*]Log in as you and delete the gnome and gconf folders (note the dot!):```

rm -rf .gconf* .gnome* .nautilus

```
[*] reboot ("sudo reboot" will reboot directly from tty1)
[/list]

Now you should see the default theme. At least I did. The next thing I would do is reinstalling kwin. Yes, I'm not joking. From synaptic or the terminal, whatever you prefer. The window manager is named kwin. Do you get any messages? 

If you also have the game kwin4 installed, I'd be glad if you also reinstalled it. 

Now please run again " sudo update-desktop-database -v". Do you still get that CRITICAL message near kwin?

---

### Post by MaximB on 2006-07-13
I am very sorry for spending your time...
you have been great...

and guess what.....
YOU'VE MADE IT !!!
I finaly can list !!!
thank you very much !!!

if you need anything I can help you with with (I can't name a thing cuz I'm a newbie , but if there will be) tell me right away...send me a privet massage...talk to me on icq...whatever I can help you with I WILL !!!
....now about my other problem...the source list...I've poset a thread already a few hours ago if you could find it...:)

and thank you again , you have been so helpfull

---

### Post by Miguel on 2006-07-13
Good night Maxddark,

Glad to hear you've finally solved your problem. I saw in your other sources.list thread other people had already posted their sources.list. I don't know if these will help, though I really hope so. I'll give a look as soon as I stop updating this machine's WinXP.

I must admit though that I'm still puzzled by that  CRITICAL thing. Maybe it was some update that didn't finish properly.

Sweet dreams ;)

---

### Post by Xdjibi on 2006-07-14
Hi everybody,

I've encountered a problem yesterday after a system update that may be related to your Nautilus troubles.
 
I wanted to move a file using Nautilus. But the permission was wrong : I was logged as normal user ghislain and the destination folder was read-only for everybody but the root.

So I modified the permission to give write rights to everybody for this folder.

This folder was open in Nautilus and this modification caused the crash of Nautilus.

I tried to reopen Nautilus and to move my file to the destination folder but Nautilus warned me : move error, you have no write right!!!

So I tried this:
# sudo chown ghislain:ghislain /Destination_folder

And then I retried to move it through Nautilus. Again Nautilus crashed after the warning.

Finally, I moved the file through the console.

But since this episode, the contents of the folder has "disappeared".
There are still five files that are listed through Nautilus but with a zero-byte size!!!

And if I try to list the contents from a console, I get this:
ghislain@Djibix:~$ ls -l Destination_folder/
total 0
?--------- ? ? ? ?                ? Destination_folder/file1
?--------- ? ? ? ?                ? Destination_folder/file2
?--------- ? ? ? ?                ? Destination_folder/file3
?--------- ? ? ? ?                ? Destination_folder/file4
?--------- ? ? ? ?                ? Destination_folder/file5

Then, if I want to go in Destination_folder, I have :
ghislain@Djibix:~$ cd Destination_folder/
bash: cd: Destination_folder/: Acces denied (translated from french)

But if I check the rights:

ghislain@Djibix:~$ ls -l
drw-rw-rw- 2 ghislain ghislain    4096 2006-07-13 23:37 Destination_folder

I use Dapper 6.06 and Nautilus 2.14.1.


If anybody has an idea or a suggestion, it will be greatly appreciated here! ](*,) 

Thanx in advance,
Djibi

---

### Post by Miguel on 2006-07-17
Hi Xdjibi,

To open folders you **also** need execute permissions. You could try "chmod 755 Destination_folder/". This might be what's giving you troubles.

Hope it helps,

Miguel

---

### Post by loserboy on 2006-07-31
heh, you helped me too, nautilus was screwing up on me and i did the reconfigure command....thanks

---

