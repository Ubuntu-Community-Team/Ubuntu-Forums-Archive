---
title: "Install of 6.06 LTS crashes Compaq nx9010"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by Andred on 2006-12-28
Hi Guys
Please help. I am trying to get an HP/Compaq nx9010 loaded. (my first install)](*,) 

File "/usr/bin/ubiquity" Line 130 in ? install (sys.argv[1])
File "/usr/bin/ubiquity/". Line 55 in Install, ret = Wizard Run()
File "/usr/lib/python2.4/site packages/ubiquity/forntend/gtkui.py" Line 264, in run self.progress_loop()
File "/usr/lib/python2.4/site packages/ubiquity/forntend/gtkui.py" Line 538, in progress_loop raise RuntimeError
Run Time Error: Install failed with Exit Code 1: see /var/log/installer/syslog and /var/log/syslog

Entered User Name and Password, Selected Time zone and corrected the time.

System was working, got the email, browser, etc working. Applications worked, but had issues with the CPU going 100% and seeming to overheat.

I have tried booting with (F6 options)
pci=noacpi Failed the same place but USB mouse did not work. System not working afterwards.

and 

noapic nolapic (Failed to complete, power management failed to shut down, CPU whent to 97.7 aith no active process on Device Manager).

Funny enough the Live CD (no changes) seems to run fine, although there are a few "Failures" in the Boot sequence on the screen.

If I had to guess then the power management seems to be the issue.

Tried to download the "339 Fixes" but the Power management fix keeps failing with a missing new line (see my other posts). [My  other Post]("http://www.ubuntuforums.org/showthread.php?p=1932335#post1932335")

Regards
Andre

---

### Post by 3rdalbum on 2006-12-28
My advice would be to try downloading and burning the Alternate CD. The installer on that has had years and years of testing behind it, and it's very reliable.

Otherwise, you could have a look at the file "/var/log/installer/syslog" after an installer crash to find if there's anything you can do: (post any relevent lines here)

Type this into a terminal:
```
nano /var/log/install/syslog
```

---

