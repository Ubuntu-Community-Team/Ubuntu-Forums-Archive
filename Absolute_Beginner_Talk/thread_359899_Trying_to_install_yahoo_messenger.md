---
title: "Trying to install yahoo messenger"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by Philmc on 2007-02-12
When I try to install yahoo messenger I get the following error:

~$ sudo dpkg -i /home/phil/ymessenger_1.0.4_1_i386.deb
Selecting previously deselected package ymessenger.
(Reading database ... 110757 files and directories currently installed.)
Unpacking ymessenger (from .../ymessenger_1.0.4_1_i386.deb) ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
 ymessenger depends on xlibs (>> 3.3.6); however:
  Package xlibs is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger


Thanks for any help you can give.

Phil

---

### Post by nickoli_02 on 2007-02-12
You're missing some packages that yahoo depends on. Do this:

```
sudo aptitude install libssl0.9.6 xlibs 
```

That should do it

---

### Post by Philmc on 2007-02-12
tried that just now. No change

Phil

---

### Post by Maestro23 on 2007-02-12
> **Philmc said:**
> tried that just now. No change

Phil

Did it find the file or it just didn't work?  Either way, you might need to enable extra repositories.

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by nickoli_02 on 2007-02-12
You know, you can use gaim (which comes with ubuntu) to chat on the yahoo protocol pretty easily.

---

### Post by PrinceArithon on 2007-02-12
Kopete is better than yahoo, so I'd just go to the synaptic manager and install kopete.

---

### Post by aysiu on 2007-02-12
I haven't been able to find any threads on this forum with foolproof instructions for installing Yahoo! Messenger successfully on recent versions (Dapper/Edgy) of Ubuntu.

Give up and use something else--GAIM, Kopete, etc.

---

### Post by Brunellus on 2007-02-12
> **PrinceArithon said:**
> Kopete is better than yahoo, so I'd just go to the synaptic manager and install kopete.
anything is better than Yahoo messenger on Linux.

---

### Post by Delvien on 2007-02-12
try GAIM it's available from instal. 

Unless you installed Kubuntu, then use Kopete.

---

### Post by pissedoffdude on 2007-02-12
This should work ```
sudo apt-get install libssl0.9.6
``` install yim and run ```
ymessenger
```

---

### Post by xxl3w on 2007-02-12
The only problem I ran into with GAIM is it doesn't have voice chat. Does the other yahoo messenger client(s) offer voice capability? If not, is there ANYTHING in Linux to offer voice capabilities?

---

### Post by Brunellus on 2007-02-12
> **xxl3w said:**
> The only problem I ran into with GAIM is it doesn't have voice chat. Does the other yahoo messenger client(s) offer voice capability? If not, is there ANYTHING in Linux to offer voice capabilities?
short answer:  no.  

Skype's linux client offers voice, but not video.

Ekiga (using SIP) offers video and voice, but only to other SIP users.

---

### Post by xxl3w on 2007-02-12
I don't really want video. I just want a voice chat. Yahoo! users use Skype, right? Is there anyway I would be able to call them or would they have to install Skype's stand-alone program? I can't wait to get off work so I can investigate how I can use this. Skype PC-to-PC is still free, right?

---

### Post by Maestro23 on 2007-02-12
> **xxl3w said:**
> I don't really want video. I just want a voice chat. Yahoo! users use Skype, right? Is there anyway I would be able to call them or would they have to install Skype's stand-alone program? I can't wait to get off work so I can investigate how I can use this. Skype PC-to-PC is still free, right?

According to their site PC-PC calls are still free: [http://www.skype.com/download/](http://www.skype.com/download/)

---

### Post by loell on 2007-02-12
> **xxl3w said:**
> The only problem I ran into with GAIM is it doesn't have voice chat. Does the other yahoo messenger client(s) offer voice capability? If not, is there ANYTHING in Linux to offer voice capabilities?

try [gyachi]("http://gyachi.sourceforge.net") if you ever want is voice chat in rooms,
it also offers webcam, smileys, few avatars, file transfer, and a bit of IM spam protection.

with regards to sip voice calls, the main stumbling is yahoo uses a proprietary voice codecs. 
the team is trying to work around on this whenever they have free time ;) , perhaps it will be added in due time.

---

