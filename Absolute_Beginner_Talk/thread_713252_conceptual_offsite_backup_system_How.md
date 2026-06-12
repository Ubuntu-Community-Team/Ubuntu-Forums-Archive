---
title: "conceptual offsite backup system: How?"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by eaglestrike7339 on 2008-03-02
Ok, well as the subject, i have been mulling over the idea to start an offsite backup storage service as a replacement for the tape backups they were currently taking (and will be going out of style sometime soon). 

The clients would probable be <5 Small businesses, but with the possibility of including personal business, They would probable have around 20GB of data each, that would need to be backed up once a night. These would most likely be Windows Server 2003

Ok, protocols: I would most likely use rsync over SSH, but if they wanted to use FTP or the like, that could also be integrated easily, right?

Data Storage: This is where it gets fun. I was thinking of using the Quota package, and creating linux users on the server, then using quota to limit thier home directory.
Is there another way to do this? Possible using MySQL? I may have read something about this in the past, but i do not know where i found this, or what it actually was. 

management: how could i get a website to automate the process of adding users, setting up the quota, expanding quota when necessary, and (if possible) view when the last databackup occured or even view/download files

what language could handle this?

also, on my end, a nice high-speed cable line, and a few Raid-5 320GB HDDs. Plus, on thier end, could i use cygwin to run the linux rsync and ssh

anyone who could give me pointers would be great. I have decent expertise in linux, but this would definitely be a learning experience to me. Also, i have some experience in website building. Thanks to all, again

m@

---

### Post by eaglestrike7339 on 2008-03-02
BUMP....plz guys, any ideas?

---

### Post by jflaker on 2008-03-02
I will EMPHASIZE one thing.  You need to keep a backup, possibly to a tape library or an offsite D2D service for disaster recovery.  

It is a great idea, I don't know where to start, but you need to think about safekeeping your data and you, yourself, would most likely need to utilize and off site service.....Which will run your price point up.

Just a thought

---

### Post by Oldsoldier2003 on 2008-03-02
> **jflaker said:**
> I will EMPHASIZE one thing.  You need to keep a backup, possibly to a tape library or an offsite D2D service for disaster recovery.  

It is a great idea, I don't know where to start, but you need to think about safekeeping your data and you, yourself, would most likely need to utilize and off site service.....Which will run your price point up.

Just a thought
offsite= safety deposit box.... moms house or whatever lol. Sometimes small businessmen have to think outside of the box

---

### Post by eaglestrike7339 on 2008-03-02
well, i figure to have a hot copy ready to restore to your newly-fixed server w/o having to take a trip to mom&#347; place couldnt hurt very much either. 

Any other ideas on what programming language to use?
or the mysql/quota+user method?

also, i will change the title of the thread, possibly to something more exciting

---

### Post by Oldsoldier2003 on 2008-03-02
> **eaglestrike7339 said:**
> well, i figure to have a hot copy ready to restore to your newly-fixed server w/o having to take a trip to mom&#347; place couldnt hurt very much either. 

Any other ideas on what programming language to use?
or the mysql/quota+user method?

also, i will change the title of the thread, possibly to something more exciting
really the offsite is more for your protection the theirs, because the absolute latest data would always be live on your machines...

---

### Post by freebeer on 2008-03-02
cygwin seems to me to be a bit overkill and adds complexity that you don't need. (well, maybe you do?)  There's an application (free) called deltacopy.  It's really rsync in a Windows wrapper.  I use that on the Windows boxes to backup daily to a local server (Ubuntu) on the LAN.  Then I use rsync to sync with my off-site server over secure shell.  (The last part is still in the implementation stage, but early tests indicate that it'll work just fine.)

---

### Post by eaglestrike7339 on 2008-03-02
wow, deltacopy sounds exactly the kind of thing i was looking for. I will look into it. 

Though, the question that i desperately need answered is: How to make scripts that interact with the server (eg. add linux users, quota home directories) that can be run from the website? Specifically after clicking of some button occurs? What language would be required to know for this?

also, i found a package called duplicity that kept an encrypted copy of the data at an offsite location. is that worth looking into?


edit: Just found a protocol called CGI. I have heard of the CGI-bin on webhosts before, but i was not sure what it did. Is this what I am looking for?

---

### Post by Oldsoldier2003 on 2008-03-02
cgi is the ability to run (perl) scripts over the webserver

---

### Post by eaglestrike7339 on 2008-03-03
oldsoldier, thank you. 

Is there a way that I can configure these perl scripts to add users to my system?

---

### Post by Oldsoldier2003 on 2008-03-03
> **eaglestrike7339 said:**
> oldsoldier, thank you. 

Is there a way that I can configure these perl scripts to add users to my system?
I don't see why not, there are web based administration panels for hosting businesses that add email accounts, ftp accounts, etc... They also can invoke backups, service restarts, and such. Some are written in perl and others in Php. Once upon a time I uses to use Microsoft excel and vba to add user accounts to a windows nt4 server.... you never know what tools you'll run across. Though tbh I would rather try and see if there is something tried and true that implements most of the features i want before i tried coding a control panel from scratch.

---

### Post by eaglestrike7339 on 2008-03-03
i will keep that in mind, about the control panel, i know of webmin which is very capable and does these things very well. 

I guess that I need to find a way to get it integrated into a website, though, and that will be it. Thanks to all, especially oldsoldier

---

