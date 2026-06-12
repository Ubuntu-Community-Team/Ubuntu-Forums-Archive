---
title: "Any tips on fixing Yaboot after OSX install on dual-boot PPC?"
date: 2015-12-31
forum: Apple Hardware Users
---

### Post by este.el.paz on 2015-12-31
Folks:

Been playing with keeping a Sawtooth running in today's online environment, and a  couple of months or more back upgraded the cpu for more speed, but doing that seemed to "corrupt" everything it touched on disk volume . . . destroying installs of OSX, and messing with Xu 12.04 . . . but 12.04 was able to "get over" the crashes and I ran that exclusively for quite awhile.  Recently, looking for a tad more functionality . . . I tried to re-install 10.4, which failed, and I wound up with a successful 10.5 install . . . but, not surprisingly Yaboot was "unblessed."  

I've tried just about all of the suggestions on the PPCFAQ, the openfirmware, the PRAM . . . I ran "rescue" from a Lu 14.04 live DVD, which went right up to the last step, then failed . . . did that 2-3 times . . . then I saw the "Have to use the same system" . . . so I used the rsavage Xu 12.04 CD . . . which didn't work.  But, while I was booted in the 12 CD I found the Yaboot.conf file . . . so all the stuff is there.  When I hold the option key I get the OSX & the Linux disk, I click on Linux, the Yaboot window opens, I select "L" . . . and the window moves back to the OSX boot loader, but, nothing then works . . . stuff is blacked out, and I have to reboot.

Any thoughts on if it is possible to re-connect to Yaboot, or, something is "messed up" and time for a fresh install???  Since the cpu is set at 1 GHz now I might not have to go back to 12 . . . but, it has sound, stuff works pretty well, it got me out the original jam of changing the cpu . . . designed and enhanced by rsavage . . . it has a special place . . . if I can fix it I'll try.  Here's the latest stuff I tried, except for the nvram gambit:

[https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot](https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot)

---

### Post by este.el.paz on 2015-12-31
PS:  I also did the TTY from the live CD and tried "sudo ybin" . . . also did not seem to do anything . . . "don't understand" was the apt response.

---

### Post by este.el.paz on 2016-01-04
bump.

---

### Post by rsavage on 2016-01-04
> **este.el.paz said:**
> PS:  I also did the TTY from the live CD and tried "sudo ybin" . . . also did not seem to do anything . . . "don't understand" was the apt response.
Everything you've written here is gibberish.

---

### Post by este.el.paz on 2016-01-04
> **rsavage said:**
> Everything you've written here is gibberish.


This post from you is not even remotely helpful, which unfortunately is not a surprise . . . .  I listed the steps that I tried to follow from the FAQ . . . but so far none have been successful.

---

### Post by rsavage on 2016-01-04
> **este.el.paz said:**
> I listed the steps that I tried to follow from the FAQ . . . but so far none have been successful.

No you haven't.

