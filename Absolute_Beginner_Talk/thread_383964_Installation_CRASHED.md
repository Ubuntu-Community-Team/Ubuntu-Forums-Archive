---
title: "Installation CRASHED"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by julie_lebou on 2007-03-13
The installation was finally working, then it crashed, this is the info:


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
  File "/usr/share/ubiquity/install.py", line 306, in run
    self.copy_all()
  File "/usr/share/ubiquity/install.py", line 484, in copy_all
    shutil.copyfile(sourcepath, targetpath)
  File "shutil.py", line 49, in copyfile
    copyfileobj(fsrc, fdst)
  File "shutil.py", line 25, in copyfileobj
    fdst.write(buf)
IOError: [Errno 28] No space left on device

---

### Post by lilchris173 on 2007-03-13
Youch thats a mouth full :-). Did you check the CD before you did the installation? Its got a handy dandy little thing so you can check the stability of the cd and ensure all the files are there and not corrupted. If that doesn't work .... VVV

"IOError: [Errno 28] No space left on device" sure sounds like you ran out of room on your Harddrive. Did you make sure the partition was roughtly 3 GB for Ubuntu to be installed on? Its smaller then Windows but its still not too tiny. Good luck! more help @ [www.theneosa.org](www.theneosa.org) if ya need it from me or one of my partners.

---

