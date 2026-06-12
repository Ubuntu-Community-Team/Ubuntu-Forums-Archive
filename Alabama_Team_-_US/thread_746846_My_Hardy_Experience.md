---
title: "My Hardy Experience"
date: 2008-04-05
forum: Alabama Team - US
---

### Post by crane on 2008-04-05
Well I got the chance today to install the Beta Ubuntu on my system. It seems to be pretty snazzy but still has a few bugs. I had to use the Alt install because of the 9600GT video card in my system. But all went well and I am up and running. 
Well let me rephrase, I got it installed. The first install just plain didn't work. Once it said the installation was complete and I needed to remove the disk and reboot it got weird. It rebooted back to the original install on hda3. I had tried to install Hardy on hda5 but it was just plain not there. No files, nothing. Really weird.
 The second try went well other than the fact that the partitioner would not in any way mount my windows partitions. I had to tell it not to mount them just to continue the installation.
 I have been playing for about 2 hours on and off today and all seems OK. I have had a couple of Firefox(3.0) freezes and a couple of small bugs so far,  I do like the default desktop background. I am getting tired of brown but it still looks nice all the same.

---

### Post by crane on 2008-04-06
Well, just as an update, i did get the nvidia card working with some beta nvidia drivers. Playe da game of Q3, Q4, Doom3, and UrT to test them out.
So far so good. Will try setting up Samba sometime next week.

---

### Post by y6FgBn)~v on 2008-04-14
I have been running it here a few weeks as well Crane. Other than a few minor burps it is for the most part very stable. 10 days to go :)

---

### Post by crane on 2008-04-14
I was enjoying it. Then I played with Foresight Linux. It would not allow me to log into either Ubuntu install.. So I decided to reinstall Hardy and ran into a grub install bug.
 I did get grub fixed but I have reinstalled Hardy. I was thinking about installing 7.10 then doing dist-upgrade or upgrade through synaptic to see how it works.

---

### Post by michaelramm on 2008-04-15
I have had mixed results with dist-upgrades. When I tried it on my T43 from Feisty to Gutsy, it appeared to go ok, but then the wireless card just flat did NOT work. I tried for 2 days to get it working again (it worked out of the box in Feisty), but finally gave up. I did a fresh install of Gutsy, and again the wireless card worked out of the box.

This makes me very wary of doing a dist-upgrade next week when Hardy finally gets released. I am finally running Ubuntu as the host OS on my (work) laptop, and really do not want to lose everything. I did separate the /home so it might not be as painful. Although I have not done an upgrade with a separate /home partition, so I will read up on it before attempting anything.

The other time I did a dist-upgrade was when I wanted to play with KDE4. I only had a Feisty Kubuntu image available and put it in a Parallels VM on my Mac, then did a dist-upgrade to Gutsy then installed the KDE4 packages. Everything appeared to work fine with that upgrade. I didn't try to configure much since I just wanted to play with KDE4 (which I HATED!!), so I cannot be 100% certain of the upgrade.

Michael

---

### Post by y6FgBn)~v on 2008-04-15
I too have had mixed results with dist-upgrade. I really prefer to back up my \home and do a fresh install. The time setting up and tweaking afterwards is minimal compared to the potential problems you may have to diagnose and repair.

---

### Post by crane on 2008-04-15
No arguments here. I much prefer to do a fresh install. Just wanted to try it and see what potential problems exist.

---

### Post by crane on 2008-04-16
Well, i didn't do a dist-upgrade like I planned. I started looking into the grub install error. It appears to be something in the repos. Maybe during the install a newer version of grub is being downloaded and installed. Well attempting to install and it fails.
 Last night I disconnected my network cable and did the install with a hitch. then I set up the network and updated. All is well now!
 I'm back on Hardy.:guitar:

---

