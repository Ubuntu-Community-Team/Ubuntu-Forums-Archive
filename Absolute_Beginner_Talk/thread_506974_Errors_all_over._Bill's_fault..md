---
title: "Errors all over. Bill's fault."
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by iUSER-Mike on 2007-07-22
I keep getting Database error. I'm going to post anyway.
 Database error 
The Ubuntu Forums database has encountered a problem. 

--------------------------------------------------------------------------------
 
Please try the following: 
Load the page again by clicking the Refresh button in your web browser.
Open the ubuntuforums.org home page, then try to open another page.
Click the Back button to try another link.
 
The ubuntuforums.org forum technical staff have been notified of the error, though you may contact them if the problem persists. 
  
I can't download Ubuntu Studio.Have tried various mirrors, and I get about 80% downloaded then I get Timed out message appear, and loose the download.Any Ideas pleas?

Cheers Mike:confused:

---

### Post by irish_flu on 2007-07-22
> **iUSER-Mike said:**
> 
  
I can't download Ubuntu Studio.Have tried various mirrors, and I get about 80% downloaded then I get Timed out message appear, and loose the download.Any Ideas pleas?

Cheers Mike:confused:

I'm not sure what the problem might be, but my suggestion is to use the Torrent download instead.  Are you familiar with BitTorrent?

---

### Post by iUSER-Mike on 2007-07-22
Hello irish_flu, I don't use Torrents. Did have a look at it one time, but could'nt figure it out. However, I normally have eMule running 24/7.Maybe that eefects the download?
Mike:guitar:

---

### Post by JesterDev on 2007-07-22
Get yourself a download manager. [http://www.freedownloadmanager.org/]("http://www.freedownloadmanager.org/") That is assuming your still running windows. This will keep trying, and will download in many parts at once making the overall speed quite a bit faster. Should also solve your problem by resuming the download when it gets interupted. 

Other then that, I suggest something like utorrent. It's easy to setup even without prior knowledge of bittorrent. Just go with the defaults so your upload rates are not set to high (in case your on cable). Download the torrent and open it with utorrent. 

[http://www.utorrent.com/]("http://www.utorrent.com/")

Utorrent also works under Linux via Wine. :)

Either that or wait till the database issues are resolved.

---

### Post by por100pre1 on 2007-07-22
Are you using Ubuntu Feisty Fawn already? If not you can install regular Ubuntu 7.04 and then copy and paste these lines one by one on a terminal:

```


sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'

wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update

sudo aptitude install ubuntustudio-desktop


```

---

