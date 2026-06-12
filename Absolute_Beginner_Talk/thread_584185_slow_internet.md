---
title: "slow internet?"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-10-20
since doing a fresh install from Feisty, my connection is now a lot slower.
it has a 2 -4 second delay before even loading, and then even slow.

this car worked flawless in Fesity,how weird.

its 

Belkin F5D700 V6, wireless PCI card.

anyone else experience slowre rconnection?

---

### Post by Akillese on 2007-10-20
Its called broad band and coz ur on wireless  by thr way get gutsy i dont have dat many errors at all any mor

---

### Post by skymera on 2007-10-20
it is broadband.

what age are we living in!?

and i do have gutsy.

---

### Post by p_quarles on 2007-10-20
Do you mean that it's slower to establish the connection, or that the connection gives you less bandwidth? Does it seem to be related to any specific applications?

---

### Post by Akillese on 2007-10-20
Noob its called Gusty i wrote it by mistake

---

### Post by p_quarles on 2007-10-20
> **Akillese said:**
> Noob its called Gusty i wrote it by mistake
Where are you getting your information? Also, please be aware that calling people names (such as "noob") is not appropriate for these forums.

---

### Post by HermanAB on 2007-10-20
Usually, a slow internet experience is caused by a bad DNS.  The DNS has to be consulted for each and every URL, advertisement, picture, or whatever piece of crud is referenced by a web page, so it has an enormous effect on the page load time.

Your nameservers are listed in /etc/resolv.conf.  Test the name servers using 'dig', then put the fastest one at the top of the list in resolv.conf:

$ dig @ipaddressofnameserver [www.yahoo.com](www.yahoo.com)

Cheers,

Herman

---

### Post by skymera on 2007-10-20
> **Akillese said:**
> Noob its called Gusty i wrote it by mistake

what is wrong with you!?!?

___

ok atm im using open dns.

first off it says

establishing connection... (for about 5 seconds)
transferring data from blah blah (generally slow)

---

### Post by mramsey on 2007-10-20
> **skymera said:**
> since doing a fresh install from Feisty, my connection is now a lot slower.
it has a 2 -4 second delay before even loading, and then even slow.

this car worked flawless in Fesity,how weird.

its 

Belkin F5D700 V6, wireless PCI card.

anyone else experience slowre rconnection?


Check your DNS ip's... I had the same problem. downloads were only hitting 25KB per sec. fixed my DNS now getting 370KB sec.:)

---

### Post by mhiggins on 2007-10-20
had the same problem. fixed up /etc/resolv.conf and am flying !! many thanks !!

---

### Post by moe_syzlak on 2007-11-29
this prolem has been solved here ---> [http://ubuntuforums.org/showthread.php?t=616744](http://ubuntuforums.org/showthread.php?t=616744)

please search the forums for a solution BEFORE asking for help. many problems advanced and some of the noob problems (such as "how do i get root on my computer," or "how to install xxxxx package" that is in the repository) have been fixed. and you can get the answers to your problem by searching

---

### Post by p_quarles on 2007-11-29
> **moe_syzlak said:**
> this prolem has been solved here ---> [http://ubuntuforums.org/showthread.php?t=616744](http://ubuntuforums.org/showthread.php?t=616744)

please search the forums for a solution BEFORE asking for help. many problems advanced and some of the noob problems (such as "how do i get root on my computer," or "how to install xxxxx package" that is in the repository) have been fixed. and you can get the answers to your problem by searching
That's great advice, but if you read carefully you'll notice that this thread is more than a month old, whereas the one you link to was only started a week ago. Please don't bump long-dead threads to chide people.

---

### Post by skymera on 2007-11-29
yeah i was here first.

dont patronise me, im not an idiot.

---

### Post by mhiggins on 2007-11-30
Dear Moe - 

Get over yourself. The whole point of the forums is to encourage people to talk to each other and share ideas. If i wanted to read FAQ's all day I buy fu*cking Windows. 

The the rest of us on this thread - POST ON and ignore those who believe that knowledge is for the"special" and "chosen few".

---

### Post by skymera on 2007-11-30
Well said :)
+10 :D

---

