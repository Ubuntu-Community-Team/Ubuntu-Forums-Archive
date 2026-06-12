---
title: "Easy to use FTP Program"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by twp_twm on 2008-04-15
I am looking for an easy to use FTP program to upload a Webpage i've constructed. Ideas anyone please!

---

### Post by notwen on 2008-04-15
FileZilla, KFTPGrabber or gFTP are all available in the repos.  Simply add them through Add/Remove or Synaptic.  =]

---

### Post by DaveySpeedstar on 2008-04-15
I love Filezilla (as much as anyone can 'love' software).

You just drag & drop the files

---

### Post by jba6511 on 2008-04-15
second filezilla for ease of use

---

### Post by Oldsoldier2003 on 2008-04-15
> **jba6511 said:**
> second filezilla for ease of use

+1 for filezilla , although all of the other programs mentioned so far are also good choices

---

### Post by redbob on 2008-04-15
FireFTP is great. It's a Firefox addon, so you could launch it besides FF. Try it! [http://fireftp.mozdev.org/](http://fireftp.mozdev.org/)

---

### Post by elmer_42 on 2008-04-15
I agree with all the people saying FileZilla, so I guess I fifth it? Anyway, I use FileZilla to manage a site for one of my friends, and it is amazingly simple. If you can use a file browser you can FileZilla. It's just so simple.

---

### Post by MeURi on 2008-04-15
> FireFTP is great. It's a Firefox addon, so you could launch it besides FF. Try it! [http://fireftp.mozdev.org/](http://fireftp.mozdev.org/)

Argh! You just beat me :-P

Thumbs up for FireFTP

---

### Post by HermanAB on 2008-04-15
Both Nautilus and Konqueror do FTP.  Just type [ftp://wherever](ftp://wherever) in the address bar.

---

### Post by hyper_ch on 2008-04-15
ktorrent as multi-pane client that supports almost any file transfer protocol to a webserver

---

### Post by brennydoogles on 2008-04-15
I agree that Fireftp is a good bet! I usually have it open in one tab, and my website up in another, so that I can test the pages immediately after I upload them.

---

### Post by crjackson on 2008-04-15
Actually, I use Gnome-Commander, Krusader (kde), and FileZilla.  The all work great.

---

### Post by munkyeetr on 2008-04-15
For updating a website I like Bluefish and it's ability to open files and edit them directly on the server, but to download a backup of the site I go to Filezilla (though thanks to this thread I will check out a few others and see if I like them :)).

---

### Post by alantony on 2008-04-15
Hi,
I have successfullly set up a Ubuntu server (LAMP) on a dedicated computer and now I would like to transfer files to the server with filezilla on my windows laptop (separate computer on the network). 

 Could someone help me with the proper host name for my local network server to put into filezilla. I call my local server ubuntu. Also,what is the right port to use? 

much thanks in advance 
not so tech al

---

### Post by jba6511 on 2008-04-16
does the ubuntu server have the ftp service enabled? If so, port 21, localhost as ubuntu and then authentication credentials if you enabled this or anonymous depending on the situation. You could also use putty and just copy the files over as well if you enable SSH.

---

### Post by alantony on 2008-04-16
thanks for your reply.

I installed proftpd (sudo apt-get install pro-ftpd) but I am not sure that it is on.  do you know **how I can turn pro-ftp on?**

I was able to SSH sucessfully but still do not know if the ftp-server is listening. 

much thanks in advance. 
aka

---

### Post by hyper_ch on 2008-04-16
btw, I didn't mean ktorrent but Konqueror ;)

---

### Post by alantony on 2008-04-29
I was able to access the ftp server by using 
server name ubuntu
username: myusername
password: mypassword

it seems that I did not have the ftp server active on the apache server.  Once I installed the ftp-server--everything started to work.
aka

---

