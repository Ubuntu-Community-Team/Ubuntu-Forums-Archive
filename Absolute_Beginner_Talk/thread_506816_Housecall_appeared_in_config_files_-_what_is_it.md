---
title: "Housecall appeared in config files - what is it?"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by stig on 2007-07-22
In my config files a folder containing lots of subfolders and files has appeared that I don't recall seeing before. It is called .housecall6.6

What is this?

---

### Post by mlentink on 2007-07-22
Have you used [this]("http://housecall.trendmicro.com/") lately?

---

### Post by por100pre1 on 2007-07-22
Weird. I know about Trend Micro HouseCall... Did you use ant Trend Micro product?

EDIT: I didn't know House Call works on LInux PCs.

---

### Post by stig on 2007-07-22
> **mlentink said:**
> Have you used [this]("http://housecall.trendmicro.com/") lately?

No - never heard of it before. And no-one else uses my PC - so I wonder how it got there?

Everything I install comes from the Ubuntu repos, but I did not install Housecall.

---

### Post by mlentink on 2007-07-22
Hmm
It's almost too much of a coincidence that TrendMicro seems to be at 6.6 as well.
What is the nature of thse files? Are they all text-files? if so, could you post one so we could have a look at the contents?

---

### Post by stig on 2007-07-22
> **mlentink said:**
> Hmm
It's almost too much of a coincidence that TrendMicro seems to be at 6.6 as well.
What is the nature of thse files? Are they all text-files? if so, could you post one so we could have a look at the contents?

Does this screenshot from Nautilus help?

I don't know which files you would want to see. For example, the local.conf file shows:

#Housecall Local Client Configuration
#Tue May 15 14:56:10 BST 2007
Package.lib-jni-engine-common=6.51.1000
Package.applet-html-java-common=6.51.1000
Time.LastUpdate=1179237354653
Package.lib-jni-engine-common.Binding.0=java\:hc.impl.lib.engine.Register
Package.lib-jni-system-engine-common=6.51.1000
Ticket.data=cad897f44e74f55d09673f397c87997c
Package.activeupdate=6.51.1000
Package.lib-jni-activeupdate-native=6.51.1000
Package.lib-jni-engine-common.Bindings=1
Package.lib-jni-activeupdate-common=6.51.1000
Package.lib-jni-engine-native=6.51.1000
Account.data=68cf89d4cfb1b2ba43c1cb706222d8dc9451a8184e88a9cd

---

### Post by mlentink on 2007-07-22
I would need to see more to be completely definitive, but googling around with a few of those file-names, Trens Micro Housecalll seems to be the most likely candidate. 
You don't remember using/installing it? I'd change passwords just in case.

---

### Post by stig on 2007-07-22
> **mlentink said:**
> I would need to see more to be completely definitive, but googling around with a few of those file-names, Trens Micro Housecalll seems to be the most likely candidate. 
You don't remember using/installing it? I'd change passwords just in case.

In the folder AU_Log there is a file TmuDump.txt. The first part of this is pasted below - it carries on much longer but seems to be repeating itself, and is all around 14:52 to 14:55 on the same day, 15 May 2007. I've checked my diary and I used the PC that day but nothing unusual. I'm always careful because I use my PC for business and have customers' personal information on it. It is networked to my other Ubuntu PC but that does not have the .housecall file. Other than email and browsing the only other Internet use is for sending files to my web site at the ISP's server and that's only about once a week. I can only think that the housecall software came from a web site I visited. I don't intentionally use any dodgy web sites but part of my work is research and I do have to visit a wide range of sites. But surely nothing can be downloaded onto my Ubuntu PC and installed without my permission?

What is the best way to get rid of this software - just delete the folder from the config files?
Thanks for he help.

Here is the first oart of the TmuDump.txt file.....

---------------------------------------

Info: Tue May 15 14:52:49 2007 P[7991] T[-1324737616] 
Load AU 2.61.0.1041 from: [/home/peter/.housecall6.6/]

---------------------------------------

