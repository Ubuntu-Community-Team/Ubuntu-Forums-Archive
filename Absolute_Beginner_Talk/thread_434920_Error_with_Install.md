---
title: "Error with Install"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by SexyLarajolie on 2007-05-06
I am trying to install Ubuntu 7.04 on an AMD based desktop computer with 2GB memory and using an IDE Hard Disk.

I insert the CD and boot into the live distro. I then proceed to press the Install shortcut on the desktop; the Install screen appears for a split second as a white box and then closes.

I decided to open a Terminal screen and ran the same command that the shortcut executes. The same thing happened, except the terminal screen fed this back to me:

[PHP]ubuntu@ubuntu:~$ iquonify
bash: iquonify: command not found
ubuntu@ubuntu:~$ ubiquity --desktop %k gtkui
Exception in GTK frontend (invoking crash handler):
Traceback (most recent call last):
  File "/usr/lib/ubiquity/bin/ubiquity", line 210, in <module> 
    main()
  File "/usr/lib/ubiquity/bin/ubiquity", line 205, in main
    install(args[0])
  File "/usr/lib/ubiquity/bin/ubiquity", line 58, in install
    ret = wizard.run()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 265, in run 
    self.disable_gvm()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 230, in disable_gvm
    preexec_fn=drop_privileges)
  File "subprocess.py", line 593, in __init__
    errread, errwrite) 
  File "subprocess.py", line 1135, in _execute_child
    raise child_exception
OSError: [Errno 8] Exec format error

Traceback (most recent call last):
  File "/usr/lib/ubiquity/bin/ubiquity", line 210, in <module> 
    main()
  File "/usr/lib/ubiquity/bin/ubiquity", line 205, in main
    install(args[0])
  File "/usr/lib/ubiquity/bin/ubiquity", line 58, in install
    ret = wizard.run()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 265, in run 
    self.disable_gvm()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 230, in disable_gvm
    preexec_fn=drop_privileges)
  File "/usr/lib/python2.5/subprocess.py", line 593, in __init__ 
    errread, errwrite)
  File "/usr/lib/python2.5/subprocess.py", line 1135, in _execute_child
    raise child_exception
OSError: [Errno 8] Exec format error
ubuntu@ubuntu:~$ 
[/PHP]

I don't understand what it means. I have tried using a different hard disk and I get the same error.
So instead I tried to boot using the "Install with Driver Update CD" but of course.... what update cd? 

Can someone help me please? Thank you :)

---

### Post by rfs1970 on 2007-05-06
Hi There,

Your AMD processor is 64bits?

Did you check if your CD is OK? 
(There is an option to check the integrity of your media).

If its ok and still not working,
try to install via text mode from the Alternate CD...
You can download it from :
[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

r.

---

