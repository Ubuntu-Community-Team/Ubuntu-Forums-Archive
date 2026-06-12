---
title: "Newbie question : installation of SABnzbd"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Pretender01 on 2007-12-13
Hi everyone,

I am new in the ubuntu and linux world and I am trying the famous Ubuntu OS.

Well first of all, thanks to every people who work on this amazing project.

Of course, I have a small problem with a software called SABnzbd.

I already have it on Windows but I was planing to put Ubuntu as my primary OS so I tried to install it.

I downloaded it and install Cherrypy, cheetah, unrar, unzip,  par2cmdline and then start sabnzbd with this command python SABnzbd.py -f SABnzbd.ini
in the Console. Here is what I get :
```

2007-12-13 14:12:10,134::INFO::SABnzbd v0.2.5
2007-12-13 14:12:10,135::INFO::Initializing SABnzbd v0.2.5
2007-12-13 14:12:10,135::DEBUG::FAIL_ON_CRC -> True
2007-12-13 14:12:10,135::DEBUG::CREATE_GROUP_FOLDERS -> True
2007-12-13 14:12:10,135::DEBUG::DO_FILE_JOIN -> True
2007-12-13 14:12:10,136::DEBUG::DO_UNZIP -> True
2007-12-13 14:12:10,136::DEBUG::DO_UNRAR -> True
2007-12-13 14:12:10,136::DEBUG::DO_SAVE -> True
2007-12-13 14:12:10,136::DEBUG::PAR_CLEANUP -> True
2007-12-13 14:12:10,137::DEBUG::CLEANUP_LIST -> []
2007-12-13 14:12:10,137::DEBUG::UMASK -> 493
2007-12-13 14:12:10,137::DEBUG::SEND_GROUP -> False
2007-12-13 14:12:10,138::DEBUG::CREATE_CAT_FOLDERS -> False
2007-12-13 14:12:10,138::DEBUG::CREATE_CAT_SUB -> False
2007-12-13 14:12:10,138::INFO::DOWNLOAD_DIR: /media/hda5/premier
2007-12-13 14:12:10,139::INFO::COMPLETE_DIR: /media/hda5
2007-12-13 14:12:10,139::INFO::NZB_BACKUP_DIR: 
2007-12-13 14:12:10,139::INFO::CACHE_DIR: /media/hda5/temp
2007-12-13 14:12:10,140::INFO::dirscan_dir: 
2007-12-13 14:12:10,140::INFO::BANDWITH_LIMIT: 0.0
2007-12-13 14:12:10,140::INFO::schedlines: []
2007-12-13 14:12:10,141::INFO::dirscan_opts: 3
2007-12-13 14:12:10,141::INFO::top_only: True
2007-12-13 14:12:10,141::INFO::auto_sort: False
2007-12-13 14:12:10,142::INFO::[sabnzbd] Loading data for bytes.sab from /media/hda5/temp/bytes.sab
2007-12-13 14:12:10,142::INFO::[sabnzbd] Loading data for queue.sab from /media/hda5/temp/queue.sab
2007-12-13 14:12:10,144::INFO::_yenc module... NOT found!
2007-12-13 14:12:10,147::INFO::celementtree module... found!
2007-12-13 14:12:10,148::INFO::par2 binary... found!
2007-12-13 14:12:10,148::INFO::rar binary... found!
2007-12-13 14:12:10,148::INFO::unzip binary... found!
2007-12-13 14:12:10,149::INFO::Starting SABnzbd v0.2.5
2007-12-13 14:12:10,149::DEBUG::[sabnzbd] Starting postprocessor
2007-12-13 14:12:10,155::DEBUG::[sabnzbd] Starting assembler
2007-12-13 14:12:10,173::DEBUG::[sabnzbd] Starting downloader
2007-12-13 14:12:10,179::INFO::Starting web-interface
13/Dec/2007:14:12:10 CONFIG INFO Server parameters:
13/Dec/2007:14:12:10 CONFIG INFO   server.environment: production
13/Dec/2007:14:12:10 CONFIG INFO   server.log_to_screen: True
13/Dec/2007:14:12:10 CONFIG INFO   server.log_file: /home/thibaud/Bureau/SABnzbd-0.2.5/cherrypy.log
13/Dec/2007:14:12:10 CONFIG INFO   server.log_tracebacks: True
13/Dec/2007:14:12:10 CONFIG INFO   server.log_request_headers: False
13/Dec/2007:14:12:10 CONFIG INFO   server.protocol_version: HTTP/1.0
13/Dec/2007:14:12:10 CONFIG INFO   server.socket_host: 
13/Dec/2007:14:12:10 CONFIG INFO   server.socket_port: 8080
13/Dec/2007:14:12:10 CONFIG INFO   server.socket_file: 
13/Dec/2007:14:12:10 CONFIG INFO   server.reverse_dns: False
13/Dec/2007:14:12:10 CONFIG INFO   server.socket_queue_size: 5
13/Dec/2007:14:12:10 CONFIG INFO   server.thread_pool: 10
13/Dec/2007:14:12:10 HTTP INFO Serving HTTP on [http://localhost:8080/](http://localhost:8080/)

```
then i open firefox and go to localhost:8080/SABnzbd; and 
the answer is a 500 internal error:confused:


500 Internal error

The server encountered an unexpected condition which prevented it from fulfilling the request.

Powered by CherryPy 2.2.1 


Anny idea please ?

---

### Post by Partyboi2 on 2007-12-14
SABnzbd will not run unless the directories are correctly edited.
Have you got the .ini file setup right?

---

### Post by felker2 on 2008-01-31
You're using SABnzbd 0.2.5. You should use SABnzbd+ 0.3.0: it's much easier to install and use.

First install the needed programs:
```

sudo apt-get install python python-cherrypy python-cheetah python-elementtree python-yenc python-celementtree python-feedparser unrar unzip par2

```
If you get errors, install them via the GUI add/remove programs, as that will take care of repositories.


Then get SABnzbdplus 0.3.0 from [http://www.sabnzbd.org/download/](http://www.sabnzbd.org/download/) and/or [http://sourceforge.net/project/showfiles.php?group_id=207766&package_id=248837](http://sourceforge.net/project/showfiles.php?group_id=207766&package_id=248837).
Finanlly unzip and run SABnzbdplus:

```

unzip sabnzbd-0.3.0.zip
cd sabnzbd-0.3.0/
python SABnzbd.py

```

Your browser will start pointing to the SABnzbd GUI. You only need to configure your binary newsserver.

HTH

---

### Post by Martje_001 on 2008-02-02
Use this:
[http://www.xs4all.nl/~mgj1/SABnzbd%20for%20linux/](http://www.xs4all.nl/~mgj1/SABnzbd%20for%20linux/)

---

