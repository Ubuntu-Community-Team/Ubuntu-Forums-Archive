---
title: "Opening a program in the terminal"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by racso39 on 2007-06-20
Hi, I want to open the Update Manager in the terminal, how is that done?

---

### Post by lamalex on 2007-06-20
you could do ```
sudo apt-get upgrade
or
sudo apt-get dist-upgrade
```
which would accomplish pretty much the same thing. 
but if you really want the update manager program do
```

gksudo update-manager
```

---

### Post by racso39 on 2007-06-20
The reason I wanted to open the Update Manager via terminal is because couldn't do it via System/Administration, i wanted to see the error, here is the copy paste:

guille@Hogar1-Ubuntu:~$ gksudo update-manager
warning: could not initiate dbus
  File "/usr/lib/python2.5/site-packages/UpdateManager/UpdateManager.py", line 664, in activate_details
    True)
RuntimeError: more keyword list entries than argument specifiers
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 90, in <module>
    app = UpdateManager(data_dir)
  File "/usr/lib/python2.5/site-packages/UpdateManager/UpdateManager.py", line 376, in __init__
    self.restore_state()
  File "/usr/lib/python2.5/site-packages/UpdateManager/UpdateManager.py", line 812, in restore_state
    True)
RuntimeError: more keyword list entries than argument specifiers
guille@Hogar1-Ubuntu:~$ 


How can I fix this?

PS: If I use the first 2 codes, I can see I am up-to-date

---

### Post by dannyboy79 on 2007-06-20
this has been discussed here: [http://ubuntuforums.org/showthread.php?t=470654&highlight=warning%3A+could+dbus](http://ubuntuforums.org/showthread.php?t=470654&highlight=warning%3A+could+dbus)

---

