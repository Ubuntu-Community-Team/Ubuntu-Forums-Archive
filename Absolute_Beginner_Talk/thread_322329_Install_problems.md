---
title: "Install problems"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by neolite on 2006-12-20
Okay, i'm currently running xp pro, but i also want to run Ubuntu, so i've created 2 partions one for the filesystem and another one so i go to install and i get this error:

Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 130, in ?
    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 55, in install
    ret = wizard.run()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 266, in run
    self.process_step()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 755, in process_step
    self.mountpoints_to_summary()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 1114, in mountpoints_to_summary
    self.progress_loop()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 550, in progress_loop
    raise RuntimeError, ("Install failed with exit code %s\n%s" %
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/install.py", line 1263, in ?
    if install.run():
  File "/usr/share/ubiquity/install.py", line 284, in run
    if not self.copy_all():
  File "/usr/share/ubiquity/install.py", line 469, in copy_all
    os.lchown(targetpath, st.st_uid, st.st_gid)
OSError: [Errno 30] Read-only file system: '/target/home'


I also have Acronis OS selector so i can select which OS to use, but do i need to install it before or after installing linux?

---

### Post by neolite on 2006-12-20
ANyone?

---

### Post by Bachstelze on 2006-12-20
Use an Alternate CD :)

---

### Post by neolite on 2006-12-20
Erm what do you mean by alternative CD?

---

### Post by Bachstelze on 2006-12-20
I mean "Alternate", not "Alternative". That's how Ubuntu calls the "old school" installation CDs. The installer is text-based so less pretty but also far less buggy. You can get such CDs from the same place where you downloaded your "Desktop" CD.

---

### Post by neolite on 2006-12-20
Ahh okay  thanks.

---

### Post by totfit on 2006-12-20
First let me say that I am no expert. I would try again, but instead of formatting for yourself, let the set up make your partitians for you. I assume you have windows on a partition, then make sure the remainder is free space on your drive. When you install just have the installation take up the free space on the drive and it will set the partitions for you. There should be no problems unless there are some hardware conflicts. Something that would even be easier to do would be to add a drive and use it for Ubuntu. Either way good luck. The installation is not so time consuming that you should give up. Post back any additional errors and maybe some of the experts can help. I have been running Ubuntu since the first of the year and Dapper is a significant improvement over Breezy. Don't give up.

---

### Post by neolite on 2006-12-20
WOuld anyone happen to know how long it usually takes the setup to partition the hard drive?

---

