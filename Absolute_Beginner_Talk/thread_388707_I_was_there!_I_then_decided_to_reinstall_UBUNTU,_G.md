---
title: "I was there! I then decided to reinstall UBUNTU, GRUB Error now.."
date: 2007-03-19
forum: Absolute Beginner Talk
---

### Post by Jamshedk on 2007-03-19
So.... I saw the promise land and now it has been taken away and bitter I am!!

I had everything up and running but when I installed NVIDIA drivers using ENVY my 3945 wireless adapter always disappeared.  I fixed it once by doing the restriced modules install but when I installed NVIDIA drivers with envy again it dissapeard and I couldnt bring it back....  plus I buggered a bunch of things.  

So I decided to just start from scractch...  I did an fdisk /mbr to get rud of grub and windows booted like normal... so I have tried the install 3 times now and I get this same darn error every single time... what am I doing wrong?  thanks guys...

[PHP]
We're sorry; the installer crashed. Please file a new bug report at https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug (do not attach your details to any existing bug) and a developer will attend to the problem as soon as possible. To help the developers understand what went wrong, include the following detail in your bug report, and attach the files /var/log/syslog and /var/log/partman:

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
  File "/usr/share/ubiquity/install.py", line 385, in run
    self.configure_bootloader()
  File "/usr/share/ubiquity/install.py", line 1163, in configure_bootloader
    raise InstallStepError(
InstallStepError: GrubInstaller failed with code 127
[/PHP]

---

### Post by Jamshedk on 2007-03-19
hmm this is probably not the right solution but

fdisk /mbr did not work

so I popped in a windows install disc and setup an install which added vistas bootmanager which suprisingly isnt the same as NTLDR which has been used since windows NT 3.51 back around 1997....


anyways its fixed thanks guys!

---

