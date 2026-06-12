---
title: "Software update tool doesnt work"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by dantastik on 2006-07-15
I hope a similar post wasnt already present, but ive been using linux for less than 24 hours so maybe i just dont know where to look.

Anyway, when i open the software update utility it says  "Your system is up to date"

I click on the "check" button anyway and it starts "downloading package information". It starts downloading files and it immediately gets to "file 5 of 9". At this point it stops for ages. I expand where it says "shows progress of single files"

Another window opens up and this is the content:

___________________________________________________________________________

[http://gb.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0), connection timed out

[http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:) Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0), connection timed out

[http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:) Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0), connection timed out

[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out

[http://www.beerorkid.com/automatix/apt/dists/dapper/Release.gpg:](http://www.beerorkid.com/automatix/apt/dists/dapper/Release.gpg:) Could not connect to [www.beerorkid.com:80](www.beerorkid.com:80) (1.0.0.0), connection timed out
___________________________________________________________________________


it cant be the connection cause im online now.
any suggestions on how i can get it to work?
is it why i cant download automatix?

Thank you very much in advance :)

dan

---

### Post by Swab on 2006-07-15
Perhaps the servers were down for a while...  You could try an update from the terminal.

```

sudo apt-get update && apt-get upgrade  (enter your password)

```

---

### Post by dantastik on 2006-07-15
i did try that, get the same results, with some extra lines...
and yes, i am logged on as the root user :)

____________________________________________________________________

oem@ubuntu:~$ sudo apt-get update && apt-get upgrade
Password:
Errhttp://security.ubuntu.com dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out

Errhttp://gb.archive.ubuntu.com dapper Release.gpg
  Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0), connection timed out

Errhttp://www.beerorkid.com dapper Release.gpg
  Could not connect to [www.beerorkid.com:80](www.beerorkid.com:80) (1.0.0.0), connection timed out

Errhttp://gb.archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0), connection timed out

Errhttp://gb.archive.ubuntu.com dapper-backports Release.gpg
  Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0), connection timed out

Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Co uld not connect to gb.archive.ubuntu.com:80 (1.0.0.0), connection timed out

Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release) .gpg  Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0), connection timed out

Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/Relea](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/Relea) se.gpg  Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0), connection time d out

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release). gpg  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out

Failed to fetch [http://www.beerorkid.com/automatix/apt/dists/dapper/Release.gpg](http://www.beerorkid.com/automatix/apt/dists/dapper/Release.gpg)  Could not connect to [www.beerorkid.com:80](www.beerorkid.com:80) (1.0.0.0), connection timed out

Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used  instead.

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by Swab on 2006-07-15
> (1.0.0.0)

That seems strange, like there is a problem resolving the addresses.  And you say internet is working otherwise?  Can you ping, say google.com from the terminal? "ping google.com"

---

### Post by dantastik on 2006-07-15
that seemed strange to me as well.

i can ping google no probs, as well as, say, beerorkid.com, which is one of those that come up as 1.0.0.0 in the update!
im puzzled and beginning to think i should should start saving up for a mac :)

___________________________________________________________________________
oem@ubuntu:~$ ping beerorkid.com
PING beerorkid.com (208.97.133.175) 56(84) bytes of data.
64 bytes from beerorkid.com (208.97.133.175): icmp_seq=1 ttl=43 time=206 ms
64 bytes from beerorkid.com (208.97.133.175): icmp_seq=2 ttl=43 time=221 ms
64 bytes from beerorkid.com (208.97.133.175): icmp_seq=3 ttl=43 time=166 ms
___________________________________________________________________________

really appreciate the quick replies :)

---

### Post by GTvulse on 2006-07-15
```

Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0)

```

That IP address is very, very wrong. There is a problem with the DNS servers you are using, be it your ISPs or the DNS proxy in your ADSL modem/router.

---

### Post by catlett on 2006-07-15
What kind of modem are you using? This issue is all over google. It is about your network connections and your hardware. 
Open Systen<Adminidtration<Networks then click on DNS tab.
You probably have DHCP. This is the typical way of accessing. The issue is the DHCP connecting you with DNS Servers.
There are a couple of things you can do but they depend on your level of linux ability.
Browse this thread for a better idea of what is happening. (Mepis is a "cousin" of Ubuntu so most of what is said is the same for ubuntu)
[http://www.mepis.org/node/10306](http://www.mepis.org/node/10306)

---

### Post by dantastik on 2006-07-15
thats what i thought, but i got confused when i realised i could ping it, and even open the site in a browser.
out of curiosity, is there any way to find out if theres people in london, uk who could sort this out for me? my boss is happy to pay for my i.t. needs :)

---

### Post by catlett on 2006-07-15
If you are serious, Ubuntu's parent corporation Canonical offers paid support for Ubuntu's desktop and server edition. [http://www.ubuntu.com/support/paid](http://www.ubuntu.com/support/paid)

---

### Post by dantastik on 2006-07-15
> **catlett said:**
> If you are serious, Ubuntu's parent corporation Canonical offers paid support for Ubuntu's desktop and server edition. [http://www.ubuntu.com/support/paid](http://www.ubuntu.com/support/paid)

I am, but is it gonna be something on the phone-email or does somebody come and do it for you? cant get things to work and people on here try to be helpful, im just wasting their time i believe. the paid support is still cheaper than a mac...

---

### Post by catlett on 2006-07-15
I don't know much about the support, I never used it myself. But Canonical has a support network outside of itself. They areh African so you might want to try them directly for help in London. If not browse the list of Ubuntu support providers [http://www.ubuntu.com/support/marketplace/europe](http://www.ubuntu.com/support/marketplace/europe) scroll down to "Northern Europe", there is a "United Kingdom" section.

---

### Post by dantastik on 2006-07-16
thanks a lot to everybody for their help.
tried all the suggestions given yesterday, didnt work.
it did this morning!

cheers :)

---

### Post by kilis on 2006-07-16
the problem was not [http://gb.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:)

But

[http://gb.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg) :P

---

