---
title: "Ubuntu Ultimate 1.2 on Intel Mac Mini"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by squeezy on 2007-03-12
Man, oh man, I hope this wonderful community can help me out.

I have an Intel Mac Mini, 1.66 core duo, 1GB RAM. I am having a hell of a time installing Ubuntu (dual boot). I have followed [these directions (link)]("https://help.ubuntu.com/community/MacBook") with no luck. I know its for the Macbook, but they have the same exact specs aside from the processor.

It will install up to the GRUB installation, which is when I get this error.

> Traceback (most recent call last):
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
InstallStepError: GrubInstaller failed with code 1

Here is what I think the problem is, but I could be completely wrong. When it asks me where to install GRUB (before the installation begins), default is (hd0). Well my drive is SATA, so that would make it "sda", right? It changes it to /dev/sda. I never did try "(sda)" though, only because this is day two of trying to get this to install.

If that's not it, then it could also be this terminal command..

> sudo gptsync /dev/sda && sudo sfdisk -c /dev/sda 3 83

It says to change the "3" to match the correct partition. I assume the "sda 3" three. I have tried 1, 2, and 3 in that case, each command executed like that last, asked if I want to overwrite my MBR, yes, and it completes. But I still get the GRUB error.

That's all I can figure out. Other than that, I'm clueless. Can anyone please help me?

If you need anymore information, please let me know!

---

### Post by squeezy on 2007-03-12
I hate to seem rude by bumping this. This is the fourth forum I've gone to for help, and no ones can seem to help me as of yet.

---

### Post by shirilover on 2007-03-13
Grub references hard drives differently.
hd0 refers to the first pyhsical drive even if it is SATA.
So, if the drive you want is sda, use hd0

---

### Post by bazzer on 2007-04-23
Any updates on how you got on with this? I'm doing similar atm.

---

