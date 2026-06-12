---
title: "Debian menu in Fiesty 7.04"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by jerrynewt on 2007-07-10
Installed Fiesty 7.04 day before yesterday and so far most everything looking pretty good, with a couple of hitches. I can't enable the Debian menu in the menu editor or HP toolbox. Had them both when I was using Dapper. Also can't access some repositories when trying to use add/remove or synaptic, mostly beryl. (I enabled the beryl repos  in the sources.list but still no go. Any ideas??

---

### Post by wolfen69 on 2007-07-10
i had to download it to get it working...did you?

---

### Post by zvacet on 2007-07-10
system>administration>software sources>chek all boxes in Ubuntu software and in updates.That will open all repositories.

---

### Post by jerrynewt on 2007-07-10
I have all the boxes checked in the ubuntu tab on the software sources, and all checked in the third party tab also. I can't download the Debian menu, Gdesklets, Hp toolbox or many of the other programs using Automatix. I tried aptitude with same result. I get this "Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "Gdesklets"
Some of my attempted downloads come back with "error code 1". I haven't downloaded anything unusual and this is a fresh (2 day) install of Fiesty. Any ideas as to what is going on?

---

### Post by Papi-KB7VGW on 2007-07-10
Hi.   I had to install menu-xdg and then from the command line it was either   menu-update or update-menu   Then just enable it thru main menu.  :)


used synaptic and it worked fine

---

### Post by macogw on 2007-07-10
Install them properly (in Synaptic or Add/Remove or with apt) instead of using Automatix.  Automatix isn't exactly known for working well and leaving systems in a healthy state.

---

### Post by jerrynewt on 2007-07-10
Thought maybe I needed to run update, so I ran in terminal "sudo aptitude update" and got this results at the end 
"Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages [4912kB]
99% [10 Packages gzip 0] [Waiting for headers]
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
  Sub-process gzip returned an error code (1)
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources [1523kB]            
99% [11 Sources gzip 0]                                               763kB/s 0s
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources                        
  Sub-process gzip returned an error code (1) ". Don't know what the heck is up with that, but it might be what is not letting me download a lot of programs via command line. Any help on this would make me one happy camper, as I can't seem to download much of anything via command line lately (since fresh install). Thanks again for all of your quick responses--makes us new guys feel like there is a light at the end of the tunnel after all, and it isn't a train !!

---

