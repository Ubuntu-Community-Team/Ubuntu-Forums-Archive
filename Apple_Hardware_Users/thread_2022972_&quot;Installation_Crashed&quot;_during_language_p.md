---
title: "&quot;Installation Crashed&quot; during language pack install - PowerPC g4 + Lubuntu"
date: 2012-07-11
forum: Apple Hardware Users
---

### Post by andersond on 2012-07-11
Hello, I have an old Powermac G4 (silver one) and from almost an year I´m trying to run some linux on it. I actually could run old ubuntu 5.x but once it was very old, i got a lack of updated software for it.

Then I tried to update it. It was a very bad experience. I tried all the releases from 7.x to 12.04 without success, due to problems with a new video driver versus a framebuffer on the Rage 128 card. I even tried lot of daily builds of the same version to see if it was corrected, using live cd´s, mini installers and even alternate cd.

Weel, about 1 month ago I tried the Ubuntu Quantal 12.10 daily build and ir ran! Opened gnome without crashing but...... veeeeeeeeryy slooooow!!! I´m am not completely sure if it happened due to framebuffer issue or because it´s a too heavy OS for the machine. Anyway, I decided to go LUBUNTU !!

Downloaded Lubuntu daily build from about 1 week ago, burned it and it ran ok, little bit faster, compared to ubuntu live cd. I proceeded to installation, and everything gone ok. But, during installation, I got a message saying that "the installation crashed for some reason" and wen I click close and ok, it allows me to send a report of the problem But after I click SEND, it opens a browser window which tries to open something which never NEVER loads.. so I neither am 100% sure if the trouble report was sent....

I am in Brazil, but also tried to set up everything in English, to test a possibility with the portuguese language pack, but have no success.. :( I also tried it "with" and "without internet updates during install" otpin checked.

Could you guys help me here? I already burned more than 20 cd´s on this soap-opera, I´m almost giving up and painting this G4 with green paint and putting it away on the jungle in order to assure that nobody will find it lol.... 

Thanks in advance!!

Anderson D. Fontes

---

### Post by 2blue on 2012-07-11
I would go for lubuntu 12.04, not the daily builds.  It works on my ibook G4 from 2005, though I haven't had a chance to configure everything yet. Have you ran the MD5 sum check on your download before burning? It does eliminate errors on the download part, and also remember to burn at lowest speed. The official 12.04 is the best one, the daily builds are mostly for those who test new developments and give feedback. It's all right to venture into the area, but for new ventures with old hardware the official version is the only one you really can work with. 

You might find support for lubuntu on the freenode irc channel too. 

What are the specs on your G4?

---

### Post by andersond on 2012-07-11
> **2blue said:**
> I would go for lubuntu 12.04, not the daily builds.  It works on my ibook G4, though I haven't had a chance to configure everything yet. Have you ran the MD5 sum check on your download before burning? It does eliminate errors on the download part. The official 12.04 is the best one, the daily builds are mostly for those who test new developments and give feedback. It's all right to venture into the area, but for new ventures with old hardware the official version is the only one you really can work with. 

You might find support for lubuntu on the freenode irc channel too. 

What are the specs on your G4?

here they are: (from code number + everymac research)
Intro Date:	January 9, 2001	Disc Date:	July 18, 2001
Order No:	M7627LL/A	Model No:	M5183 (EMC 1862)
Subfamily:	Digital Audio	Model ID:	PowerMac3,4
Std. RAM:	128 MB	Std. VRAM:	16 MB
Std. HD:	30 GB (5400 RPM)	Std. Optical:	8X CD-RW

It uses rage128 video card, so until 12.04 I could not load X by default installation and even with offb:off and other workarounds it did not run well, due to know framebuffer versus xorg driver issues. (I am talking about ubuntu)

Just with Quantal 12.10 it opened X without workarounds, but still slow. Then I got lubuntu 12.10 Do you suggest I try downloading the lubuntu 12.04 ? how about r128 framebuffer issue? Is there a definitive working step-by-step to install with it?

I did not the md5 checksum, do you believe it´s a bad burning?
I tried to create a live usb, but (newbie) did not find out how to boot the mac on it....

---

### Post by 2blue on 2012-07-11
I am all new to buntus on mac too really, but generally you need at least 256MB RAM to use the graphic installer wizard, which means you might need to get the alternate install CD, which is found [here]("http://cdimages.ubuntu.com/lubuntu/releases/precise/release/"). [Download]("http://cdimages.ubuntu.com/lubuntu/releases/precise/release/lubuntu-12.04-alternate-powerpc.iso") for alternate powerpc iso. You might need to find a guide to maneuver the commands for the install process too, but it should be managable. 

Lubuntu should run on 128RAM, but you might want to get 256 RAM if you notice lubuntu run on full all the time. Old ram cards come very cheap luckily. 

The oldest computer I installed linux on was a Packard Bell with originally 256RAM, 700MHz cpu and a tiny 10GB harddrive (or something like that), from 2001 I think it was. Lubuntu 11.10 ran fine on it, but something turned out to be wrong with the power plugin, so it got a bit too unstable. Specs was all fine for lubuntu and there were even workarounds for flash streams like youtube and TV. 

For your burn, it's hard to tell, but if you still have the same downlaod you can run the MD5 sumcheck and it will eliminate any source of errors on that part. For some reason it is a must to burn on lowest speed, other wise weird errors often occurs. 

Best of luck ;- )

