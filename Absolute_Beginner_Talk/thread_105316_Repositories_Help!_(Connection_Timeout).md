---
title: "Repositories Help! (Connection Timeout)"
date: 2005-12-18
forum: Absolute Beginner Talk
---

### Post by olieviya on 2005-12-18
I want to download Azureus on my Ubuntu system. So I've tried following the instuctions on:
[http://www.ubuntuforums.org/showthread.php?t=75272&highlight=azureus](http://www.ubuntuforums.org/showthread.php?t=75272&highlight=azureus)
&
[https://wiki.ubuntu.com/AzureusHowTo?highlight=%28azureus%29](https://wiki.ubuntu.com/AzureusHowTo?highlight=%28azureus%29)

Whatever I do I end up getting Connection Timeouts and no being able to get the files to install Azureus.

Any ideas?

---

### Post by bscbrit on 2005-12-18
Hi Olieviya,
I know that you 'have followed the instructions' from the other thread but when do you get the timeouts?  Is it when trying to download the debs, or when running Azureus? (I'm guessing the latter, but I could be wrong - I often am!)

---

### Post by olieviya on 2005-12-18
I get timeouts when doing this:

followed by a
Code:

sudo apt-get update

Do the following to install azureus:
Code:

sudo apt-get install sun-j2re1.5 libcommons-cli-java liblog4j1.2-java libseda-java libswt-gtk-3.1-java

AND (on the other how-to)

#

Add universe and multiverse, if they have not already been done. If you do not know how, see AddingRepositoriesHowto
#

Install the following programs j2re1.4 libcommons-cli-java liblog4j1.2-java libseda-java libswt-gtk-3.1-java

---

### Post by bscbrit on 2005-12-18
Does your browser work OK? For example, are you using the same computer to access this forum?
If it is _just_ when you try to download from these specific repos, then trying 'ping'ing them to see if they are still there.  Try opening them up in your browser to see if it can find the link.

---

### Post by olieviya on 2005-12-18
Browser works fine, I'm on ubuntu now.
How do you do all that?

---

### Post by bscbrit on 2005-12-18
All this is done from the command line, so open up a terminal.  'ping' sends a packet of data to an IP address and times how long it takes to get there and back.  This might seem to be pretty useless as first glance but it is not.  First of all, if your ping gets there and back, they you can be certain that your network and internet connections are working ok.  IP addresses have the form of 123.12.213.0 i.e. 4 numbers in the range 0-255 separated by dots.  Some combinations have special meanings but lets not get bogged down in the weeds too early.  For example try the following:

ping -c5 64.31.23.9

you _should_ get a reply from this - its the ubuntu forums!

But humans are not very good at numbers; we much prefer something like [www.ubuntuforums.org](www.ubuntuforums.org)  So try this next:

ping -c5 [www.ubuntuforums.org](www.ubuntuforums.org)

You should get a similar response to the first attempt with names replacing numbers BUT, if you don't, then you now know that the system that converts the human-friendly name into the IP address is not doing its job.  There may be many reasons for this but, usually, it points to a misconfiguration of your computer.  The system is called DNS and its misconfiguration is the cause of quite a few problems seen here on the forums.  

So if you can identify the name of your repos (mine is gb.archive.ubuntu.com) and ping it you can prove that your system is looking up the names correctly, it is connected to the internet properly and that the site that you are trying to talk to (or download from to be correct in this instance) is up and operating.  If you do not get a response then something in that chain is not working and you can then start trying to pinpoint what it is!

Give it a try.

---

### Post by bscbrit on 2005-12-18
The fact that your browser is working but you are getting timeouts with apt-get suggests that it might be the repo site that is not doing its job.  Perhaps it is simply overloaded, perhaps it is down for maintenance, or whatever.  Afterall, everything else seems to be working fine - your browser works and because you can type in [www.google.com](www.google.com) for instance, you know that the system for converting names into IP addresses (DNS) is working, and you are connected to the internet.  But the repo site being down is not the only possible cause.  For example, you might have a firewall that permits HTTP and 'pings' (lets not confuse ourselves with the proper technical terms yet) but it might be stopping transfer of other kinds of data which will stop you from downloading.

---

### Post by bscbrit on 2005-12-18
Olieviya,  Initially you had problems connecting with GAIM, and now possible problems with accessing the repos.  Is there anything 'unusual' in your setup.? Do you have to use a gateway provided by a college or ISP, for example?

---

### Post by olieviya on 2005-12-19
I'm in winXP now so I can't do the above, but I will asap.

No gateway, I have a router installed at home and my pc is on a home LAN. 

The problem with GAIM, I think, must be irrelevent since what I had been doing wrong in GAIM was: I had been using a proxy to acces msn when none is needed. I thought, wrongly, that since I need to enter proxy settings for firefox I thought I needed the same in GAIM, but not so. All is fixed there btw.

---

