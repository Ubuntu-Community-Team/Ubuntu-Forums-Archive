---
title: "Does Bittorrent and similar P2P softwares affect of threathen the security of Ubuntu?"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by cool_penguin on 2007-08-03
Hi Guys, 

I am relatively new to Ubuntu and have been using it just over 2 months now. I have a basic question. If i  wanna use a torrent downloading program like Bittorrent or another file sharing program like Limewire, would it affect the security and / or stability of Ubuntu?

When i say security, i mean, do any of these programs (when used) open up ports of Ubuntu and makes it susceptible to virus attacks, attacks by malicious code or hackers?

I am presently using Bittorrent on my Mac Mini, and it seems to be fine, but since my Ubuntu is more precious to me, i wanted to consult you guys before i install any of these P2P or file sharing programs. 

I would be very thankful to all of your for your inputs and feedback on the same.

Thanks a lot.

Long live UBUNTU.

Cheers,
Harry

---

### Post by Malh on 2007-08-03
I've been using Azureus for about 6-7 months and I've had no problems with security.

---

### Post by cool_penguin on 2007-08-03
Did you check for open posts with any online port scanner?

Thanks for your quick response.

Cheers,
harry

---

### Post by dannyboy79 on 2007-08-03
> **cool_penguin said:**
> Hi Guys, 

I am relatively new to Ubuntu and have been using it just over 2 months now. I have a basic question. If i  wanna use a torrent downloading program like Bittorrent or another file sharing program like Limewire, would it affect the security and / or stability of Ubuntu?

When i say security, i mean, do any of these programs (when used) open up ports of Ubuntu and makes it susceptible to virus attacks, attacks by malicious code or hackers?

I am presently using Bittorrent on my Mac Mini, and it seems to be fine, but since my Ubuntu is more precious to me, i wanted to consult you guys before i install any of these P2P or file sharing programs. 

I would be very thankful to all of your for your inputs and feedback on the same.

Thanks a lot.

Long live UBUNTU.

Cheers,
Harry
if you're torrenting correctly than yes, you have to open up ports on your computer so that leechers can connect to you so that you can join the swarm. If you don't open ports you're download speed will be horrible and you're also not following the unwritten rule of torrenting. Which is, if you want it, share it!

I am not familar with limewire but again if it's like P2P application, you'll have to open up some ports. 

I have been torrenting for more than 4 years and have not heard or read about a torrent vulnerability although I wouldn't be surprised when some1 chimes in and tells me that there is. 

You can see what ports are listening by using

netstat -pant on your local machine. IF you have a router or similar than it doesn't matter what ports are listening because that router is blocking everything coming in except for what you port forward. you can use nmap from a windows machine (gogle to download program) or you can use nmap from another Linux machine (download thru package manager) or you can use shieldsup or similar to see what ports are open and or listening.

---

### Post by Ek0nomik on 2007-08-03
dannyboy79 hit it right on the head.

If you are connecting to peers with ports open, then yes you lose some security.  I have been using bittorrent for about 4 years as well, and I have never ran into any troubles (at least none that I ever noticed).

So, yes, P2P software affects your security, but it's not a major issue (as far as I am concerned).

I shall keep torrenting until a new platform is developed.   :)

---

### Post by Inxsible on 2007-08-03
As a bonus, Linux is more secure than Windows when it comes to viruses because

1) There are not many known viruses for Linux
2) Even if a virus gets in, it will need root access to do something horribly bad (which can happen)

---

### Post by Nythain on 2007-08-03
yeah... like its already been said... TECHNICALLY you are going to lose a wee bit of security ANY time you open a port for anything.

the marvel of torrent clients though is the ability to pick your port or even have it random in some clients. As good practice you should always pick a really high and uncommon port.

overall i would say its less of a security risk than running an http or ftp server... those use very specific and common popular ports wich get attacked on a regular basis. i wouldnt worry to much about it in the end... i've been using bittorrent clients for about 5 years or so now and havent gotten attacked yet, on windows or linux.

a sidenote... your chances of attack increase slightly just by being on a popular national isp (ie RoadRunner, AOL, etc)... lots of port scnners have popular isp ip ranges set up by default so chances are there's a random script kiddie with half a brain out there scanning the entire roadrunner range of ip's for open ports right now...

---

### Post by dannyboy79 on 2007-08-03
rkhunter and chkrootkit are good apps to look for hidden stuff which can cripple your system.

I've been wanting to setup clamav to scan my entire pc but haven't figured out how to automate that yet since it's gui driven but I do have chkrootkit and rkhunter looking often thru my crontab or cron

---

### Post by Inxsible on 2007-08-03
> **dannyboy79 said:**
> rkhunter and chkrootkit are good apps to look for hidden stuff which can cripple your system.

I've been wanting to setup clamav to scan my entire pc but haven't figured out how to automate that yet since it's gui driven but I do have chkrootkit and rkhunter looking often thru my crontab or cron

Hmmm.. Thanks for the info danny. I might just give those a try :)

---

### Post by dannyboy79 on 2007-08-03
off topic i know BUT what app do you use to burn stuff in Vista? ANy free ones? I have a friend that bought a laptop for his company and wants to archive stuff onto dvd but the Nero he already owned isn't compatible. suggestions.

---

### Post by Inxsible on 2007-08-03
> **dannyboy79 said:**
> off topic i know BUT what app do you use to burn stuff in Vista? ANy free ones? I have a friend that bought a laptop for his company and wants to archive stuff onto dvd but the Nero he already owned isn't compatible. suggestions.
I have logged into Vista only once ever since I first installed Ubuntu. My Vista does not have anything installed in it except Picasa( the linux version doesn't have Web Albums- unfortunately :( )

In fact, after installation I thought I had given too much space to Windows and so got 10GB of space and gave it to Ubuntu. Now My Vista is only 25 GB for the install (jeez !!) and another 15 GB partition. Rest of the 160 GB is all Ubuntu baby !!

Sorry couldn't be of any help  but the regular CD/DVD burners like Roxio Basic came pre-installed. Haven't tried it tho !

---

### Post by Ek0nomik on 2007-08-03
> **dannyboy79 said:**
> off topic i know BUT what app do you use to burn stuff in Vista? ANy free ones? I have a friend that bought a laptop for his company and wants to archive stuff onto dvd but the Nero he already owned isn't compatible. suggestions.

Nero is without a doubt the best burning tool for Windows.  I imagine Nero has a version for Vista, but you may have to use the topic of this thread to get ahold of it.

I have never used this, but I just stumbled across it:  [http://mediakey.dk/~cc/infrarecorder-open-source-cd-burning-for-windows-xpvista/](http://mediakey.dk/~cc/infrarecorder-open-source-cd-burning-for-windows-xpvista/)

---

