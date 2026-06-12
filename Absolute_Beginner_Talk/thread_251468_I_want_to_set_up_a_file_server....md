---
title: "I want to set up a file server..."
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by mpaneitz on 2006-09-05
and have heard that Linux is the best way to go.  As I have no experience in this, is ubuntu the way I should go?

My plan is install this on an old P3 machine.  I have 4 macs and a PC on my network.  Can I just set this up as another wirless device on my network and use it wirelessly?

I apologize for the ignorant post but I'm totally unsure of the best flavor of linux.  If Ubuntu will meet my needs I will then go to the How to's for any additional questions I have.

Thanks!

---

### Post by kidders on 2006-09-05
Hi there,

I can't think of a single reason to go for one Linux over another, if all you're interested in is sharing files ... they all work pretty much identically. One possible factor is your wireless adapter ... be sure Ubuntu supports it! The other might be RAM. How much of it is there in your P3?

In terms of the actual filesharing itself, you have a few choices in terms of exactly how you go about it, depending on what the one PC you have is running on. If it's Windows, then you're stuck with sharing files Bill Gates' way :(

Assuming you *do* need a windows-compatible fileserver, take a look at samba. Once you install it, basic configuration is done in a file called /etc/smb.conf or /etc/samba/smb.conf (depending on your eventual choice of Linux flavour). I can talk you through it if you need a hand.

Another option would be to share files Apple's way, since you have so many Macs. I'm running limited AFS-based filesharing on my own network, and I'm pretty happy with it :)

Incidentally, your post is far from ignorant, so don't worry! The filesharing part is the easy bit ... doing it wirelessly will be the headache (depending on your hardware) but it should work a treat in the end.

---

### Post by Klaidas on 2006-09-05
The distro... Ah, I remember choosing
The best way to choose is to try it. Try out Ubuntu, Fedora, Gentoo, Slackware, Suse, Debian, etc and decide which of those best suits your needs ;)

---

### Post by mpaneitz on 2006-09-05
It was my understanding that SAMBA is in every version of Linux?  Is that not the case or does it just require specific setup?
Where do I find out if my wireless router is compatible?  I have a D-Link Rangebooster N router and I would like to install the rangebooster desktop adapter in this machine to make for a faster connection, if possible.

---

### Post by kidders on 2006-09-05
I'm sure you could find a Linux distro that can't handle samba if you REALLY looked hard ... but I can't think of one! Likewise, Apple filesharing works on all modern Linuxes, too.

Maybe Klaidas knows something about your wlan adapter ... I've never used it :( The Ubuntu docs will probably tell you about supported hardware, but you'd have to try to be sure, if yours isn't listed.

Btw, samba/afs setup is almost identical, regardless of your distro.

---

### Post by dmeehan on 2006-09-06
have a look at this for configuring samba: [http://ubuntuforums.org/showpost.php?p=1265314&postcount=2](http://ubuntuforums.org/showpost.php?p=1265314&postcount=2)

---

### Post by tomBorgia on 2006-09-06
you could try good ol' fashioned ftp...?

---

### Post by jd65pl on 2006-09-06
I use FTP but viewing on a windows machine is sometime odd due to firewall. works fine most of the time tho.

---

### Post by Uluen on 2006-09-06
Fileserver with wireless? I guess you won't move lots of DVD ISOs and such ;)

---

### Post by jd65pl on 2006-09-06
Mine uses wireless with FTP and takes about 10 mins to transfer  1GB

---

### Post by tomBorgia on 2006-09-06
its a bit of a difficult soluiton - samba being the best option I suppose as all 3 operating systems will work over it (if its all set up correctly!!!)
NFS would be fine for your apple pcs but won't play with your win pc. FTP is a pig to get to work with firewalls as it tends to need more than just port 21 open in some way... is it the windows pc's firewall thats the problem or the ubuntu end? I've had numerous problems with SMB on ubuntu, not that I've tried that hard to fix them... just boot into windows and access the files from there ;-)

---

### Post by jd65pl on 2006-09-06
i wouldn't say I have any real problems with it as I can fix all the issues on my windows PC. it runs fine for my just when I try to use the inbuilt ftp function in explorer it doesn't work so well. It works fine thru ftp in firefox or filezilla on windows. I have no problem what so ever accessing through my linux pc.

I was just highlighting it might not be the most stable route to go.

---

### Post by kidders on 2006-09-06
Imho, NFS and FTP wouldn't be terribly efficient options, unless the only thing you're interested in is being able to copy files from one location to another. Random access would be a real pain!

I make very heavy use of Samba (running as a domain controller) with Windows, OSX and several flavours of Linux, and I'm quite happy with it. The only problem I have with it is the silly filename restrictions, but there ain't a lot that can be done about that :(

---

### Post by tomBorgia on 2006-09-06
Think its a moot point as the only thing that will work in any kind of useful way (i.e. not ftp - it's a bit cumbersome) with your windows box, is, yes, windows tech! NFS would work similarly to windows' mapped network drive - im sure "random access" would be fine... but as I say, its a moot point cuz u can't get windows to deal with NFS at all...

---

### Post by mpaneitz on 2006-09-06
Wow, thank you all for the responses.

I believe I need to clarify.  My XP box has absolutely nothing on it.  My hd died and I had to get a new one so I installed XP, and a couple of apps but nothing else.  It's on my network but it's not a real important part to me.  

The main reason I want to go Wireless is that I don't have any space where my modem and router are located to put anything else.  But I do have a question we have a wifi network at work that allows me to transfer files pretty quickly, how would this be much slower than that?

So basically I'm looking for the best solution to transfer files from my mac and create centralized storage.

---

### Post by kidders on 2006-09-06
Samba :)

---

