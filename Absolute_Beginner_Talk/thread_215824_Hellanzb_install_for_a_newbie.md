---
title: "Hellanzb install for a newbie"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by lesigh on 2006-07-14
Hello everyone,

my Ubuntu install is one day old. I'm having no major problems - everything is intuitive and chock-full of good sense, shell tuts are everywhere, but I don't know a thing about python. I've never coded anything in my life, so I've been doing the hellanzb installation and config by osmosis. However, when I try to launch it, I get the following error message:

> maria@maria-desktop:~/hellanzb-0.9$ hellanzb.py
An unexpected error occurred while reading the config file: SyntaxError: invalid syntax (hellanzb.conf, line 43)
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/Hellanzb/Core.py", line 65, in loadConfig
    execfile(fileName)
  File "/home/maria/hellanzb-0.9/etc/hellanzb.conf", line 43
     antiIdle = 4.5 * 60,        # 4 minutes, 30 seconds
            ^
 SyntaxError: invalid syntax

An unexpected problem occurred, exiting: SyntaxError: invalid syntax (hellanzb.conf, line 43)
Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/Hellanzb/Core.py", line 450, in main
    init(options)
  File "/usr/lib/python2.4/site-packages/Hellanzb/Core.py", line 251, in init
    findAndLoadConfig()
  File "/usr/lib/python2.4/site-packages/Hellanzb/Core.py", line 47, in findAndLoadConfig
    if loadConfig(file):
  File "/usr/lib/python2.4/site-packages/Hellanzb/Core.py", line 65, in loadConfig
    execfile(fileName)
  File "/home/maria/hellanzb-0.9/etc/hellanzb.conf", line 43
     antiIdle = 4.5 * 60,        # 4 minutes, 30 seconds
            ^
 SyntaxError: invalid syntax

Traceback (most recent call last):
  File "/usr/bin/hellanzb.py", line 20, in ?
    main()
  File "/usr/lib/python2.4/site-packages/Hellanzb/Core.py", line 450, in main
    init(options)
  File "/usr/lib/python2.4/site-packages/Hellanzb/Core.py", line 251, in init
    findAndLoadConfig()
  File "/usr/lib/python2.4/site-packages/Hellanzb/Core.py", line 47, in findAndLoadConfig
    if loadConfig(file):
  File "/usr/lib/python2.4/site-packages/Hellanzb/Core.py", line 65, in loadConfig
    execfile(fileName)
  File "/home/maria/hellanzb-0.9/etc/hellanzb.conf", line 43
    antiIdle = 4.5 * 60,        # 4 minutes, 30 seconds
           ^
SyntaxError: invalid syntax


So I wonder: is this a "general problem" or something absolutely specific to hellanzb, in which case I'll post in the specific thread?

I'd appreciate any pointers.

---

### Post by kabus on 2006-07-14
As the error message says, there's something wrong in line 43 of your hellanzb.conf file. I am not sure what though, since mine seems to look exactly the same. 
Maybe there's something wrong with the surrounding lines, like a missing comma at the end of the line above.
For reference, here's the relevant part from my config:

```
defineServer(id = 'newshosting',
             hosts = [ 'unlimited.newshosting.com:8000' ],
             #hosts = [ 'news.changeme.com', 'morenews.changeme.com:8000' ],


             username = 'xxxxxxxxxxxx',
             password = 'xxxxxxxxxxxxx',
             #username = None,           # no auth
             #password = None,

             connections = 7,
             antiIdle = 4.5 * 60,          # 4 minutes, 30 seconds
             #bindTo = '204.31.33.7',    # connect FROM this ip address
             )
```

---

### Post by lesigh on 2006-07-15
You were absolutely right. I was missing a comma after the number of connections. Thanks for your piece of code - it runs perfectly now.

---

### Post by npkornett on 2007-07-17
I encountered this error when trying to install hellanzb. 

running install
running build
running build_py
creating build
error:  could not create 'build':  Permission denied

sure enough the /hellanzb directory is locked under another owner and superuser lacks the ability
to change any permissions.  Any help here would be greatly appreciated.

npk:confused:

---

### Post by jvc26 on 2007-07-17
Have you tried following this guide here on the forums. This is how I installed hella, and it worked fine.
[http://ubuntuforums.org/showthread.php?t=169749&highlight=hellanzb+howto](http://ubuntuforums.org/showthread.php?t=169749&highlight=hellanzb+howto)
Il

---

### Post by npkornett on 2007-07-17
Thanks for the link.  I will try again using this how-to.  I appreciate your help.

npk

---

