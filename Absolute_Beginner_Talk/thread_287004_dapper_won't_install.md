---
title: "dapper won't install"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by Uolirod on 2006-10-28
I am trying to install Dapper on one of my boxes.  It's an AMD Athlon 64 3000 on an Abit KV8 Pro. I have an ATI 9250 video card(AGP) installed and 2 hard drives, one is SATA with Windows XP installed on the first partition, the other is an IDE drive with 2 EXT3 partions installed.  I'm trying to install Dapper on a partition on the SATA drive and the partitioner has created root, home and swap partitions but the installer crashes before completing the install.  I've tried both the desktop and the alternate install cds and other than it being a hardware problem I don't know what it could be.  I've looked around and it looks like it could be a problem with my video card but I don't have another to swap out.  Any insights would be greatly appreciated.  I've also had problems with other applications crashing while running the LiveCD.

---

### Post by Uolirod on 2006-10-28
This is the most recent error message.

```
Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 130, in ?
    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 55, in install
    ret = wizard.run()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 266, in run
    self.process_step()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 741, in process_step
    self.mountpoints_to_summary()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 1029, in mountpoints_to_summary
    self.progress_loop()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 538, in progress_loop
    raise RuntimeError, ("Install failed with exit code %s; see "
RuntimeError: Install failed with exit code -11; see /var/log/installer/syslog and /var/log/syslog
```

And this is the contents of /var/log/installer/syslog(there was no /var/log/syslog)