There is a whole list of things to try - [https://wiki.ubuntu.com/PowerPCFAQ#I.27ve_lost_yaboot.2C_what_can_I_do.3F](https://wiki.ubuntu.com/PowerPCFAQ#I.27ve_lost_yaboot.2C_what_can_I_do.3F) .  A section that is entirely written by myself.  How helpful is that?  So the answers are there, before you asked the question.  I thought it was pretty idiot proof.

Have you confirmed your linux partition is still there?
Do you know what partition number it is?
Then you can boot the system following the instructions.

Nowhere does it say to run just "sudo ybin" - that would be stupid.  If you had run it (or [COLOR=#333333]sudo ybin --config /mnt/etc/yaboot.conf -v which it tells you to run)[/COLOR], then you would of got something more coherent than "don't understand".  I'd of thought including the actual error message would of been beneficial?  And "apt" is the advanced packaging tool, so has nothing to do with yaboot.  Hence, gibberish.

If you still can't boot, then please let us have a detailed list of your partitions.  Please print your yaboot.conf and ofboot.b files from your bootstrap partition.  Please include your yaboot.conf from your /etc directory on your installed linux system.  Please include any error messages, exactly as they are written.  Without these things then it is just guessing based on verbal diarrhoea.

---

### Post by este.el.paz on 2016-01-05
> **este.el.paz said:**
> Folks:

  but, not surprisingly Yaboot was "unblessed."  

I've tried just about all of the suggestions on the PPCFAQ, the openfirmware, the PRAM . . . I ran "rescue" from a Lu 14.04 live DVD, which went right up to the last step, then failed . . . did that 2-3 times . . . then I saw the "Have to use the same system" . . . so I used the rsavage Xu 12.04 CD [to try to run rescue] . . . which didn't work.  But, while I was booted in the 12 CD I found the Yaboot.conf file . . . ****so all the stuff is there.****  

When I hold the option key I get the OSX & the Linux disk, I click on Linux, the Yaboot window opens, I select "L" . . . and the window moves back to the OSX boot loader, but, nothing then works . . . stuff is blacked out, and I have to reboot.

Here's the latest stuff I tried, except for the nvram gambit:

[https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot](https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot)

@r:

Appreciate the follow-up, don't have time to go through and list the partition table stuff right now, I broke open my original post so it is easier to read the steps I tried.  I did copy/paste the Yaboot.conf file and email it to myself, so I can post it at some point . . . .  In terms of the "sudo ybin" being "stupid," it's mentioned in your FAQ and in the other one that I found linked through your FAQ, I believe . . . .

> se a command like this to start yaboot: boot hd:2,yabootOnce the system has booted, *****run ybin**** to make yaboot the default bootloader.  See the questio

Later,

e..

---

### Post by rsavage on 2016-01-05
> **este.el.paz said:**
>  . . . .  In terms of the "sudo ybin" being "stupid," it's mentioned in your FAQ and in the other one that I found linked through your FAQ, I believe . . . .

Yes of course you have to run ybin at some point, but it is very clear that you should do this once you've booted into your installed system.  You said you'd run sudo ybin from a live CD which is stupid, unless you specify the yaboot.conf file to use.  Are you really going to argue with this?

The use of sudo is there for a reason.  The command has the potential to be destructive.  Only use a command with sudo if you know what it is doing.

If we discount user error, and if I had to guess what has happened, and this is a wild guess, then I would suggest that possibly your bootstrap partition has somehow been renumbered in the partition order.  I don't know if this is at all a possibility, not having much experience with mac os x installs.  It seems far fetched.

But since, in this case, there is a high probability of user error, it could be anything.  It probably isn't what I've just described above.  You see the problem?  How is one supposed to offer advice, when there is almost nothing to go on?

The fact remains though, until the system is overridden then it is bootable if the instructions are followed and intelligence is applied to interpret those instructions and check configuration files.

That's me finished on this thread, I think I've answered your question.  Maybe somebody else will step in to help you further.

---

### Post by este.el.paz on 2016-01-05
Awesome.  Yes, of course user error is involved . . . doing any install or upgrade of OSX seems to "wipe" the Yaboot "fork" or whatever it is . . . and trying to follow numerous suggestions in the FAQ did not appear to "work."  Hence my post here looking for some insight into what should be a "known issue" for those who have a dual-boot set up with OSX . . . but, apparently not.

Appreciate the insights into the problem, problem is that the linux side was not booting in spite of trying different suggestions . . . hence my post.  I may try to run through the FAQ hints again and see if that makes any difference; will likely opt for the ultimate solution.

e..

---

### Post by rsavage on 2016-01-05
For what it is worth, if mac os x really does de-bless other partitions then holding down the option key won't work.  This is contrary to the advice here [https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot](https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot) , but since I didn't write it, and I don't use Mac OS X, it is for others like yourself to investigate and document.  The advice in the FAQ remains good though, the option key could work in other situations, and the other suggestions listed most definitely would work.

---

### Post by este.el.paz on 2016-01-05
> **rsavage said:**
> For what it is worth, if mac os x really does de-bless other partitions then holding down the option key won't work.  This is contrary to the advice here [https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot](https://help.ubuntu.com/community/YabootConfigurationForMacintoshPowerPCsDualBoot) , but since I didn't write it, and I don't use Mac OS X, it is for others like yourself to investigate and document.  The advice in the FAQ remains good though, the option key could work in other situations, and the other suggestions listed most definitely would work.

Well, that is indeed what is happening in the PM 3,1 . . . the option key is partially working . . . it does go to the Yaboot page, but typing "l" leads back to the OSX boot manager . . . which then is "frozen."

However, since my last post, and while fiddling with the Xu 14 system in the iBook . . . I tried to fix the Yaboot conf file there, which ***also*** got damaged while trying a daisy-chain maneuver to try to reset "start-up disk" in OSX of the PM . . . to see if that would fix the Yaboot situation in the PM . . . but, it just messed up the iBook's Yaboot powers.  But, in the iBook I hadn't done any OSX update . . . there, the Yaboot window wouldn't load upfront, but holding the option key did work to launch linux . . . .

So, after running routine "sudo updates" . . . blithely using sudo like it was meant to be . . . I nano'd the Yaboot.conf file and compared it to the data in Gparted . . . looked OK, saved it as it was . . . then ran "sudo ybin -v" . . . and got it "Blessed by Holy Penguin Pee" . . . and reboot, the Yaboot window opened as before . . . .  So, I have the procedure there, have done it awhile back . . . problem though remains getting into the linux system in the PM to run that command . . . .  Rain stopped here, might try a few of the other options in the FAQ and see if the Holy Penguin will offer it's Pee Blessing . . . or, Pee elsewhere.

e...

---

### Post by lisati on 2016-01-05
Thread closed for staff review.

---

### Post by oldos2er on 2016-01-05
I would like to remind posters in this thread of the forum's Code of Conduct, to which we all agreed when joining; in particular:

**Trolling, Attacks and Flaming:** These are always forbidden. 
[LIST]
[*]Trolling is posting in a way that provokes emotional responses.
[*]Attacks and derogatory terms of any kind are not welcome. This  includes references to any operating systems or the companies that  produce them.
[*]Flames are messages that personally attack or call any people names  or otherwise harass. These, along with any generally condescending posts  will be edited or removed at the moderators discretion.
[*]If a thread is flame-bait (appears to be intended to start an  argument or is likely to cause an argument rather than enhance  discussion, as in trolling), it will be locked or removed without  notice. Individual flame-bait comments in a post may be deleted or  edited at the moderators' discretion.
[*]If the thread turns into an argument, it can be closed to further  comment or removed without notice. Sometimes a moderator may split the  thread or jail certain portions in order to keep the discussion  going,this is not always possible.
[/LIST]


and



The purpose of the Ubuntu Forums is to provide support for Ubuntu. We  also want this to be a place where community can develop and we can  enjoy one another's company. To achieve this, we strive to maintain an  atmosphere that can be enjoyed by all and we ask all members of the  community to be respectful at all times. This means please use etiquette  and politeness. Treat people with respect. If you do this, the rest of  the code of conduct won't need more than a cursory mention.



This thread will remain closed.

---

