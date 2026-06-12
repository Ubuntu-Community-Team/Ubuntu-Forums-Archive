---
title: "Extremely Sporadic Downloading"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by jawknee530 on 2007-01-06
Backstory:  

I installed ubuntu on a windows machine and had a dual boot system going.  Edgy worked great and I didn't have too many problems and the people in this forum gave me a lot of help.  I decided that I liked ubuntu a lot and didn't need windows anymore so i backed up all of my files and reinstallned edgy on the whole hdd.  

Problem:

Since I've reinstalled edgy my downloading has gone crazy.  Most of the time it sticks around 4000 B/s......bytes!  I have a 10 Meg connection.  The wierd thing is that the downloading is only sporadic from the repositories.  From web pages and the internet in general it's still lightning fast.  I didn't have this problem before with my previous install and I don't believe that I've done anything differently.  It's taking hours just to get my software updates done.  I havn't even gotten a chance to install anything yet.  The odd part is that it will jump to 400-600 kB/s for about 10 seconds then drop down to 400 B/s for an hour and a half.  What is going on???

Edit:

I forgot to add that for a while whenever i tried to download from a rep my connection would go dead.  no web browsing or anything would work.  after a few restarts it doesn't do that anymore.  it's just extremely slow.........

---

### Post by jawknee530 on 2007-01-06
Here's the message that i get when i cancel the slow download

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_2.0.4-0ubuntu4_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_2.0.4-0ubuntu4_i386.deb)
  


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-common_2.0.4-0ubuntu4_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-common_2.0.4-0ubuntu4_all.deb)

---

### Post by iver2435 on 2007-01-06
One thing you might try is to use a packet analyzer tool like Wireshark and then filter out all the "normal" packets and see whats left......maybe there is some other device or program competing for bandwidth.

---

### Post by deadgobby on 2007-01-06
What type of internet connection do you have? Like Dial up, Broadband, Cable Modem, and ect..
 It all so can be that the server can be heavy loaded, or you internet service only allows KBS.
Gobby

---

### Post by jawknee530 on 2007-01-06
its a clean installation of edgy so no other programs.  i also bypassed my router and am wired straight to the modem.  even if something else is competing for bandwidth i would get more than 4,000 B/s out of a 10 meg cable connection with 1,250,000 B/s available.  plus when i run an online speed test it says i have 9.7 megs of bandwidth open.  also i had edgy installed on this pc earlier with the same connection and it would regularly download at 500-650 KB/s.  this is a fresh re-install and the problem never appeared on the old install.

---

### Post by bhathco on 2007-01-12
I think there's some issue with Ubuntu's repositories, or something. Every other site I go to and download from is fine, but when I try and download something from the Ubuntu repos, it takes forever.

---

### Post by MasterOfDisaster on 2007-01-13
If this is the problem, go into System --> Administration --> Software Souces.

A dialog should show up, and try changing the 'Download from:' to a different mirror.  Hopefully this solves your problem.

---

