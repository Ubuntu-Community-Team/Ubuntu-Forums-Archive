---
title: "The Ubuntu Switch"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-09-28
Well, I've been running Ubuntu 7.04 in a Virtual Machine (Virtual Box) for sometime now
and I am happy to say, I really like the way Ubuntu is set up.  Very nice and friendly OS.  

My Windows XP Professional is becoming slow again and needs a reinstall ( Happens every year ).
For some reason Windows just gets slow after some time of use. Anyways, I think I may take
the plunge and either Duel Boot or just install Ubuntu as the only OS on my Hard drive.

I have a few questions before I take the leap.  These are very important to me....

1.  I use Ghost 2003 to make a Bit for Bit Image of my Hard Drive. Does Linux have
anything like this to offer.  I'm looking for something that can BackUp to a 
Bootable DVD disc, that way if something goes wrong, I just blast the Image
back on.  I like this because it puts the system back to the way it was in like 15 minutes

2.  Since I've been told there is no real need for a Personal Firewall, Anti-Virus, or Anti-Spyware, 
am I being over confident about this or is Ubuntu that secure.  Of course, I would install all the
Updates that Ubuntu pushes out so that should the plug the known holes. I am assuming that
the reason why Windows has so many exploits is because it's a dominate OS and Malware/Virus
authors see Windows as the main target because it reaches more users. The most profit for the
effort, correct?  Ubuntu is getting popular and I would hate to not have that extra layer 
if the threat should rise. Just wanted to make sure that the security layer is there or can be easily added. 

3.  I like to keep my OS nice and tidy. When I install a program on Windows, I like to place
the program in Program Files. Of course I know that .dll and Registry files shoot all over
the drive.  Point being is when I want to install something Windows asks me where I'd like
it to go.  I've notice that when I use the Synaptic Package Manager, that it just installs
and doesn't ask.  Because of this, I don't know where things are going. Can I tell Ubuntu
where to put things or is there just a default place that certain files go?  

4. If I do decide to Duel Boot, Should I Install windows 1st then Ubuntu?
I have an AMD Athlon xp2800+ , 60 gig drive, and 1 Gig of ram.
How big would you recommend the partitions with a small 60 Gig drive?

thanks

---

### Post by jspangler on 2007-09-28
1. I´ve heard that Clonezilla is a good open-source alternative to ghost.

2. Linux is more secure both because it´s actually more secure and because fewer people are trying to make viruses for it. It´s not that viruses are impossible, it´s because the way users access their files (root, users, etc.), it´s very unlikely to spread.

3. To the best of my knowledge, synaptic usually installs files in the /usr folder (but there are different places for some programs). That being said, most programs don´t install their own libraries (windows .dll files), but often use shared libraries. You really shouldn´t need to access the files directly very often. It shouldn´t be a problem.

4. You need to install Windows first. I would recommend at least 10 gb remaining for the ubuntu partition.

---

### Post by rsambuca on 2007-09-28
1.  There may be an image program, but I am not aware of it.  In any event, if you use a separate /home partition, all of your user and settings are stored there so you can easily re-install and keep your settings (You will have to reinstall any programs though).  It should only take 20-25 minutes to install though.

2.  You are correct in thinking that the malicious software writers are targeting Windows, since 95% of all desktop usage is there.  Linux, however, is inherently more secure though, since you are not running as root (XP administrator).  The vast majority of XP users run in administrator mode.  Any viruses will attain the permission levels of the user running the system.  Thus if you are using Ubuntu, if you ever did manage to get a virus somehow, it would only have your user access and would be unable to change any system files.

3.  It is possible to change where programs are installed, but frankly I don't think it is worth the effort, as it just becomes much harder to maintain your system.  In Ubuntu, you will find that most (although not all) programs are installed in your /usr/bin folder.

4.  If you are going to dual boot and re-install everything anyways, I highly recommend the following:

- Partition your drive before installing anything.   Just makes it less likely to screw things up.
- Definitely install XP first, and to the first primary partition on the drive
- Sizes?  That is a little tougher since we don't know your usage patterns, but maybe 20GB for XP, 8GB for Ubuntu '/', a small swap, and the rest for /home.

---

