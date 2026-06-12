---
title: "Wipe Ubuntu Clean and Start Over?"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by Darko Beta on 2007-01-26
So I have made it through the ultra-noob stage and I am getting to know what I'm doing, a little bit.  I am wondering if it's advisable at this point to do a fresh install of Ubuntu.  I have installed and uninstalled a million programs, tried (and failed) to get beryl up and running--so fiddled with xorg, log-in scripts, fglrx, all that stuff--and recently ran into a problem where I was compiling from source for a prog that was conflicting with a previously installed (and uninstalled) version.  I feel like my ubuntu is a little scattered at this point!  I keep all my files on an external hd, so no worries there.  Everything works fine right now, it's just that I have screwed up my xorg and video card settings and patched them more than a few times, and bumbled my way through a lot of stuff.  How have others dealt with this stage of learning ubuntu?  Did you do a clean install after a few weeks?

---

### Post by lamego on 2007-01-26
If you have performed actions why you can't undo and which may affect your system stability I would advise you to do a clean install, if you are still learning you should keep it as it is until you feel you don't need to damage it to learn.

Next time please create your /home on a dedicated partition, that makes system reinstalls much easier because your data is not mixed with your system files.

---

### Post by ComplexNumber on 2007-01-26
> and recently ran into a problem where I was compiling from source for a prog that was conflicting with a previously installed (and uninstalled) version.thats not going to affect the rest of your system ;)


however, if you feel that you want to do a fresh install, then i **strongly agree** with what lamago has said here:
>  Next time please create your /home on a dedicated partition

---

### Post by Pobega on 2007-01-26
Yeah, I did the same thing when I was new. I messed with Ubuntu for about a month, and then I ended up deciding to just reinstall (I messed with a lot of things, and my computer ended up running extremely slow; 1GB RAM running Xubuntu shouldn't be taking 20 seconds to load Firefox). I then put my /home folder on a seperate partition, and I've enjoyed it ever since. I recently reinstalled Ubuntu (Because I don't want any non-free things on my system), and the /home partition came through for me; All of my settings, bookmarks, and themes were still all intact.

---

### Post by flipout on 2007-01-26
All the more reason to back up your config files before tinkering with them :D 

When I began fiddling with linux (SuSE 9.3 at the time) I toyed with so many config files and options, that I think I was re-installing just about every other day. Quess I got the installation down to jots and tittles :guitar:

---

### Post by ComplexNumber on 2007-01-26
**Darko Beta**
in most cases, a fresh install is not necessary. but a fresh install can feel like buying a new car (ok, slight exaggeration but you get the point). there's no scratches on the paintwork (eg no messed up config files), no cigarette stains above the drivers seat from years of smoking (ie no orphaned files scattered about the filing system), no dodgy piston (eg messed up xorg due to tinkering), etc.
everything feels 'like new'.

---

### Post by citizenofnowhere on 2007-01-26
Ditto on the home partition though it can be a bit of a pain if you have too many primary partitions and like to resize things like I do. So you can just backup instead (there's a great howto out there, I've lost the link but google for "ubuntu howto backup" and you'll find it)

If you've messed with graphics drivers, mesa and the like - reinstall! Suddenly things like 3d acceleration will work much better (especially if you've got edgy)

---

### Post by pak33m on 2007-01-27
Hello,

I will be performing a reinstall & have currently backed up home with only personal & config files.  I have several questions with regards to the reinstall & what has been discussed in this thread:

If I were to create home on a separate partition would it be done during the install through LVM or after the install through LVM or some other method?

If I do create home on a separate partition will the config files still go there?

Are there any problems with copying the backup of home, for a fresh reinstall, to the newly created home on a separate partition? Particularly with the config files?

---

### Post by citizenofnowhere on 2007-01-27
During your installation, you will be given an option to either 1) allow the ubuntu installer to partition your hard disk for you, or 2) to do it yourself using the "advanced" menu (in other words gparted).

This is probably the best time to create a separate partition - you'll have less issues with permissions down the line. Then once your installation is finished, boot up and untar your backup. I would put the extracted files in a separate folder first (if your home folder is /home/user then i'd untar into /home/user1 and copy all the files as a normal user (**not** sudo/root) into your /home/user).

This worked for me the last time I needed to reinstall. You shouldn't run into any serious issues, as long as you copy the files as a normal user. Now you'll be able to reinstall whatever you want without damaging all your precious settings! :) Have fun!

---

### Post by pak33m on 2007-01-27
Thanks citizenofnowhere!

I guess I never thought of creating a separate partition because the laptop that I have only has 30GB disk space.  I will try it this time though because I would like to install a newer version when they're stable.

I'm still wondering though if I copy the config files back into the new home if there will be problems with the new install? I know that he config files are, well, the configuration for my installed programs.  However, I just don't know if copying the config files to the new home will invite problems for the new version?

The reason that I'm doing a fresh install from Dapper is because I've had trouble with hardlocks & other minor problems.  For some reason I had been running under a 686 kernel & since have corrected that, but I still am having some problems.  I'm not afraid to move forward or run a fresh install.

---

### Post by citizenofnowhere on 2007-01-27
Sounds like a fun time - I've got 80GB on my lappie and that's nowhere near enough.

Back to your question though - there isn't anything inside your home parition that could render your system lifeless. The worst that can happen is a program might throw you errors (for instance my firefox kept telling me it couldn't install any add-ons until I deleted a couple of files and let them refresh the next time firefox started). In which case, just backup/rename the appropriate hidden folder for that program and start over. 

Are you upgrading distributions? Dapper->Edgy? I know that the gnome version is different and gaim, so there might be a couple of new/different configuration files. But most things in your home partition work on the general principle that if the file doesnt exit, the program will create it for you. 

If you're really worried, then you could try upgrading the system (from a cd repository or do a dist upgrade) THEN backing up the home partition, though that's a bit of an overkill :)

Besides, you have a backup of everything you need. Experiment :)

---

### Post by pak33m on 2007-01-27
I use this laptop the most of what I have.  There is even barley any personal data on it, except for music that I already have backed up.  I do have some programs on here that I have compiled & want to keep.  Although I'm not intimidated by having to compile gain or reinstall other programs. I'll just have to get an inventory to keep track.

Yes.  I'm going Dapper -> Edgy.  And I was even considering going to Xubuntu.  I run it on another laptop that is very slow & I have enjoyed it so far.  It's just a wee bit different than Gnome.  And some of the programs I run in Dapper require the Gnome libraries on Xubutnu. 

I think that I'll just copy over the config files for the installed programs & start anew with the rest of the OS.

I thought about a dist upgrade, but then I'm hoping a fresh install will make the unresolved problems go away.  I hate to do a fresh install just because of the problems, but it seems like I could only get so far.  I'm not afriad to move on! And I'm NOT going back to Windows because of it, but then again - NOTHING could ever have me go back there.  Sorry for the rant, but I've read enough of that here.

---

### Post by citizenofnowhere on 2007-01-27
That's the spirit! 

Doing a fresh install of Edgy is indeed a much better idea - I had quite a number of problems with the dist-upgrade. 

Having said that, I ended up messing up my Edgy so bad I had to do a clean install and I got everything back the way I like it in a matter of days.

All the best to you!

---

### Post by pak33m on 2007-01-28
I messed up a work VMware image of Dapper by peforming a dist upgrade (or manual) to Edgy!

Well, here I go.  Y'know I'm just not afraid to move on.  I beleive that this is what this OS (& Linux) is all about: freedom.

I'll post my results later.  Or during the install or post-install depending on all fairs...

---

