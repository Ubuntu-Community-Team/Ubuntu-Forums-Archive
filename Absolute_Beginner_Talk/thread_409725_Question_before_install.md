---
title: "Question before install"
date: 2007-04-14
forum: Absolute Beginner Talk
---

### Post by dutilr on 2007-04-14
I wanted to give a Linux distro a try, and a work colleague recommended Ubuntu.  I have a 6 year old Compaq computer that I just replaced, and didn't want to just throw it away.  It has a 900 mhz amd athalon processor, over 384 Meg RAM, and probably about 14 Gig left on the hard drive.  It still has Windows ME on it.  Finally had to buy a new desktop.  Anyway, enough about my old desktop.

I want to learn about Linux, and figured this would be a good way to make use of the old computer.  My questions, finally, are these.  Do i have to partition my disk before downloading Ubuntu?  Does the installer do this for me?  Is my old desktop usable for Ubuntu?  Are there any major pitfalls I should be aware of in advance before attempting the install?

Anyway, I've read a little on the forums in advance, and I'm impressed with user community and their willingness to support this OS.  

Oh yeah, one last question.  After I do get this up and running, is their a firewall available to install?  Or because it is Linux, do I not need to be as concerned with a firewall as I would with a pc running windows?  I would guess I still need to be concerned about a firewall.

Thanks in advance,

Ray

---

### Post by Error47 on 2007-04-14
I just recently intsalled ubuntu as well, and I do not regret it. I had Windows XP installed, When you pop the Ubuntu cd in your computer it should either format the HD and install Ubuntu over windows, or you have an option to duel boot, which automatically does everything for you. I did not have to set up any partitions or anything. 

I have installed ubuntu on an even older desktop (533 mhz, 256 RAM, and total of 20 Gb HD, and the worst graphics card in existance) , and it worked fine. So you shouldn't have a problem. 

A good way to start learning is to read the [ubuntu guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy") . 

I would wait until the new version of Ubuntu comes out (feisty) and install that copy, I dont know how easy upgrading will be, but thats just what I would do. I am not sure, but I think the new version comes out this month, I think on the 19th. Again, I am not sure about that date. Hope this helps.

---

### Post by dutilr on 2007-04-14
Thanks for the quick feedback.

---

### Post by userundefine on 2007-04-14
Ubuntu ships with no open ports by default.  There is a firewall installed as far as I know already.  If you want to mess with it further, you can install firestarter which is a GUI frontend to iptables.  The default install is quite secure as is, though.

---

### Post by kvonb on 2007-04-14
I would suggest waiting until the 19th of April, that is the release dat for the brand new, super fabbo release of Ubuntu called "Feisty Fawn".

You can get it right now, but I don't advise it because it is still in beta stage.

It is the easiest and friendliest version of Ubuntu to date and is WELL worth the short wait.

When you boot the CD, it boots straight to a fully useable desktop, you can try out Ubuntu without having to install anything at all, and once you are ready, you simply click on an install icon and it will guide you through the process.

It will give you several choices of partition setup, and you can also do it your own way, which is my recommended method.

It is not like arrogant Microsoft products that wipe your whole hard disk and demand the whole thing to itself, Ubuntu can live happily in only 6 gigs of space (3 at a minimum I beleive), and you will automatically have a boot menu installed that will allow you to choose to boot your old copy of ME or Ubuntu.

So give it a go, but please be open minded and expect that things are done differently, it is very easy to get frustrated and give up in anger, just relax and ask ANY question you might have, on these forums.

If you are polite, you will get fast answers and people will be willing to help you with anything, so don't be shy :)

Regards, KEv :)

---

### Post by Nythain on 2007-04-14
1. the installation will have a few different options for partitioning... i believe auto partition whole drive, auto partition free space or manually configure partitions... so if you have empty un partitioned space you are good... if its all in a windows partition, you might wanna cut a chunk off ahead of time, but i believe the partitioner can actually do that for you during install also

2. your old desktop is very usable by ubuntu/linux... some things might run a wee sluggish if you can get them working (eg Beryl/Compiz) and something things might not fly uber fast (eg KDE) but your machine should more than suffice

3. learn as much as possible about your hardware ahead of time... makes/models of pieces (eg video adapter, sound card, nic, hard drives just in case, cd rom drives)... research linux drivers for any of the above, wether or not there are free proprietary drivers or if the stock ones with ubuntu are gonna work fine... also read up on xorg.conf, what it is, what it does, how to edit it for your needs... fstab is a good thing to be familiar with but not necessary for the most part... id familiarize myself with the basics of terminal/cli commands in case something goes awry and you cant get your Desktop Environment working from the get go... then you arent totally confused as to how to edit conf. files or install drivers or packages or anything

4. ubuntu ships default with a firewall and no open ports, i dont remember the name of the firewall, and its command line driven but there is a popular gui front end for it called Firestarter

5. the rest you will learn as you get deeper into the whole linux ordeal... its a learning experience, fun and frustrating, but pretty rewarding in the end... welcome to the community and i hope we can help more when the time comes

---

### Post by dutilr on 2007-04-14
All I can say is wow.  And thanks to everyone for the quick replies and advice!  I understand this will be a learning process, and I'm looking forward to tinkering and getting this up and running.  I'll wait until after the 19th for the new version.  I am definitely open to this whole experience.  

I'm an System i (IBM AS/400) professional by background, and I hate technology bigots.  I hear more than enough disparaging comments about how I work on a dead technology, and it never fails to tick me off.  All platforms (and operating systems) have their strengths and weaknesses, and the more I can learn the better.  I look forward to bothering you all with tons of questions in the near future.

---

### Post by Maestro23 on 2007-04-14
Hey dutilr, here are some links for you to chew on.  Welcome to Ubuntu and Good luck.:D 

Useful Links:

Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

Restricted Formats(mp3, playing DVD, etc..): [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Managing Repositories: [https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

Community Docs: [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

CommandLine Beginners: [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

Basic Commands: [https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)

LinuxCommand.org(Commands & Linux File Structure): [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Using the Terminal: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Top 10 Commands for noobs: [http://blog.lxpages.com/2007/02/25/top-10-linux-commands-for-newbies/](http://blog.lxpages.com/2007/02/25/top-10-linux-commands-for-newbies/)

Graphic Card Drivers
ATI supported cards: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)
Installing ATI Drivers: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)
Installing Nvidia Drivers:[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
Envy Script(ATI/Nvidia): [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Super Grub Disk: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

How to Change Default OS: [https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS?highlight=%28grub%29](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS?highlight=%28grub%29)

Getting rid of junk: [http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

