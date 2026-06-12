---
title: "FREE antivirus recommendations"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by Cloudedbrains on 2007-05-23
Can anyone recommend an easy to install and use Antivirus package for Ubuntu Feisty :?:

I know Linux is alot safer but I want to play safe so any recommendations gratefully received O:)

---

### Post by silent1643 on 2007-05-23
> **Cloudedbrains said:**
> Can anyone recommend an easy to install and use Antivirus package for Ubuntu Feisty :?:

I know Linux is alot safer but I want to play safe so any recommendations gratefully received O:)

avast antivirus is good and simple, and its free just register to get the code.

---

### Post by Jussi01 on 2007-05-23
Clamav - its in universe so make sure you have the universe repo on and install through synaptic.

---

### Post by Sef on 2007-05-23
> Can anyone recommend an easy to install and use Antivirus package for Ubuntu Feisty

Applications > Add/Remove > Show:  set to 'All Available Applications' > Search 'Anti Virus' > Click on Virus Scanner > apply > apply > Finish.

---

### Post by angryfirelord on 2007-05-23
I know AVG has a deb package avaliable, but I haven't used it under Linux, only Windows.

If anything, a firewall is more important because it helps stop the attacks. I'd get Firestarter from the repos and it's easy to get it running.

---

### Post by Zzl1xndd on 2007-05-23
Honestly there isnt much of a point. I know coming over from windows it seems like you need to have it but you really don't. But as people have stated check the repo's and Avast & AVG both have .Debs

---

### Post by PartisanEntity on 2007-05-23
> **tweakedenigma said:**
> Honestly there isnt much of a point. I know coming over from windows it seems like you need to have it but you really don't. But as people have stated check the repo's and Avast & AVG both have .Debs

It is good to have an antivirus application installed in a Linux operating system in order to prevent the accidental forwarding of Windows-viruses from Windows user to others.

You do not need really need an antivirus application to protect your Linux based system, but it is nice/polite/helpful/useful not to send infected emails on to your friends and family, or colleagues.

---

### Post by dangermouse28 on 2007-05-23
Although there isn't much of a point just now, it's good to get into the right habits before we have to ;)

You don't want to be passing nasties on to all your windows friends either - bad for reputation!

Install ClamAV and ClamTK (the front-end gui) and you're pretty well sorted. You can set up Evolution to use ClamAV to scan incoming mail too.

There's not much point using the firewall though. If I remember correctly, Ubuntu comes with ports shut and listening services disabled out of the box. However, if you want to use SSH and some other services which will open up your defences, you'd better install Firestarter as well.

Have fun not worrying about viruses and malware :)

---

### Post by Zzl1xndd on 2007-05-23
> **PartisanEntity said:**
> It is good to have an antivirus application installed in a Linux operating system in order to prevent the accidental forwarding of Windows-viruses from Windows user to others.

You do not need really need an antivirus application to protect your Linux based system, but it is nice/polite/helpful/useful not to send infected emails on to your friends and family, or colleagues.

the problem with that being is that most linux scanners do not run in the background, so you would need to scan before forwarding any email sure its a good practice but I know i wont do it.

---

### Post by Cloudedbrains on 2007-05-23
> **Sef said:**
> Applications > Add/Remove > Show:  set to 'All Available Applications' > Search 'Anti Virus' > Click on Virus Scanner > apply > apply > Finish.