### Post by Andred on 2006-12-28
Ubiquity 1.0.12
Thu, 28 Dec 2006 19:19:08 INFO     switched to page stepLanguage
ubiquity: Starting up '['/usr/lib/ubiquity/localechooser/localechooser']' for ubiquity.components.language.Language
ubiquity: Watching for question patterns ^languagechooser/language-name
Thu, 28 Dec 2006 19:19:13 INFO     Step_before = stepLanguage
Thu, 28 Dec 2006 19:19:15 INFO     switched to page stepLocation
Thu, 28 Dec 2006 19:19:15 INFO     Step_after = stepLocation
ubiquity: Starting up '['/usr/share/ubiquity/tzsetup']' for ubiquity.components.timezone.Timezone
ubiquity: Watching for question patterns ^time/zone$
Thu, 28 Dec 2006 19:19:26 INFO     Step_before = stepLocation
Thu, 28 Dec 2006 19:19:26 INFO     switched to page stepKeyboardConf
Thu, 28 Dec 2006 19:19:26 INFO     Step_after = stepKeyboardConf
ubiquity: kbd-chooser prepare
ubiquity: Starting up '['/bin/sh', '-c', '. /usr/share/debconf/confmodule; exec /usr/lib/ubiquity/kbd-chooser/kbd-chooser']' for ubiquity.components.kbd_chooser.KbdChooser
ubiquity: Watching for question patterns ^kbd-chooser/method$, ^console-keymaps.*/keymap$, ERROR
ubiquity: apply_keyboard: us
ubiquity: apply_keyboard: layout us, model pc104
ubiquity: Display map: {u'Swedish': u'se-latin1', u'Icelandic': u'is-latin1', u'Estonian': u'et', u'Romanian': u'ro', u'Italian': u'it', u'Latin American': u'la-latin1', u'Dutch': u'nl', u'Brazilian (EUA layout)': u'br-latin1', u'Belgian': u'be2-latin1', u'Danish': u'dk-latin1', u'Bulgarian': u'bg', u'Turkish (F layout)': u'trfu', u'Hungarian': u'hu', u'Macedonian': u'mk', u'Lithuanian': u'lt', u'French': u'fr-latin9', u'Norwegian': u'no-latin1', u'Slovakian': u'sk-qwerty', u'Russian': u'ru', u'Dvorak': u'dvorak', u'Slovene': u'slovene', u'Finnish': u'fi-latin1', u'British English': u'uk', u'Spanish': u'es', u'Greek': u'gr', u'Canadian French': u'cf', u'Latvian': u'lv-latin4', u'American English': u'us', u'Croatian': u'croat', u'Portuguese': u'pt-latin1', u'Czech': u'cz-lat2', u'Ukrainian': u'ua', u'Japanese': u'jp106', u'Belarusian': u'by', u'Turkish (Q layout)': u'trqu', u'German': u'de-latin1-nodeadkeys', u'Hebrew': u'hebrew', u'Polish': u'pl', u'Brazilian (ABNT2 layout)': u'br-abnt2', u'Swiss French': u'fr_CH-latin1', u'Swiss German': u'sg-latin1', u'Serbian (Cyrillic)': u'sr-cy'}
ubiquity: Untranslated choices: [u'by', u'bg', u'croat', u'cz-lat2', u'sg-latin1', u'de-latin1-nodeadkeys', u'dk-latin1', u'us', u'uk', u'dvorak', u'et', u'es', u'la-latin1', u'fi-latin1', u'fr-latin9', u'be2-latin1', u'cf', u'fr_CH-latin1', u'gr', u'hebrew', u'hu', u'is-latin1', u'it', u'lt', u'lv-latin4', u'jp106', u'mk', u'no-latin1', u'nl', u'pl', u'pt-latin1', u'br-abnt2', u'br-latin1', u'ro', u'ru', u'sk-qwerty', u'slovene', u'sr-cy', u'se-latin1', u'trfu', u'trqu', u'ua']
ubiquity: Choices: [u'Belarusian', u'Bulgarian', u'Croatian', u'Czech', u'Swiss German', u'German', u'Danish', u'American English', u'British English', u'Dvorak', u'Estonian', u'Spanish', u'Latin American', u'Finnish', u'French', u'Belgian', u'Canadian French', u'Swiss French', u'Greek', u'Hebrew', u'Hungarian', u'Icelandic', u'Italian', u'Lithuanian', u'Latvian', u'Japanese', u'Macedonian', u'Norwegian', u'Dutch', u'Polish', u'Portuguese', u'Brazilian (ABNT2 layout)', u'Brazilian (EUA layout)', u'Romanian', u'Russian', u'Slovakian', u'Slovene', u'Serbian (Cyrillic)', u'Swedish', u'Turkish (F layout)', u'Turkish (Q layout)', u'Ukrainian']
ubiquity: console-keymaps-at/keymap db: us
Thu, 28 Dec 2006 19:19:32 INFO     Step_before = stepKeyboardConf
Thu, 28 Dec 2006 19:19:32 INFO     switched to page stepUserInfo
Thu, 28 Dec 2006 19:19:32 INFO     Step_after = stepUserInfo
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
Thu, 28 Dec 2006 19:20:01 INFO     Step_before = stepUserInfo
Thu, 28 Dec 2006 19:20:01 INFO     switched to page stepPartDisk
Thu, 28 Dec 2006 19:20:01 INFO     Step_after = stepPartDisk
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
Thu, 28 Dec 2006 19:20:10 INFO     switched to page stepPartAuto
/lib/partman/recipes.sh: line 31: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 31: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 31: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 31: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
/lib/partman/recipes.sh: line 114: local: `-': not a valid identifier
Thu, 28 Dec 2006 19:20:19 INFO     switched to page stepReady
ubiquity: Starting up '['/usr/share/ubiquity/summary']' for ubiquity.components.summary.Summary
ubiquity: Watching for question patterns ^ubiquity/summary$
swapon: /dev/hda5: Device or resource busy
swapon: /dev/hda5: Device or resource busy
swapon: /dev/hda5: Device or resource busy
swapon: /dev/hda5: Device or resource busy
umount /target/
swapoff /dev/hda5
**chroot: cannot run command `apt-get': No such file or directory**
Thu, 28 Dec 2006 19:19:45 INFO     progress_loop()
ubiquity: Starting up '['/usr/share/ubiquity/install.py']' for ubiquity.components.install.Install
ubiquity: Watching for question patterns ^.*/apt-install-failed$, CAPB, ERROR, PROGRESS
/[B]usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)[/B]
Traceback (most recent call last):
  File "/usr/share/ubiquity/install.py", line 1185, in ?
    if Install().run():
  File "/usr/share/ubiquity/install.py", line 212, in run
    if not self.copy_all():
  File "/usr/share/ubiquity/install.py", line 375, in copy_all
    st = os.lstat(sourcepath)
**OSError: [Errno 2] No such file or directory: '/rofs/usr/share/keymaps'**
ubiquity: ['/usr/share/ubiquity/install.py'] exited with code 1
Exception in GTK frontend (invoking crash handler):
Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 130, in ?
    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 55, in install
    ret = wizard.run()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 264, in run
    self.progress_loop()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 538, in progress_loop
    raise RuntimeError, ("Install failed with exit code %s; see "
RuntimeError: Install failed with exit code 1; see /var/log/installer/syslog and /var/log/syslog

---

### Post by nevernamed on 2007-01-06
I have the exact same problem. Have you figured out the answer and if so what did you do? I filed a bug report but I have no idea how long they will take to get back to me. Any help would be greatly appreciated. Thanks.

---

### Post by maniacmusician on 2007-01-06
I also recommend using the alternate install CD. It's faster, and more reliable at the same time. The interface is largely similar to ubiquity's, just in text mode. It's not any more complicated, just a lot more stable.

---

