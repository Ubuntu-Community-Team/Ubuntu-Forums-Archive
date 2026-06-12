---
title: "Avast Antivirus &quot;Simple User Interface&quot;"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by ameanjoe on 2008-04-06
I recently started using Ubuntu 7.10 and wanted to install Avast Antivirus (as I have on my Window machine). The user interface is completely different and the type fonts used are so small I want a magnifying glass to read them. I tried contacting Avast Support and after a couple of months got a reply.
First was to re-download and install "the most recent version of Avast". Did that (Same version I had)
Next was directions to install KDE/GNOME menu icons. Did that. Didn't change anything.
(sudo /usr/lib/avast4workstation/share/avast/desktop/install-desktop-entries.sh install)
Third was to modify (as root): (usr/lib/avast4workstation/bin/wrapper-script.sh) three lines starting with #136. The terminal came back saying: "No such command exists..."
Has anyone had any experience with Avast? Maybe has experienced a similar situation...

---

### Post by tdrusk on 2008-04-06
I don't use an antivirus in Ubuntu, so I can't really help you. It's not really needed.

I suggest reading the documentation for the program.

---

### Post by DariusS on 2008-04-06
I think (and correct me if I am wrong) that I speak for a large number of people in the Linux community in that anti-virus software in Linux is not explicitly necessary as it is in windows.
I myself do not even run any spyware/malware/antivirus software on my Ubuntu install, but my Winxp install has AVG and spybot, plus a third party firewall. I do have a firewall in Ubuntu (firestarter) but don't always use it. I turned off my firewall in windows for 2 hours the other day, and had to spend wayyyyy too much time fixing all the incurred problems.
I know this doesn't really help in your question, but kinda curious why you need an anti-virus app in Linux in the first place.

---

### Post by myusername on 2008-04-06
as far as i know there is only 1 type of virus that you can get in linux and it really doesn't do anything....so no need for an antivirus..but a firewall is always good (ubuntu has one built in)

---

