---
title: "anti-virus software"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by notmicrosoft on 2007-09-27
Lynux and the Ubuntu are new compared to Microsoft!?
What's the best anti virus and firewall protection etc... I can get for my new Ubuntu system?

---

### Post by floke on 2007-09-27
Do yourself a favour and do some forum searches - there's literally gazillions on this topic.
Short answer though - you don't need any.

Welcome to Linux!

** PS: Linux was invented in 1991 - so not that new - and is a clone of UNIX, which grew up in the 1970s - so really it's older than Windows.

---

### Post by lisati on 2007-09-27
You'll find a variety of opinions are out there. The general consensus of what I've read is that you probably don't need to worry too much about viruses on Linux & Ubuntu systems, and that Linux is generally more secure than "the other OS" (WIndows)

There are several options: clamav and AVG antivirus come in Linux versions, to name just two. As for firewall, I hear that Ubuntu comes with one pre-installed (called iptables) - a "front end" for this is "Firestarter" (which I haven't used and you might need to install if you want to use it.

---

### Post by oldos2er on 2007-09-27
Linux has been around since 1991.
 You might want to read [http://psychocats.net/ubuntu/security](http://psychocats.net/ubuntu/security)

---

### Post by lisati on 2007-09-27
> **floke said:**
>  <snip>
** PS: Linux was invented in 1991 - so not that new - and is a clone of UNIX, which grew up in the 1970s - so really it's older than Windows.
I might be mistaken but I think there have been versions of Windows around since the late 1980s......MS-DOS, upon which Windows first got started, has certainly been around since the 1980s.

---

### Post by prcm311 on 2007-09-27
I'm new to Ubuntu, but that best place to start is Synaptic for any programs.  Although you won't always get bleeding-edge software.

I ran a search for "anti virus" and I got a list of a few programs.  Search this forum to see which one is best for you.  Personally I don't use any.  I was always told "you can't get viruses with linux."  I know that's not entirely true... but I still don't have it.

---

### Post by ddrichardson on 2007-09-27
> **lisati said:**
> I might be mistaken but I think there have been versions of Windows around since the late 1980s......MS-DOS, upon which Windows first got started, has certainly been around since the 1980s.

I've heard that said before and it's not really the case. Windows could not be considered an OS in it's early incarnations. MS-DOS in it's earliest version 1.14 was in 1981, version 1.0 of Windows was in 1985 and was absolutely awful. Windows NT 3.51 in 1993 was the first version that embedded an OS rather than run on top of DOS and truth be told current versions of Windows have absolutely nothing to do with DOS, they relate to the New Technology (NT) kernel in 1993.

UNIX on the other hand has been around since Bell Labs in 1969. Of course the same arguments could be made for X, but that has been around since 1984.

So the long and the short of it is, age wise - UNIX, MS-DOS, Windows, Linux; making Linux the new kid on the block. But the truth is that it's comparing apples to oranges because Linux has supported a number of features that Windows didn't even consider until much later - pre-emptive multitasking for a start which doesn't appear until 1993 (in NT).

---

### Post by santiagoward2000 on 2007-09-27
> **notmicrosoft said:**
> Lynux and the Ubuntu are new compared to Microsoft!?
What's the best anti virus and firewall protection etc... I can get for my new Ubuntu system?

As most people would tell you, the antivirus is not needed in linux. Yet, if you are new to this, and are paranoid after some years in windows (I am too :lolflag: ) you could install Firestarter and ClamAV, they are in Feisty's repo.

---

### Post by expatCM on 2007-09-27
Anti virus MAY be needed ... not because a virus is going to hit your system, rather more that if you receive and forward email messages to Windows users, if any message is infected with a virus you will be seen to be spreading that virus (albeit innocently) when you forward.

The other point is that if you decide to run Wine, it may be possible for a virus infection to exist there and cause the normal havoc in the Wine directory.

Someone please make a post and tell me I am wrong here .....

---

### Post by HermanAB on 2007-09-27
Don't worry, be happy.  This is Linux, relax and enjoy it.

The reason being that firewall software is built right into Linux (netfilter, iptables, tcpwrappers), so you already have it and it is already configured in a simple but effective way.  Most people don't need anything more than the default configuration.

If you wish to run a public server that will be exposed to the public internet, then you should consider running a more serious firewall configuration script like Shorewall.  

Virus?  What is a virus? Never seen one...

If you run a mail server for a small office, then you can use ClamAV and SpamAssassin to filter email for the other users.

Here is a better explanation:
[http://www.gnu.org/fun/jokes/evilmalware.html](http://www.gnu.org/fun/jokes/evilmalware.html)

Cheers,

Herman

---

### Post by hyper_ch on 2007-09-28
[QUOTE=expatCM;3438449] not because a virus is going to hit your system, rather more that if you receive and forward email messages to Windows users, if any message is infected with a virus you will be seen to be spreading that virus (albeit innocently) when you forward.[QUOTE]

I don't care for that... if Windoze people can't handle their computers and get infected by a virus it's their fault. Why should I use my resources to give them more security?

---

### Post by bigken on 2007-09-28
if you realy feel the need for a anti virus software you could download the 
avg free version if you do run this command in a terminal after you install
[B]sudo adduser yourname avg 
[/B]

---

### Post by nowshining on 2007-09-28
no need for an anti-virus but a firewall is vital and one is incl. in ubuntu iptables - also by default ubuntu has literally no services listening out to the public internet :) i'm using arno-iptables-firewall - easy  to setup, use and modify.

---

### Post by nowshining on 2007-09-28
by the way I hate avg it sucks - i liked it on windows, but ubuntu - what a pain in the behind - it would ignore the free reg. key ,etc.. at times, etc.. I am now using f-prot for linux which is free for home use with a GUI frontend.. - both have no on-access scanning - however there is no need.

[http://www.howtoforge.com/f_prot_antivirus_ubuntu_feisty](http://www.howtoforge.com/f_prot_antivirus_ubuntu_feisty)

---

### Post by ddrichardson on 2007-09-28
AVG works well on Linux, you just need to add the user to the AVG group. It also came out well in several recent independent tests, where Norton scored as low as 7% detection rate.

As for the firewall thing, all ports are closed by default so unless you have a specific need to open a port (for torrents or such like) there is no need to panic.

---

### Post by por100pre1 on 2007-09-28
If you want, you can search for rootkits with chkrootkit and rkhunter:

```
sudo aptitude install chkrootkit rkhunter
```

To use them:

```
sudo chkrootkit
```

```
sudo rkhunter --update && sudo rkhunter -c -sk
```

---

### Post by nowshining on 2007-09-28
i installed both and the latter just a bit ago - I did get a few False positives. :P

---

### Post by SirJ77 on 2007-09-28
Ah I love the "linux doesn't have viruses" and "it the windows users problem" arguments, both of which are wrong.  Just because you run linux, doesn't make you cool.

I've had to fix enough computers over the years because of viruses, I'm not going to subject a friend to a virus just because I was too lazy (if I do, I'll probably be the one call for help).

I ran F-prot on windows for a long time (I believe the linux version is free, and I think it's in the package manager), I just installed ClamAV, see how it works for me.
Also ran the free version of AVG on windows boxes with good success (has managed to protect ppl that insist on using outlook for email).

A little tidbit for you... per one list I found there are 539 Linux viruses.  They do exist.
[http://vx.netlux.org/vl.php?dir=stat](http://vx.netlux.org/vl.php?dir=stat)
An article the says about the same thing.  Granted, it's small % of viruses, but I get in trouble when I gamble with computers, they throw me for a loop almost every time.
[http://www.contractoruk.com/news/002139.html](http://www.contractoruk.com/news/002139.html)

---

### Post by ddrichardson on 2007-09-28
> **SirJ77 said:**
> Ah I love the "linux doesn't have viruses" and "it the windows users problem" arguments, both of which are wrong.  Just because you run linux, doesn't make you cool.

I've had to fix enough computers over the years because of viruses, I'm not going to subject a friend to a virus just because I was too lazy (if I do, I'll probably be the one call for help).

I ran F-prot on windows for a long time (I believe the linux version is free, and I think it's in the package manager), I just installed ClamAV, see how it works for me.
Also ran the free version of AVG on windows boxes with good success (has managed to protect ppl that insist on using outlook for email).

A little tidbit for you... per one list I found there are 539 Linux viruses.  They do exist.
[http://vx.netlux.org/vl.php?dir=stat](http://vx.netlux.org/vl.php?dir=stat)
An article the says about the same thing.  Granted, it's small % of viruses, but I get in trouble when I gamble with computers, they throw me for a loop almost every time.
[http://www.contractoruk.com/news/002139.html](http://www.contractoruk.com/news/002139.html)

You're preaching to the converted, check out my blog if you want to see my opinion on Linux Viruses. Stand by though because the last time I voiced those opinions it nearly started a flame war ;-)

---

### Post by bigken on 2007-09-28
> **nowshining said:**
> by the way I hate avg it sucks - i liked it on windows, but ubuntu - what a pain in the behind - it would ignore the free reg. key ,etc.. at times, etc.. I am now using f-prot for linux which is free for home use with a GUI frontend.. - both have no on-access scanning - however there is no need.

[http://www.howtoforge.com/f_prot_antivirus_ubuntu_feisty](http://www.howtoforge.com/f_prot_antivirus_ubuntu_feisty)

you dont need a key now :)

---

