---
title: "One small installation mistake escalated to disaster.."
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by Donalb on 2007-09-04
Hey all, 
First , usual newbie disclaimer, my knowledge of formatting etc inherited from my DOS days .

OK, decided to use the Live CD of 7.04 to do a trial install (after having tried the LiveCD load and really liking it. The system has a 160gb ATA drive, which was defragged first, and had plenty (90GB) of free space.

 I allocated about 50gb for the ubuntu install, and everything went ok.

After the restart I found I was unable to login. So while I couldn't figure out how I had managed to misspell my name or standard password in the setup,.. nevertheless I figured that's what I did (tried all the usual caps on/off/mispellings combos, but no big deal... I'd just re-install it and make sure my login/password was correct.

Next time around however, I had 2 extra small partitions present, one had obv. been set  up for the swap. Not entirely sure what I was doing I decided to reformat them to ext so they "wouldn't be left over space".
Well on the next installation, I went off for a few minutes and when I came back everything seemed finished. I did a restart and got a grub error.(can't remember but it was pretty basic, something like "grub, error 15").

OK...
back in with LiveCD. Try again, do a reinstall again just in case. However I couldn't got partition errors. So I thought, what the hell... I'll just do an install on the full disk ( I have a Ghost image of the hdd, no big deal, hey I might be learning here). That however didn't now work. Got another partitioning error, not very clear. 

I decided to reformat the entire drive, do an install on that. Hey, take off and nuke it from orbit,  the only way to be sure right....
However.....format failed. Partition editor is now showing three partitions,  sda 1 with about 148gb file system "unknown" but with a "boot" flag set and two small partitions <2gb one titled extended and one as linux-swap. 

Concurrently In the install wizard at the prepare partitions stage I see 2 partitions, one of 158gb and one of 2gb.Trying to move on gives "no root file system is defined" 
.So right now, I'm don't know what my next step is.   Reformats seem to fail. I'd be happy to get reformat the whole disk but it doesn't seem happy about ti, though I've only tried fat32, as I wasn't sure if I tried ext 3 would i be able to revert to putting my windows image on. So I tried it anyway, still failed ext3 format. 

Hope someone can help, figured I write it all out to contextualize.
Regards
Donal

---

### Post by combatghoul on 2007-09-04
Best thing to do is use the Live CD, boot in using there and use someting
like gparted or qtparted to fix the harddrive problem.

Cheers!

---

### Post by Donalb on 2007-09-04
Thanks but GParted is what keeps returning the errors when I try to reformat the drive (to the different filesystems, ext3 and fat32).

At worst I could try rebooting from rescue CD and fdisking the drive, but since my cd burner in in the machine that's hosed, that will involve lots of extra steps (downloading a dos tools bootable iso and travelling to my ex's house for the nearest burner) just to get back to a bare netal drive. I'd prefer if I could do through the livecd. Any other suggestions?

Donal

---

### Post by philinux on 2007-09-04
Ok one thing to try.

boot from the live cd. One of the options on screen should be 
Recover a broken system

Click that.

For other info on this see this - [http://www.cyberciti.biz/faq/howto-boot-ubuntu-linux-rescue-mode/](http://www.cyberciti.biz/faq/howto-boot-ubuntu-linux-rescue-mode/)

---

### Post by Donalb on 2007-09-05
Cheers, however the LiveCD doesn't have this option on reboot so  i went for the nuclear option and re-imaged the hdd from a Ghost image on a Rev drive. Should have done that first maybe as it only took 25 mins to make the Hdd fully operational again with file structure rebuilt etc.
I then went back and did the Ubuntu install again, this time being more careful with the login passwords etc. and everything went fine, with Ubuntu now up and running on my home PC. A couple of months learning and I hope to blow away the Windows partition.

As it stands however I would say Ubuntu is still not ready for prime time clueless newbie installation.
While I know nothing about Linux, the fact that I understood how to recover my windows  partition puts me in a small group. And how many people have a full image of their HDD ready to go?
Too many things are either implied or not explained at all.
For example in the Installation info right off the Ubuntu home page, I found this sentence. "Make your way to the partition editor", and lots of other similar phrases. OK for me but crap for someone who has no idea what they mean.

My problems came about in the partitioning, the thing that is most likely to stop/scare people. The errors received were useless, and the context was never explained. There was no Help link explaining the mount concept or the sequence of events required to get a hdd up and running, confusion between what the install section on partition showed and what the gparted app showed, which to use etc.
These are all suggestions from me for areas that need work to improve the experience. Keep up the great work though, as this is meant as constructive feedback.
Regards
Donal
ps since it's unlikely many will read them in this thread, I might try to find somewhere else I can post them as to add the general installation information.

---

### Post by hyper_ch on 2007-09-05
> **Donalb said:**
> As it stands however I would say Ubuntu is still not ready for prime time clueless newbie installation.

Most people never had to install windows on their own including all the drivers and stuff ;) so I tend to think if you hand over a windows cd and cleaned computer they whould be equally cueless

> **Donalb said:**
> While I know nothing about Linux, the fact that I understood how to recover my windows  partition puts me in a small group. And how many people have a full image of their HDD ready to go?
About as many people that also did an windows install in their life ;)

> **Donalb said:**
> Too many things are either implied or not explained at all.
The same goes for Windows...


> **Donalb said:**
> For example in the Installation info right off the Ubuntu home page, I found this sentence. "Make your way to the partition editor", and lots of other similar phrases. OK for me but crap for someone who has no idea what they mean.
See above, same goes for windows... ;)

