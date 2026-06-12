---
title: "Ubuntu As NAS"
date: 2007-08-20
forum: Absolute Beginner Talk
---

### Post by Some_ux on 2007-08-20
I'd like to apologize in advance for any ignorant questions I may ask, my knowledge of Linux is fairly limited (as in almost non-existent). I'm also new to these forums. :)

I've been thinking of getting a NAS server for my home network. Checking prices for a dedicated NAS machine of reasonable quality, I noticed that prices for one were not that different from a low budget PC. 
Networking and file sharing are features which Linux systems are renown for, further more, they can do so substantially cheaper and require less computational horse power than MS operating systems. 
As I heard good things about Ubuntu's user friendliness, I concluded that a budget PC, running a user friendly Linux will fit the bill.
Coughing up a bit of dough, I bought A 64bit Sempron (3200+), An Asus M2NPV-VM Motherboard, A Gig of 667 DDRII memory and A couple of Westren Digital SATAII 250GB hard disks.

Now before I start installation, I have several questions about ubuntu 7.04 server 64bit edition.

First, having read some of the other threads on 32 vs. 64 I'm leaning towards the 64 bit edition, Is that a good idea given my hardware ?
Second, regarding the rig itself, I would like to have AMD's Cool'n'Quiet technology operational, Is that reasonable ? Working on 64bit Ubuntu?
Third, I would like my two HDs to be Raid 1, I read in one of the other threads that some of the available Raid controllers are fakes, is it the case with Asus M2NPV-VM, will I need to do software work to make it work?
Fourth, I would love to have a web based administration interface. I saw one called webmin, does it work with ubuntu ?
Finally, I would like the machine to function as a web server as well, Can I create a VPS with Ubuntu 64 ? is it even advisable considering the fact that the CPU is fairly weak (Sempron) ? 

To summarize:
Ubuntu 7.04 server 64bit  on Sempron 3200+ / Asus M2NPV-VM

- Raid 1
- SMB, SSH, HTTP and FTP access
- VPS for HTTP good/bad ?
-  AMD Cool'n'Quiet
- Webadmin

Thanks in advance

---

### Post by Mach1US on 2007-08-20
Just as a reference you might want to check this :
[http://www.pcmag.com/article2/0,1759,2146002,00.asp](http://www.pcmag.com/article2/0,1759,2146002,00.asp)

---

### Post by Some_ux on 2007-08-20
Though nice and flashy, the Drobo mentioned above is pricy(500 without the drives) and afaik is not a NAS as it does not connect to a network, I think it's a USB drive (or are we talking about a different model here). In any case, a full linux system is much more robust and can serve multiple functions, such as being a web server, a mail server even serve as a HTPC.

---

### Post by jdfreshwater on 2007-08-20
Depends on what you are going to do with the machine itself.  If you are going to use it as a desktop and a nas, you may want to use ubuntu.  If you just want to use it as a nas, you may want to check out the free nas project, as it takes up very little disc space. [http://www.freenas.org]("http://www.freenas.org")

---

### Post by Some_ux on 2007-08-20
I'd like to use the rig to learn more about linux in general, and web development with LAMP in particular (That was the reason i asked about making a virtual server for the web server). But the main, day to day function of the machine would be as a NAS.

---

### Post by jdfreshwater on 2007-08-20
Ubuntu can be used as a Nas, and would probably be a good choice if you plan on running a web server, database server and other things beyond just serving files.  You can install Samaba, openssh and various others.  Another good application to install might be rsync.

---

### Post by Pere LK on 2007-08-23
Hi,
What about the RAID installation ? Is-it working ? One of my client buy me this card and have black screen after install reboot with the Hardware RAID 1. So is anybody have a config like that ?

---

### Post by njparton on 2007-09-29
Does anyone have any views on this from a webadmin point of view?

I'm interested in doing something very very similar and if I can administer the ubuntu nas via http (from XP/Vista) that would be great.

Otherwise freenas looks good but hardware compatibility worries me.

---

### Post by njparton on 2007-10-10
It would appear that VNC is the way to go for remote admin if anyone's interested.

Install vnc server in ubnutu and then a vnc client in windows or the linux box you intend to administer from. Just need to make sure the vnc server starts automatically on reboot otherwise you'll have to plug in a keyboard, mouse and display to get it up and working again.

---

### Post by flamacue on 2007-12-02
VNC is nice.

I like webmin, too.  It includes modules for managing RAID (md & lvm), and network shares.  You can install webmin with apt/aptitude/synaptic/"Add/Remove Applications" if you add it to your repositories, see

[COLOR="Blue"][_http://www.webmin.com/deb.html_](_http://www.webmin.com/deb.html_)[/COLOR]

under the section labelled "Using the Webmin APT repository".

---

