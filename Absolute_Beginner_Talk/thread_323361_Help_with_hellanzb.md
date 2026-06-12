---
title: "Help with hellanzb"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by fearevilleet on 2006-12-22
Hello Everyone,

I am having an issue getting hellanzb to work correctly. I installed everything with no issues, but when I run it all I get is 



hellanzb v0.9 (config = /usr/etc/hellanzb.conf)
(/home/evilleet/nzb) Opening 4 connections...
hellanzb - Now monitoring queue...

Here is a copy of my config file, The only change I made was to the 
My config file ls pretty much default expect the part I was told to chage to store the nzb files

If anyone can assist me with this issue it would be very much appericated, I have been trying for hours.

defineServer(id = '/home/evilleet/nzb',
             hosts = [ 'news.giganews.com:119' ],
             #hosts = [ 'news.changeme.com', 'morenews.changeme.com:8000' ],


             username = 'myuserid',
             password = 'mypassword',
             #username = None,           # no auth
             #password = None,

             connections = 6,
             antiIdle = 4.5 * 60,        # 4 minutes, 30 seconds
             #bindTo = '204.31.33.7',    # connect FROM this ip address
             #enabled = False,           # disable this server
             #skipGroupCmd = False,      # skip sending nntp GROUP commands
             )

---

### Post by electricshoes on 2006-12-22
You will need to put your .nzb files into the daemon.queue directory. How you have your config it will be in ~/nzb/daemon.queue

Once you have an nzb in there you can run hellanzb.py

---

### Post by fearevilleet on 2006-12-22
There is a /home/evilleet/nzb/daemon.queue directory, but I had to manually create it.  I tried moving my nzb file to /home/evilleet/nzb/daemon.queue (the directory I manually made) and reran the script but it dose not seem to be downloading. I should see some type of download status or a download speed so I know I did it correctly right? 

SHould I try changing tdefineServer(id = '/home/evilleet/nzb', to something else?


Thanks

---

### Post by electricshoes on 2006-12-22
It should create an NZB dir. So if you remove the nzb/daemon.queue dir you made then run hellanzb.py , it will say it is waiting. Once this happens it will create an nzb dir when you specify in your hellanzb.conf

So change 

/home/evilleet/nzb

to

/home/evilleet/

 It needs the trailing / 

This will create an NZB folder for you once you run it.

---

