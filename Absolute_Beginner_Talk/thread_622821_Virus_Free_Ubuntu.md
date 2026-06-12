---
title: "Virus Free Ubuntu"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by expatCM on 2007-11-25
My smtp has just started to refuse my traffic.  Something about my local ISP is blacklisted on the spamhaus xbl.  Looked it up and the IP is certainly there.  Reading on spamhaus this blocking is due to a dynamic IP having been used for spamming or more likely virus infected traffic being sent form the dynamic IP (or both).

I assume that I have not received any virus infected messages from Windows users but I would like to be sure.  

I have had a look at clamav but get the idea that this is really the wrong package, this seems to be more appropriate for use on a server.  In any event it does not appear to be exactly GUI user friendly.

Free AVG keep their Linux version very hidden.  Perhaps it is no more.

Are there any suggestions of GUI managed anti virus packages which will scan Thunderbird outgoing traffic and any incoming appended files?

---

### Post by Ub1476 on 2007-11-25
You may want to try Firestarter (repos). 

But no, you wont get any Linux virus on your box, you might get Windows virus though, but they wont do anything.

---

### Post by Partyboi2 on 2007-11-25
Avg for linux:
[http://free.grisoft.com/doc/5390/us/frt/0?prd=afl](http://free.grisoft.com/doc/5390/us/frt/0?prd=afl)
(I could never get it to work)
Avast
[http://www.avast.com/eng/avast-for-linux-workstation.html](http://www.avast.com/eng/avast-for-linux-workstation.html)
(never tried it with linux, only windows)

---

### Post by candtalan on 2007-11-25
I see it as the fourth listed file at
[http://free.grisoft.com/doc/5390/us/frt/0](http://free.grisoft.com/doc/5390/us/frt/0)

Although I believe it will be most unlikely that your ubuntu will have been affected by windows viruses, it will make pretty big news if it has!

Linux is easy to secure, although it is not invulnerable. There are ways of checking it although I do not know much about this.
good luck

---

### Post by expatCM on 2007-11-25
I also agree that Ubuntu is not likely to have a virus infection but what I do want to make sure is that no Windows user has accidentally given me a Windows virus in my email ....  which I then pass on to others :)

---

### Post by tech0007 on 2007-11-25
Hi,

Clamav works for me. Make sure you have all relevant programs installed: 

clamav clamav-base clamav-freshclam libclamav2 libgmp3c2 clamtk libbit-vector-perl libcarp-clan-perl libdate-calc-perl libfile-find-rule-perl libnumber-compare-perl libtext-glob-perl.
Clamtk is the gui.

Good luck.

---

### Post by expatCM on 2007-11-25
ah ... clamtk ....  the gui I did not know existed ....  yes, that makes it a lot easier ... thank you.

---

### Post by poision_heart on 2007-11-25
hey guys do u really need antivirus for linux???i heard linux is virus free then why so many antivirus available for linux??

---

### Post by expatCM on 2007-11-25
Its so that the virus that the Windows user sent to you that you did not notice because it does not affect you is not a problem when you accidentally pass it on to another Windows user :)

---

### Post by gn2 on 2007-11-25
Let the Windows PC's look after themselves, don't bog your system down with entirely unnecessary AV software.

---

### Post by expatCM on 2007-11-25
I may be mistaken but if you are sending virus infected attachments from your Windows user friends,  some ISP's will block the traffic.

---

