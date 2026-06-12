---
title: "Help with hellanzb"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by jba6511 on 2007-05-25
I was able to install and configure this once before but ran into troubles this time around.

Here is the output:

blake@Ubuntu-Desktop:~$ hellanzb.py
An unexpected problem occurred, exiting: IOError'>: [Errno 13] Permission denied: '/var/tmp/hellanzb.log'
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/Hellanzb/Core.py", line 530, in main
    init(options)
  File "/usr/lib/python2.5/site-packages/Hellanzb/Core.py", line 326, in init
    Hellanzb.Logging.initLogFile(logFile = logFile, debugLogFile = debugLogFile)
  File "/usr/lib/python2.5/site-packages/Hellanzb/Logging.py", line 540, in initLogFile
    backupCount = backupCount)
  File "logging/handlers.py", line 109, in __init__
  File "logging/handlers.py", line 61, in __init__
  File "logging/__init__.py", line 770, in __init__
IOError: [Errno 13] Permission denied: '/var/tmp/hellanzb.log'

Traceback (most recent call last):
  File "/usr/bin/hellanzb.py", line 20, in <module>
    main()
  File "/usr/lib/python2.5/site-packages/Hellanzb/Core.py", line 530, in main
    init(options)
  File "/usr/lib/python2.5/site-packages/Hellanzb/Core.py", line 326, in init
    Hellanzb.Logging.initLogFile(logFile = logFile, debugLogFile = debugLogFile)
  File "/usr/lib/python2.5/site-packages/Hellanzb/Logging.py", line 540, in initLogFile
    backupCount = backupCount)
  File "logging/handlers.py", line 109, in __init__
  File "logging/handlers.py", line 61, in __init__
  File "logging/__init__.py", line 770, in __init__
IOError: [Errno 13] Permission denied: '/var/tmp/hellanzb.log'

Was not getting this error before I configure the hellanzb.conf file. Any idea how to restore it or uninstall hellanzb and start again?

---

### Post by jba6511 on 2007-05-25
nevermind works when I use sudo hellanzb.py

---

### Post by jba6511 on 2007-05-25
i can not drag nzbs into the queue folder. Says i do not have permission. Any way to allow permission to the folder the dir structure is /home/blake/daemon.queue

Says the owner is root. Can i change this to be me?

---

### Post by fearevilleet on 2007-05-25
Try right clicking on the que folder the go to permissions. Make sure you have read/write access for this folder. If that dose not work you can always copy the nzb files via a cli interface using SUDO.

One thing I noticed about running hellanzb as sudo is I can not delete the files because I do not have the correct permissions. In order to delete the files from the completed directory I need to do it from a cli interface a a SU.

Hope this helps, I just got hellanzb to work, and I must say it is a really great app!

---

### Post by jba6511 on 2007-05-25
I tried right clicking and changing the permissions but because the owner is root i all the options are greyed out. Is there anyway to change permissions from the terminal as root and how do I copy files into the directory via terminal (nzb files of course). I do not know what I did to install as root because I do not have this issue using it on my laptop.

---

### Post by robertpolson on 2007-05-25
"sudo chown username /folder/name/"

Try this or sudo chwon 777 /folder/name

Make sure to refresh the folder after for changes to take effect.

---

### Post by jba6511 on 2007-05-25
thanks. that worked like a charm.

---

### Post by robertpolson on 2007-05-25
Got here [http://ubuntuforums.org/showthread.php?t=169749&page=16&highlight=hellanzb](http://ubuntuforums.org/showthread.php?t=169749&page=16&highlight=hellanzb)

---

