---
title: "Newbie - don't know how to install"
date: 2005-01-22
forum: Apple PPC Users
---

### Post by mortendo on 2005-01-22
After trying hard to google any guidelines in how to install Ubuntu on an old mac 7200, I've given up. I find the one on Ubuntu, but it assumed that I knew how to use miboot - I don't. 

Does anyone know a site where I can find a "Unbuntu install on old ppc for dummies" -like thing on the web, which I can make use of.

Kind regards
Morten

---

### Post by fishfishfish on 2005-01-22
As far as I know, the PPC version of Ubuntu is for new world macs only. Sadly, it won't install on an old world mac like yours. 

I've got a couple of old world machines and have previously had them running Mandrake 9.1 PPC, which is among the easier ones to install on an old world machine, in my opinion. Debian is a bit tricky to install on an old world machine in my experience.

Matt

---

### Post by ssam on 2005-01-22
you might want to look at yellow dog linux. its based on fedora, and although the latest version officially is for newworld, i believe quite a few people run it on older machines. you might find info at [www.yellowdog-board.com](www.yellowdog-board.com) or in the #yellowdog irc room on freenode.

ssam

---

### Post by diskman_1 on 2005-01-23
I suggest starting with Yellowdog Linux 3.0 .   Do NOT try the latest 4.0 as they dropped support for OldWorld systems.  I had 4.0 running on my 4400/200 but the sound in 4.0 is broken on ALL PowerMacs.

Anyways, use the documentation from Yellowdog 3.0 or even 2.0 to configure BootX.  Its really only a matter of installing the BootX application to a folder and then selecting a kernel to run and the proper startup ramdisk for installing whatever distro you want.  I used the old Yellowdog install howto to install SuSE a long time ago on my BeigeG3.  It's all the same idea.

Then you can use the "Installing on OldWorld Machines" located at  [http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs](http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs)

If you are a Linux newbie, then I suggest Yellowdog 3.0 for that old machine.  You *might* be stuck with 2.0 or Champion Server 1.2 on something that old.  I couldn't get ANY version to run on my 6200CD last night  (Error 10 and 2s) so I eBayed it for $1.00 and busted out my 4400/200 for YellowDog and Ubunto Linux.

Hope this sheds more light for ya.  Otherwise please feel free to email me or something.

---

### Post by mortendo on 2005-01-25
Thanks  everyone.

I have tried an ydl 3.0.1 installation (bought some time ago for an installation on a 6400 - today it's back on os 9 running as file-server and jukebox)

 - The installation-process of the 7200 went well until about 4% was left - then I inserted cd-2 and nothing happened - Then I tried searching for something else and found a number of people who recommended Ubuntu (danish sites) - but as you say - the machine is to old to have it installed. I will probably go back and try the ydl, but  thanks for the quick replies - if it still doesn't work - I'll try an even older version of ydl (its only going to work as a small webserver).

Regards
Morten

---

### Post by farruinn on 2005-01-25
Um, actually Ubuntu **can** be installed on OldWorld Macs - I'm using Ubuntu on a Beige G3 (probably the worst choice considering OF bugs).  It does require some effort, but there are instructions at [http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs](http://www.ubuntulinux.org/wiki/InstallOnOldWorldMacs).  No, Ubuntu isn't "officially supported" on OldWorld macs, but it does work (and it works rather well I might add - automatically recognizes more of my hardware than debian).

~Nathan

---

### Post by farruinn on 2005-01-26
I should add that you don't have to use miBoot which is old and replaced by BootX, which there are instructions for.  If you have questions about specific parts of the installation please post so that we know exactly where you're running into trouble.

~Nathan

---

