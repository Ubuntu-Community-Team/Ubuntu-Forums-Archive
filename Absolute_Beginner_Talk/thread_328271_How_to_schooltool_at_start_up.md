---
title: "How to schooltool at start up?"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by aabento on 2006-12-30
I installed schooltool from the source in Ubuntu 6.10
and the program it's working without problem if I initiate 
through terminal session.

I installed through source because the installation through 
Synaptic package has a bug in ubuntu 6.10  :( 

_Terminal session_

>>>[COLOR="RoyalBlue"]aabento@aabento:/etc/schooltool$[/COLOR][SIZE="2"][COLOR="Red"] sudo make run[/COLOR][/SIZE]
>>>Password:
>>>test -d Zope3 || svn co svn://svn.zope.org/repos/main//Zope3/branches/3.3 Zope3
>>>test -d buildsupport/zpkgsetup || svn co >>>svn://svn.zope.org/repos/main//zpkgtools/trunk/zpkgsetup buildsupport/zpkgsetup
>>>test -d Zope3 && cd Zope3 && python setup.py build_ext -i
>>>running build_ext
>>>running build_headers
>>>python setup.py  \
>>>               build_ext -i install_data --install-dir .
>>>running build_ext
>>>running install_data
>>>PYTHONPATH=:src:Zope3/src python setup.eggs.py develop -S Zope3/src --install-dir >>>Zope3/src
>>>running develop
>>>running egg_info
>>>writing requirements to src/schooltool.egg-info/requires.txt
>>>writing src/schooltool.egg-info/PKG-INFO
>>>writing top-level names to src/schooltool.egg-info/top_level.txt
>>>writing dependency_links to src/schooltool.egg-info/dependency_links.txt
>>>writing manifest file 'src/schooltool.egg-info/SOURCES.txt'
>>>running build_ext
>>>Creating /etc/schooltool/Zope3/src/schooltool.egg-link (link to src)
>>>schooltool SVN is already the active version in easy-install.pth

>>>Installed /etc/schooltool/src
>>>Processing dependencies for schooltool==SVN
>>>python bin/remove-stale-bytecode.py
>>>python schooltool-server.py
>>>Reading configuration from schooltool.conf
>>>2006-12-30 11:48:40,565 zope.server.http (HTTP) started.
>>>      Hostname: aabento.no-ip.com
 >>>       Port: 7080
>>>2006-12-30 11:48:40,575 zope.server.http (REST) started.
>>>        Hostname: aabento.no-ip.com
>>>        Port: 7001
>>>Startup time: 17.651 sec real, 9.200 sec CPU

[SIZE="2"][COLOR="Red"]Ctrl C[/COLOR][/SIZE]

[COLOR="RoyalBlue"]aabento@aabento:/etc/schooltool$[/COLOR]


Soon that I close the terminal window Scooltool stops to work.   :(   :( 

[SIZE="2"]How can I initiate schooltool at start up?[/SIZE]

Thanks

---

### Post by shane2peru on 2006-12-30
I'm not really familiar with schooltool, however if you know how to start it through the terminal, it will be easy to start it at startup.  Just go to **System - Preferences - Sessions**  in the Sessions click on the Startup Tab, and click on add then type whatever you would type in the terminal to make it run.  That will start it every time you start up Ubuntu, or should, sometimes you have to add some sort of delay in it.

Shane

---

### Post by macogw on 2006-12-30
to run a process from terminal without it ending on ctrl C or when the window closes do this
nohup programName &
hit enter, now hit ctrl +c.  the process will keep going, but you can use the terminal or close the terminal.

---

### Post by aabento on 2006-12-31
Hello

I must thank you these helps but it seems that none of these 
solutions is working. :confused: 

 Other suggestions will be well comings.

Thanks
Arnaldo

---

### Post by shane2peru on 2007-01-01
The other way to get it to start is just hit **alt - F2**  and in the little window that pops up, type the command to get the program to start.  You will have to do this every time to get it to run but it should stay running.  Maybe if you could explain what schooltool is we can help a bit more as I'm not familiar with it.  Also perhaps you can give us the run command so we can see it.

Shane

---