```
Ubiquity 1.0.12
Ubiquity 1.0.12
Ubiquity 1.0.12
Ubiquity 1.0.12
Ubiquity 1.0.12
Ubiquity 1.0.12
Ubiquity 1.0.12
Ubiquity 1.0.12
Ubiquity 1.0.12
Sat, 28 Oct 2006 11:26:31 INFO     switched to page stepLanguage
ubiquity: Starting up '['/usr/lib/ubiquity/localechooser/localechooser']' for ubiquity.components.language.Language
ubiquity: Watching for question patterns ^languagechooser/language-name
Sat, 28 Oct 2006 11:26:34 INFO     Step_before = stepLanguage
Sat, 28 Oct 2006 11:26:35 INFO     switched to page stepLocation
Sat, 28 Oct 2006 11:26:35 INFO     Step_after = stepLocation
ubiquity: Starting up '['/usr/share/ubiquity/tzsetup']' for ubiquity.components.timezone.Timezone
ubiquity: Watching for question patterns ^time/zone$
Sat, 28 Oct 2006 11:26:41 INFO     Step_before = stepLocation
Sat, 28 Oct 2006 11:26:41 INFO     switched to page stepKeyboardConf
Sat, 28 Oct 2006 11:26:41 INFO     Step_after = stepKeyboardConf
ubiquity: kbd-chooser prepare
ubiquity: Starting up '['/bin/sh', '-c', '. /usr/share/debconf/confmodule; exec /usr/lib/ubiquity/kbd-chooser/kbd-chooser']' for ubiquity.components.kbd_chooser.KbdChooser
ubiquity: Watching for question patterns ^kbd-chooser/method$, ^console-keymaps.*/keymap$, ERROR
ubiquity: apply_keyboard: us
ubiquity: apply_keyboard: layout us, model pc104
ubiquity: Display map: {u'Swedish': u'se-latin1', u'Icelandic': u'is-latin1', u'Estonian': u'et', u'Romanian': u'ro', u'Italian': u'it', u'Latin American': u'la-latin1', u'Dutch': u'nl', u'Brazilian (EUA layout)': u'br-latin1', u'Belgian': u'be2-latin1', u'Danish': u'dk-latin1', u'Bulgarian': u'bg', u'Turkish (F layout)': u'trfu', u'Hungarian': u'hu', u'Macedonian': u'mk', u'Lithuanian': u'lt', u'French': u'fr-latin9', u'Norwegian': u'no-latin1', u'Slovakian': u'sk-qwerty', u'Russian': u'ru', u'Dvorak': u'dvorak', u'Slovene': u'slovene', u'Finnish': u'fi-latin1', u'British English': u'uk', u'Spanish': u'es', u'Greek': u'gr', u'Canadian French': u'cf', u'Latvian': u'lv-latin4', u'American English': u'us', u'Croatian': u'croat', u'Portuguese': u'pt-latin1', u'Czech': u'cz-lat2', u'Ukrainian': u'ua', u'Japanese': u'jp106', u'Belarusian': u'by', u'Turkish (Q layout)': u'trqu', u'German': u'de-latin1-nodeadkeys', u'Hebrew': u'hebrew', u'Polish': u'pl', u'Brazilian (ABNT2 layout)': u'br-abnt2', u'Swiss French': u'fr_CH-latin1', u'Swiss German': u'sg-latin1', u'Serbian (Cyrillic)': u'sr-cy'}
ubiquity: Untranslated choices: [u'by', u'bg', u'croat', u'cz-lat2', u'sg-latin1', u'de-latin1-nodeadkeys', u'dk-latin1', u'us', u'uk', u'dvorak', u'et', u'es', u'la-latin1', u'fi-latin1', u'fr-latin9', u'be2-latin1', u'cf', u'fr_CH-latin1', u'gr', u'hebrew', u'hu', u'is-latin1', u'it', u'lt', u'lv-latin4', u'jp106', u'mk', u'no-latin1', u'nl', u'pl', u'pt-latin1', u'br-abnt2', u'br-latin1', u'ro', u'ru', u'sk-qwerty', u'slovene', u'sr-cy', u'se-latin1', u'trfu', u'trqu', u'ua']
ubiquity: Choices: [u'Belarusian', u'Bulgarian', u'Croatian', u'Czech', u'Swiss German', u'German', u'Danish', u'American English', u'British English', u'Dvorak', u'Estonian', u'Spanish', u'Latin American', u'Finnish', u'French', u'Belgian', u'Canadian French', u'Swiss French', u'Greek', u'Hebrew', u'Hungarian', u'Icelandic', u'Italian', u'Lithuanian', u'Latvian', u'Japanese', u'Macedonian', u'Norwegian', u'Dutch', u'Polish', u'Portuguese', u'Brazilian (ABNT2 layout)', u'Brazilian (EUA layout)', u'Romanian', u'Russian', u'Slovakian', u'Slovene', u'Serbian (Cyrillic)', u'Swedish', u'Turkish (F layout)', u'Turkish (Q layout)', u'Ukrainian']
ubiquity: console-keymaps-at/keymap db: us
Sat, 28 Oct 2006 11:26:44 INFO     Step_before = stepKeyboardConf
Sat, 28 Oct 2006 11:26:44 INFO     switched to page stepUserInfo
Sat, 28 Oct 2006 11:26:44 INFO     Step_after = stepUserInfo
ubiquity: Starting up '['/usr/lib/ubiquity/user-setup/user-setup-ask', '/target']' for ubiquity.components.usersetup.UserSetup
ubiquity: Watching for question patterns ^passwd/user-fullname$, ^passwd/username$, ^passwd/user-password$, ^passwd/user-password-again$, ERROR
ON STATE: 1
ON STATE: 2
ON STATE: 3
ON STATE: 4
ON STATE: 5
ON STATE: 6
ON STATE: 7
ON STATE: 8
Sat, 28 Oct 2006 11:27:07 INFO     Step_before = stepUserInfo
Sat, 28 Oct 2006 11:27:07 INFO     switched to page stepPartDisk
Sat, 28 Oct 2006 11:27:07 INFO     Step_after = stepPartDisk
ubiquity: Starting up '/bin/partman' for ubiquity.components.partman.Partman
ubiquity: Watching for question patterns ^partman-auto/select_disk$, ^partman-auto/.*automatically_partition$, ^partman-partitioning/new_size$, ^partman/choose_partition$, ^partman/confirm.*, type:boolean, ERROR, PROGRESS
unsupported
kernelmodules_basicfilesystems
kernelmodules_ext3
kernelmodules_jfs
kernelmodules_reiserfs
kernelmodules_xfs
umount_target
parted
dump
update_partitions
filesystems_detected
auto_mountpoints
autouse_swap
backup
Sat, 28 Oct 2006 11:27:18 INFO     switched to page stepPartAuto
ubiquity: /bin/partman exited with code 10
Sat, 28 Oct 2006 11:27:22 INFO     Step_before = stepPartAuto
Sat, 28 Oct 2006 11:27:22 INFO     gparted_loop()
Sat, 28 Oct 2006 11:27:22 INFO     Disabling swap on /dev/sda5
Sat, 28 Oct 2006 11:27:22 INFO     switched to page stepPartAdvanced
Sat, 28 Oct 2006 11:27:22 INFO     Step_after = stepPartAdvanced
Error reading inode 2080.
Error reading inode 2129.
Error reading inode 2392.
Error reading inode 3536.
Error reading inode 4062.
Error reading inode 4079.
Error reading inode 4080.
Error reading inode 4695.
Error reading inode 4699.
Error reading inode 4858.
Error reading inode 5411.
Error reading inode 10384.
Error reading inode 10563.
Error reading inode 10683.
Error reading inode 15554.
Error reading inode 16054.
Error reading inode 16921.
Error reading inode 17479.
Error reading inode 17847.
Error reading inode 18290.
Error reading inode 19301.
Error reading inode 20765.
Error reading inode 24107.
Error reading inode 26642.
Error reading inode 26937.
Error reading inode 26940.
Error reading inode 26994.
Error reading inode 26996.
Error reading inode 27000.
Error reading inode 27001.
Error reading inode 27003.
Error reading inode 27004.
Error reading inode 27007.
Error reading inode 27010.
Error reading inode 27014.
Error reading inode 27015.
Error reading inode 27146.
Error reading inode 27148.
Error reading inode 27151.
Error reading inode 27152.
Error reading inode 27153.
Error reading inode 27155.
Error reading inode 27157.
Error reading inode 27159.
Error reading inode 27160.
Error reading inode 27163.
Error reading inode 27164.
Error reading inode 27165.
Error reading inode 27166.
Error reading inode 27167.
Error reading inode 27168.
Error reading inode 27170.
Error reading inode 27171.
Error reading inode 27842.
Error reading inode 32663.
Error reading inode 35440.
Error reading inode 35467.
Error reading inode 35472.
Error reading inode 39433.
Error reading inode 40302.
Error reading inode 44756.
Error reading inode 44882.
Error reading inode 44884.
Error reading inode 44886.
Error reading inode 44895.
Error reading inode 44907.
Error reading inode 44977.
Error reading inode 51172.
dumpe2fs 1.38 (30-Jun-2005)
dumpe2fs 1.38 (30-Jun-2005)
dumpe2fs 1.38 (30-Jun-2005)
dumpe2fs 1.38 (30-Jun-2005)
Warning: Unable to open /dev/hdc read-write (Read-only file system).  /dev/hdc has been opened read-only.
Error: Unable to open /dev/hdc - unrecognised disk label.
Sat, 28 Oct 2006 11:28:00 INFO     Step_before = stepPartAdvanced
Sat, 28 Oct 2006 11:28:01 INFO     switched to page stepPartMountpoints
Sat, 28 Oct 2006 11:28:01 INFO     Step_after = stepPartMountpoints
Sat, 28 Oct 2006 11:28:38 INFO     Step_before = stepPartMountpoints
Sat, 28 Oct 2006 11:28:38 INFO     mountpoints: {'/dev/hda1': ('/media/hda1', False, None), '/dev/hda2': ('/media/hda2', False, None), '/dev/sda4': ('/home', True, None), '/dev/sda5': ('swap', True, None), '/dev/sda1': ('/media/sda1', False, None), '/dev/sda2': ('/', True, None)}
ubiquity: Starting up '/bin/partman' for ubiquity.components.partman_commit.PartmanCommit
ubiquity: Watching for question patterns ^partman/choose_partition$, ^partman/confirm.*, type:boolean, ERROR, PROGRESS
mkdir: cannot create directory `/var/lib/partman': File exists
unsupported
kernelmodules_basicfilesystems
kernelmodules_ext3
kernelmodules_jfs
kernelmodules_reiserfs
kernelmodules_xfs
umount_target
parted
dump
update_partitions
filesystems_detected
auto_mountpoints
autouse_swap
backup
Sat, 28 Oct 2006 11:28:46 INFO     switched to page stepReady
ubiquity: Starting up '['/usr/share/ubiquity/summary']' for ubiquity.components.summary.Summary
ubiquity: Watching for question patterns ^ubiquity/summary$
swapon: /dev/sda5: Device or resource busy
swapon: /dev/sda5: Device or resource busy
swapon: /dev/sda5: Device or resource busy
swapon: /dev/sda5: Device or resource busy
umount /target/
umount /target/home
swapoff /dev/sda5
chroot: cannot run command `apt-get': No such file or directory
chroot: cannot run command `apt-get': No such file or directory
Sat, 28 Oct 2006 11:30:28 INFO     progress_loop()
ubiquity: Starting up '['/usr/share/ubiquity/install.py']' for ubiquity.components.install.Install
ubiquity: Watching for question patterns ^.*/apt-install-failed$, CAPB, ERROR, PROGRESS
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
ubiquity: ['/usr/share/ubiquity/install.py'] exited with code -11
Exception in GTK frontend (invoking crash handler):
Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 130, in ?
    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 55, in install
    ret = wizard.run()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 266, in run
    self.process_step()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 741, in process_step
    self.mountpoints_to_summary()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 1029, in mountpoints_to_summary
    self.progress_loop()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 538, in progress_loop
    raise RuntimeError, ("Install failed with exit code %s; see "
RuntimeError: Install failed with exit code -11; see /var/log/installer/syslog and /var/log/syslog
```

---

### Post by Uolirod on 2006-10-28
Bump?

---

### Post by lofgren on 2006-11-04
Hey!

Sorry this isn't help :(

*I get the same problem*     Similar hardware!!!
AMD3000 sempron processor
Sapphire Radeon 9250 Pro
Asus K8V-MX motherboard
1GB Ram

I tried several times with Dapper and finally got it installed.
Applications crash randomly as you describe. Same deal with live CD itself.
I ran the CD check which came up fine. I also ran memtest which turned up no errors.

I have Windows XP installed on hda1 - and it works fine.
I did have Debian Sid installed on the ubuntu target partition (which has now been deleted and formatted several times) - and it worked fine.

I gave up on the live CD and went to look for the alternate CD - Edgy had just been released.

I tried the Edgy 6.10 Ubuntu live CD - and it crashed once or twice before installing. However, once installed, apps crashed randomly.

I thought (seeing as they were gnome apps crashing) that Kubuntu might be more stable. Suggestions on the forum had suggested it might have been the video driver.. I also thought that perhaps something was dying during the install if it was the video driver causing issues.

I went back to the download site and got the Kubuntu 6.10 Alternate CD.
It installed without issue via the text based installer.

I still got random crashes.

So I started working on the video driver.

I went for the latest ubuntu fglrx driver package without joy.
I started looking for issues/posts related to my video card specifically and found a link to installing "radeon" drivers.
After removing the fglrx drivers properly, I got the radeon one to work.

Unfortunately, I can't report that it was more stable.

In fact, running the console via Alt-F1 or Ctrl-Alt-F1 (and "sudo killall kdm") I received Segmentation Faults when I did "sudo apt-get update" 5 out of 10 times.

I found a few posts that discussed ATI drivers.. several people have "read somewhere that they stoped support for ATI 9200 drivers in Edgy".

So.. this evening I decided to have another go at installing Dapper.. But I can't actually get it to install this time, getting: ***RuntimeError: Install failed with exit code -11***

I have posted at launchpad.net, noting we have similar hardware. Hopefully it's a known bug.

Matt

---

### Post by Uolirod on 2006-11-04
For me I think the issue was that I had it overclocked and even though memtest ran without errors and in general the overclock appeared stable once I clocked it back I got it to install fine.  I have had problems with ATI drivers and the RADEON 9250 though.  I was trying to install beryl and everything I've read says that you need fglrx to really run it properly but I can't get direct rendering to work with this card.  I have another older box with an Nvidia card in it that Beryl seems to work fine in.  I'm thinking of buying an Nvidia card for this box too.  Good luck.

---

### Post by Ilyvm on 2006-11-21
I have the same problem BUT my PC description is:

Processor Intel Pentium D 820 2.8Ghz 2Mb Cache
MainBoard Intel 945GZis
RAM Memory 512 DDR2
HDD Seagate 80Gb SATA2 7200rpm
Video Card nVidia 7300LE

I take a picture of the problem, you can see it here:
[http://img288.imageshack.us/my.php?image=pantallazowr7.png](http://img288.imageshack.us/my.php?image=pantallazowr7.png)

Thank you!

---

### Post by Uolirod on 2006-11-21
I finally broke down and bought an Nvidia 6200LE and just installed Edgy 64bit. It runs fine and I installed the Nvidia drivers with Automatix and direct rendering works now but I'm kind of paranoid about installing Beryl and maybe screwing everything up again.  Sorry I can't offer any insights into the Dapper problem.

---