### Post by ameanjoe on 2008-04-07
Thank you to all of the folks who replied to my dumb question...Having spent way too many years subjected to MicroSoft, I wasn't sure if Linux was really free of viruses. I've heard it said that it is, but you hear lots of stories and I don't like to gamble. One virus can spoil a good day....
They say you can't teach old dogs new tricks...I'm learning new ones every day.
Again, Mahalo nui loa, (Who knows, one day I'll figure out how to thank folks individually....
ameanjoe

---

### Post by SunnyRabbiera on 2008-04-07
still if you want an antivirus there is a better one for linux to scan for stuff on windows drives and also for any windows apps you can install on linux via wine, its called clamAV.
you can get it in the repositories, it also has a gui called KlamAV.

---

### Post by hyper_ch on 2008-04-07
Unlike Windows Linux has been patched for all known viruses (all in all about 60 or so)...

The main reason to use AV on linux is to scan for infected files that are shared with windows users... so if you operate a file- or mailserver you may want to virus check attachments and documents... however I'm of the opinion that each one should be responsible on their own.

---

### Post by brian_p on 2008-04-07
> **ameanjoe said:**
>  . . . . Has anyone had any experience with Avast? Maybe has experienced a similar situation...

The interface uses GTK2. There is. if I recollect correctly, a way of altering the font size in a .gtkrc file. Search with "font size" and "GTK" on your favourite search engine.

---

### Post by brian_p on 2008-04-07
> **hyper_ch said:**
> Unlike Windows Linux has been patched for all known viruses (all in all about 60 or so)...

I'd say it is the security model of Linux (separation of user and system) which makes it safer than Windows.

A virus has to be capable of spreading. There are zero viruses for Linux.

---

### Post by brian_p on 2008-04-07
> **myusername said:**
> ...but a firewall is always good (ubuntu has one built in)

Ubuntu comes with safe default configurations. Firewalling is completely unnecessary.

---

### Post by hyper_ch on 2008-04-07
> **brian_p said:**
> There are zero viruses for Linux.
There are about 60 known viruses for linux... while Linux is safer by default, don't underestimate social engineering...

> **brian_p said:**
> Ubuntu comes with safe default configurations.
By default iptables is unconfigured - but by default you don't have services listening either...

---

### Post by brian_p on 2008-04-07
> **hyper_ch said:**
> There are about 60 known viruses for linux... while Linux is safer by default, don't underestimate social engineering...

There are trojans and worms. There are no viruses.

> By default iptables is unconfigured - but by default you don't have services listening either...

Which makes a firewall completely unnecessary. I take it we are in agreement.

---

### Post by SunnyRabbiera on 2008-04-07
> **hyper_ch said:**
> There are about 60 known viruses for linux... while Linux is safer by default, don't underestimate social engineering...


By default iptables is unconfigured - but by default you don't have services listening either...

actually those viruses are really concept only, sure if people wanted to those viruses can wreak havoc but I dont think it will ever come to be as bad as it is on windows.
and you might be more thinking of apple OSX.

---

### Post by hyper_ch on 2008-04-07
> **brian_p said:**
> There are trojans and worms. There are no viruses.
There are ;)

    * Alaeda - Virus.Linux.Alaeda[6]
    * Bad Bunny - Perl.Badbunny[3][7]
    * Binom - Linux/Binom[8]
    * Bliss
    * Brundle[9]
    * Bukowski[10]
    * Diesel - Virus.Linux.Diesel.962[11]
    * Kagob a - Virus.Linux.Kagob.a[12]
    * Kagob b - Virus.Linux.Kagob.b[13]
    * MetaPHOR (also known as Simile)[14]
    * Nuxbee - Virus.Linux.Nuxbee.1403[15]
    * OSF.8759
    * Podloso - Linux.Podloso (The The iPod virus)[16][17]
    * Rike - Virus.Linux.Rike.1627[18]
    * RST - Virus.Linux.RST.a[19]
    * Satyr - Virus.Linux.Satyr.a[20]
    * Staog
    * Vit - Virus.Linux.Vit.4096[21]
    * Winter - Virus.Linux.Winter.341[22]
    * Winux (also known as Lindose and PEElf[23]
    * ZipWorm - Virus.Linux.ZipWorm[24]

---

### Post by SunnyRabbiera on 2008-04-07
yeh but look how small it is, plus with proper knowledge they can be evaded.
Now linux isnt bullet proof to be sure, but its nowhere near Windows or even OSX.
maybe in a few years we will have more, but linux has some of the best developers on the job :D

---

### Post by hyper_ch on 2008-04-07
> **SunnyRabbiera said:**
> yeh but look how small it is
So? You said there are none... q.e.d.

> **SunnyRabbiera said:**
> plus with proper knowledge they can be evaded.
That was not to be disputed...

---

### Post by brian_p on 2008-04-07
> **hyper_ch said:**
> There are ;)

    * Alaeda - Virus.Linux.Alaeda[6]
    * Bad Bunny - Perl.Badbunny[3][7]
    * Binom - Linux/Binom[8]
    * Bliss
    * Brundle[9]
    * Bukowski[10]
    * Diesel - Virus.Linux.Diesel.962[11]
    * Kagob a - Virus.Linux.Kagob.a[12]
    * Kagob b - Virus.Linux.Kagob.b[13]
    * MetaPHOR (also known as Simile)[14]
    * Nuxbee - Virus.Linux.Nuxbee.1403[15]
    * OSF.8759
    * Podloso - Linux.Podloso (The The iPod virus)[16][17]
    * Rike - Virus.Linux.Rike.1627[18]
    * RST - Virus.Linux.RST.a[19]
    * Satyr - Virus.Linux.Satyr.a[20]
    * Staog
    * Vit - Virus.Linux.Vit.4096[21]
    * Winter - Virus.Linux.Winter.341[22]
    * Winux (also known as Lindose and PEElf[23]
    * ZipWorm - Virus.Linux.ZipWorm[24]

Bliss and staog I know about. It is highly doubtful bliss has ever been in the wild and in any case it has to be run by root and doesn't spread, so it is not a virus. There is discussion about its exact nature but for simplicity's sake I'd classify it as a trojan.

Staog is a laugh. It dates back to 1996 and requires at least a 1.something kernel to get out of bed. Infects files in the same directory as itself so root would have to place it in the system files. Doesn't spread. A trojan? Who cares?

Evil Bunny and Satyr look interesting.

Google sources say Evil Bunny is a worm. It's probably not because it does not attack a network service. There is no sign of it being able to move *by itself* from user space to system space. Not a virus.

Satyr is an ELF infector like staog. It is similarly useless as a virus.

Sorry, I do not have time at present to go through the rest of the list. If others did I bet they would find that either root assistance is required to get them to even infect or that they they are worms.

---

### Post by SunnyRabbiera on 2008-04-07
> **hyper_ch said:**
> So? You said there are none... q.e.d.


That was not to be disputed...

No I didnt say there were none, just not many that worked.

---

### Post by hyper_ch on 2008-04-07
> **SunnyRabbiera said:**
> No I didnt say there were none, just not many that worked.

> **brian_p said:**
> There are no viruses.

:popcorn:

---

### Post by DariusS on 2008-04-07
I think people are getting a bit off topic here.
the point is to try to help in answering the question I believe.
I for one have not tried clamAV, but have heard nothing but positives about it. I think it's safe to say that any software native to the OS will work more intuitively, or simply. porting an app like Avast may be nothing more than a headache. Not to say I'm not for cross-platform apps, I couldn't live without Firefox on both my windows install and Ubuntu, but i don't use winamp outside of windows, I use Amarok. point is, find what works best for you. it might not always be what you want to work best, but it may give you the least headache in the long run.

---

