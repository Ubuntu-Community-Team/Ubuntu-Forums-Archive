---
title: "HellaNZB making Root Access Permission Directories?!"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by wedge421 on 2007-02-14
I jsut upgraded to Edgy and am in the process of finishing all my reinstalls.  I got HellaNZB up and running but its doing something very strage.  When it is done processing all of the files I downloaded it is putting them in the proper directory but it is making them so that they can only be deleted with root access. Any idea what could be doing this and why? I also noticed that Hella will only start if I do it with a sudo command. Any help would be appreciated.

Chris

---

### Post by steve.horsley on 2007-02-14
The first question is easy. The sudo command runs things using root's id and therefore root's privileges. Since it is running as root, it is saving the files as being owned by root, which is why mere mortals can't delete them.

As for why it only runs as root in the first place, I have no idea. Try launching it from a command line and see if it spits out any useful error messages that might give you a clue.

---

### Post by wedge421 on 2007-02-14
This is the output im getting in the terminal. Looks like a permission issue.

> An unexpected problem occurred, exiting: IOError: [Errno 13] Permission denied: '/var/tmp/hellanzb.log'
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/Hellanzb/Core.py", line 450, in main
    init(options)
  File "/usr/lib/python2.4/site-packages/Hellanzb/Core.py", line 261, in init
    Hellanzb.Logging.initLogFile(logFile = logFile, debugLogFile = debugLogFile)
  File "/usr/lib/python2.4/site-packages/Hellanzb/Logging.py", line 506, in initLogFile
    backupCount = backupCount)
  File "logging/handlers.py", line 109, in __init__
  File "logging/handlers.py", line 61, in __init__
  File "logging/__init__.py", line 757, in __init__
IOError: [Errno 13] Permission denied: '/var/tmp/hellanzb.log'

Traceback (most recent call last):
  File "/usr/bin/hellanzb.py", line 20, in ?
    main()
  File "/usr/lib/python2.4/site-packages/Hellanzb/Core.py", line 450, in main
    init(options)
  File "/usr/lib/python2.4/site-packages/Hellanzb/Core.py", line 261, in init
    Hellanzb.Logging.initLogFile(logFile = logFile, debugLogFile = debugLogFile)
  File "/usr/lib/python2.4/site-packages/Hellanzb/Logging.py", line 506, in initLogFile
    backupCount = backupCount)
  File "logging/handlers.py", line 109, in __init__
  File "logging/handlers.py", line 61, in __init__
  File "/usr/lib/python2.4/site-packages/PIL/__init__.py", line 757, in __init__
    
IOError: [Errno 13] Permission denied: '/var/tmp/hellanzb.log'


---

### Post by steve.horsley on 2007-02-15
So the problem is that you don't have permission to create or overwrite /var/tmp/hellanzb.log. That's odd. Have a look and see if it already exists and if so, who owns it. 
**ls -l /var/tmp/hellanzb.log**
If it's here and owned by someone else, you could change it to being owned by yourself:
**sudo chown MyUserName /var/tmp/hellanzb.log**

If it's not there, check your permissions in that directory. You could try and create the file from the command line:
**touch /var/tmp/hellanzb.log**

---

