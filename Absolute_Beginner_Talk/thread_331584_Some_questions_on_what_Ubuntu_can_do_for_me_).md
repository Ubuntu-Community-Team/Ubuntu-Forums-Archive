---
title: "Some questions on what Ubuntu can do for me :)"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by pauliC on 2007-01-04
Well first of all, I'm new here, so HI :D

During the last couple of days I've been playing with the idea of setting up an old pc that is  just collecting dust up in the attic right now, to take care of some day-to-day tasks at my place. (yeh holidays are on and i was bored at times :P) Basically i want to use it as a server for me and my family. I came across Ubuntu (resp. Xubuntu) and I _think_ it fits me quite well.

First of all the technical specifications of that pc:

It has an AMD Athlon XP processor (2000+ or 2200+ I'm not entirely sure)
a Nvidia graphics card (Geforce 4 MX something)
an Asus motherboard

I _think_ i used it before with a Linux distro and it went well (that was some years ago so again I'm not entirely sure...).

I'd call myself rather tech savvy (at least with windows pcs) and I'm also willing to learn a thing or two about Linux. :) What I want this (future) server to do for me is this:

- Replace the router we use right now (It's bitching around A LOT)
- Pose as a backup destination for all the pcs in our house
- Maybe audio and/or video streaming but that is not really needed, would be nice though .. ( I guess that old thing would have a hard time handling 2 or more movies being watched at the same time anyways !?)

- The box will have to handle multiple HDDs (like five or something, i was surprised how many of these we collected over the years :O ) so i guess I'll need some special hardware for this, right ? And i want to assign directories to users that only the can view (like password protection) and some public ones where files can be shared.

- Even though I will have physical access  to the computer i need to control it via a remote connection because there is no spare screen around. (so basically i want to set it up in my room and once I'm finished I want to take it down to the basement and leave it there running for the years to come...)

Now can (X)Ubuntu do that for me ? If it can, which programs will i need to achieve these goals?

Well thanks for reading my (fairly long) post and also thanks in advance for helping me :)

---

### Post by Bachstelze on 2007-01-04
> **pauliC said:**
> 
- Replace the router we use right now (It's bitching around A LOT)


I don't know much about setting up a computer as router myself but I know that quite a few people are doing it and are very happy with it.

> **pauliC said:**
> - Pose as a backup destination for all the pcs in our house

Could you define "backup" ?

> **pauliC said:**
> - Maybe audio and/or video streaming but that is not really needed, would be nice though .. ( I guess that old thing would have a hard time handling 2 or more movies being watched at the same time anyways !?)

Once again something I don't know much about :p

> **pauliC said:**
> - The box will have to handle multiple HDDs (like five or something, i was surprised how many of these we collected over the years :O ) so i guess I'll need some special hardware for this, right ? And i want to assign directories to users that only the can view (like password protection) and some public ones where files can be shared.

If all your HD's are IDE, you'll of course need to have an additional PCI/IDE card givan than most mobos only have four IDE connectors. I've never used one of these myself but I think it shouldn't be a problem. Regarding the personal/shared folders for each user, this can be done very easily. Just add user accounts to the system and use FTP, configuring permissions is very easy too.

> **pauliC said:**
> - Even though I will have physical access  to the computer i need to control it via a remote connection because there is no spare screen around. (so basically i want to set it up in my room and once I'm finished I want to take it down to the basement and leave it there running for the years to come...)

This can be done very easily, too. That's what SSH is for :)

So yes, Ubuntu will do all that for you, with very few programs. SSH can be used to login remotely as well as transfer files with a standard FTP client (SFTP).

---

### Post by bodhi.zazen on 2007-01-04
Yes you can do all this. It is not so much programs as it will be configuration.

Read up on Linux and permissions: [http://www.linux-tutorial.info/modules.php?name=Tutorial&pageid=225](http://www.linux-tutorial.info/modules.php?name=Tutorial&pageid=225)

DHCP server: [http://ubuntuforums.org/showthread.php?&t=236093](http://ubuntuforums.org/showthread.php?&t=236093)

Samba: [http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba)

Restricted formats: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

[http://www.ubuntuforums.org/showthread.php?&t=182902](http://www.ubuntuforums.org/showthread.php?&t=182902)

---

### Post by pauliC on 2007-01-05
thx for the replies :)
just two more questions:

1) do i really need samba ? because i could also do the "sharing" via ftp as HymnToLife pointed out (like have some public directories and some private ones, where users can backup data important to them), no ?

2) i've been looking for some ide controllers and mainly found ones for Ultra ATA/133. The thing is that the majority of my hdds are Ultra ATA/100. will they also work with these controllers or do i need Ùltra ATA/100 ones ?

Oh and another thing came to my mind: I will have to install two network cards in that computer right ?

So the setup would look like this: User PCs ---(Hub)---> Router Box ----> DSL Modem --> WWW

Well thx for the quick replies i guess i'll get started reading about Linux over the weekend :D

---

