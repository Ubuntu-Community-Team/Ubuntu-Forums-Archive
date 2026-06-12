---
title: "Unable to load disk image on MacBookPro 4,1"
date: 2014-08-31
forum: Apple Hardware Users
---

### Post by AFTfunwithU1 on 2014-08-31
Hello all,

Unlike most users here, I have no intention of permanently installing an Ubuntu partition onto my storage drive.  I need Ubuntu for a single purpose only:  to download, extract, and run an application that only runs on Linux (or Windows, but I don't have ready access to a Windows machine).  One and done.

Problem is, I can't even get to the "one" stage.  I successfully burned Natty Narwhal onto a CD and tried booting from it.  The result was a flashing white underscore cursor on an otherwise blank screen.  I tried rebooting directly into the Live CD by holding down the 'C' key, and this time got to the Language Select screen, at which point the computer again become unresponsive to all forms of input.

After [seeing the support matrix on the Wiki]("http://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages#Mactel%20Wiki%20Support%20Matrix"), I figured I'd try my luck with a supported version of Ubuntu, so I burned [Lucid Lynx]("http://old-releases.ubuntu.com/releases/10.04.3/") (the desktop-i386.iso) and tried booting directly into the CD.  No dice; the boot process again hung up at the flashing cursor stage.

I'm running on a MacBookPro 4,1.  I've got 4 GB of RAM, 2.6 GHz Intel Core 2 Duo processor, and an NVIDIA GeForce 8600M GT graphics card.  Again, I only want to run Ubuntu from the Live CD -- it was supposed to be easy.  Am I doing something unforgivably stupid?  I need to know.  Any help is greatly appreciated.  Thanks in advance!

---

### Post by este.el.paz on 2014-08-31
> **AFTfunwithU1 said:**
> Hello all,

Unlike most users here, I have no intention of permanently installing an Ubuntu partition onto my storage drive.  I need Ubuntu for a single purpose only:  to download, extract, and run an application that only runs on Linux (or Windows, but I don't have ready access to a Windows machine).  One and done.

After [seeing the support matrix on the Wiki]("http://wiki.ubuntu.com/MactelSupportTeam/CommunityHelpPages#Mactel%20Wiki%20Support%20Matrix"), I figured I'd try my luck with a supported version of Ubuntu, so I burned [Lucid Lynx]("http://old-releases.ubuntu.com/releases/10.04.3/") (the desktop-i386.iso) and tried booting directly into the CD.  No dice; the boot process again hung up at the flashing cursor stage.

I'm running on a MacBookPro 4,1.  I've got 4 GB of RAM, 2.6 GHz Intel Core 2 Duo processor, and an NVIDIA GeForce 8600M GT graphics card.  Again, I only want to run Ubuntu from the Live CD -- it was supposed to be easy.  Am I doing something unforgivably stupid?  I need to know.  Any help is greatly appreciated.  Thanks in advance!

@AFT:

It should be working . . . I've got roughly the same machine I think . . . but why are you using "Natty" or "Lucid"???  I have 14.04 installed on my '10 MBPro . . . you should be able to use "Trusty Tahr" . . . .  Hard to know exactly what might be the problem with your process, but these days checking the md5sum number of the downloaded iso ***before**** burning seems to be a key point.  Many times recently downloading an iso brings a different number than the number posted with the "cdimage" page . . . and if it is wrong then "problems" . . . .  You might also try the "amd64" version, because the MBPro is 64 bit . . . or, possibly not necessary but these days there is an "amd64 + mac/apple" version of the iso, which might eliminate having to add stuff for Intel macs . . . but if you arent installing it shouldn't matter, at least as far as being able to boot the live desktop and test it out . . . .

Try 14.04 LTS . . . check the md5sum or the SHAxxx something number . . . you can google how to check that in OSX, it's simple . . . if the number doesn't match . . . try again later until the number matches.

e.e.p.

---

### Post by AFTfunwithU1 on 2014-08-31
> **este.el.paz said:**
> @AFT:

It should be working . . . I've got roughly the same machine I think . . . but why are you using "Natty" or "Lucid"???  I have 14.04 installed on my '10 MBPro . . . you should be able to use "Trusty Tahr" . . . .  Hard to know exactly what might be the problem with your process, but these days checking the md5sum number of the downloaded iso ***before**** burning seems to be a key point.  Many times recently downloading an iso brings a different number than the number posted with the "cdimage" page . . . and if it is wrong then "problems" . . . .  You might also try the "amd64" version, because the MBPro is 64 bit . . . or, possibly not necessary but these days there is an "amd64 + mac/apple" version of the iso, which might eliminate having to add stuff for Intel macs . . . but if you arent installing it shouldn't matter, at least as far as being able to boot the live desktop and test it out . . . .

Try 14.04 LTS . . . check the md5sum or the SHAxxx something number . . . you can google how to check that in OSX, it's simple . . . if the number doesn't match . . . try again later until the number matches.

e.e.p.

I was using the 10.X versions because they fit on a blank CD.   I'd have to purchase a DVD or USB key to fit the latest and greatest Ubuntu.  Another reason is that I figured the older versions might play nicer with my somewhat older machine.  Ultimately, I went to Lucid because of its appearance in the Wiki support matrix that I linked in the OP.

I always verify the md5 checksum for downloads like this.  The desktop .iso's for both Lucid and Natty verified.

Though you say that having a 64-bit system shouldn't matter if I'm not installing it, I think I'll still go ahead and burn another CD using the AMD64-bit version.  I was under the mistaken impression that my processor was 32-bit; perhaps this really could be the problem.  If it works I'll edit this comment.  Thanks.

---

### Post by este.el.paz on 2014-08-31
> **AFTfunwithU1 said:**
> I was using the 10.X versions because they fit on a blank CD.   I'd have to purchase a DVD or USB key to fit the latest and greatest Ubuntu.  Another reason is that I figured the older versions might play nicer with my somewhat older machine.  Ultimately, I went to Lucid because of its appearance in the Wiki support matrix that I linked in the OP.

I always verify the md5 checksum for downloads like this.  The desktop .iso's for both Lucid and Natty verified.

Though you say that having a 64-bit system shouldn't matter if I'm not installing it, I think I'll still go ahead and burn another CD using the AMD64-bit version.  I was under the mistaken impression that my processor was 32-bit; perhaps this really could be the problem.  If it works I'll edit this comment.  Thanks.

@AFT:

Jeez, I didn't know there was a support matrix . . . I'd have to retro install to get back to their suggestion.  But, trying the 64 bit should probably not make the difference, a 64 bit machine can run both, not vice versa--so doing that **might** help or might not.  I think it might be mentioned that the apple world in the forum isn't "over supported" so in that sense you have to explore google to see if you can find your answer . . . and then post it back here . . . .  : - )  But, so far the most stable release is 12.04 LTS . . . try to find a Xubuntu 12.04 release and play around with that--it has the XFCE desktop, very stable . . . but, yes, probably should get a DVD or USB drive and try to boot from that.  However, if what you have is a "desktop" you should be able to boot from it, even on CD and at least get to the CLI Grub boot window . . . that says, "boot" with the flashing prompt.  The other option is sometime it takes several minutes before the computer "figures it out" . . . might just take some patience????

Again, like I was saying, it should be working, esp. if the md5 number has checked out . . . .

e.e.p.

---

### Post by AFTfunwithU1 on 2014-09-01
> **este.el.paz said:**
> @AFT:

Jeez, I didn't know there was a support matrix . . . I'd have to retro install to get back to their suggestion.  But, trying the 64 bit should probably not make the difference, a 64 bit machine can run both, not vice versa--so doing that **might** help or might not.  I think it might be mentioned that the apple world in the forum isn't "over supported" so in that sense you have to explore google to see if you can find your answer . . . and then post it back here . . . .  : - )  But, so far the most stable release is 12.04 LTS . . . try to find a Xubuntu 12.04 release and play around with that--it has the XFCE desktop, very stable . . . but, yes, probably should get a DVD or USB drive and try to boot from that.  However, if what you have is a "desktop" you should be able to boot from it, even on CD and at least get to the CLI Grub boot window . . . that says, "boot" with the flashing prompt.  The other option is sometime it takes several minutes before the computer "figures it out" . . . might just take some patience????

Again, like I was saying, it should be working, esp. if the md5 number has checked out . . . .

e.e.p.

Same result with Xubuntu 12.04.3.   md5 checksum verified, but my computer won't even get to the boot menu.

I did notice something peculiar this time though...when holding 'option' to enter the boot menu, the disc boot option isn't labeled 'Ubuntu'.  Instead, it's always labeled "Windows".  I have been unable to determine what implications this may have.

---

### Post by este.el.paz on 2014-09-01
> **AFTfunwithU1 said:**
> Hello all,

.  I tried rebooting directly into the Live CD by holding down the 'C' key, and this time got to the Language Select screen, at which point the computer again become unresponsive to all forms of input.
!

> **AFTfunwithU1 said:**
> Same result with Xubuntu 12.04.3.   md5 checksum verified, but my computer won't even get to the boot menu.

I did notice something peculiar this time though...when holding 'option' to enter the boot menu, the disc boot option isn't labeled 'Ubuntu'.  Instead, it's always labeled "Windows".  I have been unable to determine what implications this may have.

@AFT:

Since you mentioned the "c" key in your first post I didn't repeat it . . . but, if 12.04 disk is inserted and spinning in OSX, then restart the computer when the screen goes black, then press the c key, holding it until you either get to the GRUB or boot prompt . . . , which it looks like you did in Natty . . . if you see the flashing boot underscore in the upper left, just let it flash for even several minutes and see if it will load the live desktop . . . .  Using the option key is OK, and having OSX label a "foreign" OS by naming it "windows" is just how they handle it . . . you should be able to boot it that way . . . usually it will show it as a "CD" . . . no?  Keep trying--12.04 is very well worked through by this time and it should work.  You should get to a "splash" window that says "Try ubuntu w/o installing" . . . and you would select that option . . . for the live desktop.

e.e.p.

---

### Post by AFTfunwithU1 on 2014-09-01
> **este.el.paz said:**
> @AFT:

Since you mentioned the "c" key in your first post I didn't repeat it . . . but, if 12.04 disk is inserted and spinning in OSX, then restart the computer when the screen goes black, then press the c key, holding it until you either get to the GRUB or boot prompt . . . , which it looks like you did in Natty . . . if you see the flashing boot underscore in the upper left, just let it flash for even several minutes and see if it will load the live desktop . . . .  Using the option key is OK, and having OSX label a "foreign" OS by naming it "windows" is just how they handle it . . . you should be able to boot it that way . . . usually it will show it as a "CD" . . . no?  Keep trying--12.04 is very well worked through by this time and it should work.  You should get to a "splash" window that says "Try ubuntu w/o installing" . . . and you would select that option . . . for the live desktop.

e.e.p.

Didn't know about the OS X labeling of foreign drives.  Cool, thanks.

I held 'c' until the underscore cursor appeared.  Once there, I let it flash for 25 minutes before my patience ran out.  I just don't think this is going to work on my machine, for whatever reason.  At this point, I think it's better to find an alternate way to accomplish my task.  Thanks for your help though.

---

### Post by este.el.paz on 2014-09-02
> **AFTfunwithU1 said:**
> Didn't know about the OS X labeling of foreign drives.  Cool, thanks.

I held 'c' until the underscore cursor appeared.  Once there, I let it flash for 25 minutes before my patience ran out.  I just don't think this is going to work on my machine, for whatever reason.  At this point, I think it's better to find an alternate way to accomplish my task.  Thanks for your help though.


@AFT:

25 minutes would indeed be "too long" . . . so yeah, probably better to move on . . . too many possible variables . . . could be something simple or something very complex.  But, perhaps there is an open source app for what you want to do for OSX?  Or you could try VirtualBox and try to boot the iso from VB . . . bit of a learning curve there, but it might work . . . same with "Wine" if you have a windows app that you want to run.

Or, try another linux distro . . . all of them are based on Debian . . . perhaps there is a Debian Wheezy iso that will run on your computer . . . usually the "search" will bring a "response" . . . keep trying.  Sorry it didn't work out here, but, good luck . . . post back when you get something running or whatever worked . . . and then "tools" >mark as solved . . . if it is, etc.

e.e.p.

---

### Post by AFTfunwithU1 on 2014-09-02
> **este.el.paz said:**
> @AFT:

25 minutes would indeed be "too long" . . . so yeah, probably better to move on . . . too many possible variables . . . could be something simple or something very complex.  But, perhaps there is an open source app for what you want to do for OSX?  Or you could try VirtualBox and try to boot the iso from VB . . . bit of a learning curve there, but it might work . . . same with "Wine" if you have a windows app that you want to run.

Or, try another linux distro . . . all of them are based on Debian . . . perhaps there is a Debian Wheezy iso that will run on your computer . . . usually the "search" will bring a "response" . . . keep trying.  Sorry it didn't work out here, but, good luck . . . post back when you get something running or whatever worked . . . and then "tools" >mark as solved . . . if it is, etc.

e.e.p.

I found a solution...use a different computer.  That same XUbuntu CD that failed to boot on my laptop booted wonderfully on an iMac11,3.  I was able to perform the necessary tasks without installing Linux onto non-volatile storage, and encountered no errors at all.

It's not an ideal solution to the original problem, but it was certainly easier than trying to debug my own machine.  Thanks for the help e.e.p; I learned some things from you and for that I can't consider introducing myself here to be a waste of time :)

---

### Post by este.el.paz on 2014-09-02
> **AFTfunwithU1 said:**
> I found a solution...use a different computer.  That same XUbuntu CD that failed to boot on my laptop booted wonderfully on an iMac11,3.  I was able to perform the necessary tasks without installing Linux onto non-volatile storage, and encountered no errors at all.

It's not an ideal solution to the original problem, but it was certainly easier than trying to debug my own machine.  Thanks for the help e.e.p; I learned some things from you and for that I can't consider introducing myself here to be a waste of time :)