Thanks have done that but how do I set it up and use it now :(
This is so different to my XP setup and my other networked pc :(
Sorry for dumb questions :(

I aint got a software firewall as I have a hardware one built into my modem/router :)

---

### Post by silent1643 on 2007-05-23
> **tweakedenigma said:**
> the problem with that being is that most linux scanners do not run in the background, so you would need to scan before forwarding any email sure its a good practice but I know i wont do it.

yeah i agree, i haven't seen one that runs in the background and runs on access scans.

---

### Post by Cloudedbrains on 2007-05-23
So do I use this to scan downloaded files etc then ???

I use Thunderbird for email - would that use this to scan emails ???

---

### Post by silent1643 on 2007-05-23
i would just play around with avast and clam and see which one fits your needs.. i only use avast command line scanner every once in awhile.. i dont think it does auto email scanning.

---

### Post by Arjunus on 2007-05-23
i would suggest avg. just go to the [www.avg.com](www.avg.com) and download the install file for linux. then its just a matter of double clicking on it.. very similar to what u would do on xp:)

---

### Post by Cloudedbrains on 2007-05-23
I dunna like Clam :(
Will have a look at others tomorrow thanks ;)

---

### Post by Cows on 2007-05-23
Is a antivirus even needed for Linux since it's already extremely secure?

---

### Post by Cloudedbrains on 2007-05-23
From what a friend who is computer security boffin says YES as email can still spread viruses to others under linux, or thats what he says anyway ;)

---

### Post by bodhi.zazen on 2007-05-23
At this time viruses are rare, at best, on Linux.

[http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss](http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss)

For more information :

Linux virus:
		[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)
		[http://librenix.com/?inode=21](http://librenix.com/?inode=21)
		[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)
		[http://math-www.uni-paderborn.de/~axel/bliss/](http://math-www.uni-paderborn.de/~axel/bliss/)
		[http://software.newsforge.com/article.pl?sid=06/04/18/1941251&tid=78](http://software.newsforge.com/article.pl?sid=06/04/18/1941251&tid=78)

As PartisanEntity indicated, the main reason to run antivirus on Linux is as a courtesy to Windows users.

The problem with Linux antivirus programs is that false positives are too frequent, so best leave the viruses and antivirus with windows.

---

### Post by Cloudedbrains on 2007-05-24
So would you Linux boffins recommend I stay away from anitvirus software for now or not ;)

My mates more a windows security boffin but he keeps telling me I should but from what I seen on here you lot think otherwise and as a newbie I am getting confused :(

---

### Post by bodhi.zazen on 2007-05-24
> **Cloudedbrains said:**
> So would you Linux boffins recommend I stay away from anitvirus software for now or not ;)

My mates more a windows security boffin but he keeps telling me I should but from what I seen on here you lot think otherwise and as a newbie I am getting confused :(

:lolflag:

I understand where you are coming from, the only advice I can offer is Linux is NOT Windows. Take Linux advice form Linux Gurus and Windows advice from Windows Gurus.

Part of learning a new OS is learning security. As with and OS, there are potential security holes in Ubuntu BUT viruses are not one of them. Neither is spyware.

If you like, here is a how-to antivirus on Lniux : 

[http://doc.gwos.org/index.php/How_to_ClamAV](http://doc.gwos.org/index.php/How_to_ClamAV)

You SHOULD learn Linux security. This is a broad topic ... and there is never total agreement on ssecurity issues.

This is a good start : [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

From there search the forums, google, depends on your interest.

---

### Post by Cloudedbrains on 2007-05-24
Thanks

---

### Post by JNowka on 2007-05-28
A few things I would like to add about Linux and anti-virus.

First:
Yes there is a such think as on access scans on Linux.  It is just a pain to set up.  ClamAV has an on access feature that is disabled in Ubuntu.  The main reason is that it is not enabled is probably because that dazuko, the module that makes it possible, is not recommended in production environments.  Dazuko has also been disabled in Ubuntu.  So in order to get on access scans you have to install a module, then you have to download the ClamAV source, ensure the debian/rules doesn't disable clamuko, and install.

Second:
I am going to take a differant road because of a problem I had recently.  I use wine for a few programs.  Recently I got a virus in wine that effected all my windows files.  It did not however effect anything in Linux.  If you plan on using this I would suggest you download and install an anti-virus program and scan your wine folder weekly, and scan any Windows programs you plan to install.  I got my virus from just using IE to test a web page I was setting up for school on my schools internal network.  I thought that I would be safe hiding behind my schools central server, and behind their industrial strength anti virus.  I was wrong, and I was stupid.  So that's my two cents

---

