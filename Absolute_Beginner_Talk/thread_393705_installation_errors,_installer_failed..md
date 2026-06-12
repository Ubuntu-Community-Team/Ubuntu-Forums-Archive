---
title: "installation errors, installer failed."
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by s2k600rr on 2007-03-26
another linux noob here

i recently ran into problems while installing ubuntu in this "new" computer that i had just put together

used to have a pentium 2 450mhz 256mb ram 12gb hdd from 1998 (and still kicking) and ubuntu installed fine on this system.

now i just put together a "newer" system (made of used parts...i'm poor), pentium 4 2.0ghz 2gb ram 160gb+40gb hdd, and now i am having trouble installing ubuntu on this system to do a dual boot (xp and ubuntu).

as the ubuntu cd boot up, and i choose the "Start or Install" option on the menu, it would attemp to load and produce this errors.

> 
[17179718.268000] hdc : ide_intr : huh? expected NULL handler on exit
[17179718.316000] Buffer I/O error on device hdc, logical block 357564

it would repeat that errors with different numbers at the beginning, this goes on for a while until the screen is filled up, im a patience guy so i just kept on waiting.

it would finally boot up after that into the main screen.

now i double click on install and goes through all the steps, setting time, username/pass, partitions...etc...and it installs...but the install was interrupted mid way with this error.

> 
We're sorry; the installer crashed. Please file a new bug report at [https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug](https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug) (do not attach your details to any existing bug) and a developer will attend to the problem as soon as possible. To help the developers understand what went wrong, include the following detail in your bug report, and attach the files /var/log/syslog and /var/log/partman:

Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 166, in ?
    main()
  File "/usr/bin/ubiquity", line 161, in main
    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 57, in install
    ret = wizard.run()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 305, in run
    self.process_step()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 856, in process_step
    self.progress_loop()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 628, in progress_loop
    raise RuntimeError, ("Install failed with exit code %s\n%s" %
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/install.py", line 1404, in ?
    install.run()
  File "/usr/share/ubiquity/install.py", line 344, in run
    self.configure_network ()
  File "/usr/share/ubiquity/install.py", line 1075, in configure_network
    shutil.copy2(path, os.path.join(self.target, path[1:]))
  File "shutil.py", line 92, in copy2
    copyfile(src, dst)
  File "shutil.py", line 52, in copyfile
    fdst.close()
IOError: [Errno 28] No space left on device


this happens multiple times when i try the installation again.

i am stumped, dont know what to do, help!

---

### Post by Stickymaddness on 2007-03-26
> **s2k600rr said:**
> 
[17179718.268000] hdc : ide_intr : huh? expected NULL handler on exit
[17179718.316000] Buffer I/O error on device hdc, logical block 357564


Those sound like hardware errors to me, are you sure your hard drive is in good condition

> **s2k600rr said:**
> IOError: [Errno 28] No space left on device

Check that you have enough free space to install ubuntu!

---

### Post by s2k600rr on 2007-03-26
> **Stickymaddness said:**
> Those sound like hardware errors to me, are you sure your hard drive is in good condition




the hdd's are used but seems to work fine, i have xp installed and havent ran into any problems.
but doesnt ubuntu load the live linux into the ram and not the hdd?


> **Stickymaddness said:**
> 


Check that you have enough free space to install ubuntu!


heres the partition size that i allocated

/ - 250mb
/usr - 5gb
/home - 10gb
swap - 1gb

that should be enough right?


thanks for the quick reply!

---

