---
title: "E: Problem parsing dependency Depends"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by drifting on 2006-08-07
Anyone any ideas? Not able to update or use Synaptic.

I have been fighting with this machine for weeks, had quite a few problems even getting Ubuntu installed, downladed about 4 ISO before I got the the alternate, finally got Alternate AMD64 installed, plagued by disk corruption, intermittant network card, and now this :-

E: Problem parsing dependency Depends
E: Error occurred while processing mibsasl2 (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

If anyone is interested I built this machine specifically for Ubuntu (And no I don't need a smart comment about hardware compatability, as I have found that out myself ](*,)  )

Anyway.

MSI K9N Platinum
AMD Athelon 64 AM2 
2GB Kingston Hyper Memory
7900GT Nvidia
1 x 80GB SATA
1 x 160GB SATA

Love hacking around and reading up, but the novelty is waring a tad thin, Windows XP runs fine without issue, which really rubs salt in the wounds.

Paul.

---

### Post by halfvolle melk on 2006-08-07
You could try to copy /var/lib/dpkg/status-old to /var/lib/dpkg/status as suggested here (post #4):
[http://www.linuxquestions.org/questions/showthread.php?t=155478](http://www.linuxquestions.org/questions/showthread.php?t=155478)

Edit: Ps. you can't have Synaptic open and use apt from the CLI at the same time.

---

### Post by drifting on 2006-08-07
> **halfvolle melk said:**
> You could try to copy /var/lib/dpkg/status-old to /var/lib/dpkg/status as suggested here (post #4):
[http://www.linuxquestions.org/questions/showthread.php?t=155478](http://www.linuxquestions.org/questions/showthread.php?t=155478)

Edit: Ps. you can't have Synaptic open and use apt from the CLI at the same time.

Thanks for the reply. I did find that post, sadly made no difference. I knew I should have mentioned that, the bit that bothered me was the re install statment.:rolleyes: 

Paul.

---

### Post by halfvolle melk on 2006-08-07
Hehe, ok.

What did you try so far? No guarantees but some the following _might_ help, or at least provide some more debugging info:
```
sudo apt-get -f install
```
or clean out the cache
```
sudo apt-get clean
sudo apt-get update
```
And there might be some usefull info in /var/log/dpkg.log though I wouldn't know cause I never had an error of this kind.

---

### Post by drifting on 2006-08-07
Tried all the above so far, still get the error as above on the update.

I have also restored a previous sources.list same error.

Paul.

---

### Post by halfvolle melk on 2006-08-07
One more thought. You could try removing and reinstalling the offending package. THIS MAY BORK YOUR SYSTEM! What is mibsasl2 anyway and from what repository (run "sudo apt-cache policy mibsasl2")? Google says maybe I mean libsasl2. I don't know what depends on it and how dangerous removing it is.

edit: libsasl looks pretty important and removing it is bound to breaksomething!

---

### Post by drifting on 2006-08-07
paul@ubuntu:~$ sudo apt-cache policy mibsasl2
Password:
E: Problem parsing dependency Depends
E: Error occurred while processing mibsasl2 (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
paul@ubuntu:~$

To be honest I have installed so many things on here, the last batch were network monitoring software, which would imply SMTP based with mib? in the name?
However I cannot uninstall anything, it just keeps saying the same error. It's beginning to look like a reinstall, not what I wanted to do, but hey suppose it's good experience. Wished Linux had a program like "go back" which  put things back after I muck them up ;) 

Paul.

---

### Post by drifting on 2006-08-07
Whoo Hoo.

Solved it. Not exactly sure how, but started at the beginning and went through the whole sequence again. Think it may have been the status problem mentioned earlier.

Thanks ever so much for helping, it was greatly appreciated.

Paul.

---

