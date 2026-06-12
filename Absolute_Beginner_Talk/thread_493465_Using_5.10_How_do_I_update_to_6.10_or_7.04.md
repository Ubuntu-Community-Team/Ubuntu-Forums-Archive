---
title: "Using 5.10 How do I update to 6.10 or 7.04"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by jrfoleyjr on 2007-07-05
I am a new ubuntu linux user. I'm trying to make the move from windoze (using xp and w2k on other boxes here.)

I had trouble getting 6.10 and 7.04 to install (kept getting a grub error even after a fresh reformat). I have an old cd with 5.10 and it installed with no problems. The update manager in 5.10 says I have the latest versions and I can not figure out how to do an online upgrade. Is it possible or do I have to do a fresh install of a newer version?

Thanks...  Jim

---

### Post by tgalati4 on 2007-07-05
Give us a detailed description of your hardware.

I would try Dapper 6.06.1 if it's an older machine.

---

### Post by jrfoleyjr on 2007-07-07
It is an older desktop with a pentium 200 mhz and 64 mb ram that I was given. I decided to turn it into a linux box as an educational tool. It came with Win95 on it which seemed to work. But Win95 is such a step backwards that I had to change it. It is so old and slow that any newer version of windoze is hopeless so either I use it as a dos box or put linux on it. Everything I have read says linux should run on it fine.

Ubuntu 5.10 loads in beautifully and even runs ok.When I look for upgrades of anything on it, I get messages that 5.10 is no longer supported and that everything is up to date. Hmmm

I did a reinstall using Ubuntu 6.06 desktop version that I downloaded and burned to cd. Every indication was that it installed PERFECTLY. It told me to remove the cd and reboot. I did with this result...

[INDENT]Loading Boot Record from CDROM...Failed[/INDENT]
[INDENT]Loading Boot Record from IDE-0...OK[/INDENT]

[INDENT]GRUB Loading stage1.5.[/INDENT]

[INDENT]GRUB Loading, please wait...[/INDENT]
[INDENT]Error 18[/INDENT]

...and there it stops!

There is no other OS on the hard drive (a 40 gig Western Digital IDE hd)
I am puzzled!

---

### Post by jediborger on 2007-07-07
It sounds like the cd has some errors. You might want to try the "Check Disk" option when you boot the cd and possibly check the md5sums of your downloaded image and/or burn the cd at a lower speed to prevent errors. I'm presuming that you're using Windows to burn the cd and for some reason it makes a big deal out a simple task. Also from the specs you listed you might be better off trying Xubuntu [http://www.xubuntu.org]("http://www.xubuntu.org") since it runs better on lower specs. Hope this helps.

---

### Post by annda on 2007-07-07
i don't think you will have much fun with the latest releases of ubuntu with your hardware. i suggest you stick with 5.10 or try [damn small linux]("http://www.damnsmalllinux.org/download.html") - it has a modern kernel with modest hardware requirements.

---

### Post by Sef on 2007-07-07
If you want to stick with ubuntu, I would use [Fluxbuntu]("http://fluxbuntu.org/").

---

### Post by ramjet_1953 on 2007-07-08
As said earlier, with only 64 Mb of RAM you will be struggling with a GUI.

Ubuntu requires a minimum of 256 Mb to run decently.

Either buy some more RAM, or dowlnoad damn small linux.

Regards,
Roger 8)

---

### Post by jrfoleyjr on 2007-07-08
I downloaded the xubuntu last night but the md5 didnt match so I have to try again.

The checksum of the Ubuntu 6.06 desktop that I tried installing checked out ok. That is the one that installs ok but would not boot.

I'll check back later after I get a good download of xubuntu an try to install.

---

### Post by jrfoleyjr on 2007-07-08
Thanks for the info Jedi!  I downloaded and installed xubuntu 6.06.1 (Dapper Draker) Alternate Install. This was what I needed. 

===

Thanks Ramjet.... more ram is not an option for me in this case. The alternate install disk for Xubunti 6.06.1 works fine in 64 megs.

===

Thanks all for your help! Now to see if I can learn enough to want to change over the rest of my network from Windoze.

---

### Post by jrfoleyjr on 2007-07-16
I have 6.06.1 up and running but to get rid of the GRUB errors, I had to reinstall Win2k and then add Ubuntu as second OS with the grub boot loader.I wanted to use JUST ubuntu but grub would not allow it. With just ubuntu, it insisted on loading grub and then giving a grub 18 or 17 error after the install and reboot.

 Now i can go either way. But only wanted ubuntu.

Thanks for the help.  :popcorn:

---

### Post by oilchangeguy on 2007-07-16
if you're wanting to learn linux. why not use a more modern machine. you're not going to learn on this old under powered computer. i'd suggest do a dual boot on a more modern machine, or at the very least run a live cd on a newer machine.

---

### Post by jediborger on 2007-07-16
Hmm, you seem to have an interesting grub problem. Am I correct that you're saying it only works when there's another distro installed? It's possible that there was an error with it before, working with older hardware can sometimes just have plain old data problems. But if it's working now, you should just be able to delete the windows partition with Gparted and delete the entry from your grub menu file at /boot/grub/menu.lst. I would try this and if it fails for some reason put in your xubuntu install disc and there's a recovery option there that will reinstall grub as well. Weird problem, but hope that helps.

---

