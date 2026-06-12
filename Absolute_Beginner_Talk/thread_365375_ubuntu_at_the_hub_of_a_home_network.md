---
title: "ubuntu at the hub of a home network"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by getaboat on 2007-02-19
various flavours of MS PCs + dapper + soon edgy. I'd like to have a low spec ubuntu box at the centre to act as 
- file server (shared files and back-ups) - automated backups from cron?
- print server (3 printers + scanner)
- possible mini-exchange server (shared calendar and common - thunder and sun bird)

Will I have less hair than now if I start off down this route?

---

### Post by MrFSL on 2007-02-19
I would say that this is ambitious but not impossible. The only part I would discourage is the "mini-exchange server" (two reasons 1. I hate exchange and 2. I could never get linux and exchange working well)

I have a headless print / scanner server. To setup I would point you to:
[http://www.ubuntuforums.org/showthread.php?p=1831119]("http://www.ubuntuforums.org/showthread.php?p=1831119")
and
[http://tips.linux.com/article.pl?sid=06/10/13/1751234&tid=100&tid=13]("http://tips.linux.com/article.pl?sid=06/10/13/1751234&tid=100&tid=13")

As a file server you have lots of options. Most people would direct you to using samba since you are sharing with mulitiple MS PCs. I however prefer using ssh. I'm sure you can find free
thrid-party software for MS. If not samba is easy to setup.

Automatic backups are easy. There are several choices in software and methods. UbuntuForums, [http://help.ubuntu.com](http://help.ubuntu.com), and google are all great resources to get ideas.

All in all I dont see this as a huge undertaking (that is if you drop your dependance on exchange.)

---

### Post by n8bounds on 2007-02-19
SSH is slow, as it has to encrypt and decrypt all your transferred data.  Samba is not that hard, you can even make it an ftp server.  

As with many things here, you have OPTIONS

---

### Post by getaboat on 2007-02-21
Thanks for the replies. It's good to know this stuff isn't off the radar.

I think I'll try to do it through samba. 

The exchange bit falls into the "would be nice" catagory.

Now all I have to do is start winning stuff on ebay for the file server.

---

