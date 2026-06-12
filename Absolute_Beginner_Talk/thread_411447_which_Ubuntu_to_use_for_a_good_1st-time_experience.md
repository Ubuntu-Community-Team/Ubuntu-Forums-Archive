---
title: "which Ubuntu to use for a good 1st-time experience?"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by tstockma on 2007-04-16
Hi, I'm trying Ubuntu for the first time, I wish to set up a dual-boot with W2K.

What Ubuntu version will be most likely to deliver a good experience?  I've been trying Dapper Drake, but I'm running into an apparently common problem, the "kernel load / root file system" loading issue, where I can't get any form of the desktop or alternate LiveCD to load the kernel.

I'd appreciate some guidance on which version I'm more likely to have a good experience with.  I have an Athlon 2000+ CPU, 1GB RAM, and 2 IDE HDs.  The primary master is an 80GB currently devoted to NTFS and Windows 2000, the primary slave is an empty 160GB Seagate that I planned to use for the Ubuntu install.

Thanks for any help!  Tom

---

### Post by wesley_of_course on 2007-04-16
Wesley here ;

        Have Fun and hang on , this is a Blast !

                 [http://www.ubuntu.com/](http://www.ubuntu.com/)                      :popcorn:

---

### Post by NeoLithium on 2007-04-16
I'd say anything from Edgy is good; be it Kubuntu, Ubuntu or Xubuntu; the real difference between those 3 is the Desktop Environment/Window Manager.  It's a personal preference really when it comes down to those, and you can always install something like KDE over your GNOME installation, etc with quite a bit of ease.

---

### Post by RomeReactor on 2007-04-16
Hi. I recommend you wait a few days to download Ubuntu Feisty Fawn, which will be released on April 19; once you download it and burn it, give it a spin to see if it properly recognizes your hardware before you decide to install it or not. If you want to see what the different desktop environments look like before settling on one, look [here]("http://shots.osdir.com/") for **Ubuntu**, **Kubuntu** and **Xubuntu**.

---

### Post by tstockma on 2007-04-16
All right, thanks!  Three Edgy users, who all think Edgy is good & one of them says, Feisty in a few days will be even better.

I'll give Edgy a quick try, which I'll probably then replace after initial bugs prove non-lethal with Fiesty.

Thanks again!  Hope this goes better than my Dapper Disaster!

Tom

---

### Post by stmiller on 2007-04-16
Feisty. Newer kernel, newer gnome, kde, much better networking and wireless. 3D support in official mirrors, NTFS read/write support,... I could go on.

---

### Post by josephus on 2007-04-16
If you don't want to wait till Thursday for Feisty, I think that installing the latest build of Feisty might be a better bet than installing Edgy today and upgrading next week (but maybe that's just me since I think a fresh install is better than a distribution upgrade).

[http://cdimages.ubuntu.com/daily/20070415/](http://cdimages.ubuntu.com/daily/20070415/)

---

### Post by gnoel on 2007-04-16
I would consider partitioning your Windows disk and installing Ubuntu there, then moving all your data and media files to your second 160 GB harddrive.  If you want to be safe format it as FAT32, though Feisty is supposed to have NTFS support.

The advantage to this is that

a) You can fool around with your OS disk and not worry about trashing your data
b) You just boot into the OS best suited for what you need to do, e.g. you may use windoze for games and video editing and Ubuntu for everything else :) 
c) Once you are feeling overconfident, you can add smaller partitions to your OS drive and install , play with, and even break several Linux distros worry-free.

BTW, I've found gnome to be very stable - very happy with it.

Good luck!

---

### Post by tstockma on 2007-04-16
Thanks, guys.  I have old prejudices against going with either Beta or the first Production release of anything, but I'm going to give Feisty a whirl anyway.  Good comment, Gnoel, ultimately I'd like both OS's to live on the same HD...I just plan to feel my way around some before risking the W2K partition...

And Josephus, I agree with your thinking...so my plan is, install Edgy just to experiment & learn, then delete it.  So it won't be an upgrade to Feisty, it'll be a fresh install.

Thanks!  I'm looking forward to this.

---

### Post by hyper_ch on 2007-04-17
Well, I'd also say Feisty... and beta on linux isn't the same as beta on windows...
The same goes critical security patches on linux isn't the same as critical security patches on windows...