> **Donalb said:**
> My problems came about in the partitioning, the thing that is most likely to stop/scare people. The errors received were useless, and the context was never explained. There was no Help link explaining the mount concept or the sequence of events required to get a hdd up and running, confusion between what the install section on partition showed and what the gparted app showed, which to use etc.
Hmmm, normally linux does give feedback of what's going wrong... this sounds to me very odd...

> **Donalb said:**
> These are all suggestions from me for areas that need work to improve the experience. Keep up the great work though, as this is meant as constructive feedback.
They are appreciated and, until Linux comes preinstalled like windows, those thigns need to be improved... but then, on windows you have the same problems if a normal windows user has to install his system on his own... by comparison I tend to think the Ubuntu install is much cleaner and less complicated than a windows install... (and it's also faster if you remember your login ;))

---

### Post by jw5801 on 2007-09-05
Ok, the reason you'll be getting errors in the first place is because gnome-volume-manager will attempt to automount any existing partitions, which makes it very hard to partition properly.

Try using the GParted LiveCD (see the link in my sig.) to partition your drive however you want, you might want to restore your ghost image if you're looking to dual boot before you do this, then partition like you originally intended. Then you'll have your partitions set up all ready to go and you can simply tell the installer to install to the partition you prepared. This is the way I've always done it, I never like letting any installer automagically set up my partitions, it just seems safer to retain control of the process.

Some errors/info/advice can be slightly ambiguous to the new user... but that's why we have such an incredible support forum!

Lastly, **please don't turn this thread into a Linux is/isn't ready for the Desktop thread**, there is one of those and we don't need another! I know there's only been one post so far, but I've seen it happen so many times and the OP's problem just gets lost in a sea of debate, all constructive and to the good, but this isn't really the place for it... :p

---

### Post by Donalb on 2007-09-05
Thanks for the feedback guys. As I said it wasn't meant to be a negative response. My comments were actually due to the fact that i'd have no similar problems in windows, just because of experience I guess, but at the critical partition point in the ubuntu install  with the errors I was clueless. 

I have seen quite a few references to the "recover from a broken system" or whatever it is in the LiveCD boot options, but which is def. not on my LiveCD.

Anyway, thanks again. I'm up and running anyway.
Regards
Donal

---