Info: Tue May 15 14:52:49 2007 P[7991] T[-1324737616] 
new context for thread: 2970229680

---------------------------------------

Info: Tue May 15 14:52:49 2007 P[7991] T[-1324737616] 
new context for thread: 2970229680

---------------------------------------

Info: Tue May 15 14:52:49 2007 P[7991] T[-1324737616] 
key: [SocketTimeout]

Info: Tue May 15 14:52:49 2007 P[7991] T[-1324737616] 
value: [120]

---------------------------------------

Info: Tue May 15 14:52:49 2007 P[7991] T[-1324737616] 
key: [ResumeDownload]

Info: Tue May 15 14:52:49 2007 P[7991] T[-1324737616] 
value: [1]

---------------------------------------

Info: Tue May 15 14:52:49 2007 P[7991] T[-1324737616] 
key: [CachePath]

Info: Tue May 15 14:52:49 2007 P[7991] T[-1324737616] 
value: [/home/peter/.housecall6.6/Update]

---------------------------------------

Info: Tue May 15 14:52:49 2007 P[7991] T[-1324737616] 
key: [RetryCount]

Info: Tue May 15 14:52:49 2007 P[7991] T[-1324737616] 
value: [3]

---------------------------------------

Info: Tue May 15 14:52:49 2007 P[7991] T[-1324737616] 
Start TmuGetUpdateInfo()

Info: Tue May 15 14:52:49 2007 P[7991] T[-1324737616] 
Creating Temp dir [/home/peter/.housecall6.6/AU_Temp/7991_2970229680]

Info: Tue May 15 14:52:49 2007 P[7991] T[-1324737616] 
Downloading [[http://housecall65.trendmicro.com/housecall/activeupdate](http://housecall65.trendmicro.com/housecall/activeupdate)
/ini_xml.zip] to [/home/peter/.housecall6.6/AU_Temp/7991_2970229680/ini_xml
.zip]...

Info: Tue May 15 14:52:49 2007 P[7991] T[-1324737616] 
HttpConnection: Client Error: HTTP 404 Not Found

Info: Tue May 15 14:52:49 2007 P[7991] T[-1324737616] 
TmDownloader: Connection fail when try to open resource

Error: Tue May 15 14:52:49 2007 P[7991] T[-1324737616] 
Downloader returns: 4

Info: Tue May 15 14:52:49 2007 P[7991] T[-1324737616] 
Download ini_xml.zip fail, try plain file.

Info: Tue May 15 14:52:49 2007 P[7991] T[-1324737616] 
Downloading [[http://housecall65.trendmicro.com/housecall/activeupdate](http://housecall65.trendmicro.com/housecall/activeupdate)
/server.ini] to [/home/peter/.housecall6.6/AU_Temp/7991_2970229680/server
.ini]...

Info: Tue May 15 14:52:49 2007 P[7991] T[-1324737616] 
HttpConnection: Connect to source success

Info: Tue May 15 14:52:49 2007 P[7991] T[-1324737616] 
Start Download...

Info: Tue May 15 14:52:50 2007 P[7991] T[-1324737616] 
Successfully wrote [14664]B

Info: Tue May 15 14:52:50 2007 P[7991] T[-1324737616] 
TmDownloader: Download Success

Info: Tue May 15 14:52:50 2007 P[7991] T[-1324737616] 
Serverini Analyzer Init: /home/peter/.housecall6.6/AU_Temp/7991_2970229680
/server.ini

Info: Tue May 15 14:52:50 2007 P[7991] T[-1324737616] 
Callback with Tmu_GET_UPDATE_INFO: item[2][131072][0][0], newest version[8
.1.1002], url[[http://housecall65.trendmicro.com/housecall/activeupdate](http://housecall65.trendmicro.com/housecall/activeupdate)
/engine/engv81_linux.zip]

Info: Tue May 15 14:52:50 2007 P[7991] T[-1324737616] 
UpdateManager endwith 0 (0): Success

Info: Tue May 15 14:52:50 2007 P[7991] T[-1324737616] 
End TmuGetUpdateInfo()

---