---

### Post by tstockma on 2007-04-17
Thanks, hyper_ch, while beta on Windows is indeed horrible, my aversion atually predates Windows, coming from past experience  with companies like IBM, Sun, DEC, Oracle, Ingres, Unisys...!

TROUBLE WITH EDGY

So I'm downloading Feisty now.  Same trouble with Edgy that I had with Dapper.  The load of the install Kernel hangs, hangs, hangs.   I'll find out what Feisty does, then hope for more response on these forums with debugging that problem than I had with Dapper...

---

### Post by hyper_ch on 2007-04-17
Could it be the ACPI issue?

---

### Post by tstockma on 2007-04-17
Could be.  I've been trying acpi=off, nolapic, and ide=nodma...still getting that same hung load of the LiveCD linus kernel on Dapper, Edgy, Feisty.   I still can't find any documentation about "boot options", other than, they exist, and some threads suggest a few now and then.

I'm about to post a new thread, something like "no, seriously this time, which Ubuntu to use..."  I have put in perhaps 36 hours over the last 48 working on this issue, and have exactly nothing to show for it.

Obviously, I'm a tad frustrated!  I'll try not to let it boil over.  Any suggestions or links you have would be much appreciated.

---

### Post by tstockma on 2007-04-17
I asked a question last night, "which version of ubuntu might deliver a good 1st experience?", as I've been struggling with a Dapper Drake install.  

Many folks said, Edgy is much better & probably installs fine, but just wait 3 days for Feisty!  So I've tried Edgy and the current Feisty test download.  These are mostly the Desktop versions, also the Dapper Alternate.

I'm still getting the same issue on attempting to install.  No LiveCD kernel load seems to work, they all just hang and sit there.  I've used F6 to nuke the "quiet splash" options, and tried many variations of "verbose acpi=off nolapic ide=nodma".  