@AFT:

Great work, and my pleasure if I could help . . . .  But, right, the apple user world in linux is kind of a "niche" and so it's hard to get feedback . . . at all.  So, perseverance furthers . . . and trying to "innovate" using tools that you can find on google or the forum to accomplish the mission is actually the "fun" of linux . . . which by tradition is a DIY system . . . for geeks by geeks . . . .  For those like me that have been used to OSX, doing it all quite well, the jump over to linux on mac can lead to some frustrating moments . . . but it certainly has been educational . . . .  I now have a linux LTS version loaded on a partition on each of my computers . . . and I jump on every once in a while and do stuff . . . so far the Xu/Lu flavors have been the most stable . . . able to survive updates w/o blowing up, etc. 

It's good work that you continued to try stuff and got it to work . . . when you get to a "rainy" day, maybe try to run an install on one of the machines . . . prepare for the winding road . . . enjoy the drive.

e.e.p.

---

### Post by AFTfunwithU1 on 2014-09-02
> **este.el.paz said:**
> @AFT:

Great work, and my pleasure if I could help . . . .  But, right, the apple user world in linux is kind of a "niche" and so it's hard to get feedback . . . at all.  So, perseverance furthers . . . and trying to "innovate" using tools that you can find on google or the forum to accomplish the mission is actually the "fun" of linux . . . which by tradition is a DIY system . . . for geeks by geeks . . . .  For those like me that have been used to OSX, doing it all quite well, the jump over to linux on mac can lead to some frustrating moments . . . but it certainly has been educational . . . .  I now have a linux LTS version loaded on a partition on each of my computers . . . and I jump on every once in a while and do stuff . . . so far the Xu/Lu flavors have been the most stable . . . able to survive updates w/o blowing up, etc. 

It's good work that you continued to try stuff and got it to work . . . when you get to a "rainy" day, maybe try to run an install on one of the machines . . . prepare for the winding road . . . enjoy the drive.

e.e.p.

Your post is damn near poetic, sir.  I enjoyed reading it.  I'll keep all that in mind, and who knows...maybe I'll find myself back here one day.  :)

---

### Post by este.el.paz on 2014-09-02
> **AFTfunwithU1 said:**
> Your post is damn near poetic, sir.  I enjoyed reading it.  I'll keep all that in mind, and who knows...maybe I'll find myself back here one day.  :)


@AFT:

Thanks again . . . you could always try to PM me through the forum if and when you find your way back here with an issue . . . and responses are slow or non-existent . . . or I'm subscribed to this thread . . . .  I don't always sit on the forum; it's only because I was trying to get some help on my 14.04 upgrade in my iBook that I was paying attention . . . got parts of my iBook thingie straightened out . . . so far not too much feedback here on it . . .  "PPC" is even more niche than "Apple" these days . . . .  Later on . . . .

e.e.p.

---