---

### Post by andersond on 2012-07-11
Thank you very much! Actually the RAM is about 800mb..

I burned it again on the slowest speed 2x, did not even "look" at it and used it to install. Now i had no problem, and it installed and it´s now running smoothly (not that quick but ok for web and IM)- I installed it in English to avoid the problem regading the language pack during installation

About the root password, I was not asked to set it up during installation.

Now I want to install the portuguese language pack (it´s beacause this mac will serve to my mother and she does not understand a word in english), through the Language Support section, but it asks for password. What is the default root password? Or how to do it through the console? Thanks in advance!!

---

### Post by str8bs on 2012-07-11
not sure if this answers your question, but the password is the same as your user login in *buntu

ie: sudo whatever command and use the password for your username and not root

PS: FWIW, I've gotten Kubuntu to a use-able state on a G3 before. Lubuntu is great for systems low on RAM, but if you spend some time going through the FAQ and getting more work out of your GPU, you would be surprised how "heavy" a desktop these can run. 
As to framebuffer question in other thread: aty128fb was put back in kernel I believe at least from 12,04 3.2.0-25 and later.

---

### Post by 2blue on 2012-07-12
I finally manage to get connected to the web, and did all the updates. And yes, lubuntu asks for password for everything related to changes on the system. It is the password you registered during install, right under computer name, the one you had to type in twice (to double check spelling and safety/difficult to hack). I´m not totally sure, but there might have been a Portuguese language option during install, and it`s not possible to switch to it after installation is done. However spelling libraries and similar is all fine.

---

### Post by andersond on 2012-07-13
Well, when I uso sudo, it accepts my password, but when I use su it does not.. it gives "authentication failed" 
 
I am trying to install a msn-compatible instant messenger app, but none is working well.. pidgin closes unexpectdly after less 1 minute connecter.. emesene also connects, but most times the contacts window get grayed and crashes (I got to kill it), I also tried empathy, and kopete, but they don´t connect..
Also got the ekg2 (something like this) puls the gtk UI from the repo but it simply does not appear available on the lubuntu menus.. but I know  it is somewhere there, I entered the console ui it via command line..
 
I also looked for aMSN on the repositories, but it´s not there. Then I tried to install it via apt-get command line, without success, got an error message (I post it later, I´m at work now)...
 
Which IM do you reccommend for my box?

---

### Post by 2blue on 2012-07-13
Pidgin chrashes as soon as I try to do anything here too, on both irc and msn account, I tested both, not sure about facebook. I get as far as adding and account and that is about it. 

You can install some stuff straight from their site, and some will turn up in package manage if you mark of for third party software or something similar. You have to add the third party source to be able to install from terminal too. 

I`ve never set up empathy properly so I don`t know it very well. There might be a fix or alternative though. I need to try differnt IM ware too.

---