Thrice I've gotten actual text flying by from the kernel load as it processes, twice it even got to a command line.  But I cannot get it to repeat that behavior, and didn't know how (still don't) to get to GRUB or any Install options from that command line.

Massive sifting thru forum & knowledge-base articles suggest many causes, including a bug that I believe is commonly a factor in Dapper but also the other versions.

What I especially need is a version of Ubuntu that's better at handling this.  Also very welcome would be a comprehensive documentation of "boot options" for the F6 command.  Neither DEBCONF_DEBUG=5 or BOOT_DEBUG=2|3 seem to reliably produce that "verbose" output I'm looking for.

Any help would be much appreciated...thanks!

---

### Post by Terl on 2007-04-17
Are you trying the alternate cd or the "live" version?  If you have the live version is it going to the desktop at all or is this where it is hanging?

---

### Post by insane_alien on 2007-04-17
try burning the disks with a slower speed. if you burn at maximum then errors can be introduced. you could use the 'check disk for errors' option as well. that should take around 10 minutes. also, how much RAM does your computer have? it needs more than 192MB to run the Desktop CD.

If you run the  alternative CD then you won't get a live desktop to install from and you'll need to use the old textbased installer(not that its hard, same options just less fancy looking)

---

### Post by tstockma on 2007-04-17
I've been trying both the Desktop LiveCD, and the Alternate.  I burned all of them at the slowest speed burnatonce will go, sometimes that's 4x, sometimes 8x.  I've run MD5 on the downloads.  I have 1GB memory.

I can't run the text-based installer from the Alternate version, I can't run "check CD" from any version...those all require the LiveCD linux kernel to load.

As soon as I pick any choice from the 1st menu that comes up on the 1st splash screen, I get "loading linux kernel" in a pop-up, which is loading the LiveCD linux kernel.  It immediately hangs.  I never get another splash screen, a desktop, or a menu with any choices.

F6 on that very 1st menu, the one I do get, "more options", gives me the ability to specify command-line options for that LiveCD linux kernel load.  I'm hoping to find there's options here that will display "verbose" output from the load so I can ID what's going on...or better yet, some other way to install Ubuntu that bypasses these issues...

Thanks again for any help!

---

### Post by zvacet on 2007-04-17
You don´t need live CD to chek Cd.When you boot up you will see several options and one of them is chek Cd integity or something like that(I don´t remember quite well).Select that option and you will see wich result you get.Maybe is bad download,maybe something else.When you know exactly what it is post here if you need any help or advice.

---

### Post by tstockma on 2007-04-17
Thanks for checking in, zvacet.  I took a few minutes before I replying, so I could verify...which I just did...

On both Dapper-Alternate and Feisty-Desktop, the "check CD" options _do_ load a linux kernel.  And that kernel freezes, nothing happens.

I don't know what the problem is, that's why I'm posting.  If it's a bad download, it's 4 downloads that were all checked using md5.  If it's a bad CD burn, it's 5 different burns.


ITEM OF INTEREST

On Feisty, I accidentally did something I haven't before...I hit escape while sitting on that graphical menu.  It escapes to a text boot option!  I got a pop-up saying, "You are leaving the graphical boot menu and starting the text mode interface."   With buttons to continue or cancel.

Continue got me a command-line type prompt, which was this: "boot:"  SO assuming I could then enter whatever parms I want, I could boot from there.  My suspicion is, it would boot the same kernel as all the other commands from the graphical menu, and if I know the correct parms, I could try this to see what happens...damn, again I'm back at asking, what are the possible parms?

Again, any help or advice is welcome & appreciated, as I struggle thru trying to get this to install.

I gotta go, my employment beckons.  So I won't see a reply here until hours from now.  I will leave the system in one of those hung installs, just to see if many hours makes a difference...regards!

Tom

---

### Post by earobinson on 2007-04-17
id vote for the latest and greatest! honnest!

---

### Post by annda on 2007-04-17
for kernel parameters:

from knoppix, but they should be the same:
[http://www.kernel.org/pub/dist/knoppix-dvd/knoppix-cheatcodes.txt](http://www.kernel.org/pub/dist/knoppix-dvd/knoppix-cheatcodes.txt)

Linux BootPrompt-HowTo:
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

and for the latest feisty kernel see the attachment

---

### Post by hyper_ch on 2007-04-17
Have you tried the altnernate install?

---

### Post by theDaveTheRave on 2007-04-17
Tsockma.

I would go for the suggestion of gnoel and install both OS's onto the same HDD, then use your second HDD as a shared files storage.

This has worked straight off for me with a number of distro's (SuSe old and new, and now ubuntu).

I must admit that when I first installed Dapper i was more than a little confused by some of the requirements during the install process, and i seriously thought i was going to loose my XP partition for a while. But you are able to "abort" the install untill you are happy with the options.

Your other alternative may be to load all your windows stuff (re-install basically) onto your second HDD, don't do any partioning when installing Ubuntu so as it doesn't format the drive by accident, then if the worst does happen and you loose your first one you will be able to just swap them over and make it your primary disk and get all your info back.

One thing i will mention though.... I have 2 HDD's in my pc, both have a version of windoze on, and both are available from the GRUB loader at boot, however, the version on the slave disk will not boot up..... not that I need it though!

I must admit I am looking forward to getting a new pc with just fiesty or edgy installed.

right now I'm off to do an upgrade on the laptop to edgy :popcorn: 

Dave

---

### Post by Neobuntu on 2007-04-18
Not fiesty. It has not even been out a while.

Dapper. Because any of it's imperfections have ready solutions. It's the best thing going and it is LTS.

---

### Post by tstockma on 2007-04-18
A big thank you to all that posted, I see lots of good info.  Let me sum up what I'm now thinking:

- I left the Edgy desktop CD in the machien for 12 horus...no luck, so it isn't a problem that I'm giving up & rebooting too soon while the boot kernel loads.

- Aanda, lots of gratitude here for your information - those 2 links you posted are what I've been wanting to find for several days now!  I'll be carefully reading those for a couple hours today, and I think I'm much better off for having your information.

- DaveTheRave, I do like your suggestion best, to get my linux system running from that partition.  I'll do some experiementing with Grub & hopefully get my comfort level at a better place...it'd be a real problem to lose that existing Windows partition off the main drive.

- For all others, regarding which version to go with...I'd probably prefer Edgy at this point, as the latest fairly stable one...any of them, up and running would be acceptable!  Now that I know for sure my problem is a Ubuntu problem in general, not just one of the releases, at this point I'd any _anything_ that loads...!

I'd still appreciate any more comments and solutions...I will be reading Annda's links, and hopefully trying a few of the boot options I see there.  Thanks again for all the help.

Tom

---

