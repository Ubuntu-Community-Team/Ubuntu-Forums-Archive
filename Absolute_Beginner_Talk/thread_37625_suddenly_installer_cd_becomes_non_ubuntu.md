---
title: "suddenly installer cd becomes non ubuntu"
date: 2005-05-27
forum: Absolute Beginner Talk
---

### Post by diogena on 2005-05-27
I seemed to have no problem with the installer cd I burned from my ubuntu download until I got to the last step in installation. Before restarting to finish installation, I was informed to make sure the cd drive was empty so that GRUB would start from the hard drive. So I took out the installer cd. When my pc restarted, I got instructions to insert an ubuntu cd into the cd drive. Well, I'm just in the installing stage so the only ubuntu cd I have is the one I just used to install ubuntu, but now I am told that this cd is a non ubuntu cd. 

I am very noobie, but I understand that ubuntu is looking for some files on that disk and can't find them....it offers me to select ftp, http, manual entering....

I partitioned my drive so that I have XP on a primary NTFS (or is it NTSF) partition, and the other half free space. I installed ubuntu in the free space. I also had a little 1.5 Gig partition that was created into swap. 

Now when I start my pc (Dell 2400 n, 2.4 gigahertz, 512 ram, 80 gig HD) Grub gives me a choice of some ubuntu boots or XP. XP works fine. Ubuntu keeps wanting an ubuntu disk to do some configuring, and won't recognize the disk it installed from....

But this is fun. I feel very close to getting to the point of having to solve driver issues, which I am looking forward to. ;-)

---

### Post by poofyhairguy on 2005-05-28
[QUOTE=diogena]I seemed to have no problem with the installer cd I burned from my ubuntu download until I got to the last step in installation. Before restarting to finish installation, I was informed to make sure the cd drive was empty so that GRUB would start from the hard drive. So I took out the installer cd. When my pc restarted, I got instructions to insert an ubuntu cd into the cd drive. Well, I'm just in the installing stage so the only ubuntu cd I have is the one I just used to install ubuntu, but now I am told that this cd is a non ubuntu cd. 

I am very noobie, but I understand that ubuntu is looking for some files on that disk and can't find them....it offers me to select ftp, http, manual entering....

I partitioned my drive so that I have XP on a primary NTFS (or is it NTSF) partition, and the other half free space. I installed ubuntu in the free space. I also had a little 1.5 Gig partition that was created into swap. 

Now when I start my pc (Dell 2400 n, 2.4 gigahertz, 512 ram, 80 gig HD) Grub gives me a choice of some ubuntu boots or XP. XP works fine. Ubuntu keeps wanting an ubuntu disk to do some configuring, and won't recognize the disk it installed from....

But this is fun. I feel very close to getting to the point of having to solve driver issues, which I am looking forward to. ;-)[/QUOTE]


I've got a better way. Do you have broadband? If you do, plug it in. Put the install cd in. Except this time at the first screen type "server" before you hit enter. Let it do its install thing. Then it will drop you to a command line. Put in this command:

sudo pico /etc/apt/sources.list

when that file comes up comment out (by putting two #  before it) the CD line and uncomment (by deleting the #) every other line that starts with "deb." hit control and x at the same time to exit.  tell it to save.

then at the command line type:

sudo apt-get update

then when that is done:

sudo apt-get install ubuntu-desktop

If you don't have broadband, don't do this. In that case, your CD might be bad and you might need another.

---

### Post by wallijonn on 2005-05-28
When I first installed Warty, when it asked if I wanted to go out to the internet to get the latest updated files, I answered no. This allowed me to install Warty without typing up the network. I then started SPM and did the updates.

On my second machine I did allow it to access the internet instead, thereby bypassing the CD, and things like mouse pointers were automatically installed. 

But if you're so buried down to the level where you are doing an FTP install (holy Debian Sarge, freeBSD, Fedora, SuSE, Slackware, Batman!), you may want to try a simple install first. It's either that or you elected to try to install Ubuntu on its own partition (/, /boot) instead on in the MBR (master boot record). Do you have a LiveCD? If so you should be able to cd over to it and change the menu.lst. There's a few threads about GRUB out there. [img]http://ubuntuforums.org/images/smilies/eusa_whistle.gif[/img]

---

### Post by diogena on 2005-05-28
Poofyhairguy and Wallijonn,
I went ahead and did a reinstallation, this time typing *enter* rather than *expert*. I typed expert because someone online mentioned something about having more control with it, and I am such a control freak....
Maybe one of those times in the manual enter part of the expert install, I clicked ok when I should have entered something spec., but when I let the installer do its own thing it must have detected what it needed. Now I am on to greater problems!
But both of your replies are highly educational to me in my noobie phase.
Cheers!

---

### Post by bored2k on 2005-05-28
[QUOTE=diogena]Poofyhairguy and Wallijonn,
I went ahead and did a reinstallation, this time typing *enter* rather than *expert*. I typed expert because someone online mentioned something about having more control with it, and I am such a control freak....[/QUOTE]

It's the other way around. Expert asks less questions.

---

### Post by TravisNewman on 2005-05-28
*blinks* expert asked me a lot more questions

---

